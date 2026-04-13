Lab Notes — DNS Tunneling Detection via Zeek (No Alerts)

Objective



Simulate DNS tunneling using dnscat2 and detect the activity using Zeek network telemetry in Security Onion without relying on IDS alerts.



Tools Used

Security Onion 2.4

Zeek

Suricata

Kali Linux

Ubuntu Server

dnscat2

Attack Simulation

Started dnscat2 server on Ubuntu DNS host

Connected Kali dnscat2 client to the DNS server

Established encrypted DNS tunnel

Executed commands over DNS



Commands executed:



whoami

ls

ip a

cat /etc/passwd



Detection Method



No Suricata alerts were triggered.



Investigation was performed using:



Security Onion → Hunt → Zeek DNS logs



Indicators observed:



Repeated DNS queries

Long encoded domain names

DNS TXT record responses

Continuous DNS communication pattern

Key Finding



DNS tunneling activity was successfully detected using Zeek telemetry analysis despite the absence of signature-based alerts.



This demonstrates the importance of behavioral analysis and threat hunting techniques in SOC environments.



Lessons Learned

Not all malicious activity generates alerts

Analysts must validate suspicious network behavior

Zeek logs provide deep visibility into DNS traffic

DNS tunneling can be detected through anomaly analysis

