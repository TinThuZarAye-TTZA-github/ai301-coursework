# Rubric: is this a good first issue?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever checks
you define here. It ships empty on purpose: the judgment is your work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where. Name the source
     (repo-facts block, issue body, comment thread, or the locations in
     references/evidence-guide.md). "The repo" is not a source; "the last
     5 default-branch commit dates" is.
   - Pass condition: a condition someone else could apply and get your
     answer. Prefer thresholds with numbers ("a maintainer commented
     within 30 days") over adjectives ("maintainer is responsive").
   - Weight: `required` (a fail here rejects the issue) or `preferred`
     (never changes the verdict; a nice-to-have that helps rank the
     issues you accept).

2. A verdict rule below the table: how the check grades combine into
   accept or reject, including how `unclear` is treated. The verdict
   space is binary. If you write no rule for `unclear`, the skill treats
   it as fail.

Cover what actually kills first contributions. The lecture named four
families: the maintainer is alive, the repo is in use, the scope fits a
newcomer, and nobody else is already on it. A rubric that ignores a family
will fail eval issues designed around that family.
-->

## Checks

| Check              | Evidence                                                                                              | Pass condition                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | Weight   |
| ------------------ | ----------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- |
| maintainer-active  | Repo facts: last 5 default-branch commits and maintainer first-response sample                        | Pass if at least one non-bot default-branch commit occured within 90 days of the capture data OR a maintainer responseded to a sampled issue within 30 days                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | required |
| repo-active        | Repo facts: archived flag, latest release and last push to any branch                                 | Pass if the reposity is not archived and either the latest release or last push occoured within 180 days of the capture data                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        | required |
| newcomer-scope     | Issue body and Comments section                                                                       | Pass if the issue describes one coherent task or bug with enough settle direction to begin implementaion. A long description, multiple files, a checklist, multiple suggested fixes, or a terse description do not by themselves make an issue unbounded. A. maintainer/collaborator-authored issue or good-fit-issue label can support that the scope is suitable when tere is no contrary evidence. Fail if the issue is explicitly an umberlla or tracking issue (a list of sub-items meant to be split into separate work) intended to be split into separate work, a pure support question, an unresolved design/priduct decision with key requirement stil TBD, work a maintainer says requires core internals or the history shows repeated abandoned implementation/PR attmepts suggesting hidden dificulty | required |
| unclaimed          | Repo facts: issue assigness and linked PR states; Comments section for active claims or mentioned PRs | Pass if the issue has no assignee and no active open PR indicating that someone is already implementing it                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          | required |
| contrbution-policy | Repo facts: contribution-policy                                                                       | Pass unless the repository explicitly bans AI-assisted contributions. Conditional requirements such as disclosure, testing, understanding, or human review pass. No stated AI policy also passes                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | required |

## Verdict rule

Accept if every required check passes. Reject if any required check fails. An unclear result on a required check counts as fail.
