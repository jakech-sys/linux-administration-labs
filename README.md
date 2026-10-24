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
| [01-non-interactive-user/](01-non-interactive-user/) | First lab: implementation, evidence, and lessons |
| [templates/lab-template.md](templates/lab-template.md) | Reusable structure for future lab write-ups |
| [.gitignore](.gitignore) | Excludes common credentials, local settings, and temporary files |

## Documentation approach

- Explain the task and identify the machine where each command runs.
- Record commands actually executed and preserve relevant output.
- Separate observed results from suggested follow-up checks.
- Describe troubleshooting briefly, without publishing credentials.
- Add screenshots only when they provide useful evidence.

Commands are intended for authorized practice environments. Review the target host and account before making changes. A command that creates a user is not automatically safe to rerun.

## Learning direction

Future exercises may cover permissions, groups, SSH, processes, services, storage, networking, and Bash automation. These are learning goals, not claims of completed work.

## Attribution

The first exercise was completed in a [KodeKloud](https://kodekloud.com/) practice environment while following the 100 Days of Cloud (Azure) learning challenge. It demonstrates Linux administration; no Azure resources were provisioned in this exercise.

The write-ups document my execution and learning. KodeKloud owns its training material and lab scenarios. This is an independent learning portfolio, not an official KodeKloud resource.

**Maintained by [John Akech](https://github.com/jakech-sys).**
