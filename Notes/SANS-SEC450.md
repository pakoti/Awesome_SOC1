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





## NSM Data

• Network extraction
• Routers and switches
• Network firewalls
• IDS/IPS/NDR
• Proxy
• Web application firewalls
• Service logs
• DHCP, DNS, HTTP(S), SMTP, SMB,
FTP, SSH, Kerberos, etc.



## Endpoint and App Data

• Authentication logs
• Antivirus, HIDS/HIPS, EDR
• Process command line
• Executables
• Vulnerability scanners
• DLP
• Application access logs
• Application audit logs



## Common sources for network data include:

• Network extraction tools like Zeek
• NetFlow from routers and switches
• Firewall logs that may contain block/allow actions or, in the case of "next-gen firewalls", actual Layer 7 application info
• IDS/IPS or NDR (network detection and response) logs with a rule name that matched and a potential recording of the traffic itself
• Proxy logs that can tell which user was going to which site, including Layer 7 attributes such as URLs and HTTP methods
• Service logs from servers running things like Apache, Windows/BIND DNS, or DHCP




## Endpoint data information:

• Authentication data showing successful and failed login attempts
• Antivirus logs showing files identified as malicious
• Host IDS/IPS logs that may show which files were modified, or if any suspicious processes were created
• Process creation logs to describe how each new process was created
• Application and System informational and error logs
• Digital Loss Prevention logs, which may show how users moved files or interacted with sensitive data
• Access logs for an application, requests made to a web server 
• Audit logs created for an application

## defensible networks requires 2 Things
and remeber Centralization of data is crucial.
1. Network Monitoring
2. Endpoint and application data monitoring

## Events, Alerts, and Incidents
based on NIST SP800-61
<ul>
<li>Events: Any observable occurrence in a system or network</li>
<li>Alerts: An event of interest that may be unwanted or unauthorized</li>
<li>Incidents: A violation or imminent threat of violation of computer security policies, acceptable use policies,or standard security practices</li>
</ul>

## How Much Should I Collect?
more is good but remember it is costly and it will takes too much time to search in logs.


<p align="center">
  <img src="/Notes/img/event-log-flow.jpg" >
</p>


## Alerts types:

1. Known-bad signatures
2. Anomaly-based



## Incident Management Systems – Systems View

<p align="center">
  <img src="/Notes/img/ims-system-view.jpeg" >
</p>

## PlayBooks

<p align="center">
  <img src="/Notes/img/PlayBook.jpeg">
</p>


## Threat Definition
 combination of intent, capability and opportunity.

• Intent is a malicious actor’s desire to target your organization
• Capability is their means to do so (such as specific types of malware)
• Opportunity is the opening the actor needs (such as vulnerabilities, whether it be in software, hardware, or personnel)

<p align="center">
  <img src="/Notes/img/cti-diagram.jpeg" >
</p>


## TIP Workflow

<p align="center">
  <img src="/Notes/img/tip-workflow.jpeg" >
</p>



## Storing and Sharing Threat Intelligence In a Safe Way: De-fanged Indicators
Because we gather live ips and real threat just when you want to present these things!!! just do it in a safe way ...

## A SIEMs Job

SIEM duties:
• Receive all log data
• Parse it correctly
• Filter unwanted events
• Enrich useful events with additional data
• Index log into database
• Fast searching
• Visualization and dashboard creation
• Analytics and correlation for alerting

<p align="center">
  <img src="/Notes/img/siem-jobs.jpeg">
</p>

## Hacktivism

Common goals:
• DDoS
• Site defacement
• Data theft and release
• Doxing
• Reputation damage


## Dividing Attacks into Two General Types
Smaller scope, less expensive Likely will not halt your organization.targeted(bigger) scope is Disruptive/expensive problems Highest priority!!
<p align="center">
  <img src="/Notes/img/2SCOPE.jpeg">
</p>


## Opportunistic Attackers

• Adversary Goal: High-volume, untargeted compromise
• Strategy: Collect infected computers, control as botnet,leverage volume of devices as a method for accomplishing goal

Tactics:

• Malicious and scam email
• Web drive-by downloads
• Web scanning and exploitation
• Browser-based social engineering
• FakeAV/popups, etc.


## Targeted Attackers (APTs)

• Goal: Target people/organizations, get specific info, access specific systems, or disrupt YOUR business
• Strategy: Attacks tailored to you and your organization

Tactics:

• Spear-phishing
• Watering holes (strategic web compromise)
• People/physical attack (social-engineering, USB)
• Targeted service-side exploitation and zero-days
• "Double extortion"


## Network monitoring concepts and attack detection



## What is 802.1X used for?
802.1X is an IEEE standard framework for encrypting and authenticating a user who is trying to associate to a wired or wireless network















## All Pictures in one glance

<p align="center">
  <img src="/Notes/img/Course1.jpeg" alt="what and How Much Should I Collect?">
</p>


<p align="center">
  <img src="/Notes/img/Course2.jpeg" alt="what and How Much Should I Collect?">
</p>