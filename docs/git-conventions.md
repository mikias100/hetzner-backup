\# Git Commit Conventions



This project follows strict Git commit conventions to keep the history clean, auditable, and reviewable for the final assessment. As Git Manager, I (Member A) enforce these rules across all team contributions.



\## Commit message rules



All commit messages MUST be:



1\. \*\*In English\*\* — required by the assignment.

2\. \*\*In imperative mood\*\* — "Add", "Fix", "Update" — not "Added", "Fixed", "Updated".

3\. \*\*Concise\*\* — under 72 characters in the subject line.

4\. \*\*Atomic\*\* — one logical change per commit. Do not bundle unrelated changes.



\## Examples



Good:



\- `Add dd-over-SSH backup script`

\- `Fix GRUB boot failure on VirtualBox`

\- `Update README with team roles`

\- `Document partition layout for source server`



Bad:



\- `stuff` — not descriptive

\- `Fixed a bunch of things and added the backup script` — not atomic

\- `Added backup script` — past tense

\- `lade till backup-skript` — Swedish, not English



\## Phase milestone commits



Each phase ends with a checkpoint commit using this exact pattern:



\- `Complete Phase 1: research and toolchain selection`

\- `Complete Phase 2: backup pipeline implemented and tested`

\- `Complete Phase 3: VirtualBox restore verified`

\- `Complete Phase 4: documentation finalized and video uploaded`



\## Branch policy



\- `main` is the default branch.

\- Small-team direct commits to `main` are permitted given the project scope.

\- Always `git pull` before starting work each day.

\- Push at least once per work session to avoid losing changes.



\## Conflict handling



If a merge conflict arises, the person who pushed last is responsible for resolving it by rebasing on top of `main` before re-pushing.

