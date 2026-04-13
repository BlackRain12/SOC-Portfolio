DNS Tunneling Detection Lab — Security Onion

Overview



This lab simulates a DNS tunneling attack using dnscat2 and demonstrates detection through Zeek network telemetry in Security Onion without relying on IDS alerts.



The objective was to identify covert command-and-control activity using behavioral analysis rather than signature-based detection.



Lab Architecture



See:



architecture.png



Tools Used

Security Onion

Zeek

Suricata

Kali Linux

Ubuntu Server

dnscat2

Attack Simulation



A DNS tunneling channel was established between a Kali Linux client and an Ubuntu DNS server using dnscat2.



Commands were executed over DNS to simulate covert command-and-control communication.



Example commands:



whoami

ls

cat /etc/passwd



Detection Method



No Suricata alerts were generated.



Detection was achieved through manual analysis of Zeek DNS logs using the Security Onion Hunt interface.



Observed indicators:



Long DNS query names

DNS TXT record responses

Repeated DNS communication

Encoded payload patterns

Key Findings



Malicious DNS tunneling activity can exist without triggering IDS alerts.



Network telemetry analysis using Zeek provides visibility into covert communication channels.



This highlights the importance of proactive threat hunting in Security Operations Centers.



Skills Demonstrated



Threat Hunting

Network Traffic Analysis

DNS Protocol Analysis

Security Onion Investigation

Incident Detection Without Alerts



MITRE ATT\&CK Mapping



Technique:



T1071.004 — Application Layer Protocol: DNS



Screenshots



See the screenshots folder for investigation evidence.



Author

David Siaw-Darfour

SOC Analyst / Threat Hunter Portfolio Lab

