<h1>Azure Honeynet: SOC Simulation Real-World Cyber Attacks</h1>

![image alt](https://github.com/tranxjason/Azure/blob/0b7f9e0f6b605894cf9d2a0168864c983a470888/azure%20honenet.jpg)

<h2>Description</h2>
In this project, a honeynet is created using Microsoft Azure to attract real-world traffic from attackers across the globe. The primary objective is to showcase security practices in cybersecurity, incident response strategies, and the impact of hardening a networked environment. To achieve this, virtual machines are deliberately deployed without protections, exposing them to the public internet and inviting malicious activity. After collecting logs into a Log Analytics Workspace, Microsoft Sentinel is used to generate attack maps, alerts, and incident reports. This setup allows us to compare metrics before and after implementing security hardening, based on incidents captured over a 24-hour period.
<br />


<h2>Azure Components Utilized</h2>

- <b>Azure Virtual Network (VNet)</b> 
- <b>Azure Network Security Group</b>
- <b>Virtual Machines (2x Windows, 1x Linux)</b>
- <b>Log Analytics Workspace with Kusto Query Language (KQL) Queries</b>
- <b>Azure Key Vault for Secure Secrets Management</b>
- <b>Azure Storage Account for Data Storage</b>
- <b>Microsoft Sentinel for Security Information and Event Management (SIEM)</b>
- <b>Microsoft Defender for Cloud to Protect Cloud Resources</b>

<h2>Methodology</h2>

- <b>*Creating the honeynet:* Began by deploying multiple vulnerable virtual machines in Azure, simulating an insecure environment.</b>


- <b>*Monitoring and analysis:* Azure was configured to ingest log sources from various resources into a log analytics workspace. Microsoft Sentinel was then used to build attack maps, trigger alerts, and create incidents based on the collected data.</b>


- <b>*Security metrics measurement:* Observed the environment for 24 hours, recording key security metrics while it was insecure. This provided a baseline to compare against after implementing remediation measures.</b>


- <b>*Incident response and remediation:* After addressing the incidents and identifying vulnerabilities, I began the process of hardening the environment by applying security best practices and Azure-specific recommendations.</b>


- <b>*Post-remediation analysis:* Re-observed the environment for another 24 hours to measure security metrics again, comparing the results with the initial baseline.</b>
  
<h2>Architecture Prior to Implementing Hardening Measures and Security Controls</h2>

![image alt](https://github.com/tranxjason/Azure/blob/0863ef447cfd8ee41be521132cfd82091bc119e4/architecture%20before.jpg)

- <b>In the "BEFORE" stage of the project, all resources were initially deployed with public exposure to the internet. This setup was intentionally insecure to attract potential cyber attackers and observe their tactics. The Virtual Machines had both their Network Security Groups (NSGs) and built-in firewalls wide open, allowing unrestricted access from any source. Additionally, all other resources, such as storage accounts and databases, were deployed with public endpoints visible to the internet, without utilizing any Private Endpoints for added security.</b>

This attack map showcases the number of incidents generated by leaving the Network Security Group (NSG) open

![image alt](https://github.com/tranxjason/Azure/blob/243e3c9ae9987f003ba935f8aeb7ba983ce45127/nsg.jpg)

This attack map highlights the incidents for syslog authentication failures experienced by the Linux server.

![image alt](https://github.com/tranxjason/Azure/blob/5be56244a8d7171834f46faf3abd8c4d97ac1e7a/syslog.jpg)

This attack map showcases RDP and SMB failures against the Window machine.

![image alt](https://github.com/tranxjason/Azure/blob/5be56244a8d7171834f46faf3abd8c4d97ac1e7a/syslog.jpg)

This attack map showcases failures against the MSSQL server.

![image alt](https://github.com/tranxjason/Azure/blob/6a666566d6633d5e8c8bbb6182d34a039a498dba/mssql.jpg)

<h2>Architecture After Implementing Hardening Measures and Security Controls</h2>

![image alt](https://github.com/tranxjason/Azure/blob/0863ef447cfd8ee41be521132cfd82091bc119e4/architecture%20after.jpg)
In the "After" stage, based off the incidents created from the "Before" 24 hour capture, hardening measures and security controls were implemented to improve the environment's security from attackers.

These improvements included:

- <b>*Network Security Groups (NSGs):* Hardened the NSGs by only allowing my own public IP address to come thrugh otherwise all other traffic would be blocked by the new parameteres created.</b>

- <b>*Built-in Firewalls:* In the virtual machines, configured the built-in firewalls so that it would deny access from unauthorized users.</b>

- <b>*Private Endpoints:* For other Azure resources, replaced the public endpoints with private endpoints. This ensured that access to sensitive resources, such as storage accounts and databases, was limited to only the virtual network.</b>

<h2>Attack Maps After Hardening/Security Controls</h2>


`All map queries actually returned no results due to no instances of malicious activity for the 24 hour period after hardening.`


<h2>Metrics Before Hardening/Security Controls</h2>

The following table shows the metrics we measured in our insecure environment for 24 hours:
Start Time 2023-05-03 09:15 AM
Stop Time 2023-05-04 09:15 AM

| Metric                                 | Count |
|----------------------------------------|-------|
| SecurityEvent (Windows VM)             | 4358  |
| Syslog (Linux VM)                      | 2345  |
| SecurityAlert (Microsoft Defender for Cloud) | 6     |
| SecurityIncident (Sentinel Incidents)  | 73    |
| NSG Inbound Malicious Flows Allowed    | 103   |

<h2>Metrics After Hardening/Security Controls</h2>

The following table shows the metrics we measured in our secure environment for 24 hours:
Start Time 2023-05-04 4:25 PM
Stop Time 2023-05-05 4:25 PM

| Metric                                 | Count |
|----------------------------------------|-------|
| SecurityEvent (Windows VM)             | 2364  |
| Syslog (Linux VM)                      | 24    |
| SecurityAlert (Microsoft Defender for Cloud) | 0     |
| SecurityIncident (Sentinel Incidents)  | 0     |
| NSG Inbound Malicious Flows Allowed    | 0     |

<h2>Utilizing NIST 800.61r2 Computer Incident Handling Guide</h2>

For each simulated attack practiced incident responses following NIST SP 800-61r2.

![image alt](https://github.com/tranxjason/Azure/blob/83751934fd6b4ec91a1c580a66851dd2e5253fa7/irl%20cycle.jpg)

Each organization will have policies related to an incident response that should be followed. This event is a walkthrough for possible actions to take in the detection of malware on a workstation.

Preparation

- <b>The Azure lab was set up to ingest all of the logs into the Log Analytics Workspace, Sentinel and Defender were configured, and alert rules were put in place.</b>

Detection & Analysis

- <b>Malware has been detected on a workstation with the potential to compromise the confidentiality, integrity, or availability of the system and data.</b>
- <b>Assigned alert to an owner, set the severity to "High", and the status to "Active".</b>
- <b>Identified the primary user account of the system and all systems affected.</b>
- <b>A full scan of the system was conducted using up-to-date antivirus software to identify the malware.</b>
- <b>Verified the authenticity of the alert as a "True Positive".</b>
- <b>Sent notifications to appropriate personnel as required by the organization's communication policies.</b>

Containment, Eradication & Recovery 

- <b>The infected system and any additional systems infected by the malware were quarantined.</b>
- <b>If the malware was unable to be removed or the system sustained damage, the system would have been shut down and disconnected from the network.</b>
- <b>Depending on organizational policies the affected systems could be restored known clean state, such as a system image or a clean installation of the operating system and applications. Or an up-to-date anti-virus solution could be used to clean the systems.</b>

Post-Incident Activity

- <b>In this simulated case, an employee had downloaded a game that contained malware.</b>
- <b>All information was gathered and analyzed to determine the root cause, extent of damage, and effectiveness of the response.</b>
- <b>Report disseminated to all stakeholders.</b>
- <b>Corrective actions are implemented to remediate the root cause.</b>
- <b>A lessons-learned review of the incident was conducted.</b>

<h2>Conclusion</h2>

A small honeynet was deployed in Microsoft Azure, with log sources integrated into a Log Analytics workspace. Microsoft Sentinel was utilized to monitor the environment by generating alerts and incidents based on ingested log data. Metrics were collected in the unsecured environment, and again after applying security controls. The noticeable decrease in security events and incidents following the implementation of these controls demonstrates their effectiveness in protecting the environment.

It's important to note that if the network resources had been actively used by regular users, the number of security events and alerts observed during the 24-hour post-hardening period could have been higher.











<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
