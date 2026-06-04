# Day 5: SELinux Installation and Configuration

## Objective

Learn what SELinux is, how to install the required SELinux packages, and how to configure SELinux on a Linux server.

---

## What is SELinux?

SELinux (Security-Enhanced Linux) is a security framework built into Linux that provides mandatory access control (MAC).

It helps protect the system by controlling what users, processes, and applications can access.

### Benefits of SELinux

* Improves system security
* Restricts unauthorized access
* Limits damage from compromised applications
* Enforces security policies

---

## SELinux Modes

SELinux can operate in three modes:

### 1. Enforcing Mode

SELinux policies are actively enforced.

```text
SELINUX=enforcing
```

All security rules are applied and violations are blocked.

---

### 2. Permissive Mode

SELinux does not block actions but logs violations.

```text
SELINUX=permissive
```

Useful for troubleshooting and testing.

---

### 3. Disabled Mode

SELinux is completely disabled.

```text
SELINUX=disabled
```

No SELinux policies are enforced.

---

## Check Current SELinux Status

```bash
sestatus
```

Example Output:

```text
SELinux status:                 enabled
Current mode:                   enforcing
```

---

## Install SELinux Packages

On RHEL/CentOS/Rocky/AlmaLinux:

```bash
sudo yum install -y selinux-policy selinux-policy-targeted policycoreutils
```

or

```bash
sudo dnf install -y selinux-policy selinux-policy-targeted policycoreutils
```

Verify installation:

```bash
rpm -qa | grep selinux
```

---

## SELinux Configuration File

SELinux settings are stored in:

```text
/etc/selinux/config
```

View the configuration:

```bash
cat /etc/selinux/config
```

Example:

```ini
SELINUX=enforcing
SELINUXTYPE=targeted
```

---

## Permanently Disable SELinux

Open the configuration file:

```bash
sudo vi /etc/selinux/config
```

Locate:

```ini
SELINUX=enforcing
```

Change it to:

```ini
SELINUX=disabled
```

Save and exit:

```vim
:wq
```

---

## Verify Configuration

```bash
grep ^SELINUX= /etc/selinux/config
```

Expected Output:

```text
SELINUX=disabled
```

---

## Common SELinux Commands

### Check Status

```bash
sestatus
```

### View Current Mode

```bash
getenforce
```

Possible outputs:

```text
Enforcing
Permissive
Disabled
```

### Temporarily Set Permissive Mode

```bash
sudo setenforce 0
```

### Re-enable Enforcing Mode

```bash
sudo setenforce 1
```

Note: `setenforce` changes are temporary and do not survive a reboot.

---

## KodeKloud Practice Task

### Requirement

1. Install required SELinux packages.
2. Permanently disable SELinux.
3. Do not reboot the server.
4. Ensure SELinux will be disabled after the next reboot.

### Solution

Install packages:

```bash
sudo yum install -y selinux-policy selinux-policy-targeted policycoreutils
```

Edit configuration:

```bash
sudo vi /etc/selinux/config
```

Change:

```ini
SELINUX=enforcing
```

to:

```ini
SELINUX=disabled
```

Save and exit:

```vim
:wq
```

Verify:

```bash
grep ^SELINUX= /etc/selinux/config
```

Expected output:

```text
SELINUX=disabled
```

---

## Vim Quick Reference

### Save and Exit

```vim
:wq
```

### Exit Without Saving

```vim
:q!
```

### Search Text

```vim
/SELINUX
```



## Key Takeaways

* SELinux provides mandatory access control for Linux systems.
* SELinux modes are Enforcing, Permissive, and Disabled.
* Configuration is stored in `/etc/selinux/config`.
* `SELINUX=disabled` permanently disables SELinux after reboot.
* `sestatus` and `getenforce` are used to check SELinux status.
* `setenforce` changes are temporary.
