# oss-audit-24BAI10348
**Open Source Software: NGMC Capstone Project**
**VIT | Course: Open Source Software**

---

## Student Details

| Field | Details |
|-------|---------|
| **Name** | Pallavi Joshi |
| **Registration Number** | 24BAI10348 |
| **Course** | Open Source Software (NGMC) |
| **Date** | March 31, 2026 |
---

## About This Project

This repository contains the shell scripts for my Open Source Audit capstone project. I chose Git, which was created by Linus Torvalds in 2005 when the Linux community needed a better tool since the earlier ones were not working well.

In this audit, I covered how Git started, its GPL v2 license, some ethical aspects of open source, how Git is used in Linux, and its role in the FOSS ecosystem.

---

## Repository Structure

```
oss-audit-[rollnumber]/
├── README.md
├── script1_system_identity.sh       # System welcome screen with OS and license info
├── script2_package_inspector.sh     # Checks if Git is installed + philosophy note
├── script3_disk_permission_auditor.sh  # Audits directories and Git config permissions
├── script4_log_analyzer.sh          # Analyzes log files for keyword occurrences
└── script5_manifesto_generator.sh   # Interactive open-source manifesto generator
```

---

## Dependencies

All scripts run on **Ubuntu Linux**. The following must be installed:

```bash
sudo apt update
sudo apt install git lsb-release -y
```

No additional Python, Node.js, or third-party tools are required.

---

## How to Run Each Script

### Setup: Clone the Repository

```bash
git clone https://github.com/[your-github-username]/oss-audit-[rollnumber].git
cd oss-audit-[rollnumber]
chmod +x *.sh
```

---

### Script 1: System Identity Report

Displays a welcome screen with distro name, kernel version, logged-in user, home directory, uptime, current date/time, and the open-source license covering the OS.

```bash
./script1_system_identity.sh
```

**Expected output:** A formatted terminal display showing system information and a note about the Linux GPL v2 license.

---

### Script 2: FOSS Package Inspector

Checks whether Git is installed on the system, displays its version and license info, and prints a philosophy note using a `case` statement.

```bash
./script2_package_inspector.sh
```

**Expected output:** Installation status, version, and a one-paragraph philosophy note about Git.

**To test with a different package**, edit line 10 in the script:
```bash
PACKAGE="git"   # change to: apache2, firefox, vlc, mysql, python3, etc.
```

---

### Script 3: Disk and Permission Auditor

Loops through a list of important system directories and reports permissions, ownership, and disk usage. Also checks for Git's system and user config files.

```bash
./script3_disk_permission_auditor.sh
```

**Expected output:** A table of directories with their permissions and sizes, followed by a Git config directory check.

---

### Script 4: Log File Analyzer

Reads a log file line by line, counts how many lines contain a specified keyword, and prints the last 5 matching lines.

```bash
# Basic usage — searches /var/log/syslog for "error"
./script4_log_analyzer.sh /var/log/syslog error

# Search for warnings
./script4_log_analyzer.sh /var/log/syslog warning

# Search auth log for failed login attempts
./script4_log_analyzer.sh /var/log/auth.log failed

# Run without arguments — auto-detects an available log file
./script4_log_analyzer.sh
```

**Note:** Some log files require root access. If permission is denied, run with `sudo`:
```bash
sudo ./script4_log_analyzer.sh /var/log/auth.log failed
```

---

### Script 5: Open Source Manifesto Generator

Interactively asks you three questions and generates a personalised open-source philosophy statement, saving it to a `.txt` file.

```bash
./script5_manifesto_generator.sh
```

**Expected output:** Three prompts appear. After answering, a manifesto is generated, saved to `manifesto_[username].txt`, and printed to the terminal.

**Example interaction:**
```
1. Name one open-source tool you use every day: git
2. In one word, what does 'freedom' mean to you in software? transparency
3. Name one thing you would build and share freely with the world: a study planner
```

---

## Shell Concepts Used

| Script | Concepts Demonstrated |
|--------|-----------------------|
| Script 1 | Variables, `echo`, command substitution `$()`, `lsb_release`, `uname`, `whoami`, `date` |
| Script 2 | `if-then-else`, `case` statement, `dpkg -l`, `grep`, `awk`, pipe operators |
| Script 3 | `for` loop, arrays, `ls -ld`, `du -sh`, `awk`, directory existence check `[ -d ]` |
| Script 4 | `while read` loop, `if-then` inside loop, counter variables, `$1`/`$2` arguments, retry logic |
| Script 5 | `read` for user input, string concatenation, file redirection `>` and `>>`, `date`, alias concept (commented) |

---

## Notes for the Evaluator

1. All scripts are tested on Ubuntu 22.04 LTS and Ubuntu 24.04 LTS.
2. Scripts use `dpkg` rather than `rpm` as the target system is Debian-based.
3. Script 4 includes a retry loop if the log file is not immediately found, and gracefully handles empty files.
4. Every non-obvious line in each script includes an inline comment explaining what it does.
5. Script 5 demonstrates the alias concept via a comment block, as aliases are shell-session constructs and cannot be meaningfully embedded in a non-interactive script.

---

## References

1. GNU GPL v2: https://www.gnu.org/licenses/gpl-2.0.html
2. Git official documentation: https://git-scm.com/docs
3. Pro Git book (free): https://git-scm.com/book
4. The Linux Command Line: https://linuxcommand.org/tlcl.php
5. GNU Bash Manual: https://www.gnu.org/software/bash/manual/
