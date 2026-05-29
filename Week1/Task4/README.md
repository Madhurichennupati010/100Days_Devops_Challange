# Day 4 - Script Execution Permissions

## Task

Grant executable permissions to a shell script so that all users can execute it.

This is commonly required for:

* Backup scripts
* Automation scripts
* Deployment scripts
* Monitoring scripts

---

# Objective

* Understand Linux file permissions
* Grant execute permission
* Verify script execution permissions

---

# Script Details

Example script:

```text
/tmp/xfusioncorp.sh
```

---

# Step 1: Check Current Permissions

```bash id="v5m3kj"
ls -l /tmp/xfusioncorp.sh
```

Example Output:

```text id="k2x8sw"
-rw-r--r-- 1 root root 120 May 29 10:00 /tmp/xfusioncorp.sh
```

Explanation:

| Symbol | Meaning              |
| ------ | -------------------- |
| rw-    | Owner can read/write |
| r--    | Group can read       |
| r--    | Others can read      |

No execute permission exists.

---

# Step 2: Grant Execute Permission

## Method 1 - Symbolic Mode

```bash id="q7jlwm"
chmod a+x /tmp/xfusioncorp.sh
```

Where:

| Option | Meaning                |
| ------ | ---------------------- |
| a      | all users              |
| +x     | add execute permission |

---

## Method 2 - Numeric Mode

```bash id="n4w8cz"
chmod 755 /tmp/xfusioncorp.sh
```

Meaning:

| Number | Permission |
| ------ | ---------- |
| 7      | rwx        |
| 5      | r-x        |
| 5      | r-x        |

---

# Step 3: Verify Permissions

```bash id="r8l4mf"
ls -l /tmp/xfusioncorp.sh
```

Expected Output:

```text id="jlwm7d"
-rwxr-xr-x
```

Now all users can execute the script.

---

# Step 4: Execute Script

```bash id="x2v9t1"
./tmp/xfusioncorp.sh
```

or

```bash id="h6k3qp"
/tmp/xfusioncorp.sh
```

---

# Understanding Linux Permissions

## Permission Structure

Example:

```text id="y1m7lz"
-rwxr-xr-x
```

Breakdown:

| Section | Meaning            |
| ------- | ------------------ |
| rwx     | Owner permissions  |
| r-x     | Group permissions  |
| r-x     | Others permissions |

---

# Permission Types

| Symbol | Meaning |
| ------ | ------- |
| r      | Read    |
| w      | Write   |
| x      | Execute |

---

# Numeric Permission Values

| Number | Permission |
| ------ | ---------- |
| 7      | rwx        |
| 6      | rw-        |
| 5      | r-x        |
| 4      | r--        |

---

# Real-Time Use Cases

Script execution permissions are used for:

* Cron jobs
* CI/CD pipelines
* Backup automation
* Monitoring tools
* Deployment scripts

---

# Useful Commands

## Remove Execute Permission

```bash id="d5n7kj"
chmod a-x /tmp/xfusioncorp.sh
```

---

## Give Owner Only Execute Permission

```bash id="l9m3qx"
chmod u+x /tmp/xfusioncorp.sh
```

---

## Change Ownership

```bash id="f1v6ze"
chown user:user /tmp/xfusioncorp.sh
```

---

## Check File Type

```bash id="p8t2sy"
file /tmp/xfusioncorp.sh
```

---

# Interview Questions

## What does `chmod` do?

Changes file or directory permissions.

---

## Difference between symbolic and numeric permissions?

| Symbolic  | Numeric   |
| --------- | --------- |
| chmod a+x | chmod 755 |

---

## What does `755` mean?

```text id="jlwm9p"
Owner  → rwx
Group  → r-x
Others → r-x
```

---

## Why execute permission is required?

Without execute permission, scripts cannot run.

---

# Commands Summary

```bash id="t4q8jlwm"
ls -l /tmp/xfusioncorp.sh
chmod a+x /tmp/xfusioncorp.sh
chmod 755 /tmp/xfusioncorp.sh
```

---

# Key Concepts Learned

* Linux permissions
* chmod command
* Script execution
* Symbolic permissions
* Numeric permissions
* File security

