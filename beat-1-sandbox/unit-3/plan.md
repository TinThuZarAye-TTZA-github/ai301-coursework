# Plan for Issue #18

## Diagnosis

My Unit 2 reproduction confirmed that `GitHubTool` successfully fetches repository metadata, but the returned data does not contain a `file_structure` field.

The reproduction produced:

```text
GitHubTool success: True
file_structure present: False
has_tests: False
has_ci: False
```

The repository used for the reproduction actually contains both a `tests` directory and `.github/workflows`, so the `False` values do not match the repository contents.

After tracing the code, `GitHubTool._fetch_repo_metadata()` returns repository metadata but does not collect or return a file list. `RepoAnalyzer._detect_tests()` and `RepoAnalyzer._detect_ci()` both depend on `file_structure`. When that field is missing, they inspect an empty string and return `False`.

`IngestionPipeline.ingest_repo_metadata()` passes `repo_data` directly to `RepoAnalyzer.parse()` without adding file-structure information.

Therefore, the reproduced failure occurs because the analyzer expects file-structure information that the GitHub metadata path does not currently provide.

## Scope

In scope:

- Provide repository file-structure information to the analyzer through the GitHub metadata path.
- Keep the existing `RepoAnalyzer` detection logic working from the `file_structure` field.
- Add or update tests to verify that repositories containing test files/directories and CI configuration are detected correctly.

Not in scope:

- Rewriting the repository analyzer.
- Changing unrelated ingestion behavior.
- Changing the database or embedding pipeline.
- Refactoring unrelated GitHub metadata fields.

## Files / Areas

I expect the main implementation change to be in:

- `agent/tools/github_tool.py` — collect repository file information and include it in the metadata passed downstream.
- Relevant tests for `GitHubTool` and/or repository analysis — verify that the file structure reaches the analyzer and produces the expected `has_tests` and `has_ci` values.

I do not expect `ingestion/pipeline.py` to require a behavioral change because it already passes the repository metadata dictionary to `RepoAnalyzer`.

I also do not currently expect the detection methods in `ingestion/parsers/repo_analyzer.py` to require a behavioral change because they already inspect `file_structure`. I will only change these areas if implementation or testing reveals that the existing format assumptions need a small compatibility adjustment.

## Approach

1. Inspect the existing GitHub API interaction and tests to determine the repository file-list representation that fits the current code and test conventions.
2. Extend `GitHubTool` to retrieve repository file information and add it to the returned metadata as `file_structure`.
3. Preserve the existing metadata fields and error-handling behavior.
4. Pass the resulting metadata through the existing ingestion path without adding unrelated pipeline logic.
5. Add or update automated tests to verify that file-structure information is included and that test and CI indicators can be detected from it.
6. Run the relevant existing tests to check for regressions.

## Test Plan

First, rerun the Unit 2 reproduction command against the change:

```bash
.venv/bin/python - <<'PY'
from agent.tools.github_tool import GitHubTool
from ingestion.parsers.repo_analyzer import RepoAnalyzer

tool = GitHubTool()

result = tool.execute({
    "github_username": "codepath",
    "repo_name": "pathreview-ai301-fa26-s3"
})

print("GitHubTool success:", result.success)
print("file_structure present:", "file_structure" in result.data)

analysis = RepoAnalyzer().parse(result.data)

print("has_tests:", analysis.metadata["has_tests"])
print("has_ci:", analysis.metadata["has_ci"])
PY
```

Before the fix, the observed result was:

```text
GitHubTool success: True
file_structure present: False
has_tests: False
has_ci: False
```

After the fix, for this repository I expect:

```text
GitHubTool success: True
file_structure present: True
has_tests: True
has_ci: True
```

I will also run the relevant automated tests for `GitHubTool` and `RepoAnalyzer`. The tests should verify that repositories with recognizable test and CI paths are detected correctly and that the existing repository metadata behavior continues to work. Because `file_structure` is also used by tech-stack detection, I will include this behavior in the relevant new or updated tests as a regression check.

## Risks and Unknowns

The exact GitHub API endpoint and representation to use for the repository file list still need to be confirmed against the existing project conventions before implementation.

Repository trees may also be large or require handling API limitations, so I will keep the implementation limited to the file information needed by the existing analyzer rather than assuming that every repository can be fetched in the same way.

Because `file_structure` is also used by tech-stack detection, providing this field may affect metadata beyond `has_tests` and `has_ci`. I will avoid expanding the issue into unrelated tech-stack changes unless testing shows that a small compatibility change is necessary.

## Deviations

Implementation followed the posted plan. I added repository file-tree retrieval to `GitHubTool` and a focused unit test. No scope changes were needed.
