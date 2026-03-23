\# Firewall Logging Lab



\*\*Objective:\*\*  

Detect and log SSH and ICMP (ping) attempts using iptables on Kali Linux.



\*\*Steps:\*\*  

1\. Configured iptables logging rules:

&nbsp;  - `iptables -A INPUT -p tcp --dport 22 -j LOG --log-prefix "SSH\_ATTEMPT: "`

&nbsp;  - `iptables -A INPUT -p icmp -j LOG --log-prefix "PING\_DETECTED: "`

2\. Monitored logs via `dmesg -w` and `journalctl -f -k`

3\. Simulated attacks:

&nbsp;  - SSH login attempts using PuTTY

&nbsp;  - ICMP ping from another machine



\*\*Outcome:\*\*  

\- Logs were generated for every attempted connection

\- Demonstrates capability to detect unauthorized access attempts

