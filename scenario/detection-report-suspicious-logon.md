# Detection Use Case: Suspicious Logon Times (After-Hours Login)

## Scenario Description
I simulated an after-hours login by setting my Linux VM’s time to 2:30 AM and SSH’ing into it from my host Windows machine (IP: 192.168.123.1). The target VM (IP: 192.168.123.128) had an Apache web server running, but the attack focused on SSH access using the user `admin1`.

## Objective
The goal was to detect logins outside normal business hours (9 AM–5 PM) and create a Splunk alert to flag suspicious logon times, mapping to MITRE ATT&CK T1078 (Valid Accounts).

## Tools Used
- **SIEM:** Splunk (installed on host Windows machine)
- **Log Source:** Linux VM (Ubuntu 22.04)
- **Attack Method:** SSH login from host Windows machine

## Event ID / Data Source Mapping
- **Log File:** `/var/log/auth.log` on the Linux VM
- **Sourcetype:** `linux_secure` in Splunk
- **Event Description:** Successful SSH logins logged as “Accepted password” entries with timestamps

## Detection Logic / Query
I used this Splunk query to detect logins outside 9 AM–5 PM:This query checks the hour of login events and triggers an alert for anything before 9 AM or after 5 PM.

## Sample Alert Screenshot
[Attach a screenshot of the Splunk alert showing the login at 2:30 AM]

## Logs or Sample Event
Here’s a sample log from `/var/log/auth.log` during the attack:This shows a successful login at 2:30 AM, outside business hours.

## Analyst Notes
- This alert might flag legitimate late-night logins (e.g., by an admin working late). I’d refine it by adding user or IP filters to reduce false positives.
- The simulation was effective, as Splunk caught the exact timestamp of the login.

## Detection Status
Successfully implemented.
