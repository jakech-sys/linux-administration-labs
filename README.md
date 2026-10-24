# Linux Administration Labs

Practical Linux administration exercises with commands, observed results, and concise explanations.

I am building hands-on skills for systems administration and infrastructure engineering. This repository records what I configure, how I verify it, and what I learn along the way.

## Lab index

| Lab | Topic | Evidence |
| --- | --- | --- |
| [01 · Non-interactive user](01-non-interactive-user/README.md) | User management and service account login shells | Account entry confirms `/sbin/nologin` |

**Current scope:** One documented lab. The recorded terminal output verifies the account configuration; a KodeKloud grader result has not been recorded.

## Repository guide

| Path | Purpose |
| --- | --- |
| [01-non-interactive-user/README.md](01-non-interactive-user/README.md) | First lab: implementation, evidence, and lessons |
| [templates/lab-template.md](templates/lab-template.md) | Reusable structure for future lab write-ups |
| [.gitignore](.gitignore) | Excludes common credentials, local settings, and temporary files |

## Documentation approach

- Explain the task and identify the machine where each command runs.
- Record commands actually executed and preserve relevant output.
- Separate observed results from suggested follow-up checks.
- Describe troubleshooting briefly, without publishing credentials.
- Add screenshots only when they provide useful evidence.

Commands are intended for authorized practice environments. Review the target host and account before making changes. A command that creates a user is not automatically safe to rerun.

## Adding the next lab

1. Create a numbered folder at the repository root, such as `02-user-permissions/`.
2. Copy [the lab template](templates/lab-template.md) into that folder as `README.md`.
3. Replace the placeholders with the task, commands executed, observed output, and lessons.
4. If useful, place redacted screenshots in that lab's `screenshots/` subfolder and embed them with relative links.
5. Add one row to the lab index above and commit with a descriptive message.

Keep each lab self-contained. The template's back link works for a lab folder directly under the repository root. A screenshot is optional when terminal output already supplies clear evidence.

## Learning direction

Future exercises may cover permissions, groups, SSH, processes, services, storage, networking, and Bash automation. These are learning goals, not claims of completed work.

## Attribution

The first exercise was completed in a [KodeKloud](https://kodekloud.com/) practice environment while following the 100 Days of Cloud (Azure) learning challenge. It demonstrates Linux administration; no Azure resources were provisioned in this exercise.

The write-ups document my execution and learning. KodeKloud owns its training material and lab scenarios. This is an independent learning portfolio, not an official KodeKloud resource.

**Maintained by [John Akech](https://github.com/jakech-sys).**
