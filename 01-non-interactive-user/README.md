# Lab 01: Non-Interactive User Account

[Return to the lab index](../README.md)

| Item | Detail |
| --- | --- |
| Date | October 24, 2026 |
| Environment | KodeKloud Linux practice environment |
| Target | App Server 2; remote hostname displayed as `stapp02` |
| Administrative login | `steve` |
| Account created | `ravi` |
| Verification | Local account entry specifies `/sbin/nologin` |

## Objective

Create the `ravi` account with a non-interactive login shell to meet a backup-agent requirement.

An account can own files and run service processes without providing an interactive shell. Configuring `nologin` restricts shell login; file permissions and service privileges require separate configuration.

## Implementation

### 1. Establish the SSH session

Connection command reported for this exercise:

```bash
ssh steve@server02
```

The remote terminal displayed:

```text
[steve@stapp02 ~]$
```

The connection name and displayed hostname differ. The lab's **Details of all Users and Servers** panel is the reference for identifying the assigned server.

### 2. Create the account

Executed on App Server 2 as `steve`:

```bash
sudo useradd -s /sbin/nologin ravi
```

| Component | Function |
| --- | --- |
| `sudo` | Executes the command with administrative privileges |
| `useradd` | Creates the user account |
| `-s /sbin/nologin` | Assigns the non-interactive login shell |
| `ravi` | Specifies the username |

The command returned to the prompt without an error after successful authentication.

### 3. Verify the configuration

Executed on App Server 2:

```bash
grep "ravi" /etc/passwd
```

Recorded output:

```text
ravi:x:1001:1001::/home/ravi:/sbin/nologin
```

| Field | Value | Interpretation |
| --- | --- | --- |
| Username | `ravi` | Local account name |
| Password field | `x` | Password information is maintained in the shadow password database |
| User ID | `1001` | Numeric user identity |
| Primary group ID | `1001` | Numeric primary group identity |
| Comment | Empty | No account description supplied |
| Home directory | `/home/ravi` | Configured home path; directory existence was not checked |
| Login shell | `/sbin/nologin` | Non-interactive login shell |

## Operational Notes

- Two initial `sudo` authentication attempts failed; a subsequent attempt succeeded.
- `useradd` requires an unused username. Inspect an existing account before attempting to change it.
- The `nologin` executable's path can vary by distribution.
- The command does not explicitly request a system account with `-r`, create a home directory with `-m`, or assign backup permissions.
- Ctrl+C interrupts a command or cancels input. Use `exit` to close the SSH session.

## Additional Verification

The following checks are recommended for a repeat exercise. They were not included in the recorded execution.

```bash
# Retrieve the exact account through configured account sources.
getent passwd ravi

# Inspect the account's identity and group membership.
id ravi

# Match the exact username in the local account file.
grep '^ravi:' /etc/passwd
```

An exact lookup avoids matching unrelated text elsewhere in an account entry.

## Result

The recorded output confirms that the local `ravi` account is configured with `/sbin/nologin`. Interactive login behavior and backup-agent operation were not tested. A KodeKloud grading result was not included in the execution record.

## Attribution

Practice environment and original scenario: [KodeKloud](https://kodekloud.com/). This report documents the implementation and observed result in the author's own words.
