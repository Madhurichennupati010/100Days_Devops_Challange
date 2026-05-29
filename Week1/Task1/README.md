# Day 1 - Linux User Setup with Non-Interactive Shell

## Task

Create a user with a non-interactive shell so the user cannot log in to the server directly.

This is commonly used for:

* Service accounts
* Application users
* Security hardening

---

## Objective

* Create a user
* Assign a non-login shell
* Verify the shell configuration

---

# Step 1: Create User with Non-Interactive Shell

Example:

```bash id="w4lf98"
sudo useradd -s /sbin/nologin devuser
```

Alternative shell:

```bash id="5pkjlwm"
sudo useradd -s /bin/false devuser
```

---

# Step 2: Verify User Details

```bash id="26nr86"
grep devuser /etc/passwd
```

Expected Output:

```text id="4yqsv9"
devuser:x:1002:1002::/home/devuser:/sbin/nologin
```

---

# Step 3: Test Login

```bash id="4zq9lj"
su - devuser
```

Expected Message:

```text id="kvjlwm1"
This account is currently not available.
```

---

# Understanding Non-Interactive Shells

| Shell         | Purpose                    |
| ------------- | -------------------------- |
| /sbin/nologin | Prevent login with message |
| /bin/false    | Immediately exits login    |
| /bin/bash     | Normal interactive shell   |

---

# Real-Time Use Cases

Non-login users are used for:

* Jenkins
* Nginx
* MySQL
* Docker services
* System applications

Example:

```text id="r9m9b5"
nginx:x:998:998::/var/cache/nginx:/sbin/nologin
```

---

# Useful Commands

## Check User Shell

```bash id="y22w0e"
cat /etc/passwd | grep devuser
```

---

## Change Existing User Shell

```bash id="ep2z11"
sudo usermod -s /sbin/nologin devuser
```

---

## List All Non-Login Users

```bash id="mk5cl5"
grep nologin /etc/passwd
```

---

# Interview Questions

## What is a non-interactive shell?

A shell that prevents users from logging into the system.

---

## Difference between `/sbin/nologin` and `/bin/false`

| nologin                | false            |
| ---------------------- | ---------------- |
| Displays message       | Exits silently   |
| Preferred for security | Simpler behavior |

---

## Why use non-login users?

To improve security by preventing direct user access.

---

# Commands Summary

```bash id="jlwm0w"
sudo useradd -s /sbin/nologin devuser
grep devuser /etc/passwd
su - devuser
```

---

# Key Concepts Learned

* Linux user management
* Shell configuration
* Security hardening
* Service accounts
* Non-interactive access


