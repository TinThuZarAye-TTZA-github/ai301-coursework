# Unit 4 — Test and Submit

Path: `beat-1-sandbox/unit-4/pull-request.md`

Record of the pull request you opened against the Path Review repo, and of the evaluation
runs that produced `eval-run.txt`. This file is graded at the path above; a copy kept
anywhere else in the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the wrong
label is not graded.

---

## Your pull request

**Pull request**

https://github.com/codepath/pathreview-ai301-fa26-s3/pull/155

[Link to the pull request you opened. It must be the pull request's own page on the Path
Review repo, not your fork's branch page.]

**Branch**

fix/18-repo-file-structure

[The name of the branch the pull request comes from, exactly as it appears in your fork.
The naming shape is a type prefix, then the issue number, then a short description. **The
issue number in the branch name must be the number of the issue the pull request fixes** —
a name carrying any other number does not satisfy this field.]

## Eval iterations

Answer all four sections. Quote source text directly; paraphrase does not satisfy these
fields.

**Run history**
# Unit 4 — PR Precheck Skill

## Run History

I built the `pr-precheck` Claude skill to evaluate whether a pull request is ready for submission. The skill checks plan fidelity, test evidence, diff quality, and repository standards.

I first tested the skill using the `calib-01` calibration package. The skill correctly returned `accept`, matching the expected verdict.

I then ran the full evaluation against 20 packages using Claude Sonnet. The skill achieved 20/20 agreement (100%), exceeding the required passing score of 18/20.

Category results:
- Clear accept: 7/7
- Silent drift: 4/4
- Not tested: 4/4
- Unreviewable: 3/3
- Standards wall: 2/2

The complete evaluation results are saved in `eval-run.txt`.
[The agreement score of each run you did, in order. A single run is a complete answer if
only one run occurred. **The last score in your list must match the agreement line in the
`eval-run.txt` you committed** — that file is the record of your final run.]
Evaluation history:
1. Calibration test (`calib-01`): accept — matched the gold label. Not scored.
2. Full evaluation: 20/20 agreement — PASS (required: 18/20).

The final scored evaluation achieved 20/20 agreement,
matching the result saved in eval-run.txt.
**Package analysis**
## Package Analysis

The evaluation included 20 PR packages across five categories.

- Clear accept (7/7): The skill correctly accepted PR packages that met all required checks.
- Silent drift (4/4): The skill correctly rejected PR packages with changes that did not match the approved plan.
- Not tested (4/4): The skill correctly rejected PR packages with insufficient test evidence.
- Unreviewable (3/3): The skill correctly rejected PR packages with changes that were difficult to review or included unrelated modifications.
- Standards wall (2/2): The skill correctly rejected PR packages that did not meet repository contribution requirements.

All 20 verdicts matched the expected results. The evaluation showed that the skill could distinguish submission-ready PRs from PRs with problems in implementation, testing, reviewability, or documentation.
For example, pkg-03 belongs to the silent-drift category.
The gold label was `reject`, and my rubric also returned `reject`.
This matched the expected result because the plan fidelity check
requires the implemented changes to remain within the planned
scope or to disclose any deviations. A PR with undisclosed
scope changes should not be accepted.
[Pick one scored package (`pkg-01` through `pkg-20` — the four `calib-` packages are never
scored). Name it by id, say what your rubric decided and what the gold label said, and
explain why your rubric read it that way.]

**Check rationale**

## Check Rationale

I designed four required checks for the `pr-precheck` skill.

1. **Plan fidelity:** Confirms that the implemented changes match the approved plan and that any deviations are disclosed. This prevents silent changes in scope.

2. **Test evidence:** Verifies that the PR provides evidence supporting its claims, including test commands, results, and known limitations. This prevents untested changes from being presented as verified.

3. **Diff quality:** Examines whether the committed changes are focused, understandable, and free from unrelated modifications or debugging artifacts. This makes the PR easier to review.

4. **Standards and communication:** Checks whether the PR follows repository contribution requirements, including the PR template, issue references, and AI-use disclosure when required.

I made all four checks required because a PR should not be accepted if it fails any one of these essential submission-readiness criteria.

[Quote one check from the `rubric.md` you uploaded to `tools/pr-precheck/`, exactly as it reads now.
Then say why it reads that way — what you revised to get there, or what you rejected in
favour of it.]
I chose the following required check from my rubric.md:

> Plan fidelity | Compare the candidate PR diff and description against the plan's scope, implementation steps, deviations, and related issue. | Every substantive change is within the planned scope or explained by an honest deviation. Incomplete planned work is disclosed. The description does not claim behavior the diff lacks. | required

I chose this wording because checking whether a PR follows the plan is not enough by itself. The check also needs to detect undisclosed scope changes, incomplete planned work, and descriptions that claim functionality the code does not implement. I kept this check required because these issues can make a PR misleading even when its tests pass.
**Trade-offs**

## Trade-offs

I chose a strict evaluation approach that rejects a PR when any required check fails or has insufficient evidence. This reduces the risk of approving incomplete or misleading PRs, but it may also reject PRs that are correct but poorly documented.

I separated the skill into SKILL.md, rubric.md, procedure.md, and evidence-guide.md. This makes the evaluation criteria easier to maintain and understand, although it requires the skill to read multiple files.

I also designed the skill to distinguish between an honestly disclosed limitation and an unsupported claim. A disclosed limitation does not automatically mean rejection, but the PR must provide enough evidence to justify its readiness.

The evaluation achieved 20/20 agreement, but this result only demonstrates performance on the provided evaluation packages. Real-world pull requests may contain additional scenarios that require further testing.
One trade-off is that my rubric treats unclear evidence as a failed required check. This may reject a PR that is technically correct but lacks sufficient documentation.

I accepted this trade-off because the purpose of pr-precheck is to determine submission readiness, not just code correctness.

I did not change the rubric after the full evaluation because all 20 scored packages matched their gold labels, including every failure category. However, this does not guarantee that the rubric will handle every real-world PR correctly.
[Every check gives something up. Any one of these is a complete answer: a package whose
result it changes, a canary you re-ran with `--only`, a case you accept it will miss, or a
stated reason nothing changed elsewhere. "Nothing changed, and here is how I know" earns
the point in full when the reason follows.]

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/pr-precheck/`.
