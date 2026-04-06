\# Lab 02: SSH Brute Force Detection using Security Onion



\## Objective



The objective of this lab was to simulate an SSH brute force attack and detect the activity using a Security Information and Event Management (SIEM) and Network Intrusion Detection System (NIDS).



This lab demonstrates the ability to generate malicious traffic, monitor network activity, analyze alerts, and investigate potential security incidents.



\---



\## Lab Environment



Attacker Machine:



\* Kali Linux



Target Machine:



\* Metasploitable 2



Monitoring System:



\* Security Onion (Suricata + Kibana)



Network:



\* Virtual Lab Environment



\---



\## Attack Simulation



A brute force attack was launched against the SSH service on the target machine using Medusa.



Command used:



hydra-like command equivalent:



medusa -h 192.168.247.138 -u msfadmin -P rockyou.txt -M ssh



The attack generated multiple login attempts against the SSH service.



\---



\## Detection



Security Onion detected the suspicious activity and generated alerts indicating a potential SSH scan.



Alert Name:



ET SCAN Potential SSH Scan OUTBOUND



Indicators observed:



\* Multiple connection attempts to port 22

\* Repeated login attempts

\* High volume of SSH traffic

\* Suspicious scanning behavior



\---



\## Investigation



The alert was analyzed using Kibana to identify:



Source IP address:

Kali Linux attacker system



Destination IP address:

Metasploitable target system



Destination Port:

22 (SSH)



Additional log analysis confirmed repeated failed login attempts in the system authentication logs.



\---



\## Tools Used



Kali Linux

Medusa

Security Onion

Suricata

Kibana

Wireshark



\---



\## MITRE ATT\&CK Mapping



Technique:



T1110 — Brute Force



T1046 — Network Service Discovery



\---



\## Outcome



The simulated attack successfully generated detectable network activity.



Security Onion identified the attack behavior and produced alerts that allowed investigation of the incident.



This lab demonstrates practical SOC analyst skills in threat detection, monitoring, and investigation.



\---



\## Screenshots



\* SSH Scan Alert Detected

\* Alert Details View

\* Kibana Query Results

\* Failed Login Attempts



