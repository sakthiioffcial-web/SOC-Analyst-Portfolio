# Day 6 Portfolio — Log Correlation & Attack Timeline Investigation

## Objective

Simulate a brute-force SSH attack and correlate authentication logs to build an attack timeline and identify attacker behavior.

---

## Environment

* Kali Linux (VMware)
* OpenSSH Server
* Linux Terminal
* /var/log/auth.log

---

## Step 1 — Failed Login Detection

### Command Used

sudo grep "Failed password" /var/log/auth.log

### Purpose

Identify failed SSH login attempts that may indicate brute-force activity.

### Observation

Detected multiple failed login attempts generated during simulation.

### Screenshot

![alt text](<Screenshot (20).png>)

---

## Step 2 — Successful Login Detection

### Command Used

sudo grep "Accepted password" /var/log/auth.log

### Purpose

Identify successful authentication events.

### Observation

Observed successful login following failed attempts.

### Screenshot

![alt text](<Screenshot (20)-1.png>)

---

## Step 3 — Log Correlation

### Command Used

sudo grep -E "Failed password|Accepted password" /var/log/auth.log

### Purpose

Correlate failed and successful login events to understand attack progression.

### Observation

Verified sequence of failed attempts followed by successful authentication.


---

## Step 4 — Attack Timeline Extraction

### Command Used

sudo grep "Failed password" /var/log/auth.log | cut -d' ' -f1-3

### Purpose

Extract timestamps to build an attack timeline.

### Observation

Identified timing pattern of repeated login attempts.

---

## Step 5 — Attacker Frequency Analysis

### Command Used

sudo grep "Failed password" /var/log/auth.log | awk '{print $(NF-3)}' | sort | uniq -c

### Purpose

Count login attempts per source IP.

### Observation

Confirmed repeated attempts from a single source address.

### Screenshot

![alt text](<Screenshot (21).png>)

---

## Skills Developed

* Log correlation
* Brute-force attack detection
* Timeline reconstruction
* Indicator extraction
* SOC investigation workflow

---

## Conclusion

Simulated and analyzed a brute-force SSH attack using authentication logs. Correlated events to reconstruct an attack timeline and identify attacker behavior, demonstrating foundational SOC analysis skills.
