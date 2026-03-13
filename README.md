# Splunk SSH Brute Force Detection Lab

## Overview
This project demonstrates how to detect SSH brute force attacks using Splunk SIEM.

## Lab Setup

Attacker: Kali Linux  
Victim: Ubuntu Server  
SIEM: Splunk Enterprise  

## Attack Simulation

Brute force attack using Hydra:

hydra -l ubuntu -P rockyou.txt ssh://192.168.56.105

## Logs

Ubuntu authentication logs:

/var/log/auth.log

## Splunk Detection

Example SPL query:

index=main "Failed password"

## Skills Demonstrated

- SIEM monitoring
- Log analysis
- Brute force detection
- SOC lab design
