# siem-internship-phase-1,2
Hey there! This repo is my work for internship where I built a virtual SOC (Security Operations Center) to simulate and detect cyber attacks. I used a Linux VM as the target, my Windows host as the attacker, and Splunk for log analysis. The goal was to simulate attacks, detect them with Splunk, and document everything.
Project Setup

Target: Linux VM (Ubuntu 22.04) in VMware, IP: 192.16x.xxx.xxx.
Attacker: My host Windows machine, IP: 192.16x.xxx.x.
SIEM: Splunk on my host, collecting logs from the Linux VM via Splunk Universal Forwarder.
Logs Monitored: /var/log/auth.log, /var/log/audit/audit.log, /var/log/apache2/access.log.

I set up SSH and Apache on the Linux VM to simulate attacks, and used auditd for detailed monitoring.
Scenarios Covered
I simulated and detected the following attacks:

DDoS (HTTP Flood): Flooded the Apache server with HTTP requests using hping3. Detected with Splunk by spotting traffic spikes.
Suspicious Logon Times (T1078): SSH’d into the Linux VM at 2:30 AM to mimic an after-hours login. Flagged it in Splunk for logins outside 9 AM–5 PM.
Log Tampering (T1070): Cleared /var/log/auth.log to hide tracks. Caught it using auditd logs in Splunk.
Hidden User Creation (T1136): Created a user hiddenuser on the Linux VM. Detected it with auditd logs in Splunk.

Each scenario has a detailed report, logs, and screenshots in the scenarios/ folder.
Folder Structure

scenarios/
ddos/: DDoS attack report, logs, and screenshot.
suspicious-logon/: Suspicious logon times report, logs, and screenshot.
log-tampering/: Log tampering report, logs, and screenshot.
hidden-user/: Hidden user creation report, logs, and screenshot. 
and many more adding as i am completing this all tasks

How to Replicate

Set Up the Target: Create a Linux VM in VMware (Ubuntu 22.04), install SSH (openssh-server) and Apache (apache2), and enable auditd.
Set Up the Attacker: Use a Windows machine to simulate attacks (e.g., hping3 for DDoS, SSH for logins).
Set Up Splunk: Install Splunk on your host, add a Universal Forwarder on the Linux VM to send logs (/var/log/auth.log, /var/log/audit/audit.log, /var/log/apache2/access.log).
Simulate Attacks: Follow the steps in each scenario’s report to replicate the attacks.
Detect with Splunk: Use the Splunk queries in the reports to create alerts and detect the attacks.

Key Learnings

Logs are everything in cybersecurity—without them, you’re blind to attacks.
Setting up a SIEM like Splunk and writing detection rules is critical for a SOC.
Mapping attacks to MITRE ATT&CK (e.g., T1070, T1136) helps understand real-world threats.

Future Improvements

Add more VMs to simulate a larger network.
Include a Windows target for scenarios like RDP lateral movement.
Use a dedicated SIEM VM instead of installing Splunk on my host.

Contact
Feel free to reach out if you have questions or want to collaborate! Check my GitHub profile for contact details.

Created on May 30, 2025, as part of my cybersecurity internship journey.
