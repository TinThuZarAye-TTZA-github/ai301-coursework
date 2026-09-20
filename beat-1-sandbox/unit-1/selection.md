# Unit 1 — Issue Selection

Path: `beat-1-sandbox/unit-1/selection.md`

Record of the issue carried into Unit 2, and of the evaluation runs that produced
`eval-run.txt`. This file is graded at the path above; a copy kept anywhere else in
the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the
wrong label is not graded.

---

## Selected issue

**Issue link**

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/18

**Verdict output**

Summary (live mode, graded 2026-09-20; in-scope: codepath/pathreview-ai301-fa26-s3)

- maintainer-active — pass. Last non-bot default-branch commit 2026-09-16 by Andrew Burke (Aburke225), 4 days ago, well inside 90.
- repo-active — pass. archived: false, last push 2026-09-16T21:50:20Z (4 days), inside 180. No releases exist, but the rule is an OR.
- newcomer-scope — pass. One coherent bug with settled direction (GitHubTool must populate file_structure; two named files; "Estimated effort: 2–4 hours"). Opened by a COLLABORATOR, labeled good first issue / tier-1. Not an umbrella, not a support question, no TBD requirements, no abandoned attempts.
- unclaimed — pass. assignees: [], no linked PRs in the timeline, 0 comments, and the repo has zero PRs open or closed. (Path Review house rule on classmate claims never came into play — there are no claims.)
- contribution-policy — pass. docs/CONTRIBUTING.md (189 lines) and the PR template state no AI policy at all; their requirements are green CI, passing tests, and removing the @pytest.mark.xfail marker — conditions, not a ban.

All five required checks pass → accept. On fit, this one lands squarely in your profile: Python backend work on an agent tool that calls the GitHub REST API, feeding an analyzer in an AI/RAG codebase — backend + APIs + AI/ML at once, with a test fixture to update rather than a UI to design.

{
  "item": "https://github.com/codepath/pathreview-ai301-fa26-s3/issues/18",
  "checks": [
    {"name": "maintainer-active", "grade": "pass",
     "evidence": "Last default-branch commit 2026-09-16 by human Aburke225 ('chore: track five more manifest entries against the tracker'), 4 days before the 2026-09-20 grading date."},
    {"name": "repo-active", "grade": "pass",
     "evidence": "archived: False and pushed_at 2026-09-16T21:50:20Z — 4 days, inside the 180-day window (no releases published)."},
    {"name": "newcomer-scope", "grade": "pass",
     "evidence": "Single bounded bug, COLLABORATOR-authored, labeled 'good first issue'/'tier-1', names 2 files and 'Estimated effort: 2-4 hours'; verified repo_analyzer.py:111-127 reads file_structure while github_tool.py never sets it."},
    {"name": "unclaimed", "grade": "pass",
     "evidence": "assignees: [], 0 comments, timeline shows only label + rename events, and the repo has 0 pull requests in any state."},
    {"name": "contrbution-policy", "grade": "pass",
     "evidence": "docs/CONTRIBUTING.md and .github/PULL_REQUEST_TEMPLATE.md mention no AI/LLM policy; only conditions (green CI, tests, remove xfail marker)."}
  ],
  "verdict": "accept"
}

**The verdict must record `accept` for this issue.** Choose an issue your own skill
accepts. If your skill rejects every candidate you try, that is a signal about your
rubric rather than about the issues: revise it and re-run — retries are unlimited and a
partial re-run costs about $0.20 — or run the skill on different candidates. Output
recording `reject` for the issue you chose earns no credit for this field.

```
paste the output here, including the closing JSON block
```

---

## Eval iterations

Quote source text directly in each field below. Paraphrase does not satisfy them.

**Run history**

[The agreement score of each run you did, in order. A single run is a complete answer if
only one run occurred. **The last score in your list must match the agreement line in the
`eval-run.txt` you committed** — that file is the record of your final run.]

**Issue analysis**

[One scored issue, identified by id (`issue-01` through `issue-20`; the `calib-`
issues are not scored). State your rubric's decision, the gold label, and the
reasoning that produced your rubric's result.]

**Check rationale**

[One check from the `rubric.md` uploaded to `tools/issue-select/`, quoted as it is
currently written, with the reasoning behind its current form.]

**Trade-offs**

[What the quoted check gives up. Any one of these is a complete answer: an issue whose
result it changes, a canary you re-ran with `--only`, a case you accept it will miss, or a
stated reason nothing changed elsewhere. "Nothing changed, and here is how I know" earns
the point in full when the reason follows.]

---

## Selection rationale

Graded on whether all three are answered, in your own words. Not on how good the
reasoning is, and not on length — a short honest answer to each earns the full marks.
This is also the basis for the claim comment you write in Unit 2.

**Selection rationale**

[Answer all three:

1. The issue's fit to your interests and to the time available.
2. What the verdict identified correctly, and what you weighed that the rubric could
   not.
3. The anticipated difficulty in claiming it.]

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/issue-select/`.
