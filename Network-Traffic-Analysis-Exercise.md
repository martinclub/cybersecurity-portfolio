# Cybersecurity Incident Report: Network Traffic Analysis

## Section 1: Identify the security incident

### Summary of the Problem
Several customers of a client company reported being unable to access the website `www.yummyrecipesforme.com`. When attempting to load the page, they received a "destination port unreachable" error. As a cybersecurity analyst, I was tasked with investigating the network traffic to determine the cause of this service interruption and identify which protocol was affected.

### Analysis of the Data (tcpdump Log Findings)
To troubleshoot the issue, I used the network analyzer tool `tcpdump`. The analysis of the captured packet data revealed the following:

- **Initial Request:** My computer (`192.51.100.15`) sent a **UDP** packet to the DNS server (`203.0.113.2`) on **port 53** to retrieve the IP address for the domain name.
- **Error Response:** Instead of a DNS resolution, the server returned an **ICMP** packet containing the error message: `udp port 53 unreachable`.
- **Timestamp:** The incident was recorded at `13:24:32.192571`.
- **Conclusion from Logs:** The request for an "A record" (mapping domain to IP) failed because the receiving DNS port was not listening for incoming traffic.

---

## Section 2: Analyze the incident

### Incident Root Cause
The root cause of the incident was a failure in the **DNS (Domain Name System)** service. While the network path to the server `203.0.113.2` was open (evidenced by the ICMP response), the DNS service on port 53 was either stopped, crashed, or misconfigured. Because the UDP message could not be delivered to port 53, the domain name could not be resolved to an IP address, preventing any further communication (like HTTPS requests) with the web server.

### Impact on the Organization
- **Availability:** The primary website was completely unavailable to the public, leading to a total service outage.
- **User Experience:** Customers were frustrated by the "destination port unreachable" error, which could lead to loss of traffic and business.
- **Technical Stall:** Without DNS resolution, all subsequent network protocols (TCP/HTTPS) were blocked from initiating, making the website non-functional for all users.

### Mitigation and Prevention
To resolve this incident and prevent future occurrences, the following steps are recommended:
1. **Service Recovery:** Restart the DNS daemon on the server and verify it is binding correctly to UDP port 53.
2. **Implementation of Redundant DNS:** Configure a secondary (backup) DNS server in the network settings so that if the primary server fails, resolution can still occur.
3. **Continuous Monitoring:** Implement automated monitoring for port 53. If the service stops responding, an alert should be sent immediately to the security or IT operations team.
4. **Firewall Rule Review:** Ensure that the firewall on the DNS server explicitly allows inbound UDP traffic on port 53 from authorized sources.

---
*Note: This report was developed as part of the Google Cybersecurity Professional Certificate.*