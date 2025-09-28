🔐 Security Alert Monitoring & Incident Response (Task 2)
📌 Introduction

This repository contains Task 2: Security Alert Monitoring & Incident Response completed as part of the Future Interns Cybersecurity Program (Batch 01).
The task focused on generating authentication logs, uploading them to Splunk, and simulating incident detection through failed and successful login attempts.

🎯 Objectives

Install and configure SSH server to generate authentication logs.

Simulate failed login attempts (brute-force scenario) and successful logins.

Export system and authentication logs (auth.log, syslog.log).

Upload logs into Splunk for monitoring and analysis.

Create alerts in Splunk to detect suspicious login behavior.

🛠️ Implementation Steps

Installed SSH server using:
sudo apt install -y openssh-server  
sudo systemctl enable --now ssh  

Generated failed login attempts (brute-force simulation):
for i in {1..5}; do ssh wronguser@127.0.0.1 -o ConnectTimeout=2 || true; done  

Performed a successful login:
ssh kali@127.0.0.1  
exit  

Exported SSH-related logs:
sudo journalctl -u ssh --no-pager > ~/future_interns/logs/auth.log  
sudo journalctl -b --no-pager > ~/future_interns/logs/syslog.log  

Uploaded logs to Splunk:
    Opened Splunk Web → Settings → Add Data → Upload.
    Uploaded auth.log and syslog.log.

Analyzed data in Splunk:
    Detected failed vs. successful login attempts.
    Created an alert for multiple failed logins to simulate incident response.
