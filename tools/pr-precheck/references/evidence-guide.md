# Evidence guide: where evidence lives in a PR package

<!--
THIS IS THE PART YOU WRITE (third week running: the map stays in your
hands). Your tool uses this guide as its map: for every kind of
evidence a rubric check names, this file says WHERE to find it in a PR
package and WHAT GOOD LOOKS LIKE when you do.

The four families below are the harness's failure categories under
the names the eval README uses: plan fidelity = silent-drift, test
evidence = not-tested, diff quality = unreviewable, standards and
comms = standards-wall. A package that fails none of them is a
clear-accept. Under each family heading below, write:

- Where it lives: the exact places to look. In an eval bundle (which
  section of the package: the plan-context block's scope pair and test
  plan, the candidate PR's diff, commits, description, or
  test-evidence section, the repo-facts block's template asks and
  stated policy). In live mode (where in your working copy and on
  GitHub: your plan.md and its deviation notes, your branch's diff,
  your draft title and description, your captured test output, the
  repo's PR template and CONTRIBUTING.md).
- What good looks like: one or two sentences someone else could apply.
  Prefer observable conditions ("every changed file falls inside the
  plan's stated boundary or a deviation note") over adjectives ("the
  diff is clean").

A rubric check whose evidence this guide cannot locate is a check
nobody else can execute, and this week that cuts three ways: your
procedure says WHEN to gather each family, this guide says WHERE, and
your SKILL.md says the tool reads both. Write the map you wish your
executor had.
-->

## Plan fidelity (harness category: silent-drift)
### Where it lives

- Eval mode: Read the plan-context block's scope pair,
  implementation steps, and deviation notes. Compare these
  with the candidate PR's changed files, diff, commits,
  and description.
- Live mode: Read `plan.md`, including its scope and
  deviations. Compare it with `git diff main...HEAD`
  and the PR title and description in `pr_draft.md`.
  Check the related GitHub issue for the intended scope.

### What good looks like

Every substantive change in the diff matches the plan's
scope or is explained in a documented deviation. Planned
work that was not completed is also disclosed.

The PR description accurately describes what the diff
implements. A change added without explanation, omitted
without disclosure, or claimed without implementation
is silent drift.
<!-- Where the plan states its scope, boundary, and deviation notes,
and where the diff shows what actually changed. What it means for a
diff to match the plan, for an honest deviation to re-tie a mismatch,
and what silent drift looks like in each direction (more than the
plan, or less with no note). The description's fidelity claims read
against the diff live here too: a description claiming more or less
than the diff delivers is silent drift, not a comms problem. -->

## Test evidence (harness category: not-tested)
### Where it lives

- Eval mode: Read the plan-context block's test plan,
  reproduction steps, and expected results. Compare them
  with the candidate PR's test-evidence section,
  testing claims, and repo-facts block.

- Live mode: Read the test plan in `plan.md` and the
  results recorded in `test_evidence.md`. Compare them
  with the Testing section of `pr_draft.md`.

- Check the repository's required validation commands,
  including `make test-unit`, `make test-integration`,
  `make lint`, and `make typecheck`, when applicable.

### What good looks like

Test evidence identifies the commands executed, their
actual outcomes, and observable behavior before and
after the fix.

The expected-after behavior matches the plan's test
plan, and the results support the PR's testing claims.

Missing tests, failed checks, or unavailable environments
must be disclosed with their limitations. A statement
such as "tests pass" without supporting results is
not sufficient evidence.

<!-- Where the PR shows its proof: the test-evidence section's
before/after against the plan's test plan and the reproduction's own
steps, and the outcome of the repo's own checks or suite. What
decisive looks like (an observable behavior named, the expected-after
stated, the checks' outcome visible) next to "tests pass". -->

## Diff quality (harness category: unreviewable)
### Where it lives

- Eval mode: Inspect the candidate PR's diff, changed-file
  list, and commits. Compare the changes with the issue
  and the plan-context block.

- Live mode: Run `git diff main...HEAD --stat` to identify
  changed files, then `git diff main...HEAD` to inspect
  the actual code changes.

- Look for unrelated modifications, generated files,
  debug statements, commented-out code, accidental
  secrets, and unnecessarily large changes.

### What good looks like

The diff contains only changes needed to implement the
issue and any clearly documented deviations.

Changed files are organized so a reviewer can understand
the implementation without sorting through unrelated
edits or debugging leftovers.

A diff is unreviewable when unnecessary changes obscure
the intended fix or prevent a reviewer from identifying
what behavior changed.
<!-- Where the change itself lives: the unified diff and the commit
list. What a reviewable change looks like (the fix visible, nothing
unrelated riding along) and the debris tells: debug leftovers, dead
code, commented-out blocks, formatting churn, drive-by edits. -->

## Standards and comms (harness category: standards-wall)
### Where it lives

- Eval mode: Read the candidate PR's title, description,
  and testing claims. Compare them with the repo-facts
  block, including the PR template and stated policies.

- Live mode: Read the title and description in
  `pr_draft.md`. Compare them with
  `.github/PULL_REQUEST_TEMPLATE.md`, `CONTRIBUTING.md`,
  the related GitHub issue, and the committed diff.

- Check required PR sections, issue references,
  testing information, AI-use disclosure, and
  documented deviations.

### What good looks like

The PR title clearly identifies the change, and the
description follows the repository's required template
and contribution guidelines.

The description accurately explains the implementation,
references the correct issue, reports testing outcomes,
and discloses AI assistance when required.

A standards-wall failure occurs when applicable
repository requirements are missing or violated,
even if the implementation itself works.

<!-- Where the repo states its asks (the repo-facts block's PR
template sections, contributing instructions, and stated policy,
including AI-use disclosure) and where the PR honors them: the
stated sections filled with real content, the disclosure present,
explicit maintainer direction in the thread engaged. What compliant
looks like next to boilerplate or a visibly ignored ask. (Whether
the description's claims match the diff is plan fidelity, above.) -->
