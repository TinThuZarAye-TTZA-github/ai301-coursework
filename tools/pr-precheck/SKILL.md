---
name: pr-precheck
description: Grade a PR package (a candidate pull request read against the plan it claims to implement and the issue that plan belongs to) and decide whether it is ready to submit. Use when checking your own branch, draft PR title, and description before opening the pull request, or when grading an eval package bundle.
---

# pr-precheck: rubric-driven PR grading

<!--
THIS IS THE PART YOU WRITE, and it is the last one: the frame itself.
Weeks 1 through 3 handed you a working SKILL.md and you filled the
files behind it; this week the frame ships as headings, and you write
what it says. The frontmatter above and the section headings below are
fixed (CONTRACT.md's layout rule); the instructions under each heading
are yours. Write instructions to the tool, in the imperative, the way
weeks 1-3's frames spoke to you: what to read, in what order, what to
refuse, what to emit. Your executor in the rotation is the test: a
frame gap they hit (cannot tell what the tool reads, or how a verdict
gets assembled) is a missing sentence here.

One section is not yours: the JSON schema in "Verdict and output" is
reproduced from CONTRACT.md verbatim and may not be altered. Your
words decide everything around it.
-->

## The question
Decide whether a candidate pull request is ready to submit.

Grade the PR package against the related issue, implementation
plan, documented deviations, repository requirements, and
available test evidence.

A PR package includes the proposed PR title and description,
committed branch diff, implementation plan, test evidence,
and relevant issue context.

Evaluate whether the implementation follows the plan,
the testing claims are supported, the diff is reviewable,
and the PR meets repository standards.

Do not grade the implementation plan alone. Grade the
actual proposed pull request and its supporting evidence.
<!-- State, in your words, the one question this tool answers and what
a PR package is: what artifacts it contains and what they are read
against. CONTRACT.md fixes the question; your frame has to say it so
the tool cannot wander into grading something else. -->

## Inputs and modes
Decide whether a candidate pull request is ready to submit.

Grade the PR package against the related issue, implementation
plan, documented deviations, repository requirements, and
available test evidence.

A PR package includes the proposed PR title and description,
committed branch diff, implementation plan, test evidence,
and relevant issue context.

Evaluate whether the implementation follows the plan,
the testing claims are supported, the diff is reviewable,
and the PR meets repository standards.

Do not grade the implementation plan alone. Grade the
actual proposed pull request and its supporting evidence.
<!-- Define both modes. Live mode: name every input (your plan.md with
its deviation notes, your branch's diff, your draft PR title and
description, your test evidence, your issue), where each comes from,
and what a house-chain student reads instead. The branch's diff is
everything the branch changes relative to the repo's default branch:
`git diff main...HEAD` (three dots), run from the working copy, is
the command that produces it; name the source that concretely. Eval
mode: state that the bundle is the whole world, nothing is fetched,
and every check runs with the full verdict rule. -->

## The scope seam (live mode only)

In live mode, read scope.md before grading the PR.

1. Identify the allowed repository and any scope
   restrictions defined in scope.md.

2. Verify that the current repository matches the
   allowed repository.

3. If the repository does not match, refuse to grade
   and explain the scope mismatch.

4. If the repository field still contains an unfilled
   placeholder, refuse to grade until it is configured.

5. Apply all scope restrictions before collecting
   PR evidence.

6. In eval mode, ignore scope.md entirely.
   Grade only the supplied evaluation package.


<!-- Tell the tool when to read scope.md, what to do with the rules it
finds there, what to refuse, and what to do when the scope's repo line
is an unfilled placeholder. State that eval mode ignores scope.md
entirely. CONTRACT.md names the required behavior; your frame has to
instruct it. -->

## The voice seam (live mode only)

In live mode, read voice-guide.md before evaluating
the proposed PR title and description.

1. Apply the voice guide's writing rules to the
   title and description in pr_draft.md.

2. Identify specific violations and explain
   which rule was broken.

3. Suggest a corrected title or description
   when useful.

4. Report voice violations in the human-readable
   feedback.

5. Do not reject a PR solely because of a voice
   violation unless an applicable rubric check
   explicitly makes that requirement decisive.

6. In eval mode, ignore voice-guide.md entirely.
   Do not apply its writing rules to eval packages.
<!-- Tell the tool when to read voice-guide.md, which outgoing text it
gates (the PR title and description), how to report a broken rule, and
why it never changes the verdict on its own. State that eval mode
ignores it entirely. -->

## Component reads

Before grading a PR package, read the following components:

1. Read rubric.md to identify all grading checks,
   pass conditions, check weights, and the verdict rule.

2. Read references/evidence-guide.md to locate
   the evidence required for each rubric check.

3. Read procedure.md and execute its four stages
   in order:
   - Read order
   - Evidence gathering
   - Check execution
   - Verdict assembly

4. Use the rubric to decide what qualifies as
   pass, fail, or unclear.

5. Use the procedure to determine how to gather
   evidence, execute checks, and assemble the verdict.

6. If rubric.md or procedure.md contains no
   substantive instructions, refuse to grade
   the PR package and explain what is missing.

7. If the procedure does not explain a required
   step, report the gap. Do not invent a new
   grading procedure or silently skip the step.

8. Complete every required rubric check before
   producing the final verdict.

<!-- Tell the tool how the pieces connect: rubric.md defines the
checks and the verdict rule, references/evidence-guide.md maps where
each evidence family lives, procedure.md is executed as written. Say
what the tool does when the procedure is silent on a step (report the
gap, never improvise around it) and what it does when rubric.md or
procedure.md has no content (the refusal rule, stated as an
instruction). -->

## Verdict and output
Produce a binary verdict for every PR package:

- accept: The PR is ready to submit because all required
  rubric checks pass.
- reject: The PR should be held because at least one
  required check fails or is unclear.

Provide a concise human-readable explanation of the
verdict, including the deciding evidence and any
important issues that need correction.

Report every rubric check with its grade and supporting
evidence.

End the response with the exact fenced JSON schema
provided below. Populate the item, checks, grades,
evidence, and verdict using the review results.

The JSON must be valid and must be the final content
in the response. Do not write anything after it.
<!-- State the binary verdict space (accept means submit, reject means
hold) and instruct the tool to end its reply with the fenced JSON
block below, valid and last, with nothing after it. The schema is
CONTRACT.md's, verbatim; do not edit it. -->

```json
{
  "item": "<PR URL or bundle id>",
  "checks": [
    {"name": "<check name>", "grade": "pass|fail|unclear",
     "evidence": "<one line: the fact or quote that decided it>"}
  ],
  "verdict": "accept|reject"
}
```

## Grading discipline

1. Grade evidence, not assumptions. Use facts from the
   PR package to support every check.

2. Grade the actual implementation and its supporting
   evidence, not how polished the PR description sounds.

3. Apply the checks and verdict rule defined in
   rubric.md. Do not invent additional requirements.

4. Follow procedure.md to determine the reading order,
   evidence gathering, check execution, and verdict.

5. Assign pass only when the evidence satisfies the
   rubric's pass condition.

6. Assign fail when the evidence contradicts the
   rubric's pass condition.

7. Assign unclear when necessary evidence is missing
   or insufficient to determine whether a check passes.

8. If the rubric does not specify how unclear affects
   the verdict, treat unclear as failing for required
   checks.

9. Distinguish honestly disclosed limitations from
   unsupported claims. Apply the rubric consistently.

10. Complete every check, even if an earlier check
    already establishes a reject verdict.

11. Never invent test results, implementation details,
    deviations, or repository requirements.

<!-- Write the standing rules the tool grades under: evidence first,
grade the thing not the polish, the rubric decides, the procedure
decides how, and how unclear grades are treated when the rubric's
verdict rule is silent. CONTRACT.md states each as a guarantee; your
frame has to make them instructions. -->
