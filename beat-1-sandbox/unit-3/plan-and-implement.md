# Unit 3 — Plan and Build

Path: `beat-1-sandbox/unit-3/plan-and-implement.md`

Record of your plan, the branch you built it on, and the evaluation runs that produced
`eval-run.txt`. This file is graded at the path above; a copy kept anywhere else in the
repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the wrong
label is not graded.

---

## Posted upstream

**GitHub username**

TinThuZarAye-TTZA-github

**Plan comment**

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/18#issuecomment-5941622374

Hi! I reproduced this issue and traced the data flow from `GitHubTool` to `RepoAnalyzer`.

My reproduction showed that `GitHubTool` succeeds, but its returned metadata does not contain `file_structure`. `RepoAnalyzer` uses that field to detect tests and CI, so `has_tests` and `has_ci` remain `False` even though the repository contains both `tests/` and `.github/workflows`.

My plan is to update the GitHub metadata path so repository file information is provided to the existing analyzer, while keeping the change limited to this data flow. I also plan to add or update tests for the file-structure behavior.

After the change, I will rerun my Unit 2 reproduction and expect `file_structure` to be present and both `has_tests` and `has_ci` to be `True` for the Path Review repository.

One implementation detail I still need to verify is the appropriate GitHub API approach for retrieving the repository file information within the project's existing conventions.

---

## Your branch

**Branch**

fix/18-repo-file-structure

**Evidence**

### Before

Command:

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

Output:

```text
GitHubTool success: True
file_structure present: False
has_tests: False
has_ci: False
```

### After

Command:

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

Output:

```text
2026-10-01 15:18:50 [info] github_repo_fetched language=Python repo=pathreview-ai301-fa26-s3 stars=6 username=codepath
GitHubTool success: True
file_structure present: True
has_tests: True
has_ci: True
```

## Eval iterations

**Run history**

20/20 scored items

**Package analysis**

`pkg-15` was categorized as `scope-creep`. My rubric decided `reject`, and the gold label was also `reject`. The package identified a specific root cause: the bundled runtime's 250 ms `autoSelectFamilyAttemptTimeout` was causing the connection failures. However, the proposed plan went beyond the direct fix by also proposing to “replace `node-fetch` with `undici`,” add a new timeout setting, change the sync error UI, and add retry-with-backoff. My `bounded-scope` check rejected this because these additional changes expanded the work beyond the reproduced timeout issue.

**Check rationale**

`test-plan` — Evidence: “The plan's test steps and expected results read against the reproduction evidence” — Pass condition: “Pass if the tests exercise the relevant behavior and define observable results that would demonstrate whether the reproduced problem is fixed without hiding regressions.” — Weight: `required`.

I revised this check to require a test plan with observable results instead of simply saying to run tests. For my issue, the plan reruns the Unit 2 reproduction and compares `file_structure`, `has_tests`, and `has_ci` before and after the fix. I also included relevant regression testing so the plan can show that the reproduced problem is fixed without hiding regressions.

**Trade-offs**

The `bounded-scope` check can reject a plan even when some of its additional changes could be useful, because it prioritizes keeping the implementation focused on the reproduced issue. For example, `pkg-15` proposed useful related work such as replacing `node-fetch` with `undici`, adding a timeout setting, improving sync error reporting, and adding retry-with-backoff, but those changes expanded beyond the direct timeout fix. I accepted this trade-off because the purpose of the check is to prevent unnecessary scope expansion. In the final evaluation, the rubric rejected all four `scope-creep` packages, and the overall agreement was `20/20 scored items`.
