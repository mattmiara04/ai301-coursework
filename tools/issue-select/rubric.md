\# Rubric: is this a good first issue?



\## Checks



| Check | Evidence | Pass condition | Weight |

|---|---|---|---|

| Maintainer activity | Repo-facts block: last 5 default-branch commits and maintainer first-response sample; also the issue comment thread and commenter author\_association. | Pass if at least one non-bot default-branch commit is within 90 days of the capture date, OR the maintainer first-response sample contains a response within 30 days, OR a maintainer has commented in this issue within 30 days. | required |

| Repository in use | Repo-facts block: archived flag, last push to any branch, and latest release. | Pass only if the repository is not archived AND either the last push was within 180 days or the latest release was within 365 days of the capture date. | required |

| Newcomer-sized scope | Issue body, issue labels, comment thread, and linked/mentioned PR history. | Pass if the issue requests one bounded piece of work. Fail only when the issue is explicitly an umbrella/tracking issue, is purely a usage/support question, has an unresolved design discussion with no maintainer-settled direction, or a maintainer explicitly states that the fix requires changes to core internals. A short or terse issue, missing reproduction steps, or previous abandoned attempts do not by themselves cause failure. | required | Issue body, issue labels, comment thread, and linked/mentioned PR history. | Pass if the issue asks for one bounded contribution and is not a pure usage/support question, umbrella/tracking issue, unresolved design discussion, or work that a maintainer explicitly says requires changes to core internals. Also fail if the history shows 2 or more abandoned implementation attempts unless a maintainer later narrowed or clarified the work. | required |

| Issue is available | Repo-facts block for this issue: assignees and linked PRs; issue comment thread for claim comments and mentioned PRs. | Pass if there is no current assignee, no open linked or mentioned PR implementing the issue, and no unretracted claim comment from another contributor within the last 30 days. A closed unmerged PR does not count as an active claim. | required |

| AI-assisted contribution allowed | Repo-facts contribution-policy line, CONTRIBUTING.md, dedicated AI policy files, and required PR templates. | Pass unless the repository explicitly bans AI-generated or AI-assisted contributions. Disclosure, testing, human-review, or personal-understanding requirements pass. If no AI policy is stated, pass. | required |

| First-issue signal | Issue labels, issue body, and maintainer comments. | Pass if the issue has a good-first-issue/help-wanted style label or a maintainer explicitly describes it as beginner-friendly, contained, low-risk, or suitable for a first contribution. | preferred |



\## Verdict rule



Accept only when every required check passes. A required check graded unclear counts as a failure. Preferred checks never change an accept/reject verdict; they are used only to rank accepted issues. If a required check has conflicting evidence, use the most recent specific evidence from a maintainer or the current issue/repository state.

