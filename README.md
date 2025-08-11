# 🛡️ Self-Updating Security Patch Script in Kali Linux

## 📌 Overview
Keeping systems updated is one of the simplest yet most effective ways to stay protected against cyber threats. This project automates **security patch updates** in Kali Linux using a **Bash script**, scheduled execution via **cron jobs**, and log management with **logrotate**.  

With this script, your system will:
- Automatically check for and install security patches.
- Keep detailed logs of updates.
- Rotate and compress logs to save disk space.
- Run updates on a fixed schedule without manual intervention.

---

## ✨ Features
- **Automated Updates** – Installs the latest security patches using `apt`.
- **Scheduling with Cron** – Runs updates at your chosen time (default: 2:00 AM daily).
- **Detailed Logging** – Records all update activities with timestamps.
- **Log Rotation** – Manages log size using `logrotate` to prevent storage issues.
- **Easy Setup** – Minimal commands to get up and running.

---

## 📂 Project Structure
├── security_patch_update.sh # Main Bash script
├── /var/log/security_patch_update.log # Log file location
├── /etc/logrotate.d/security_patch_update # Logrotate config
└── README.md # Project documentation

yaml
Copy
Edit

---

## 🛠 Tools & Technologies
- **Kali Linux** – OS environment
- **APT (Advanced Package Tool)** – Package updates & upgrades
- **Bash** – Automation scripting
- **Cron** – Scheduling system tasks
- **Logrotate** – Log management

---

## 🚀 Installation & Usage

### 1️⃣ Create the Script
```bash
sudo nano security_patch_update.sh
Paste the following code:

bash
Copy
Edit
#!/bin/bash

LOGFILE="/var/log/security_patch_update.log"

echo "[$(date)] Starting security updates..." >> $LOGFILE

apt update -y >> $LOGFILE 2>&1
apt upgrade -y >> $LOGFILE 2>&1

echo "[$(date)] Security updates completed." >> $LOGFILE
echo "----------------------------------------" >> $LOGFILE
2️⃣ Make it Executable
bash
Copy
Edit
chmod +x security_patch_update.sh
3️⃣ Move to System Path
bash
Copy
Edit
sudo mv security_patch_update.sh /usr/local/bin/
4️⃣ Schedule with Cron
bash
Copy
Edit
sudo crontab -e
Add:

ruby
Copy
Edit
0 2 * * * /usr/local/bin/security_patch_update.sh
5️⃣ Setup Log Rotation
bash
Copy
Edit
sudo nano /etc/logrotate.d/security_patch_update
Add:

lua
Copy
Edit
/var/log/security_patch_update.log {
    daily
    rotate 7
    compress
    missingok
    notifempty
    create 640 root adm
}
6️⃣ Test the Script
bash
Copy
Edit
sudo /usr/local/bin/security_patch_update.sh
cat /var/log/security_patch_update.log
📊 Benefits
Prevents vulnerabilities from going unpatched.

Reduces downtime caused by outdated software.

Saves admin time by removing repetitive manual work.

Maintains compliance with security policies.

📅 Project Timeline
Week 1 – Requirements & planning

Week 2 – Script development & testing

Week 3 – Cron & logrotate setup

Week 4 – Documentation & presentation

📌 Future Enhancements
Email notifications after each update.

Error detection and alert system.

GUI/web dashboard for monitoring update status.

👨‍💻 Author
V Uday Kiran
Cybersecurity Enthusiast | B.Tech CSE Student
📧 vuday8463@gmail.com | 📱 +91 91824 41078






