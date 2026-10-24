# Lab 01 · Create a non-interactive user

[Back to the lab index](../README.md)

| Item | Detail |
| --- | --- |
| Date | October 24, 2026 |
| Environment | KodeKloud Linux practice environment |
| Target | App Server 2; terminal prompt showed `stapp02` |
| Login account | `steve` |
| User created | `ravi` |
| Result | Account entry verified with `/sbin/nologin` |
| Platform grading | Not recorded |

## Objective

Create a user named `ravi` with a non-interactive login shell for a backup-agent scenario.

A service can use an account identity to own files and run processes without requiring a human login session. Assigning `nologin` refuses shell logins; it does not prevent a service or an administrator from running a process under that user's identity. File permissions and service configuration remain separate controls.

## Prerequisites and repeat-run considerations

- Access to the assigned practice server and an account authorized to use `sudo`.
- Confirmation that the target is App Server 2 using the lab's infrastructure panel.
- A valid `nologin` executable at the configured path. Its location can vary between distributions.
- A new username: `useradd` creates an account and will fail if `ravi` already exists. Inspect an existing account before deciding whether any change is appropriate.

The recorded command does not request a system account with `-r`, create a home directory explicitly with `-m`, or assign backup permissions. The exercise required a non-interactive shell; those additional settings were outside its scope.

## Implementation

### 1. Connect to the target server

From the lab's starting terminal, I connected using:

```bash
ssh steve@server02
```

The remote prompt showed:

```text
[steve@stapp02 ~]$
```

The connection name and displayed hostname differ. For a repeat of this lab, confirm the target against KodeKloud's **Details of all Users and Servers** panel rather than assuming the names are interchangeable in another environment.

### 2. Create the account

Run on **App Server 2**, signed in as `steve`:

```bash
sudo useradd -s /sbin/nologin ravi
```

| Component | Purpose |
| --- | --- |
| `sudo` | Run with administrator privileges |
| `useradd` | Create the account |
| `-s /sbin/nologin` | Set its login shell to `/sbin/nologin` |
| `ravi` | Specify the username |

The command returned to the prompt without an error after authentication.

### 3. Verify the account entry

Run on **App Server 2**:

```bash
grep "ravi" /etc/passwd
```

Observed output:

```text
ravi:x:1001:1001::/home/ravi:/sbin/nologin
```

This is the actual verification output from the exercise, not example output.

| Field | Observed value | Meaning |
| --- | --- | --- |
| Username | `ravi` | Created account |
| Password field | `x` | Password information is stored separately in the shadow password database |
| UID | `1001` | Numeric user identity |
| Primary GID | `1001` | Numeric primary group identity |
| Comment | Empty | No account description was specified |
| Home | `/home/ravi` | Configured home path; this does not prove the directory exists |
| Shell | `/sbin/nologin` | Configured non-interactive login shell |

UIDs and GIDs may differ in another environment.

## Troubleshooting and lessons

Two initial `sudo` password attempts were rejected. Authentication subsequently succeeded, and the account entry was present. The password prompt was for `steve`, the invoking user.

The captured session ends with Ctrl+C at the prompt. Ctrl+C cancels input or interrupts a foreground command; it does not close an SSH session. Use `exit` to leave the remote shell. No exit command is included in the captured evidence.

## Suggested follow-up checks

**These commands were not part of the recorded execution.** Run them on the target server if further verification is needed:

```bash
# Look up the exact username through configured account sources.
getent passwd ravi

# Inspect the numeric identity and group membership.
id ravi

# Alternatively, match only this username in the local account file.
grep '^ravi:' /etc/passwd
```

The original `grep "ravi"` worked here, but it can match text elsewhere in an account entry. An exact account lookup is clearer.

## Outcome and limits

The observed account entry confirms that `ravi` exists locally and is configured with `/sbin/nologin`. No interactive login test, backup-agent execution, home-directory check, or KodeKloud grading result is claimed.

## Source

Practice environment and original scenario: [KodeKloud](https://kodekloud.com/). This write-up summarizes my execution without reproducing the full assignment.
