# Common Network Security Threats
## Author
**name:** Himanshu Ajay Bhartiya  

---

## Introduction
In today's hyper-connected digital landscape, network security is a critical pillar of modern cybersecurity infrastructure. As organizations migrate sensitive data, critical services, and proprietary operations to networked environments, the surface area for potential security breaches has expanded exponentially. Sophisticated threat actors constantly exploit vulnerabilities in network protocols, hardware configurations, and human factors to compromise confidentiality, integrity, and availability. Understanding common network security threats, their execution methodologies, real-world ramifications, and actionable defense mechanisms is essential for maintaining robust systems, protecting user data, and ensuring operational continuity across enterprises worldwide.

---

## 1. Denial of Service (DoS) / Distributed Denial of Service (DDoS) Attacks

### Explanation of How It Works
A **Denial of Service (DoS)** attack aims to render a target service, server, or network resource unavailable to its intended users by overwhelming it with a flood of malicious traffic or exploiting protocol vulnerabilities. A **Distributed Denial of Service (DDoS)** attack amplifies this threat by leveraging a distributed network of compromised devices (a "botnet") controlled remotely by the attacker. DDoS attacks typically operate across different network layers, including:
* **Volume-based attacks:** Flooding network bandwidth with massive volumes of traffic (e.g., UDP floods, ICMP floods).
* **Protocol attacks:** Consuming actual server resources or intermediate communication equipment like firewalls (e.g., SYN floods, Ping of Death).
* **Application-layer attacks:** Directing high volumes of requests at specific web applications to exhaust server processing capacity (e.g., HTTP GET/POST floods).

### Real-World Example
* **Incident:** *The 2016 Dyn Cyberattack*
* **Details:** In October 2016, major Domain Name System (DNS) provider Dyn was targeted by a massive DDoS attack executed through the Mirai botnet, which comprised hundreds of thousands of infected IoT devices (cameras, routers). The attack flooded Dyn's infrastructure with DNS lookup requests at rates estimated up to 1.2 Tbps, disrupting access to major platforms including Twitter, Netflix, Reddit, GitHub, and Spotify across North America and Europe.

### Impact
* **Operational Disruption:** Complete or partial downtime of mission-critical services and applications.
* **Financial Loss:** Revenue loss during downtime, costs incurred for emergency response, and potential SLA violation penalties.
* **Reputational Damage:** Loss of customer trust and brand credibility due to service unreliability.

### Specific Mitigation Strategies
1. **Deploy Anycast Routing & Cloud DDoS Protection:** Utilize cloud-based scrubbing services (such as Cloudflare, Akamai, or AWS Shield) that leverage Anycast routing to distribute incoming attack traffic across global data centers, absorbing and filtering volumetric floods before they reach the origin server.
2. **Implement Rate Limiting & Web Application Firewalls (WAF):** Configure rate limiting on load balancers, firewalls, and application gateways to cap the number of requests a single IP address can make within a given timeframe.
3. **Strict Network Perimeter & Protocol Hardening:** Implement SYN cookies to defend against SYN flood attacks, configure firewalls to drop spoofed/unrouted traffic, and drop incoming ICMP/UDP packets at the network edge when not strictly required.

---

## 2. Man-in-the-Middle (MITM) Attacks

### Explanation of How It Works
A **Man-in-the-Middle (MITM)** attack occurs when an attacker secretly intercepts, relays, and potentially alters the communication between two unsuspecting parties who believe they are communicating directly with each other. The attacker inserts themselves into the communication channel by exploiting insecure network protocols or unencrypted channels. Common vectors include:
* **ARP Spoofing/Poisoning:** Sending fake ARP messages over a Local Area Network (LAN) to associate the attacker's MAC address with the IP address of a legitimate gateway.
* **Rogue Wi-Fi Access Points:** Setting up malicious, unencrypted Wi-Fi hotspots ("Evil Twin") that mimic legitimate public networks to capture client traffic.
* **SSL/TLS Stripping:** Downgrading secure HTTPS connections to unencrypted HTTP using tools like Moxie Marlinspike’s SSLStrip.

### Real-World Example
* **Incident:** *Superfish Malware Pre-installation (Lenovo, 2015)*
* **Details:** Computer manufacturer Lenovo pre-installed software called "Superfish Visual Discovery" on consumer laptops. Superfish installed a self-signed root certificate authority (CA) into the Windows certificate store and used a single, easily cracked private key across all machines. This effectively allowed local attackers or untrusted networks to perform MITM attacks on HTTPS web traffic without triggering browser certificate warnings.

### Impact
* **Data Interception & Theft:** Exposure of sensitive credentials, personally identifiable information (PII), session tokens, and banking details.
* **Data Tampering:** Unauthorized modification of transmitted payload data (e.g., altering financial transfer destinations or inserting malicious code into HTTP downloads).
* **Session Hijacking:** Stealing active user session cookies to gain unauthorized access to user accounts.

### Specific Mitigation Strategies
1. **Enforce End-to-End Encryption (HTTPS/TLS 1.3):** Ensure all web communications use HTTPS with robust TLS configurations. Implement **HSTS (HTTP Strict Transport Security)** to force web browsers to strictly connect over encrypted channels only.
2. **Implement Dynamic ARP Inspection (DAI) & Port Security:** Network administrators should deploy DAI on managed switches to validate ARP packets against a DHCP snooping database, blocking malicious ARP spoofing attempts within local networks.
3. **Use Virtual Private Networks (VPNs) & Mutual Authentication:** Enforce the use of secure VPN tunnels when connecting over public networks, and implement **mTLS (Mutual TLS)** to authenticate both client and server before establishing connections.

---

## 3. IP Spoofing

### Explanation of How It Works
**IP Spoofing** is the creation of Internet Protocol (IP) packets with a forged source IP address for the purpose of impersonating another computer system or disguising the sender's identity. Because the basic IP protocol lacks inherent mechanism for verifying packet origin, attackers modify the header of an IP packet to make it appear as though it originated from a trusted internal host or a legitimate outside source. IP spoofing is commonly utilized in:
* **Reflective DDoS Attacks:** Sending requests with the target's IP address as the source to third-party servers (e.g., NTP, DNS, Memcached), causing those servers to direct massive response payloads to the target host.
* **Bypassing IP-Based Authentication:** Overriding access control lists (ACLs) that rely solely on source IP verification to grant administrative network access.

### Real-World Example
* **Incident:** *GitHub Memcached DDoS Attack (2018)*
* **Details:** In February 2018, GitHub was hit with a record-breaking DDoS attack reaching 1.35 Tbps. Attackers utilized IP spoofing to send small requests with GitHub's spoofed source IP address to publicly exposed Memcached servers running UDP port 11211. The Memcached servers responded with amplified data streams directed straight back to GitHub, causing significant traffic amplification (up to 50,000x).

### Impact
* **Amplified DDoS Capabilities:** Facilitates massive reflective DDoS attacks by obfuscating the attacker's true origin and abusing third-party services.
* **Unauthorized Access:** Grants malicious actors entry to restricted internal networks by faking trusted IP addresses.
* **Evasion of Forensic Tracking:** Complicates incident response and forensic analysis by obscuring the true origin of network packets.

### Specific Mitigation Strategies
1. **Implement BCP 38 / Ingress and Egress Filtering:** ISPs and enterprise network administrators must implement ingress and egress network filtering (RFC 2827 / BCP 38) to ensure that outgoing packets carry source IP addresses assigned exclusively to that local subnet and drop any illegitimate external IP headers.
2. **Disable IP Source Routing:** Disable IP source routing options on all enterprise routers and switches so attackers cannot specify the exact path a packet takes through the network.
3. **Cryptographic Network Authentication:** Transition away from IP-address-based authentication schemes in favor of strong cryptographic protocols like IPSec, SSH, or TLS that rely on public-key infrastructure and digital certificates.

---

## 4. DNS Poisoning / DNS Spoofing

### Explanation of How It Works
**DNS Poisoning** (also known as DNS Cache Poisoning or DNS Spoofing) is a form of network attack in which corrupt Domain Name System data is injected into a DNS resolver's cache. This causes the DNS server to return an incorrect IP address for a legitimate domain name. When users attempt to visit a trusted website (e.g., `bank.com`), the poisoned DNS resolver redirects their traffic to a malicious IP address hosted by the attacker. 

Attackers achieve this by guessing transaction IDs (XIDs) and flooding a recursive DNS resolver with forged response packets before the legitimate authoritative DNS server responds.

### Real-World Example
* **Incident:** *MyEtherWallet DNS Hijack (2018)*
* **Details:** Attackers executed a combined BGP route hijacking and DNS spoofing attack against Amazon’s Route 53 DNS servers. Users trying to access `myetherwallet.com` were seamlessly redirected to a fake server hosted in Russia that mirrored the legitimate cryptocurrency wallet site. Unaware of the spoofing, users entered their private keys, allowing attackers to steal approximately $150,000 in Ethereum within hours.

### Impact
* **Credential Harvesting & Phishing:** Users unknowingly supply sensitive credentials, passwords, and personal details to convincing clone websites.
* **Malware Distribution:** Threat actors can redirect domain traffic to servers that serve drive-by downloads or exploit kits.
* **Loss of Data Confidentiality:** Secure communications intended for legitimate domains can be intercepted and logged by malicious endpoints.

### Specific Mitigation Strategies
1. **Deploy DNSSEC (DNS Security Extensions):** Implement DNSSEC to add digital signatures to DNS records. DNS resolvers can then verify the cryptographic signature of the DNS response against trusted root keys, rejecting forged or tampered records.
2. **Implement DNS Resolver Hardening & Source Port Randomization:** Utilize modern DNS resolver software that randomizes source UDP ports alongside transaction IDs (UDP source port randomization), making it statistically improbable for attackers to inject forged responses.
3. **Use Trusted & Secure DNS Resolvers:** Configure network infrastructure to utilize secure DNS services that implement **DNS-over-HTTPS (DoH)** or **DNS-over-TLS (DoT)**, encrypting DNS queries to prevent local eavesdropping and cache injection.

---

## Comparison Table

| Threat / Attack Vector | Attack Vector | Target / Who is at Risk? | Difficulty to Execute | Ease of Mitigation |
| :--- | :--- | :--- | :--- | :--- |
| **DoS / DDoS** | Volumetric, Protocol, and Application Traffic Flooding | Web Applications, Data Centers, Online Platforms, Financial Services | Low to Medium (botnet-for-hire services available) | Medium (requires specialized cloud/scrubbing infrastructure) |
| **Man-in-the-Middle (MITM)** | ARP Poisoning, Rogue Access Points, SSL Stripping | Public Wi-Fi users, Unencrypted Web Traffic, Enterprise LANs | Medium (requires local network presence or tool sets) | Easy to Medium (solved primarily by mandatory HTTPS/TLS & network isolation) |
| **IP Spoofing** | Forged IP Packet Headers, UDP Reflection Amplification | Public Services, Network Infrastructure, Systems using IP-ACLs | Low to Medium | Easy to Medium (requires strict ISP/edge ingress & egress filtering) |
| **DNS Poisoning / Spoofing** | DNS Cache Injection, BGP Hijacking, Transaction ID Guessing | Web Browsers, Enterprise DNS Resolvers, Online Banking/E-commerce | Medium to High | Easy to Medium (requires DNSSEC adoption and hardened resolvers) |

---

## Conclusion: 3 Key Takeaways for a Network Administrator

1. **Default to End-to-End Encryption Across All Channels:** Never rely on network-level perimeter boundaries alone. Enforce TLS 1.3, HTTPS with HSTS, and IPSec/VPNs across internal and external networks to neutralize MITM threats and reduce the impact of spoofing.
2. **Enforce Multi-Layered Defense-in-Depth:** No single security control deters all network threats. Combine network-edge filtering (BCP 38 ingress/egress filtering) with protocol-level protections (DNSSEC, DAI, Rate Limiting) and cloud-level scrubbing for DDoS resiliency.
3. **Harden Protocol Configurations & Eliminate Legacy Defaults:** Modernize legacy infrastructure by disabling weak protocols, randomizing UDP ports/transaction IDs, requiring strict authentication instead of IP-based ACLs, and enforcing continuous patch management across all networking equipment.

---

## References

1. **NIST (National Institute of Standards and Technology):** *Special Publication 800-81-2: Secure Domain Name System (DNS) Deployment Guide*. Available at: [https://nist.gov](https://nist.gov)
2. **CISA (Cybersecurity and Infrastructure Security Agency):** *Understanding and Responding to Distributed Denial-of-Service (DDoS) Attacks*. Available at: [https://cisa.gov](https://cisa.gov)
3. **SANS Institute:** *Reading Room - Understanding Man-in-the-Middle Attacks and Effective Countermeasures*. Available at: [https://sans.org/reading-room](https://sans.org/reading-room)
4. **MITRE ATT&CK Framework:** *Technique T1557 (Adversary-in-the-Middle) & Technique T1498 (Network Denial of Service)*. Available at: [https://attack.mitre.org](https://attack.mitre.org)
