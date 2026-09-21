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

---

## Eval iterations

Quote source text directly in each field below. Paraphrase does not satisfy them.

**Run history**

Run 1 : 15/20  
Run 2 : 19/20

**Issue analysis**

issue-19
My rubric's decision: reject
Gold label: accept
My rubric rejected issue-19 because the "newcomer-scope" check failed. The issue described one bug but also included multiple possible causes and additional suggestions. My rubric interpreted this as not having enough settled direction to begin implementation, so the required "newcomer-scope" check failed. Because my verdict rule required check to pass, the final decision was reject.

**Check rationale**

| newcomer-scope | Issue body and Comments section | Pass if the issue describes one coherent task or bug with enough settle direction to begin implementaion. A long description, multiple files, a checklist, multiple suggested fixes, or a terse description do not by themselves make an issue unbounded. A. maintainer/collaborator-authored issue or good-fit-issue label can support that the scope is suitable when tere is no contrary evidence. Fail if the issue is explicitly an umberlla or tracking issue (a list of sub-items meant to be split into separate work) intended to be split into separate work, a pure support question, an unresolved design/priduct decision with key requirement stil TBD, work a maintainer says requires core internals or the history shows repeated abandoned implementation/PR attmepts suggesting hidden dificulty | required |

I choose newcomer-scope check because I wanted to make sure an issue is clear and manageable for newcomer. After my first evaluation, I learned that a long description, multiple files or multiple suggested fixes do not necessarily make an issue too difficult. I also learned that unresolved requirements or repeated abandoned attempts can be signs of hidden difficulty. I updated this check to consider both of these situations. 

**Trade-offs**

The change to my `newcomer-scope` check changed issue-15 from `accept` in my first run to `reject` in my final run. I added repeated abandoned implementation or PR attempts as a sign of hidden difficulty. This helped my rubric correctly reject issue-15, but the trade-off is that it could also reject an issue that had previous unsuccessful attempts but is still manageable for a newcomer.

---

## Selection rationale

Graded on whether all three are answered, in your own words. Not on how good the
reasoning is, and not on length — a short honest answer to each earns the full marks.
This is also the basis for the claim comment you write in Unit 2.

**Selection rationale**


1. The issue's fit to your interests and to the time available?
This issue fits my interests because it involves Python, debugging, GitHub APIs, and an AI agent. I have experience with Python, APIs, and AI projects, so I am interested in learning more about how these parts work together. The scope of the issue also seems manageable with the time I have available.
2. What the verdict identified correctly, and what you weighed that the rubric could
   not.
The verdict correctly identified that the issue is a good-first issue, currently unclaimed, and matches my technical background. The rubric could not fully consider what I personally want to learn, so I also considered my interest in gaining more experience with AI agents and backend API develo
3. The anticipated difficulty in claiming it.
 I think the issue should be fairly easy to claim because the issue is currently unclaimed and there are no linked pull requests. However, another student may choose the same issue, so I will follow the claiming process in Unit 2.


---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/issue-select/`.
