# Evidence guide: where proof lives in a reproduction package

<!--
THIS IS THE PART YOU WRITE (new this week: Unit 1 handed you this file
finished; the scaffolding fades). The skill uses this guide as its map:
for every kind of proof a rubric check names, this file says WHERE to
find it in a package and WHAT GOOD LOOKS LIKE when you do.

Under each family heading below, write:

- Where it lives: the exact places to look. In an eval bundle (which
  section of the package: the issue context, the repo-facts block, the
  claim comment, the repro report and its parts). In live mode (where
  on GitHub or in the draft: the issue thread, the repo's docs, the
  student's draft comment).
- What good looks like: one or two sentences someone else could apply.
  Prefer observable conditions ("the versions named match what the
  issue targets, or the difference is called out") over adjectives
  ("environment is thorough").

A rubric check whose evidence this guide cannot locate is a check
nobody else can execute; the rubric swap showed you what that feels
like. Write the map you wish your grader had.
-->

## Environment

<!-- Where the environment record lives, and what a sufficient one
looks like against the issue's stated target. -->

Where it lives:
In eval mode, look at the original issue context and the environment section of the candidate repro report. In live mode, compare the original GitHub issue with the environment information in the student's draft repro comment.

What good looks like:
The report states the software version and relevent system/environment information used for testing. The environment should match the issue's target when possible, or clearly explain any important differences.

## Steps

<!-- Where the reproduction steps live, and what makes them followable
by a stranger, starting state to trigger. -->

Where it lives:
In eval mode, look at the commands, inputs, setup and execution steps in the repro report and compare them with the original issue. In live mode, compare the GitHut issue's reproduction information with the student's draft repro comment.
What good look like:
The commands, input and setup are complete enough for another person to follow from the starting state and attempt to trigger the same behavior. Important inputs or commands from the original issue should not be changed without explanation.

## Behavior shown

<!-- Where the artifacts live (output excerpts, logs, screenshots),
and what it means for an artifact to show the issue's behavior rather
than an adjacent one. -->

What it lives:
In eval mode, look at output excerpts, error messages, logs, screenshots, or other artifacts in the repro report and compare them with the behavior described in the original issue. In live mode, compare the evidence in the student's draft with the GitHub issue.
What good look like:
The evidence shows the same behavior described by the original issue. A different error or related failure does not prove that the original bug was reproduced.

## Honesty

<!-- Where claims and their backing meet: how to tell a report that
says exactly what happened (including an honest cannot-reproduce) from
one that claims more than its evidence shows. -->

What is lives:
Compare the conclusion in the repro report with the commands, outputs, logs, screenshots, and other evidence shown in the package

What good looks like:
The conclusion says what the evidence actually demostrates, If the issue cannot be reproduced, clearly reporting that result with supporting evidence is acceptable. The report should not claim successful reproduction when the evidence shows a different result

## Comms

<!-- Where the words meet the repo: the claim comment against the
issue, the comments against the repo's stated templates and
contribution policy (including AI-use disclosure requirements), and
what specific-and-honest looks like next to boilerplate. -->

Where it lives:
In eval mode, compare the claim comment and repro report with the issue
context, repo-facts block, contribution guidelines, templates, and any
stated AI-use policy. In live mode, check the GitHub issue, repository
contribution documentation, and the student's draft comments.

What good looks like:
The comments are specific to the issue, accurately describe what the
student did or plans to do, and follow the repository's stated contribution
requirements. If the repository requires disclosure of AI assistance, the
comment includes that disclosure.
