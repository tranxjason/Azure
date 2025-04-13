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

<p align="center">
Launch the utility: <br/>
<img src="https://i.imgur.com/62TgaWL.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Select the disk:  <br/>
<img src="https://i.imgur.com/tcTyMUE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Enter the number of passes: <br/>
<img src="https://i.imgur.com/nCIbXbg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Confirm your selection:  <br/>
<img src="https://i.imgur.com/cdFHBiU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Wait for process to complete (may take some time):  <br/>
<img src="https://i.imgur.com/JL945Ga.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Sanitization complete:  <br/>
<img src="https://i.imgur.com/K71yaM2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Observe the wiped disk:  <br/>
<img src="https://i.imgur.com/AeZkvFQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
