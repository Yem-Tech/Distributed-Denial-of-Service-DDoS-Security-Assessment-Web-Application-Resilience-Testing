# Distributed Denial of Service (DDoS) Security Assessment & Web Application Resilience Testing

![Cybersecurity](https://img.shields.io/badge/Cybersecurity-DDoS%20Assessment-red?style=for-the-badge\&logo=securityscorecard)
![Platform](https://img.shields.io/badge/Platform-Kali%20Linux-blue?style=for-the-badge\&logo=kalilinux)
![Focus](https://img.shields.io/badge/Focus-Web%20Application%20Security-success?style=for-the-badge)
![MITRE ATT\&CK](https://img.shields.io/badge/MITRE-Impact%20Technique-critical?style=for-the-badge)

---

# 📌 Project Overview

This project demonstrates an authorized **Distributed Denial of Service (DDoS) Security Assessment** performed to evaluate the resilience of a web application and the effectiveness of a deployed **Web Application Firewall (WAF)** against traffic flooding attacks.

The assessment focuses on:

* Understanding DoS and DDoS attacks
* Evaluating Availability within the CIA Triad
* Testing WAF rate-limiting controls
* Monitoring web application resilience under stress
* Identifying deployed WAF technologies
* Reviewing MITRE ATT&CK impact techniques
* Implementing mitigation and remediation strategies

> ⚠️ **DISCLAIMER**
>
> This assessment was conducted strictly in an authorized testing environment for educational and defensive cybersecurity purposes only. Unauthorized DDoS activity against systems you do not own or have explicit permission to test is illegal and unethical.

---

# 🛡️ CIA TRIAD REFERENCE

Cybersecurity is built around three key principles:

| Principle       | Meaning                                                     |
| --------------- | ----------------------------------------------------------- |
| Confidentiality | Protecting sensitive information from unauthorized access   |
| Integrity       | Ensuring data remains accurate and unaltered                |
| Availability    | Ensuring systems and services remain accessible when needed |

This project specifically focuses on:

# 🔴 Availability

Availability ensures that users can access systems, applications, and services whenever required.

### Example Scenario

A customer attempts to withdraw money from a bank, but the banking application becomes unreachable due to network congestion or malicious traffic flooding.

Although the data still exists, the service becomes inaccessible.

This is an **Availability Compromise**, commonly associated with **DoS/DDoS attacks**.

---

# 📚 What is Denial of Service (DoS)?

A **Denial of Service (DoS)** attack occurs when a system or web application is flooded with traffic beyond its capacity, causing legitimate users to lose access to the service.

### Common Characteristics

* Single attacking source
* Traffic flooding
* Resource exhaustion
* Service degradation
* Application crashes
* HTTP 404/503 errors

---

# 🌐 What is Distributed Denial of Service (DDoS)?

A **Distributed Denial of Service (DDoS)** attack is similar to DoS, but traffic originates from multiple devices or IP addresses simultaneously.

This makes the attack:

* More powerful
* Faster
* Harder to mitigate
* More difficult to trace

---

# 🎯 MITRE ATT&CK REFERENCE

This assessment aligns with the **MITRE ATT&CK Impact Tactic**.

| Tactic | Technique                  |
| ------ | -------------------------- |
| Impact | Endpoint Denial of Service |
| Impact | Network Denial of Service  |

### Objective

To disrupt or degrade the availability of targeted resources and services.

---

# 🧪 SECURITY ASSESSMENT OBJECTIVES

The primary objective of this assessment is to determine:

* The strength of the deployed Web Application Firewall
* Whether rate-limiting mechanisms exist
* The resilience of the web application during traffic flooding
* How the infrastructure responds under attack conditions
* Whether endpoint services are properly protected

---

# 🖥️ ASSESSMENT ENVIRONMENT

| Component           | Technology                    |
| ------------------- | ----------------------------- |
| Operating System    | Kali Linux                    |
| Attack Tool         | Xerxes                        |
| WAF Detection Tool  | wafw00f                       |
| Testing Methodology | Authorized Offensive Security |
| Focus Area          | DDoS Resilience Testing       |

---

# ⚙️ TOOL USED — XERXES

**Xerxes** is a lightweight DoS stress testing tool commonly used in controlled environments to evaluate how systems react to traffic flooding.

---

# 📸 PROJECT WALKTHROUGH

# 1️⃣ Cloning the Xerxes Repository

```bash
git clone https://github.com/XCHADXFAQ77X/XERXES
```

### 📷 Attach Screenshot:[clone xerxes](https://github.com/Yem-Tech/Distributed-Denial-of-Service-DDoS-Security-Assessment-Web-Application-Resilience-Testing/blob/main/Screenshots/01-git_clone_xerxes_DDOS%20-%20Copy.png)

`01-git_clone_xerxes_DDOS - Copy(1).png`

---

# 2️⃣ Verifying Downloaded Files

```bash
ls
```

### 📷 Attach Screenshot:

`02-GIT_CLONE_XERXES_DDOS-ls - Copy(1).png`

---

# 3️⃣ Navigating into the Directory

```bash
cd XERXES
```

### 📷 Attach Screenshot:

`03-cd_XERXES - Copy(1).png`

---

# 🔨 Compiling Xerxes

```bash
gcc -o xerxes xerxes.c
```

---

# 🎯 Resolving the Target IP Address

```bash
ping halisans.com -c2
```

Resolved IP:

```text
66.29.153.49
```

### 📷 Attach Screenshot:

`04-halisans_IP_address(2).png`

---

# 🚀 Launching the DoS Simulation

### Command Syntax

```bash
./xerxes IP PORT
```

### Example

```bash
./xerxes 66.29.153.49 443
```

### Targeted Ports

| Port | Service |
| ---- | ------- |
| 80   | HTTP    |
| 443  | HTTPS   |

### 📷 Attach Screenshot:

`05-DOS_activated(2).png`

---

# 📈 Traffic Flood Observation

The generated traffic continuously floods the target application to test:

* Rate limiting
* WAF resilience
* Application availability
* Traffic handling capability

### 📷 Attach Screenshot:

`05-DoS_activated_2(2).png`

---

# 🔥 WEB APPLICATION FIREWALL (WAF) DETECTION

# Installing wafw00f

```bash
sudo apt install wafw00f
```

---

# Detecting the Firewall

```bash
wafw00f halisans.com
```

### Result

The target was identified as using:

* LiteSpeed Technologies WAF

### 📷 Attach Screenshot:

`06-Dos_wafw00f(2).png`

---

# 🧠 Recommended WAF Technologies

```bash
wafw00f -l
```

### 📷 Attach Screenshot:

`07-wafw00f_recommendation_(2).png`

### 📷 Attach Screenshot:

`08-WAF_DDoS_designedfor(2).png`

---

# 🛡️ OBSERVED WAF BEHAVIOR

During testing, the WAF demonstrated effective:

* Rate limiting
* Request throttling
* Traffic normalization
* Attack mitigation

### Key Observation

Traffic spikes increased aggressively but were repeatedly reduced by the firewall mechanisms.

This demonstrated:

* Active anti-DoS protection
* Automated request control
* Effective resilience engineering

Additionally, the web application remained accessible during testing, indicating strong service availability and defensive posture.

---

# 💻 ENDPOINT DENIAL OF SERVICE TESTING

DDoS testing can also target endpoint services such as:

| Service | Port |
| ------- | ---- |
| SSH     | 22   |
| RDP     | 3389 |

---

# 🔐 WINDOWS FIREWALL MITIGATION DEMONSTRATION

# Opening Inbound Firewall Rules

### 📷 Attach Screenshot:

`09-inbound_rule(1).png`

---

# Creating a New Firewall Rule

### 📷 Attach Screenshot:

`10-inbount_new_rules(2).png`

---

# Selecting TCP Ports

Blocked ports:

* 22 (SSH)
* 3389 (RDP)

### 📷 Attach Screenshot:

`11-ports_block_perm(2).png`

---

# Naming the Security Rule

### 📷 Attach Screenshot:

`12-ssh_rdp_port_(2).png`

---

# Confirmation of Blocked Ports

### 📷 Attach Screenshot:

`13-ssh_rdp_blocked_confirmed(2).png`

---

# 📊 KEY FINDINGS

| Assessment Area              | Observation                  |
| ---------------------------- | ---------------------------- |
| Web Application Availability | Maintained                   |
| WAF Presence                 | Confirmed                    |
| WAF Vendor                   | LiteSpeed Technologies       |
| Rate Limiting                | Effective                    |
| Traffic Mitigation           | Successful                   |
| Endpoint Exposure            | Mitigated via firewall rules |
| Application Resilience       | Strong                       |

---

# 🛠️ MITIGATION STRATEGIES

# 1️⃣ Ingress Traffic Filtering

Restrict inbound traffic to trusted IP ranges.

### Example

Allow SSH and RDP access only from authorized administrative networks.

---

# 2️⃣ Egress Traffic Filtering

Block unauthorized outbound communications.

### Example

Prevent connections to malicious command-and-control servers.

---

# 3️⃣ Protocol-Based Filtering

Restrict vulnerable or unnecessary protocols.

### Example

Disable SMBv1 to reduce exploitation risks.

---

# 4️⃣ Application Layer Filtering

Deploy Web Application Firewalls to inspect malicious HTTP/S requests.

### Example

* Block SQL injection attempts
* Mitigate abnormal traffic spikes

---

# 5️⃣ Network Segmentation

Separate critical systems into isolated VLANs.

### Benefits

* Reduced attack surface
* Improved containment
* Controlled lateral movement

---

# 🔐 SECURITY RECOMMENDATIONS

* Deploy enterprise-grade WAF solutions
* Enable adaptive rate limiting
* Implement CDN-based DDoS protection
* Use load balancing and traffic scrubbing
* Restrict administrative ports
* Monitor traffic anomalies continuously
* Enable SIEM logging and alerting
* Conduct periodic resilience testing

---

# 🧭 CONCLUSION

This project demonstrates how authorized DDoS simulations can be leveraged defensively to evaluate:

* Web application resilience
* Firewall effectiveness
* Rate-limiting capabilities
* Infrastructure availability under stress

The assessment confirmed that the tested environment successfully mitigated excessive traffic through active WAF protections and maintained service availability during simulated attack conditions.

---

# 📖 SKILLS DEMONSTRATED

* Offensive Security Testing
* DDoS Simulation
* Web Application Security
* WAF Analysis
* MITRE ATT&CK Mapping
* Linux Administration
* Firewall Configuration
* Security Hardening
* Network Security Monitoring
* Threat Mitigation

---

# 🏷️ TAGS

```text
#CyberSecurity
#DDoS
#DoS
#WAF
#KaliLinux
#Xerxes
#MITREATTACK
#OffensiveSecurity
#BlueTeam
#WebSecurity
#SOC
#ThreatDetection
```

---

# 📌 GITHUB REPOSITORY DESCRIPTION

```text
Professional DDoS security assessment focused on availability testing, WAF analysis, endpoint protection, and mitigation strategies aligned with MITRE ATT&CK.
```

---

# 👨‍💻 AUTHOR

**Olayemi Owoeye**
Cybersecurity Analyst | Offensive Security | Security Operations | Threat Detection
