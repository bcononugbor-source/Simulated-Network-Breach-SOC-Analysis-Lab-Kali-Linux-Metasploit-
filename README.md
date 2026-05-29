# Simulated-Network-Breach-SOC-Analysis-Lab-Kali-Linux-Metasploit-
Simulated a full network breach in Kali Linux using Metasploit, covering exploitation, persistence, and lateral movement. Established reverse shell access, maintained control via cron, and analysed indicators of compromise using Linux tools, demonstrating both offensive and SOC-level defensive skills.
Simulated Network Breach & SOC Analysis Lab (Kali Linux + Metasploit + Wazuh SIEM)

 ##Project Overview

This project demonstrates a full end-to-end simulation of a network breach within a controlled lab environment using Kali Linux and Metasploit Framework, with all activities centrally monitored and captured through Wazuh.

The objective was to replicate real-world attacker behaviour across the cyber kill chain while simultaneously validating SOC detection, alerting, and MITRE ATT&CK mapping through centralized log analysis.

All attacker actions were ingested, correlated, and visualised in Wazuh, enabling full visibility of persistence, privilege escalation attempts, account creation, and lateral movement.

##The lab covers:

Initial access simulation
Reconnaissance and enumeration
Exploitation via reverse shell payloads
Post-exploitation and credential discovery
Persistence mechanisms
Lateral movement between users
SIEM-based detection and forensic analysis (Wazuh)
Full system cleanup

## Key Skills Demonstrated
Offensive Security (Red Team fundamentals)
Defensive Security (SOC detection and threat hunting)
SIEM analysis and alert interpretation in Wazuh
Linux system administration and process analysis
Threat detection using native Linux tools
MITRE ATT&CK framework mapping and interpretation
Incident investigation and IOC identification

## Lab Environment
Attacker Machine: Kali Linux
Target: Simulated local Linux users
SIEM: Wazuh (central log collection + alerting)

## Tools Used:

Metasploit Framework
msfvenom
Netcat
Linux native utilities (ps, crontab, ls, etc.)
Wazuh agent + dashboard

## Execution Breakdown (Fully SIEM-Monitored)
1. Initial Access Simulation
Created a low-privilege user (victim)
Generated reverse shell ELF payload using msfvenom
Deployed payload into user directory
Wazuh Visibility: User creation + file activity logs captured and indexed

2. Reconnaissance & Enumeration
Performed local port scanning using Metasploit auxiliary modules
Identified exposed services on the host system

 Wazuh Visibility: Network and system scan behaviour mapped to MITRE reconnaissance tactics

3. Exploitation & Session Establishment
Configured Metasploit handler
Executed payload under victim context
Established Meterpreter session

 Wazuh Visibility: Execution traces and process creation events captured

4. Post-Exploitation (Credential Access)
System enumeration (getuid, sysinfo)
Simulated credential discovery in user space

 Wazuh Visibility: Suspicious shell activity and file access events logged

5. Privilege Escalation Attempt
Attempted privilege escalation via Meterpreter (getsystem)
Attempt failed (no exploitable vector present)

 Wazuh Visibility: Privilege escalation behaviour mapped to MITRE ATT&CK detection rules

6. Persistence Mechanism
Established cron-based persistence (crontab -e)
Payload executed every minute

 Wazuh Visibility:

Cron job modification detected
Scheduled task persistence flagged in MITRE ATT&CK dashboard
High-risk persistence behaviour logged and correlated

7. Lateral Movement Simulation
Created second user (lateral)
Deployed separate payload
Executed and established additional session

 Wazuh Visibility:

New account creation detected
sudo-based user switching logged
Cross-user execution behaviour correlated as lateral movement
8. Detection & Threat Hunting (SOC Perspective)

All attacker actions were investigated using Linux tools and fully validated in Wazuh:

crontab -l → persistence detection
ps aux → malicious process identification
/home directory analysis → suspicious binaries
sudo logs → privilege switching analysis

 Key Indicators of Compromise (IOCs):

Unauthorized cron persistence
Suspicious ELF execution in user directories
Privilege escalation attempts (sudo -u)
Lateral movement between user accounts
Reverse shell activity

9. Cleanup & System Restoration
Removed cron jobs, payloads, and users
Restored system to baseline state

 Wazuh Context: Cleanup ensured no persistent alerts remained active in SIEM environment

## Key Takeaways
All attacker actions were fully observable through Wazuh
Persistence, privilege escalation, and lateral movement were successfully mapped to MITRE ATT&CK
SIEM correlation significantly improves visibility of attack chains
Linux native tools combined with SIEM provide strong SOC investigation capability

## Standout Highlights
End-to-end Red Team + Blue Team simulation in one environment
Full SIEM visibility using Wazuh for every attack phase
MITRE ATT&CK mapping across all detected behaviours
SOC-style investigation using native Linux + centralized logs
Demonstrated real-world detection of persistence and lateral movement

## Future Improvements
Deploy Wazuh rules tuning for higher severity correlation
Add external network pivot simulation
Integrate Suricata or Zeek for network-level detection
Automate IOC detection dashboards inside Wazuh

## Conclusion

This lab demonstrates a complete cyber kill chain simulation with full SIEM visibility using Wazuh. It highlights both offensive attack techniques and defensive detection workflows, providing practical SOC and penetration testing experience aligned with real-world security operations.
