# SANS Sec 450
Blue Teams and Operations


<ul>
<li> People: Mindset, mental models, career progression, burnout</li>
<li>Process: Analysis, investigation theory, triage, and data flow</li>
<li> Technology: Network and host monitoring, understanding protocols,spotting attacks, scripting and automation</li>
</ul>





## The problem is, SOC work can be tough…

<ul>
<li> High barrier to entry</li>
<li> Ticket/alert based, repetitive work</li>
<li> Tiered structure may limit visibility and scope</li>
<li> Over-prescribed workflow restricts freedom</li>
<li> Repetitive clicking and information filling</li>
<li> High turnover means "revolving door" of coworkers</li>
</ul>



## A modern defense is our only hope, this means:
<ul>
<li> Presumption of Compromise</li>
<li> Detection Oriented Defense</li>
<li> Proactive Detection: Hunt Teams</li>
<li> Post-Exploitation Focus</li>
<li> Response-Driven</li>
<li> Risk Informed Strategy</li>
</ul>




## The Components of Security Operations
<ul>
<li>People: Performing analysis and investigation, design and run processes</li>
<li>Process: The defined sequence of events performed to achieve an end goal</li>
<li>Technology: Hardware and software used to accomplish the mission</li>
</ul>

<p align="center">
  <img src="/Notes/img/soc-abstracted.jpeg" alt="soc abstracted">
</p>


## Four core questions 
1. What are we trying to protect?
2. What are the threats?
3. How do you detect them?
4. How will you respond?


## Tiered SOCs

1. Tier 1: Initial triage and analysis, ticket generation
2. Tier 2: Attack scoping,further analysis, tactical and remediation support
3. Tier 3: Deep analysis,methodology development, strategic support, hunting


## Tierless and Tiered SOCs

Neither is "right" – just optimized for different things

Tierless:
• Everyone works together to get everything done
• Must carefully manage alerts
• Even new analysts can use all available data and tools
• Stay engaged, learn quickly but must know limits
• Analysts more self-guided,teamwork crucial
• Senior and Lead titles for career progression

Tiered:
• Defined roles, clear path for promotion
• More structured processes, efficient handoffs and processing
• Often have less freedom to use all tools/data restrictions
• Less ability to explore and learn?
• Slow progression, repetitiveness may lead to retention issues

<p align="center">
  <img src="/Notes/img/soc-diagram.jpeg" alt="soc diagram">
</p>

## Core SOC Activities:
• Data Collection: What’s happening on the network/devices 
• Detection: Identifying items of interest from data collected,for example IDS,ANTI VIRUS,SIEM
• Triage and Investigation: Confirming and prioritizing detected issues
• Incident Response: Responding to and minimizing the impact of attacks <a href="/Notes/SANS-SEC504.md">Look Here for more</a>

<p align="center">
  <img src="/Notes/img/inside-soc.jpeg" alt="what soc structure look like!">
</p>


## Specialty/Auxiliary Capabilities:

• Threat Intelligence: Collecting information to improve attack detection
• Forensics: Supporting I.R. with deep research and reverse engineering
• Self-Assessment: Inventory, config monitoring, vuln. assessment, Red Team, etc



## Critical SOC Information

• Network diagram: Simplified version for easy reference
• Points of visibility: Taps and span ports, full PCAP
• Data flow diagram: How does traffic reach the internet?
• Log flow diagram: Where do logs come from/go?
• Incident response plan: What to do when things go wrong
• Communication plan: Who to inform, and when
• List of critical assets and points of contact
• Disaster recovery/business continuity plans
• Any other relevant policies, standards, procedures, guidelines


## defensible network is:

According to Richard Bejtlich these are standards that a modern network must meet in order to be defendable against a
modern adversary.

• Monitored: Network and host data is captured and centralized
• Inventoried: Knowing your network
• Controlled: Traffic ingress/egress, network connection access…
• Claimed: Owners of services known, operation of assets planned
• Minimized: System attack surface is reduced
• Assessed: Weaknesses identified, defenses tested
• Current: Patched and known vulnerabilities addressed
• Measured: SOC and IT measure progress against previous steps Gives you the chance to resist intrusion


## What Can You See on Your Network?
Consider your network data collection 
• Can you see high-level bandwidth statistics and traffic flow?
• Do you know which ports are actually in use?
• Which protocols are actually being used on those ports?
• What applications are being accessed with those services?
• Do you know which domains are being visited and by whom?
• Can you retrieve the full packet data from the transaction?
• Can you detect suspicious encrypted traffic?


## What is Network Security Monitoring (NSM)?
• Analyzing network traffic – "data in motion"
• Network Services: DNS, HTTP(S), SMB, RDP, FTP, SSH, etc.
• May be logged by an endpoint, or network sensor
• Using network data to Identifying suspicious behavior
• Exploit delivery
• Suspicious file transfers
• Internal network recon and pivoting
• Command and control traffic/Data exfiltration
• Suspicious usage of network protocols within your network

<p align="center">
  <img src="/Notes/img/company-network.jpg" alt="what company networks look like!">
</p>


## what should we look for in an endpoint?

<ul>
<li>installed unauthorized applications</li>
<li>scripts have been ran</li>
<li>exploits is the system vulnerable</li>
<li>any critical system files or configurations change</li>
<li>suspicious startup items</li>
<li>users logging in to the system</li>
</ul>


## Continuous Security Monitoring (CSM):

• Configuration and baseline monitoring
• Vulnerability scanning
• File/registry integrity monitoring
• Running processes, Services
• Autorun items
• Application Logs
• Access and authentication logs
• Activity audit logs


## Endpoint collection sources:

• Security suite logging
• EDR, XDR, endpoint protection suites
• Antivirus, HIDS/HIPS
• Vuln. Scanner, FIM, Application Control
• Operating System & Application Logs
• Authentication logs
• Service and process logging
• Autorun items
• Application access and audit logs

