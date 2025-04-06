# 🧠 OSQuery – Command Reference for System Auditing

This repository contains essential `osquery` commands used for auditing a Linux system. The commands are grouped by functionality and serve as a quick reference for system monitoring, process auditing, file integrity checking, and network inspection.


---

## 📂 What's Included

- ✅ `COMMANDS.md` — A categorized list of SQL-like `osquery` commands used to:
  - Monitor system processes and memory
  - Audit installed packages and kernel modules
  - Inspect open network ports and socket activity
  - Perform file integrity monitoring (FIM)
  - Track login sessions and user activity
  - Enable event-based logging 

---

## 🧱 Sections Covered in `COMMANDS.md`

### 🟦 Basic Monitoring
- Running processes
- Kernel version and modules
- Installed packages (Ubuntu-based)
- SUID binary detection

### 🌐 Network & Process Monitoring
- Listening ports and open sockets
- Interface traffic statistics
- Gateway routing information
- Privilege escalation detection (EUID ≠ UID)
- Process memory consumption

### 🛡️ Event and Syslog Logging
- Checking event-based logging status
- Listing active query packs

### 🛠️ File Integrity Monitoring (FIM)
- Tracking file creation/modification using `file_events`

---

## 📋 Requirements

- `osquery` installed on a Linux system (Ubuntu 20.04+ or 24.04 recommended)
- Access to `osqueryi` interactive shell or `osqueryd` for scheduled queries

---

## 📜 Usage

Clone the repository and explore the `COMMANDS.md` file:

```bash
git clone https://github.com/<your-username>/osquery-command-reference.git
cd osquery-command-reference
less COMMANDS.md
