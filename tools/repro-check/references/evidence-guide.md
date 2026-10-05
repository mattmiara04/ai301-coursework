# Evidence guide: where proof lives in a reproduction package

## Environment

**Where it lives:** In an eval bundle, inspect the repro report's environment record and the repo-facts block, then compare them with any environment, version, dependency, platform, or setup requirements stated in the issue context. In live mode, inspect the issue thread and repository documentation for the expected environment, then compare those facts with the environment recorded in the student's draft repro report.

**What good looks like:** The record identifies the repository/revision and the runtime, dependency, configuration, or platform details that materially affect the reproduction. Those details match the issue's target environment, or any meaningful difference is explicitly identified rather than silently ignored.

## Steps

**Where it lives:** In an eval bundle, inspect the ordered reproduction commands and actions in the repro report together with prerequisite setup information in the environment record. In live mode, read the student's draft repro report from its starting state through the action that is supposed to trigger the behavior.

**What good looks like:** A stranger can start from the stated environment and perform the actions in order without guessing a material command, input, configuration, file, or prerequisite. The steps actually exercise the behavior described by the issue rather than merely reaching a nearby feature or code path.

## Behavior shown

**Where it lives:** In an eval bundle, inspect the repro report's output excerpts, logs, screenshots, test results, or other artifacts and read them against the issue context's expected and observed behavior. In live mode, inspect the evidence included or referenced in the draft repro report and compare it directly with the behavior the GitHub issue describes.

**What good looks like:** The artifacts visibly support what happened when the relevant reproduction steps were run. Successful reproduction evidence shows the specific incorrect behavior described by the issue; cannot-reproduce evidence shows the relevant test was actually performed and that the reported behavior did not occur. Evidence of only an adjacent or different failure is not proof of the target issue.

## Honesty

**Where it lives:** In an eval bundle, compare the claim comment and the repro report's stated outcome with the commands, outputs, logs, screenshots, and other artifacts supplied in the package. In live mode, compare every factual assertion in the draft comments with the evidence the student actually obtained.

**What good looks like:** The wording does not claim more certainty or success than the evidence supports. A clear, evidenced cannot-reproduce result is honest and acceptable; claiming reproduction when the artifacts show a different failure, no failure, or insufficient evidence is not.

## Comms

**Where it lives:** In an eval bundle, inspect the claim comment and repro comment against the issue context, repo-facts block, and any repository contribution, comment-template, or AI-disclosure requirements included in the package. In live mode, inspect the GitHub issue thread and the repository's CONTRIBUTING files, templates, README, AI policy, or other stated contribution policies, then compare those requirements with the student's draft comments.

**What good looks like:** The claim identifies the specific issue and describes the intended investigation without pretending the result is already known. The repro comment states what was actually tested and observed in the student's own words and follows applicable repository-specific requirements. If the repository requires AI-use disclosure for issues or comments, the candidate comments must include that disclosure at the required level of detail; an omitted required disclosure is a failure even when the reproduction itself is otherwise sound.