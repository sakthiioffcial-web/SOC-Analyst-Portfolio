# Day 5 Portfolio — Linux Process & Network Investigation

## Objective

Investigate running processes and active network connections to identify suspicious activity and practice basic SOC threat hunting techniques.

---

## Environment

* Kali Linux (VMware)
* Linux Terminal

---

## Step 1 — Process Enumeration

### Command Used

ps aux

### Purpose

List all running processes to detect unusual or suspicious activity.

### Observation

Reviewed active system processes and identified root-owned processes. Checked for unknown or abnormal commands.

### Screenshot

![alt text](<Screenshot (14).png>)

---

## Step 2 — Filtering Root Processes

### Command Used

ps aux | grep root

### Purpose

Focus on high-privilege processes that could indicate potential security risks.

### Observation

Verified legitimate root processes and confirmed no suspicious high-privilege activity.

### Screenshot

![alt text](<Screenshot (15).png>)
---

## Step 3 — Real-Time Monitoring

### Command Used

top

### Purpose

Monitor CPU and memory usage in real time to detect abnormal resource consumption.

### Observation

Observed stable system performance with no unusual spikes.

### Screenshot

![alt text](<Screenshot (15).png>)

---

## Step 4 — Network Port Analysis

### Command Used

sudo netstat -tulnp

### Purpose

Identify listening ports and associated services.

### Observation

Reviewed active ports and verified legitimate system services.

### Screenshot

![alt text](<Screenshot (17).png>)

---

## Step 5 — Cross-Checking Connections

### Command Used

ss -tulnp

### Purpose

Confirm active network connections using a modern networking tool.

### Observation

Validated results from netstat and confirmed expected open ports.


## Step 6 — Suspicious Process Simulation

### Commands Used

sleep 300 &
ps aux | grep sleep
kill <PID>

### Purpose

Simulate and detect a suspicious background process, then terminate it.

### Observation

Successfully created, detected, and terminated a background process.

### Screenshot

![alt text](<Screenshot (18).png>)

---

## Skills Developed

* Linux process investigation
* Real-time system monitoring
* Network port analysis
* Process hunting and termination
* Basic SOC threat hunting workflow

---

## Conclusion

Performed a structured investigation of running processes and network activity. Simulated suspicious behavior and practiced identifying and responding to it using Linux command-line tools.
