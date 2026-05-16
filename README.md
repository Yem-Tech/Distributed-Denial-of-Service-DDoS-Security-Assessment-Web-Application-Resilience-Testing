📌 Project Overview

This project demonstrates a Distributed Denial of Service (DDoS) Security Assessment performed within an authorized offensive security testing environment to evaluate the resilience of a web application and the effectiveness of its Web Application Firewall (WAF) against high-volume traffic attacks.

The assessment focuses on:

Understanding DoS and DDoS attacks
Evaluating availability within the CIA Triad
Testing rate-limiting controls
Identifying deployed Web Application Firewalls
Observing application resilience under stress
Reviewing MITRE ATT&CK impact techniques
Implementing mitigation and remediation strategies

⚠️ Disclaimer:
This assessment was conducted strictly in an authorized testing environment for educational and defensive cybersecurity purposes only. Unauthorized DDoS activity against systems you do not own or have explicit permission to test is illegal and unethical.

🛡️ CIA Triad Reference

Cybersecurity revolves around three major principles:

Principle	Meaning
Confidentiality	Protecting sensitive information from unauthorized access
Integrity	Ensuring data remains accurate and unaltered
Availability	Ensuring systems and data remain accessible when needed

This project specifically focuses on:

🔴 Availability

Availability ensures users can access systems, applications, and services whenever required.

Example:

A customer attempts to withdraw money from a bank, but the banking application becomes unreachable due to network congestion or malicious traffic flooding.

Although the data still exists, the service becomes inaccessible.

This is an availability compromise, commonly associated with DoS/DDoS attacks.

📚 What is Denial of Service (DoS)?

A Denial of Service (DoS) attack occurs when a system or web application is flooded with traffic beyond its capacity, causing legitimate users to lose access to the service.

Common Characteristics:
Single attacking source
Traffic flooding
Service degradation
Application crashes
HTTP 404/503 errors
Resource exhaustion
🌐 What is Distributed Denial of Service (DDoS)?

A Distributed Denial of Service (DDoS) attack is similar to DoS, but traffic originates from multiple devices or IP addresses simultaneously.

This makes the attack:

More powerful
Faster
Harder to mitigate
More difficult to trace
🎯 MITRE ATT&CK Reference

This activity aligns with the MITRE ATT&CK Impact Tactic.

Tactic	Technique
Impact	Endpoint Denial of Service
Impact	Network Denial of Service
Objective:

To disrupt or degrade the availability of targeted resources and services.

🧪 Security Assessment Objectives

The primary objective of this assessment is to determine:

The strength of the deployed Web Application Firewall
Whether rate-limiting mechanisms exist
The resilience of the web application during traffic flooding
How the infrastructure responds under attack conditions
Whether endpoint services are exposed and protected
🖥️ Assessment Environment
Component	Technology
Operating System	Kali Linux
Attack Tool	Xerxes
WAF Detection Tool	wafw00f
Testing Methodology	Authorized Offensive Security
Focus Area	DDoS Resilience Testing
⚙️ Tool Used — Xerxes

Xerxes is a lightweight DoS stress testing tool commonly used in controlled environments to evaluate how systems react to traffic floods.

📸 Project Walkthrough
1️⃣ Cloning the Xerxes Repository
git clone https://github.com/XCHADXFAQ77X/XERXES
<img width="100%" src="./01-git_clone_xerxes_DDOS%20-%20Copy(1).png">
2️⃣ Verifying Downloaded Files
ls
<img width="100%" src="./02-GIT_CLONE_XERXES_DDOS-ls%20-%20Copy(1).png">
3️⃣ Navigating Into the Directory
cd XERXES
<img width="100%" src="./03-cd_XERXES%20-%20Copy(1).png">
🔨 Compiling Xerxes
gcc -o xerxes xerxes.c
🎯 Target Identification

Before testing, the target IP address and port must be identified.

Example Case Study:
ping halisans.com -c2

Resolved IP:

66.29.153.49
<img width="100%" src="./04-halisans_IP_address(2).png">
🚀 Launching the DoS Simulation

Command syntax:

./xerxes IP PORT

Example:

./xerxes 66.29.153.49 443
Targeted Port:
Port	Service
80	HTTP
443	HTTPS
<img width="100%" src="./05-DOS_activated(2).png">
📈 Traffic Flood Observation

The generated traffic continuously floods the target application to test:

Rate limiting
WAF resilience
Application availability
Traffic handling capability
<img width="100%" src="./05-DoS_activated_2(2).png">
🔥 Web Application Firewall (WAF) Detection
Installing wafw00f
sudo apt install wafw00f
Detecting the Firewall
wafw00f halisans.com
Result:

The target was identified as using:

LiteSpeed Technologies WAF
<img width="100%" src="./06-Dos_wafw00f(2).png">
🧠 Recommended WAF Technologies

The following command lists supported and recommended WAF technologies:

wafw00f -l
<img width="100%" src="./07-wafw00f_recommendation_(2).png"> <img width="100%" src="./08-WAF_DDoS_designedfor(2).png">
🛡️ Observed WAF Behavior

During testing, the WAF demonstrated effective:

Rate limiting
Request throttling
Traffic normalization
Attack mitigation
Observation:

Traffic spikes increased aggressively but were repeatedly reduced by the firewall mechanisms.

This demonstrated:

Active anti-DoS protection
Automated request control
Effective resilience engineering

Additionally, the web application remained accessible during testing, indicating strong service availability and defensive posture.

💻 Endpoint Denial of Service Testing

DDoS testing can also target endpoint services such as:

Service	Port
SSH	22
RDP	3389
🔐 Windows Firewall Mitigation Demonstration
Opening Inbound Firewall Rules
<img width="100%" src="./09-inbound_rule(1).png">
Creating a New Inbound Rule
<img width="100%" src="./10-inbount_new_rules(2).png">
Selecting TCP Ports

Blocked ports:

22 (SSH)
3389 (RDP)
<img width="100%" src="./11-ports_block_perm(2).png">
Naming the Security Rule
<img width="100%" src="./12-ssh_rdp_port_(2).png">
Confirmation of Blocked Ports
<img width="100%" src="./13-ssh_rdp_blocked_confirmed(2).png">
📊 Key Findings
Assessment Area	Observation
Web Application Availability	Maintained
WAF Presence	Confirmed
WAF Vendor	LiteSpeed Technologies
Rate Limiting	Effective
Traffic Mitigation	Successful
Endpoint Exposure	Mitigated via firewall rules
Application Resilience	Strong
🛠️ Mitigation Strategies
1️⃣ Ingress Traffic Filtering

Restrict inbound traffic to trusted IP ranges.

Example:
Allow SSH and RDP access only from authorized administrative networks.
2️⃣ Egress Traffic Filtering

Block unauthorized outbound communications.

Example:
Prevent connections to malicious command-and-control servers.
3️⃣ Protocol-Based Filtering

Restrict vulnerable or unnecessary protocols.

Example:
Disable SMBv1 to reduce exploitation risks.
4️⃣ Application Layer Filtering

Deploy Web Application Firewalls to inspect malicious HTTP/S requests.

Example:
Block SQL injection attempts
Mitigate abnormal traffic spikes
5️⃣ Network Segmentation

Separate critical systems into isolated VLANs.

Benefits:
Reduced attack surface
Improved containment
Controlled lateral movement
🔐 Security Recommendations
Deploy enterprise-grade WAF solutions
Enable adaptive rate limiting
Implement CDN-based DDoS protection
Use load balancing and traffic scrubbing
Restrict administrative ports
Monitor traffic anomalies continuously
Enable SIEM logging and alerting
Conduct periodic resilience testing
🧭 Conclusion

This project demonstrates how authorized DDoS simulations can be leveraged defensively to evaluate:

Web application resilience
Firewall effectiveness
Rate-limiting capabilities
Infrastructure availability under stress

The assessment confirmed that the tested environment successfully mitigated excessive traffic through active WAF protections and maintained service availability during simulated attack conditions.

📖 Skills Demonstrated
Offensive Security Testing
DDoS Simulation
Web Application Security
WAF Analysis
MITRE ATT&CK Mapping
Linux Administration
Firewall Configuration
Security Hardening
Network Security Monitoring
Threat Mitigation
🏷️ Tags

#CyberSecurity #DDoS #DoS #WAF #KaliLinux #Xerxes #MITREATTACK #OffensiveSecurity #BlueTeam #WebSecurity #SOC #ThreatDetection

📌 Author

Gbemisola
Cybersecurity Analyst | Offensive Security | Security Operations | Threat Detection
