# Voice guide: how I talk upstream

<!--
THIS IS THE PART YOU WRITE (new this week). Live mode reads this file
before any comment of yours goes out the door; eval mode ignores it
entirely, because your voice is yours and carries no gold labels.

This is not etiquette. "Be polite and concise" is advice for everyone
and therefore rules for no one. Write rules YOU need, in your own
words, each one concrete enough that the skill can hold a draft
against it and say which rule it breaks.

Three sections. Fill all three.
-->

## Who I am in threads

<!-- 2-3 lines. Who is talking when you comment on an issue: your
experience level stated plainly, what you are doing in this repo, what
readers can expect from you. This is the register your rules protect. -->

I am a student learning open-source contribution and AI engineering.
I am working on this repository to understand issues, reproduce bugs, and contribute where I can. I will be clear about what I have tested and what I still need to investigates.

## Rules I write by

<!-- 3-5 rules, drafted from the lecture's slide-12 moment. Each rule
needs a wrong/right pair from your own hand: one line you might
actually have written that breaks the rule, and the line you would
post instead. The pair is what makes a rule executable; a rule without
one is a wish.

Format each rule like this:

### Rule: <short name>

<The rule, one or two sentences.>

- Wrong: "<a line that breaks it>"
- Right: "<the line to post instead>"

-->

## Rule: Say only what I know

I will describe what I actually tested or observed and will not claim something is confirmed when I am not sure

- Wrong: "I confirmed this is the exact cause of the bug."
- Right: "I reproduced the report behavior and I am investigating the cause"

## Rule: Do not promise a fix

When I claim an issue, I will say what I plan to investigate instead of promising that I will fix it

- Wrong: "I will fix this issue and submit a PR by tomorrow"
- Right: "I would like to investigate this issue and wil share my reproduction results"

## Rule: Be specific to the issue

My commnents should mention what I am investigating instead of using a generic claim message.

- Wrong: "Hi, I would like to work on this issue"
- Right: "I would like to investigate why the repo analyzer is not receiving the file list and why has_tests and has_ci remain false"

## Rule: Separate results from assumptions

I will clearly separate what my test showed from what I think might be causing the problem

- Wrong: "The GitHub API is causing this problem"
- Right: "I reproduced the behavior, I will investigate whether the file-list data is being passed corretly

## Rule: Follw the repository's requirement

Before posting, I will check the repository's contribution instructions
and follow any requirements that apply to my comment.

- Wrong: "I don't need to check the contribution guidelines for a comment."
- Right: "I checked the repository's contribution guidance before posting my results."

## Things I never post

- A promise that I will definitely fix an issue.
- A deadline that I cannot guarantee.
- A claim that I reproduced something when my evidence shows a different behavior.
- A guess presented as if it were a confirmed fact.
- A generic comment that does not show what I plan to investigate.

<!-- A short list. Promises you cannot keep, tones you refuse,
shortcuts you know you reach for when tired. The skill quotes this
list back at you when a draft crosses it. -->
