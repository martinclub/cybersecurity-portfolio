# Internal Security Audit Report: Botium Toys

## Scope and Goals
**Scope:** The entire security program at Botium Toys, including all assets, internal processes, and procedures related to controls and compliance.

**Goals:** Assess existing assets, complete a controls and compliance checklist, and identify improvements to enhance the company's security posture.

---

## Controls Assessment Checklist

| Control | In Place? | Explanation |
| :--- | :---: | :--- |
| **Least Privilege** | No | All employees currently have access to customer data; privileges must be restricted to reduce breach risks. |
| **Disaster recovery plans** | No | No plans are in place, which threatens business continuity in the event of a disaster. |
| **Password policies** | Yes | Requirements are nominal/weak, making it easier for threat actors to compromise accounts. |
| **Separation of duties** | No | CEO manages day-to-day operations and payroll; needs implementation to reduce fraud risks. |
| **Firewall** | Yes | Successfully blocks traffic based on defined security rules. |
| **Intrusion detection system (IDS)** | No | Required to help identify and alert on possible intrusions by threat actors. |
| **Backups** | No | Critical data is not backed up, posing a major risk to recovery and business continuity. |
| **Antivirus software** | Yes | Installed and regularly monitored by the IT department. |
| **Manual monitoring (Legacy)** | Yes | Monitored, but lacks a regular schedule and clear intervention policies. |
| **Encryption** | No | Not used; implementation is vital for the confidentiality of sensitive financial/personal data. |
| **Password management system** | No | Absence affects productivity and security; implementation would enforce stronger policies. |
| **Locks (Physical)** | Yes | Sufficient locks are in place for offices, storefront, and warehouse. |
| **CCTV surveillance** | Yes | Functioning surveillance is installed at the physical location. |
| **Fire detection/prevention** | Yes | Functioning fire alarms and sprinkler systems are present. |

---

## Compliance Checklist

### Payment Card Industry Data Security Standard (PCI DSS)
| Best Practice | Adhered? | Explanation |
| :--- | :---: | :--- |
| Authorized access only to CC info | No | All employees currently have access to internal data. |
| Secure CC processing environment | No | Lack of encryption and broad access creates an insecure environment. |
| Data encryption procedures | No | Confidentiality of financial info is not ensured through encryption. |
| Secure password management | No | Policies are weak and no management system is in place. |

### General Data Protection Regulation (GDPR)
| Best Practice | Adhered? | Explanation |
| :--- | :---: | :--- |
| EU customer data kept private | No | Lack of encryption fails to ensure data confidentiality. |
| 72-hour breach notification plan | Yes | A plan is already established to notify EU customers. |
| Data classified and inventoried | No | Assets are inventoried but not yet classified by sensitivity. |
| Enforced privacy policies | Yes | Policies are developed and enforced among the IT team and staff. |

### System and Organizations Controls (SOC type 1, SOC type 2)
| Best Practice | Adhered? | Explanation |
| :--- | :---: | :--- |
| User access policies established | No | Lack of Least Privilege and Separation of Duties policies. |
| Sensitive data (PII/SPII) private | No | Encryption is missing to ensure PII/SPII confidentiality. |
| Data integrity (Validation) | Yes | Controls are in place to ensure data consistency and accuracy. |
| Data availability to authorized users | Yes | Data is available, but access needs to be restricted to *only* authorized users. |

---

## Recommendations

The audit identifies several critical gaps that result in a **Risk Score of 8/10**. To improve security posture and meet compliance (PCI DSS, GDPR, SOC), Botium Toys should prioritize:

1.  **Technical Controls:**
    *   Implement **AES Encryption** for data at rest and in transit.
    *   Deploy an **Intrusion Detection System (IDS)**.
    *   Establish an automated **Backup schedule** and a **Disaster Recovery Plan**.
    *   Adopt a **Centralized Password Management System**.

2.  **Administrative Controls:**
    *   Enforce the **Principle of Least Privilege** and **Separation of Duties**.
    *   Formalize a **Legacy System Maintenance** schedule.
    *   Conduct **Data Classification** to properly protect SPII/PII.

3.  **Compliance Alignment:**
    *   Restrict access to cardholder data to meet PCI DSS requirements.
    *   Ensure all EU customer data handling aligns with GDPR confidentiality standards through technical safeguards.
