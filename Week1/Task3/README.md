# Day 3 - Secure Root SSH Access

## Task

Disable direct root SSH login on Linux servers to improve system security.

This is a common security hardening practice in production environments.

---

# Objective

* Disable direct root login via SSH
* Restart SSH service
* Verify configuration

---

# Why Disable Root SSH Login?

Direct root login is dangerous because:

* Root has full system access
* Brute-force attacks target root user
* Reduces accountability
* Increases security risks

Best practice:

```text
Login with normal user → Use sudo
```

---

# Step 1: Open SSH Configuration File

```bash id="ev3jlwm"
sudo vi /etc/ssh/sshd_config
```

---

# Step 2: Find `PermitRootLogin`

Search for:

```text id="jlwmp9"
PermitRootLogin
```

If commented:

```text id="o4lf3w"
#PermitRootLogin prohibit-password
```

Change it to:

```text id="i3x9gx"
PermitRootLogin no
```

---

# Step 3: Save the File

In vi editor:

```text id="jlwm8m"
ESC → :wq
```

---

# Step 4: Restart SSH Service

## RHEL/CentOS

```bash id="k4vjlwm"
sudo systemctl restart sshd
```

## Ubuntu/Debian

```bash id="g9h4m1"
sudo systemctl restart ssh
```

---

# Step 5: Verify Configuration

```bash id="e6lm2v"
sudo sshd -T | grep permitrootlogin
```

Expected Output:

```text id="d5zjlwm"
permitrootlogin no
```

---

# Alternative Verification

```bash id="h2s1zt"
sudo grep PermitRootLogin /etc/ssh/sshd_config
```

Expected:

```text id="jlwm2s"
PermitRootLogin no
```

---

# Important Troubleshooting

Sometimes multiple config files exist.

Check all SSH configs:

```bash id="t3a7u1"
sudo grep -R "PermitRootLogin" /etc/ssh/
```

If another file contains:

```text id="jlwm4r"
PermitRootLogin yes
```

change it to:

```text id="l5c8wj"
PermitRootLogin no
```

---

# Real-Time Use Cases

Used in:

* Production Linux servers
* Cloud infrastructure
* Banking systems
* Enterprise security hardening
* DevOps environments

---

# Useful Commands

## Check SSH Service Status

```bash id="p1l4n8"
sudo systemctl status sshd
```

---

## Test SSH Config Syntax

```bash id="jlwm6u"
sudo sshd -t
```

No output means configuration is valid.

---

## Reload SSH Without Restart

```bash id="k8x4mj"
sudo systemctl reload sshd
```

---

# Interview Questions

## Why disable root SSH login?

To improve security and prevent direct privileged access.

---

## What does `PermitRootLogin no` do?

Prevents root user from logging in through SSH.

---

## Difference between restart and reload?

| Restart                  | Reload                              |
| ------------------------ | ----------------------------------- |
| Stops and starts service | Applies config without full restart |

---

## Which file controls SSH configuration?

```text id="w9jlwm"
/etc/ssh/sshd_config
```

---

# Commands Summary

```bash id="u4h7qv"
sudo vi /etc/ssh/sshd_config
sudo systemctl restart sshd
sudo sshd -T | grep permitrootlogin
```

---

# Key Concepts Learned

* Linux security hardening
* SSH configuration
* Root access restriction
* Service management
* SSH daemon validation

