# Rubric: is this pull request ready to submit?

<!--
THIS IS THE PART YOU WRITE (fourth week running; this is the rubric's
final form in the sandbox). Your frame in SKILL.md executes whatever
checks you define here, via your procedure.md. It ships empty on
purpose: the judgment is your work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four
   columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where in the package. Name
     the part (the diff read against the plan's scope, the test
     evidence read against the plan's test plan, the description read
     against the diff, the repo-facts block's template asks) or a
     location from your references/evidence-guide.md. "The PR" is not
     a source; "the diff's changed files read against the plan's
     stated boundary" is.
   - Pass condition: a decision rule about the OUTCOME that someone
     else could apply and get your answer. Judge the thing itself
     (does the diff fall inside the plan plus its deviation notes? is
     the claimed evidence observable?), never the write-up's shape
     (how long the description is, how many commits there are).
     Structure-shaped checks are what make graders disagree with
     themselves.
   - Weight: `required` (a fail here holds the package) or `preferred`
     (never changes the verdict).

2. A verdict rule below the table: how the check grades combine into
   accept (submit) or reject (hold), including how `unclear` is
   treated. The verdict space is binary. State the `unclear`
   treatment explicitly: the frame here is YOUR SKILL.md, so a rubric
   that stays silent is only covered if your frame's grading
   discipline says what happens (the contract's own default is that
   an unverifiable claim fails).

Cover what actually gets bad PRs submitted. The failure families the
lecture named ARE the harness's scoring categories, same names as the
eval README: silent drift (the diff silently does more or less than
the posted plan, or the description claims fidelity the diff
contradicts), not tested (the evidence proves nothing observable, or
the repo's own checks were never run), unreviewable (debris or
unrelated hunks bury the change), and standards wall (the repo's
stated template and disclosure asks are ignored). Your evidence
guide's four headings map onto these one to one (plan fidelity =
silent drift, test evidence = not tested, diff quality =
unreviewable, standards and comms = standards wall), and the category
floor is scored on exactly these names plus clear accept. A rubric
that ignores a category will fail the eval packages built around
that category. And remember the honest-outcome
rule, fourth week running: a PR that honestly discloses a shortfall
can be ready; a rubric that equates "less than everything" with
"hold" fails the set.
-->

## Checks


| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Plan fidelity | Compare the candidate PR diff and description against the plan's scope, implementation steps, deviations, and related issue. | Every substantive change is within the planned scope or explained by an honest deviation. Incomplete planned work is disclosed. The description does not claim behavior the diff lacks. | required |
| Test evidence | Compare the plan's test plan and reproduction steps against the PR's test evidence, reported commands, outcomes, and repository checks. | Evidence supports the claimed behavior with observable results. Missing or failing checks are accurately disclosed, and the PR does not claim unsupported test success. | required |
| Diff quality | Inspect changed files, diff hunks, and commits against the issue's intended scope. | The changes are focused and reviewable, without unrelated edits, accidental files, debugging leftovers, or unnecessary modifications that obscure the fix. | required |
| Standards and communication | Compare the PR title and description against the repository's PR template, contribution requirements, and stated disclosure policies. | All applicable repository requirements are met, including required sections, issue references, and AI-use disclosure where required. | required |
## Verdict rule
Accept the PR package only when every required check
receives a pass grade.

Reject the PR package if any required check receives
a fail or unclear grade.

An unclear grade counts as failing for the final verdict
because the necessary evidence is insufficient.

Preferred checks, if any, provide recommendations but
never change the accept or reject verdict.

An honestly disclosed limitation does not automatically
cause rejection. Evaluate whether the available evidence
satisfies each check's pass condition.

Complete and report every check, even when one required
check already fails.
<!-- State how the grades above combine into accept or reject, and how
unclear is treated. Example shape (write your own): "accept if every
required check passes; preferred checks never change the verdict;
unclear counts as fail." -->
