\# Investigation Notes — SSH Brute Force Detection Lab



\## Analyst



David Siaw-Darfour



\## Date



06/04/2026



\## Lab Title



SSH Brute Force Detection using Security Onion



\---



\## Objective



The purpose of this lab was to simulate an SSH brute force attack against a vulnerable system and detect the activity using network-based monitoring tools. The lab demonstrates the ability to identify suspicious network behavior, analyze alerts, and document security incidents.



\---



\## Environment Overview



Attacker System:

Kali Linux



Target System:

Metasploitable 2



Monitoring System:

Security Onion



Detection Tools:

Suricata (Network Intrusion Detection System)

Kibana (SIEM / Log Analysis)



Network Type:

Virtual Lab Environment



\---



\## Attack Description



A brute force attack was simulated against the SSH service running on the target machine using a password attack tool.



The attack generated multiple login attempts against port 22 (SSH), which resulted in abnormal network behavior detectable by the monitoring system.



The attack behavior included:



\* Repeated connection attempts to SSH

\* High number of authentication attempts

\* Rapid connection frequency

\* Suspicious scanning pattern



\---



\## Detection Summary



The monitoring system generated alerts indicating suspicious SSH activity.



Alert Name:



ET SCAN Potential SSH Scan OUTBOUND



Severity:



Medium



Category:



Network Scan / Brute Force Attempt



Detection Source:



Suricata Network Intrusion Detection System



\---



\## Observed Indicators



The following indicators were observed during the investigation:



Source IP Address:

Kali Linux attacker system



Destination IP Address:

Metasploitable target system



Destination Port:

22 (SSH)



Protocol:

TCP



Behavior Observed:



Multiple connection attempts

Repeated login attempts

High traffic volume to SSH service

Scanning behavior detected



\---



\## Investigation Steps



1\. Logged into the Security Onion management console



2\. Navigated to:



SOC → Alerts



3\. Identified alert:



ET SCAN Potential SSH Scan OUTBOUND



4\. Reviewed alert details including:



Source IP

Destination IP

Destination Port

Event timestamp



5\. Verified suspicious activity targeting SSH service



\---



\## Findings



The simulated brute force attack successfully generated detectable network activity.



Security Onion identified the attack behavior and produced alerts indicating a potential SSH scan.



Although system authentication logs were not accessible, network-based detection provided sufficient evidence of suspicious activity consistent with brute force behavior.



\---



\## MITRE ATT\&CK Mapping



Technique:



T1110 — Brute Force



T1046 — Network Service Discovery



\---



\## Lessons Learned



Network intrusion detection systems can identify suspicious behavior even without direct access to system logs.



Repeated connection attempts to critical services such as SSH can indicate brute force attacks.



Security monitoring tools provide visibility into network activity and support incident investigation.



\---



\## Recommendations



Enable centralized logging for authentication events.



Implement account lockout policies to prevent brute force attacks.



Monitor network traffic for abnormal connection patterns.



Deploy SIEM alerts for repeated login attempts.



\---



\## Conclusion



This lab demonstrated the successful detection of suspicious SSH activity using Security Onion.



The investigation confirmed that network-based monitoring tools can identify brute force behavior through traffic analysis and alert generation.



This exercise strengthened skills in threat detection, alert analysis, and incident documentation within a Security Operations Center (SOC) environment.



