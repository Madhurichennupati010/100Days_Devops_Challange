# Day 4: Understanding Cronie, Crond, and Cron Jobs

## Objective

Learn how Linux schedules automated tasks using Cron and how to manage the Cron service.

---

## What is Cron?

Cron is a job scheduler in Linux that automatically runs commands or scripts at specified times.

Examples:

* Run a backup every day at 2:00 AM.
* Clean temporary files every week.
* Monitor disk usage every 5 minutes.

---

## What is Cronie?

Cronie is the package that provides the Cron scheduling system on RHEL/CentOS-based Linux distributions.

When Cronie is installed, it provides:

* `crond` service
* `crontab` command
* Cron configuration files

### Install Cronie

```bash
sudo yum install -y cronie
```

Verify installation:

```bash
rpm -q cronie
```

---

## What is Crond?

`crond` (Cron Daemon) is the background service that continuously checks for scheduled jobs and executes them when their scheduled time arrives.

### Start Crond

```bash
sudo systemctl start crond
```

### Enable Crond at Boot

```bash
sudo systemctl enable crond
```

### Check Status

```bash
sudo systemctl status crond
```

Example Output:

```text
● crond.service - Command Scheduler
   Active: active (running)
```

---

## Understanding Crontab

A crontab file contains scheduled tasks.

View current cron jobs:

```bash
crontab -l
```

Edit cron jobs:

```bash
crontab -e
```

---

## Cron Job Format

```text
* * * * * command
│ │ │ │ │
│ │ │ │ └── Day of Week (0-7)
│ │ │ └──── Month (1-12)
│ │ └────── Day of Month (1-31)
│ └──────── Hour (0-23)
└────────── Minute (0-59)
```

---

## Example Cron Jobs

### Every Minute

```cron
* * * * * echo hello
```

### Every 5 Minutes

```cron
*/5 * * * * echo hello
```

### Every Day at Midnight

```cron
0 0 * * * /backup.sh
```

### Every Sunday at 2 AM

```cron
0 2 * * 0 /cleanup.sh
```

---

## KodeKloud Practice Task

### Requirement

1. Install Cronie package.
2. Start Crond service.
3. Create a cron job for root user:

```cron
*/5 * * * * echo hello > /tmp/cron_text
```

### Solution

Install Cronie:

```bash
sudo yum install -y cronie
```

Start service:

```bash
sudo systemctl start crond
sudo systemctl enable crond
```

Edit root crontab:

```bash
sudo crontab -e
```

Add:

```cron
*/5 * * * * echo hello > /tmp/cron_text
```

Verify:

```bash
sudo crontab -l
```

---

## How to Exit Common Linux Screens

### Exit `systemctl status`

When viewing:

```bash
sudo systemctl status crond
```

Press:

```text
q
```

### Exit Vim and Save

```vim
:wq
```

### Exit Vim Without Saving

```vim
:q!
```

### Exit SSH Session

```bash
exit
```

or

```text
Ctrl + D
```

---

## Key Takeaways

* Cron schedules automated tasks.
* Cronie provides the Cron utilities.
* Crond is the service that executes scheduled jobs.
* Crontab stores user-specific schedules.
* `*/5 * * * *` means "every 5 minutes".
* Press `q` to exit `systemctl status`.
* Use `:wq` to save and exit Vim.
