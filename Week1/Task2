# Day 2 - Temporary User Setup with Expiry

## Task

Create a temporary user account with an expiry date.

This is useful for:

* Contract employees
* Temporary developers
* Vendor access
* Short-term project assignments

---

# Objective

* Create a user
* Set account expiry date
* Verify expiry configuration

---

# Step 1: Create User with Expiry Date

Example:

```bash id="jlwm5y"
sudo useradd -e 2027-02-17 kirsty
```

Where:

* `-e` → expiry date
* `2027-02-17` → account expiration date
* `kirsty` → username

---

# Step 2: Set Password

```bash id="y4ybbq"
sudo passwd kirsty
```

---

# Step 3: Verify Expiry Date

```bash id="6g97w9"
sudo chage -l kirsty
```

Expected Output:

```text id="9vv8ij"
Account expires : Feb 17, 2027
```

---

# Understanding User Expiry

After expiry date:

* User cannot log in
* SSH access denied
* Account becomes inactive

---

# Real-Time Use Cases

Temporary accounts are used for:

* External consultants
* Interns
* Support engineers
* Client access
* Audit users

---

# Useful Commands

## Check User Details

```bash id="fjlwmx"
grep kirsty /etc/passwd
```

---

## Modify Expiry Date

```bash id="x1zhjx"
sudo usermod -e 2027-03-01 kirsty
```

---

## Remove Expiry Date

```bash id="87q9i4"
sudo usermod -e "" kirsty
```

---

## Lock User Account

```bash id="z5c7e6"
sudo passwd -l kirsty
```

---

## Unlock User Account

```bash id="0mt8ew"
sudo passwd -u kirsty
```

---

# Check Account Status

```bash id="jjlwm9"
sudo chage -l kirsty
```

---

# Interview Questions

## What does `useradd -e` do?

Sets account expiration date for the user.

---

## How to check user expiry?

```bash id="5qlz3l"
chage -l username
```

---

## Difference between lock and expiry?

| Lock                | Expiry                    |
| ------------------- | ------------------------- |
| Manual disable      | Automatic disable         |
| Can happen anytime  | Date-based                |
| Uses passwd/usermod | Uses expiry configuration |

---

## What happens after account expiry?

User authentication fails and login is denied.

---

# Commands Summary

```bash id="uxjlwm"
sudo useradd -e 2027-02-17 kirsty
sudo passwd kirsty
sudo chage -l kirsty
```

---

# Key Concepts Learned

* Linux user management
* Temporary account setup
* Account expiry handling
* User security controls
* Access lifecycle management
