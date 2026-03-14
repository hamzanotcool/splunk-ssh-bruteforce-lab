# Splunk SSH Brute Force Detection Lab

## Overview

This project demonstrates how a Security Operations Center (SOC) can detect SSH brute force attacks using a SIEM platform.

The lab simulates a real-world attack scenario where an attacker performs multiple SSH login attempts against a Linux server. Authentication logs are forwarded to Splunk for analysis and detection.

---

## Lab Architecture

Attacker: Kali Linux
Victim: Ubuntu Server
SIEM: Splunk Enterprise

Attack flow:

Attacker (Hydra) → Ubuntu Server (SSH logs) → Splunk SIEM (Detection)

---

## Tools Used

* Splunk Enterprise
* Splunk Universal Forwarder
* Hydra
* Kali Linux
* Ubuntu Server
* VirtualBox

---

## Attack Simulation

A brute force SSH attack is generated using Hydra from the attacker machine:

```
hydra -l ubuntu -P /usr/share/wordlists/rockyou.txt ssh://192.168.56.105
```

This generates multiple failed authentication attempts in the Ubuntu authentication logs.

---

## Log Collection

The Ubuntu server sends authentication logs to Splunk using the Splunk Universal Forwarder.

Monitored log file:

```
/var/log/auth.log
```

---

## Detection in Splunk

Example SPL query used to detect brute force attempts:

```
index=main "Failed password"
```

This query displays all failed SSH login attempts detected in the logs.

---

## Example Detection

Splunk successfully identifies multiple failed authentication attempts from the attacker IP address.

Indicators of compromise:

* Multiple failed SSH login attempts
* Same source IP address
* Repeated authentication failures in a short period

---

## MITRE ATT&CK Mapping

Technique: **T1110 – Brute Force**

[https://attack.mitre.org/techniques/T1110/](https://attack.mitre.org/techniques/T1110/)

---

## Skills Demonstrated

* SIEM monitoring
* Log analysis
* SSH brute force detection
* Linux security monitoring
* SOC lab design
* Threat detection

---

## Author

GitHub:
[https://github.com/hamzanotcool](https://github.com/hamzanotcool)
