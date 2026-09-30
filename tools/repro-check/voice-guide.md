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
I'm a professional backend/database developer doing my first open-source contribution as part of a course. I'm investigating this issue, not claiming to have already fixed it — readers should expect a careful, evidence-first account of what I actually tried and found, not a confident sales pitch.

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
### Rule: Name the actual date, day, and time

Whenever I mention time or duration — when I'll follow up, when I ran something, how long a step took — I state the specific date, day of week, and/or time instead of a relative or vague phrase.

- Wrong: "I'll post the repro report in a few days."
- Right: "I'll post the repro report by Friday, October 3rd."

### Rule: Name the thing, not "it," "this," or "that"

Every reference to a file, command, error, or behavior names the specific thing, instead of a pronoun the reader has to trace back through the thread.

- Wrong: "I ran it and it failed the same way."
- Right: "I ran `yq eval --input-format=hcl . input.hcl` and got the same `panic: not a string` in `decoder_hcl.go`."

### Rule: Open with a greeting, close with thanks

Every comment opens with "Hi" (plus a name, when I know one) and closes with a thank-you line — never a comment that just starts with technical content and stops cold at the end.

- Wrong: "Ran the repro, here's the output: [...]"
- Right: "Hi [maintainer], here's the repro: [...] Thank you for taking a look!"

## Things I never post

<!-- A short list. Promises you cannot keep, tones you refuse,
shortcuts you know you reach for when tired. The skill quotes this
list back at you when a draft crosses it. -->
- A promise of a fix, or a date for a fix — I only ever promise investigation and a report, never a resolution.
- A claim of reproduction my own output doesn't actually support — if the behavior doesn't match, I say so plainly instead of writing around it.
- A vague time reference anywhere ("soon," "later," "in a bit") — see Rule 1.
- A comment with no greeting or no thank-you — see Rule 3.

