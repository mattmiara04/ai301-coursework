# Voice guide: how I talk upstream

## Who I am in threads

I am a student contributor learning to work in an existing open-source codebase. When I comment on an issue, I am investigating and reproducing the reported behavior before attempting a fix. Readers can expect me to be specific about what I tested, what I observed, and what I have not confirmed yet.

## Rules I write by

### Rule: Do not claim results before testing

Before reproducing an issue, I describe what I plan to investigate instead of acting like I already know the cause or result.

- Wrong: "I found the bug and I'll fix the phone-number regex."
- Right: "I'd like to reproduce this issue and check how the PII scrubber handles parenthesized US phone numbers."

### Rule: Say exactly what I observed

I describe the actual result of my reproduction attempt and do not make the evidence sound stronger than it is.

- Wrong: "The scrubber is completely broken for phone numbers."
- Right: "I reproduced the reported case: the parenthesized phone number remained in the output instead of being redacted."

### Rule: Keep the issue scope specific

I keep my comments focused on the behavior reported in the issue instead of making broad claims about unrelated parts of the project.

- Wrong: "The PII scrubber has a lot of regex problems."
- Right: "I tested the parenthesized US phone-number case described in this issue."

### Rule: Make reproduction details useful

When reporting a reproduction, I include the relevant environment, commands or inputs, and observed result so another contributor can check the same behavior.

- Wrong: "Confirmed, same problem here."
- Right: "I reproduced this using the repository setup and the issue's sample input. The parenthesized phone number remained unchanged in the scrubber output."

### Rule: Be clear about uncertainty

If I cannot reproduce something or have not confirmed its cause, I say that directly instead of guessing.

- Wrong: "This is definitely caused by the regex in `pii_scrubber.py`."
- Right: "I reproduced the behavior, but I have not yet confirmed which part of the scrubber causes it."

## Things I never post

- A promise that I will fix or merge something before I have investigated it.
- A claim that I reproduced an issue when my evidence does not show the reported behavior.
- Guesses about the root cause presented as facts.
- "Same here" or "can confirm" without my own reproduction details.
- Broad claims about the project based on one issue.
- AI-generated boilerplate that does not describe what I actually tested.