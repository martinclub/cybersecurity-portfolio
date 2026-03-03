# Cybersecurity Incident Report: TCP SYN Flood Attack

## Section 1: Identify the security incident

### Attack Name
**TCP SYN Flood (Denial of Service - DoS)**

### Description of the Attack
The security incident was identified as a **TCP SYN Flood attack**. This is a type of Denial of Service (DoS) attack where a malicious actor sends a massive volume of TCP SYN (Synchronize) requests to a web server from an unfamiliar or spoofed IP address. 

The attacker exploits the standard **TCP three-way handshake** by requesting a connection but intentionally never sending the final ACK (Acknowledge) packet. This leaves the server's connection slots in a "half-open" state. As the server allocates resources for each request while waiting for a response that never arrives, its backlog queue becomes exhausted, preventing legitimate users from establishing a connection.

### Symptoms
- **System Alerts:** Automated monitoring systems triggered an alert indicating a critical problem with the web server's responsiveness.
- **User Impact:** Both employees and customers received "connection timeout" errors when attempting to access the sales and promotions webpage.
- **Packet Data:** Analysis using a packet sniffer revealed an abnormally large number of SYN requests originating from a single, unrecognized IP address, with no corresponding completion of the handshake process.

---

## Section 2: Analyze the incident

### Impact on the Organization
The attack had a severe negative impact on the travel agency's business operations and customer experience:
- **Service Disruption:** The primary sales platform became completely inaccessible, resulting in a total Denial of Service.
- **Operational Loss:** Employees were unable to perform their duties, specifically searching for vacation packages for clients, leading to a standstill in internal productivity.
- **Financial Loss:** Potential sales were lost during the downtime as customers could not view or book promotions.
- **Reputational Damage:** Frequent or prolonged outages can decrease customer confidence in the company’s digital infrastructure.

### Log Data Analysis
Based on the analysis of the `HTTP-log.xlsx` and the Wireshark packet capture guidance:
- **Traffic Pattern:** The logs show a repetitive and rapid sequence of SYN packets directed at the web server's ports (80/443).
- **Incomplete Handshakes:** There is a notable absence of ACK packets following the server's SYN-ACK responses. This pattern confirms that the traffic was not legitimate user behavior but a coordinated attempt to saturate server resources.
- **Source Identification:** The unfamiliar IP address was identified as the sole source of this flood, allowing for immediate (though temporary) blocking at the firewall level.

### Mitigation and Prevention (Suggested)
To prevent recurrence and strengthen the network's resilience, the following measures are recommended:
1. **Enable SYN Cookies:** This allows the server to keep track of connection requests without pre-allocating memory, effectively neutralizing the "half-open" state exploitation.
2. **Implement Rate Limiting:** Configure the network firewall to limit the number of SYN packets allowed from a single IP address within a specific timeframe.
3. **Firewall Hardening:** Regularly update firewall rules to identify and block spoofed IP addresses and known malicious ranges.
4. **Load Balancing:** Use a load balancer with built-in DDoS protection to filter out malicious traffic before it reaches the primary web server.

---
*Note: This report was developed as part of the Google Cybersecurity Professional Certificate.*