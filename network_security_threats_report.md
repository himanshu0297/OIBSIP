# Common Network Security Threats

## Author

**Name:** Himanshu Ajay Bhartiya

---

# Introduction

Network security refers to the set of policies, practices, and technologies designed to protect the confidentiality, integrity, and availability of data as it travels across or resides within computer networks. It encompasses hardware and software mechanisms such as firewalls, intrusion detection systems, encryption protocols, and access control policies that work together to prevent unauthorized access, misuse, or disruption of network resources.

In recent years, network security threats have increased significantly due to the rapid expansion of internet connectivity, the growing adoption of cloud services, remote work infrastructure, and the proliferation of Internet of Things (IoT) devices. Attackers now have a wider attack surface to exploit, and the tools required to launch attacks have become more accessible, even to individuals with limited technical expertise. Additionally, the increasing value of digital data has made networks attractive targets for financially motivated cybercriminals, hacktivists, and state-sponsored actors.

Protecting computer networks is critical because a single successful attack can lead to data breaches, financial losses, reputational damage, and operational downtime. For organizations, robust cybersecurity is no longer optional; it is a fundamental requirement for maintaining customer trust, ensuring regulatory compliance, and safeguarding business continuity. Understanding common network threats is the first step toward building effective defense strategies, which is the primary objective of this report.

---

# 1. DoS / DDoS Attack

## Definition

A **Denial-of-Service (DoS)** attack is a malicious attempt to disrupt the normal functioning of a targeted server, service, or network by overwhelming it with excessive traffic or requests. A **Distributed Denial-of-Service (DDoS)** attack is an amplified version of this, where the attack traffic originates from multiple compromised systems, often forming a botnet, making it significantly harder to block.

## How it Works

Attackers flood the target system with an overwhelming volume of requests, consuming its bandwidth, processing power, or memory resources. As legitimate resources become exhausted, genuine users are unable to access the service, resulting in downtime or severe performance degradation.

## Types of DDoS

- **Volumetric Attack** – Floods the network with massive amounts of traffic to consume all available bandwidth.
- **Protocol Attack** – Exploits weaknesses in network protocols (such as TCP/IP) to exhaust server resources, for example SYN flood attacks.
- **Application Layer Attack** – Targets specific applications, such as web servers, by overwhelming them with seemingly legitimate HTTP requests.

## Real-World Example

In 2016, the **Mirai Botnet** compromised hundreds of thousands of insecure IoT devices, such as routers and cameras, and used them to launch a massive DDoS attack against **Dyn**, a major DNS provider. This attack disrupted access to popular platforms including **Twitter, Netflix, and Reddit** for several hours.

## Impact

- Service downtime and loss of availability
- Financial losses due to interrupted business operations
- Damage to brand reputation and customer trust
- Increased operational costs for incident response

## Prevention and Mitigation

- **Rate Limiting** – Restrict the number of requests a client can make within a specific time frame to prevent traffic floods from overwhelming servers.
- **Web Application Firewall (WAF)** – Deploy a WAF to filter and monitor incoming HTTP traffic, blocking malicious requests before they reach the application.
- **Content Delivery Networks (CDN) and Load Balancing** – Distribute traffic across multiple servers and geographic locations to absorb large traffic spikes and maintain service availability.
- **DDoS Protection Services** – Utilize specialized cloud-based DDoS mitigation services that can detect and filter malicious traffic in real time.

---# Common Network Security Threats

## Author

**Name:** Himanshu Ajay Bhartiya

---

# Introduction

Network security refers to the set of policies, practices, and technologies designed to protect the confidentiality, integrity, and availability of data as it travels across or resides within computer networks. It encompasses hardware and software mechanisms such as firewalls, intrusion detection systems, encryption protocols, and access control policies that work together to prevent unauthorized access, misuse, or disruption of network resources.

In recent years, network security threats have increased significantly due to the rapid expansion of internet connectivity, the growing adoption of cloud services, remote work infrastructure, and the proliferation of Internet of Things (IoT) devices. Attackers now have a wider attack surface to exploit, and the tools required to launch attacks have become more accessible, even to individuals with limited technical expertise. Additionally, the increasing value of digital data has made networks attractive targets for financially motivated cybercriminals, hacktivists, and state-sponsored actors.

Protecting computer networks is critical because a single successful attack can lead to data breaches, financial losses, reputational damage, and operational downtime. For organizations, robust cybersecurity is no longer optional; it is a fundamental requirement for maintaining customer trust, ensuring regulatory compliance, and safeguarding business continuity. Understanding common network threats is the first step toward building effective defense strategies, which is the primary objective of this report.

---

# 1. DoS / DDoS Attack

## Definition

A **Denial-of-Service (DoS)** attack is a malicious attempt to disrupt the normal functioning of a targeted server, service, or network by overwhelming it with excessive traffic or requests. A **Distributed Denial-of-Service (DDoS)** attack is an amplified version of this, where the attack traffic originates from multiple compromised systems, often forming a botnet, making it significantly harder to block.

## How it Works

Attackers flood the target system with an overwhelming volume of requests, consuming its bandwidth, processing power, or memory resources. As legitimate resources become exhausted, genuine users are unable to access the service, resulting in downtime or severe performance degradation.

## Types of DDoS

- **Volumetric Attack** – Floods the network with massive amounts of traffic to consume all available bandwidth.
- **Protocol Attack** – Exploits weaknesses in network protocols (such as TCP/IP) to exhaust server resources, for example SYN flood attacks.
- **Application Layer Attack** – Targets specific applications, such as web servers, by overwhelming them with seemingly legitimate HTTP requests.

## Real-World Example

In 2016, the **Mirai Botnet** compromised hundreds of thousands of insecure IoT devices, such as routers and cameras, and used them to launch a massive DDoS attack against **Dyn**, a major DNS provider. This attack disrupted access to popular platforms including **Twitter, Netflix, and Reddit** for several hours.

## Impact

- Service downtime and loss of availability
- Financial losses due to interrupted business operations
- Damage to brand reputation and customer trust
- Increased operational costs for incident response

## Prevention and Mitigation

- **Rate Limiting** – Restrict the number of requests a client can make within a specific time frame to prevent traffic floods from overwhelming servers.
- **Web Application Firewall (WAF)** – Deploy a WAF to filter and monitor incoming HTTP traffic, blocking malicious requests before they reach the application.
- **Content Delivery Networks (CDN) and Load Balancing** – Distribute traffic across multiple servers and geographic locations to absorb large traffic spikes and maintain service availability.
- **DDoS Protection Services** – Utilize specialized cloud-based DDoS mitigation services that can detect and filter malicious traffic in real time.

---# 4. DNS Poisoning (DNS Spoofing)

## Definition

**DNS Poisoning** is an attack in which false information is inserted into a DNS cache, causing users to be redirected to fake or malicious websites instead of legitimate ones.

## How it Works

Attackers manipulate DNS records so that when a user enters a genuine website address, they are redirected to a malicious website designed to steal sensitive information.

## Real-World Example

Cybercriminals have targeted banking websites by redirecting users to fake login pages, resulting in stolen usernames, passwords, and financial information.

## Impact

- Redirects users to malicious websites
- Theft of personal and financial information
- Malware distribution
- Loss of trust in online services

## Prevention and Mitigation

- Enable DNSSEC
- Use trusted DNS servers
- Regularly clear DNS cache
- Monitor DNS traffic for suspicious activity

---

# Comparison Table

| Threat | Primary Target | Main Impact | Prevention |
|--------|----------------|-------------|------------|
| DoS / DDoS | Servers & Networks | Service disruption | Rate Limiting, WAF, CDN |
| MITM | Communication | Data theft | HTTPS, VPN, MFA |
| IP Spoofing | Network Traffic | Identity masking | ACLs, Packet Filtering |
| DNS Poisoning | DNS Servers | Fake website redirection | DNSSEC, Trusted DNS |

---

# Conclusion

Network security threats continue to evolve and can seriously affect organizations and individuals. Attacks such as **DoS/DDoS, Man-in-the-Middle, IP Spoofing, and DNS Poisoning** can cause data loss, financial damage, and service disruption. Implementing strong security measures such as firewalls, encryption, secure DNS, regular monitoring, and employee awareness can significantly reduce these risks.

### Key Takeaways

- Understand common network attacks and their impact.
- Apply preventive security measures and keep systems updated.
- Monitor network traffic regularly and follow cybersecurity best practices.

---

# References

1. National Institute of Standards and Technology (NIST) – https://csrc.nist.gov/
2. Cybersecurity and Infrastructure Security Agency (CISA) – https://www.cisa.gov/
3. MITRE ATT&CK Framework – https://attack.mitre.org/
4. SANS Institute – https://www.sans.org/
