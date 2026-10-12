# Week 7 – Authentication in Linux

## Aim

This tutorial concerns creation of Linux user identities, password-based authentication, password-policy considerations, and the storage of credentials in the account database.

## 1. User accounts established

The available terminal evidence shows six departmental accounts being created on a Linux node:

- HR: `hr_user1`, `hr_user2`
- Finance: `fin_user1`, `fin_user2`
- IT: `it_user1`, `it_user2`

The screenshot uses `sudo useradd -m -s /bin/bash -G <group> <user>`; this creates home directories, specifies the Bash shell and assigns supplementary group memberships.

![Six Linux user accounts created](images/w07_user_accounts_created.png)

The `groups` command then confirmed each account's departmental supplementary group. This supports account provisioning evidence, although it is also part of the Week 8 access-control exercise.

![Group memberships inspected for Linux accounts](images/w07_group_memberships.png)

## 2. Password prompts and user switching

The supplied terminal screenshots show `su - hr_user1`, `su - fin_user1`, `su - it_user1` and other department users with a `Password:` prompt followed by a user-specific shell. The ability to reach a prompt as the selected user is consistent with successful authentication in those captured attempts; the screenshot **does not disclose or verify** which passwords were assigned.

![User switching and file creation after password prompts](images/w08_files_created_by_users.png)

**Security interpretation:** Authentication checks *who* is requesting access; group-based permissions then control *what* the authenticated identity can read, change, or execute. The following Week 8 work applies that distinction directly.

## 3. Tutorial theory: password policies and credential storage

The tutorial asks students to compare the security and convenience consequences of password policies. A long unique password or passphrase is harder to guess, while password reuse and predictable patterns permit credential-stuffing attacks across systems. Password managers support unique passwords but require secure protection of the manager itself. Policy recommendations should be attributed to the relevant CQU procedure before being stated as institutional requirements.

On common Linux systems:

- `/etc/passwd` stores account metadata such as name, UID, GID, home directory and login shell. It does not normally store usable plaintext passwords.
- `/etc/shadow` stores protected password **hashes** and ageing fields, readable only by privileged processes.
- `passwd` changes a user's password; `passwd -S` shows account/password status on systems supporting that option.

These points explain the mechanisms. **No provided screenshot independently demonstrates inspection of `/etc/passwd`, `/etc/shadow`, password-hash format, or `passwd` operations.**

## Evidence summary

**Documented:** Linux user-account creation, group membership and interactive authentication prompts (`su`).  
