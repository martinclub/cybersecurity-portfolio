# Incident Report Analysis: DoS Attack on Multimedia Company

## Section 1: Identify
**Summary of the security event:**
The organization experienced a Denial of Service (DoS) attack that lasted for approximately two hours. The attack was characterized by a massive flood of ICMP packets directed at the internal network. This volume of traffic overwhelmed the network infrastructure, causing all internal network services to stop responding. As a result, employees and clients were unable to access critical network resources during the incident.

**Cause of the event:**
The investigation revealed that the attack was successful due to an unconfigured firewall. This vulnerability allowed a malicious actor to send unlimited ICMP "ping" requests into the network without any filtering or rate-limiting in place.

**Targeted Systems:**
*   Internal Network Infrastructure
*   Web and Graphic Design Servers
*   Internal Communication and Marketing Tools

**Impact:**
*   Two-hour total service outage.
*   Loss of productivity for all departments (Web Design, Graphic Design, Social Media Marketing).
*   Potential disruption to client-facing services and deadlines.

---

## Section 2: Protect
**Immediate Action Plan:**
To mitigate the risk of future DoS attacks, the following technical controls and procedures must be implemented:
*   **Firewall Hardening:** Implement a new firewall rule specifically designed to limit the rate of incoming ICMP packets (Rate Limiting).
*   **IP Verification:** Enable source IP address verification on the firewall to identify and block spoofed IP addresses, which are commonly used in DoS attacks to bypass simple filters.
*   **Security Configuration Baseline:** Establish a mandatory configuration audit for all new and existing firewalls to ensure no device is left in an "unconfigured" or default state.

---

## Section 3: Detect
**Monitoring and Detection Strategy:**
The organization will enhance its visibility into network traffic to identify suspicious patterns before they lead to an outage:
*   **Network Monitoring Software:** Deploy software to establish a baseline of "normal" traffic. This will allow for the immediate detection of abnormal spikes in traffic volume or unusual protocol usage (like excessive ICMP).
*   **IDS/IPS Implementation:** Integrate an Intrusion Detection/Prevention System (IDS/IPS) to automatically filter out ICMP traffic that exhibits suspicious characteristics or originates from known malicious sources.
*   **Alerting Protocols:** Configure automated alerts to notify the cybersecurity team when traffic thresholds are exceeded, enabling a faster response time.

---

## Section 4: Respond
**Response and Containment Plan:**
The goal of the response plan is to neutralize threats quickly and analyze the "how" and "why" to prevent recurrence:
*   **Containment:** The incident management team will continue the practice of blocking offending traffic types (e.g., ICMP) and temporarily taking non-critical services offline to preserve bandwidth for critical operations.
*   **Analysis:** Utilize logs from the firewall and the new monitoring software to trace the origin and methodology of the attack.
*   **Incident Neutralization:** Once the source is identified and blocked, verify the integrity of the network before bringing all services back online.
*   **Process Improvement:** Conduct a "Post-Incident Review" (PIR) after every major event to update response playbooks and refine firewall rules based on real-world data.

---

## Section 5: Recover
**Recovery and Restoration:**
To ensure a smooth return to normal operations:
*   **Service Prioritization:** Restore critical business services first (client web design platforms, primary databases) followed by non-critical internal tools.
*   **Data Integrity Check:** While DoS attacks primarily affect availability, verify that no secondary breaches or data corruption occurred during the period of network instability.
*   **Continuous Monitoring Post-Recovery:** Maintain high-alert monitoring for 24-48 hours after the incident to ensure no "aftershocks" or follow-up attacks occur.
*   **Stakeholder Communication:** Provide a summary report to management and relevant clients explaining the resolution and the steps taken to prevent future occurrences.
