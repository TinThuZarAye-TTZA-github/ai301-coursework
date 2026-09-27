# Unit 2 — Claim and Reproduce

Path: `beat-1-sandbox/unit-2/reproduction.md`

Record of your claim and reproduction on the issue you chose in Unit 1, and of the
evaluation runs that produced `eval-run.txt`. This file is graded at the path above; a copy
kept anywhere else in the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the wrong
label is not graded.

---

## Your identity upstream

TinThuZarAye-TTZA-github

---

## Posted upstream

**Claim comment**

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/18#issuecomment-5859073758

Hi! I'd like to investigate this issue.

I plan to reproduce the behavior where the repo analyzer does not receive the file list and has_tests and has_ci remain False. I will look at how the file list is passed between GitHubTool and the repo analyzer and report my reproduction results here before making any changes.

**Reproduction comment**

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/18#issuecomment-5859650437

\*\*Reproduction Report
Environment
macOS on Apple Silicon (arm64)
Python 3.14.7
PathReview project virtual environment (.venv)
httpx 0.28.1
Repository: codepath/pathreview-ai301-fa26-s3
Steps to Reproduce
From the PathReview repository, I ran the following command using the project's virtual environment:

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
PY\*\*

Observed Result

GitHubTool success: True
file_structure present: False
has_tests: False
has_ci: False

## Eval iterations

Answer all four sections. Quote source text directly; paraphrase does not satisfy these
fields.

**Run history**

Run 1: 17/20 — below the 18/20 bar. Category results were: clear-accept 6/8, disclosure 0/1, no-evidence 4/4, unfollowable-comms 3/3, wrong-target 4/4.
Run 2: 18/20 — PASS. Category results were: clear-accept 7/8, disclosure 1/1, no-evidence 4/4, unfollowable-comms 2/3, wrong-target 4/4.

**Package analysis**

I analyzed pkg-20. On my first evaluation run, my rubric decided accept, while the gold label was reject.
My rubric accepted the package because my original repo-conventions check was not specific enough about required AI-use disclosure. The package was from a repository with an AI disclosure requirement, but the candidate did not provide the required disclosure. Because my check did not clearly require this evidence, the package incorrectly passed.
I revised the repo-conventions check so that when a repository requires AI-use disclosure, the claim comment or reproduction report must include the required disclosure, including the tool and extent of assistance when the policy asks for them. After this revision, pkg-20 correctly changed from accept to reject.

**Check rationale**
My final repo-conventions check:
repo-conventions — Evidence: Claim comment and repro report read against the repository's contribution guidelines, templates, and stated AI/disclosure policies. Pass if the comments follow the repository's stated contribution requirements. If the repository requires AI-use disclosure, the claim comment or repro report must include the required disclosure, including the tool and extent of assistance when the policy asks for them. If required disclosure is missing, fail. If no relevant convention is stated, pass.

I revised this check after the first evaluation run because pkg-20 showed that my rubric could accept a reproduction package even when it did not follow the repository's AI disclosure policy. I wanted the check to distinguish between repositories that require disclosure and repositories that do not. If no relevant convention is stated, the package can still pass this check.

**Trade-offs**
Strengthening repo-conventions changed the result for pkg-20 from accept on my first run to reject on my second run, which matched the gold label. This improved the disclosure category from 0/1 to 1/1.
The trade-off is that this check depends on the repository's stated contribution policies being available and clear. It does not automatically reject a package just because it does not mention AI use. If the repository has no relevant AI disclosure requirement, the check passes. This avoids requiring disclosures that the repository itself does not require.

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/repro-check/`.
