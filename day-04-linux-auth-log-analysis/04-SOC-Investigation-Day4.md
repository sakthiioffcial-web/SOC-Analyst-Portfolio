# Day 4 Portfolio — Linux Authentication Log Analysis (Failed SSH Login Investigation)

## Objective

Simulate failed SSH login attempts and analyze Linux authentication logs to detect and investigate brute-force activity.

---

## Environment

* Kali Linux (VMware)
* Linux Terminal
* /var/log/auth.log

---

## Step 1 — Viewing Authentication Logs

### Command Used

sudo less /var/log/auth.log

### Purpose

Examine system authentication logs to understand login activity.

### Observation

Reviewed authentication entries including login attempts and system events.

### Screenshot

![alt text](<Screenshot (11)-1.png>)

---

## Step 2 — Simulating Failed SSH Logins

### Command Used

ssh fakeuser@<local_ip>

### Purpose

Generate failed login attempts to simulate a brute-force attack scenario.

### Observation

Multiple authentication failures were triggered intentionally.



## Step 3 — Detecting Failed Password Attempts

### Command Used

sudo grep "Failed password" /var/log/auth.log

### Purpose

Filter authentication logs to detect failed login attempts.

### Observation

Identified multiple failed SSH login entries linked to the simulated attack.

### Screenshot
![alt text](<Screenshot (12).png>)

---

## Step 4 — Counting Failed Attempts

### Command Used

sudo grep "Failed password" /var/log/auth.log | wc -l

### Purpose

Quantify total failed login attempts.

### Observation

Counted total failed attempts to measure attack intensity.


## Step 5 — Extracting Attacker IP

### Command Used

sudo grep "Failed password" /var/log/auth.log | awk '{print $(NF-3)}'

### Purpose

Identify the source IP address of failed login attempts.

### Observation

Extracted attacker IP from authentication logs.

### Screenshot

![alt text](<Screenshot (13).png>)
---

## Skills Developed

* Linux log analysis
* SSH authentication investigation
* Brute-force detection
* Command-line log filtering (grep, awk)
* Basic SOC investigation workflow

---

## Conclusion

Simulated and investigated SSH brute-force activity using Linux authentication logs. Practiced identifying failed login attempts, extracting indicators, and documenting findings in a structured SOC investigation format.
