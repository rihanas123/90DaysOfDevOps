# Day 04 - Linux Practice: Processes and Services

This document summarizes practical Linux exercises focused on **process management, service control, and log analysis**.  
All commands were tested using the **SSH service** on an Ubuntu-based AWS EC2 instance.

### 🔧 Lab Environment

- **Operating System:** Ubuntu (AWS EC2)
- **Access Method:** SSH with key-based authentication
- **Service Analyzed:** SSH (`sshd`)

---

## 🔹 Process Management Commands

### 1️⃣ `pgrep -a sshd`

### What It Does:
Displays all active `sshd` processes along with their full command-line arguments.

### Key Findings:
- `1036` → Primary SSH daemon (listening process)
- `1037`, `1523` → Privileged SSH processes
- `1445`, `1581` → Active login sessions (`pts/0`, `pts/1`)

> ✔ Each new SSH login creates a separate process — this is expected behavior.

---

### 2️⃣ `ps aux | grep sshd`

### What It Does:
Provides detailed information about running SSH processes, including CPU usage, memory usage, and ownership.

### Key Findings:
- Main SSH daemon runs under the `root` user
- Logged-in sessions run under the `ubuntu` user
- Multiple SSH connections result in multiple `sshd` processes

> ✔ This confirms how Linux isolates user sessions for security and stability.

---

## 🔹 Service Management Commands

### 3️⃣ `systemctl status ssh`

### What It Does:
Shows the current status of the SSH service managed by `systemd`.

### Key Findings:
- SSH service is **active and running**
- Listening on **port 22**
- EC2 Instance Connect is handling SSH key injection
- Successful public key authentication confirmed

> ✔ `systemctl` is the primary tool for managing services in modern Linux systems.

---

### 4️⃣ `systemctl list-units --type=service --state=running`

### What It Does:
Lists all services that are currently running on the system.

### Key Findings:
- `ssh.service` is active
- Essential services such as:
  - `cron`
  - `systemd-journald`
  - `networkd`
- System appears stable and healthy

> ✔ Useful for checking overall system service health.

---

## 🔹 Log Monitoring Commands

### 5️⃣ `journalctl -u ssh -n 20`

### What It Does:
Displays the latest 20 log entries related specifically to the SSH service.

### Key Findings:
- SSH service startup entries
- Confirmation of port 22 listening
- Public key authentication success logs
- Session start records

> ✔ `journalctl` is powerful for reviewing service-specific logs.

---

### 6️⃣ `tail -n 20 /var/log/auth.log`

### What It Does:
Shows the most recent authentication and authorization logs.

### Key Findings:
- SSH session opened for user `ubuntu`
- `sudo` usage recorded
- `cron` jobs executed as root
- Clear activity trail for auditing and security checks

> ✔ Essential for monitoring login attempts and administrative actions.

---

## ✅ Summary of Learning

- Each SSH login creates a separate process
- AWS EC2 relies on key-based authentication for secure access
- `systemctl` is used to manage and inspect system services
- Logs (`journalctl` and `/var/log/auth.log`) are critical for troubleshooting and security auditing

---

🚀 This hands-on practice strengthened understanding of how Linux handles processes, services, and logging in real-world cloud environments.
