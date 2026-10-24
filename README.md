# Linux Administration Labs

A portfolio of practical Linux administration exercises documenting configuration changes, verification results, and operational lessons.

Maintained by [John Akech](https://github.com/jakech-sys), with a focus on systems administration and infrastructure engineering.

## Lab Index

| Lab | Focus | Verified Result |
| --- | --- | --- |
| [01 — Non-Interactive User Account](01-non-interactive-user/README.md) | User creation and login-shell configuration | Local account entry for `ravi` specifies `/sbin/nologin` |

## Documentation Standards

Each lab identifies its objective, environment, implementation steps, and verification evidence. Commands executed during the exercise are distinguished from optional checks. Results are limited to what the recorded evidence supports.

Lab reports are maintained in numbered directories, with a dedicated `README.md` for each exercise. Supporting screenshots are included when they provide additional evidence. Credentials are excluded from published documentation.

## Repository Contents

| File | Purpose |
| --- | --- |
| [Lab 01](01-non-interactive-user/README.md) | Account configuration, command explanations, and observed output |
| [.gitignore](.gitignore) | Exclusion rules for common credential files, local settings, and temporary files |

## Attribution

The first lab was completed in a [KodeKloud](https://kodekloud.com/) practice environment as part of the 100 Days of Cloud (Azure) learning challenge. It covers Linux user administration.

This independent portfolio documents the author's execution and observations. KodeKloud retains ownership of its training materials and lab scenarios.
