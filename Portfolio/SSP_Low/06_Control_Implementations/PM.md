# 06. Control Implementations – PM: Program Management  
APJ SecureCloud – FedRAMP Low (LI-SaaS)

Because APJ SecureCloud operates a metadata-only SaaS on Azure Government IL2,
most Program Management controls (PM-family) are inherited from Microsoft’s
FedRAMP-authorized environment and do not require system-level implementation.

APJ implements program-level governance only where applicable to SaaS
operations, security oversight, and FedRAMP continuous monitoring.

---

# **PM-1 – Information Security Program Plan (Inherited + APJ)**

### **Inherited**
Azure Government maintains the overarching security program covering:
- Physical protections  
- Infrastructure management  
- Datacenter operations  
- Environmental safeguards  
- Supply chain protections  

### **APJ Responsibilities**
APJ SecureCloud maintains a lightweight security program that includes:
- SaaS-level policies  
- SSP ownership  
- Access control governance  
- Continuous monitoring reporting  
- Incident response lifecycle  
- AI governance (where applicable)  

Program plan is documented in:
`Portfolio/M365_Security/Policies/Security_Program_Plan.md`

---

# **PM-2 – Senior Information Security Officer (APJ)**

APJ designates a **Security Program Lead** responsible for:
- Approving SSP updates  
- Overseeing FedRAMP Low compliance  
- Reviewing ConMon reports  
- Supervising security operations  
- Interfacing with auditors  

No direct authority over Azure Gov infrastructure (inherited).

---

# **PM-3 – Information Security Resources (APJ)**

APJ allocates resources for:
- Sentinel maintenance  
- CI/CD security updates  
- IaC governance  
- IR activities  
- Review cycles  
- Policy creation and updates  

Azure Gov covers all physical, environmental, and hardware resources.

---

# **PM-4 – Plan of Action and Milestones (APJ)**

APJ maintains a POA&M that includes:
- Vulnerabilities  
- Remediation timelines  
- Responsible parties  
- Status tracking  
- Risk scoring  

POA&M files stored here:
`Portfolio/POAM/`

APJ tracks POA&M updates as part of ConMon submissions.

---

# **PM-5 – Information System Inventory (APJ)**

APJ maintains a metadata-only system inventory including:
- Storage accounts  
- App Services  
- Functions  
- Sentinel workspace  
- Key Vault instances  
- API components  

Inventory stored in:
`Portfolio/SSP_Low/04_Component_Inventory/`

Azure Gov maintains hardware inventory.

---

# **PM-6 – Information Security Measures of Performance (APJ)**

APJ tracks measurable security indicators such as:
- Sentinel alert volume  
- Mean time to detect (MTTD)  
- Mean time to respond (MTTR)  
- Log ingestion uptime  
- PIM elevation approvals  
- IaC pipeline compliance rate  

Dashboards stored here:
`Portfolio/Dashboards/`

---

# **PM-7 – Enterprise Architecture (Inherited)**

Azure Government provides all enterprise-level architecture for:
- Datacenter layout  
- Network segmentation  
- Compute/storage architecture  
- Shared cloud services  

APJ relies entirely on Azure Gov’s FedRAMP-approved architecture.

---

# **PM-8 – Critical Infrastructure Plan (Inherited)**

Azure Gov ensures:
- Service availability  
- National security-grade continuity planning  
- Critical infrastructure redundancy  

APJ inherits without modification.

---

# **PM-9 – Risk Management Strategy (APJ)**

APJ maintains a SaaS-level risk strategy that includes:
- Metadata-only classification  
- No PII storage  
- Low baseline control applicability  
- Azure Gov shared responsibility model  
- Annual risk assessment  
- AI risk considerations (if ML modules are used)

Risk documentation stored here:
`Portfolio/Risk/Register.xlsx`

---

# **PM-10 – Authorization Process (APJ)**

APJ supports authorization by:
- Maintaining the SSP  
- Providing evidence to assessors  
- Supporting FedRAMP Low audits  
- Submitting POA&M and ConMon packages  

Authorization is specific to SaaS boundary, not Azure infrastructure.

---

# **PM-11 – Mission / Business Process Definition (APJ)**

APJ defines the mission of SecureCloud as:

> Providing metadata-level insight and analytics without storing or processing customer content, operating as a secure, compliant SaaS in Azure Gov.

The business process includes:
- Log ingestion  
- Metadata correlation  
- Health analytics  
- Dashboard visualization  
- IR and ConMon support  

---

# **PM-12 – Insider Threat Program (Inherited + APJ)**

### **Inherited**
Azure Gov implements background screening, personnel monitoring, and physical
security controls to prevent insider threats.

### **APJ Responsibilities**
APJ implements:
- RBAC  
- PIM with approval workflow  
- Least-privilege access  
- Sentinel monitoring for anomalous admin activity  
- Annual training  

---

# **PM-13 – Security & Privacy Workforce (APJ)**

APJ ensures staff performing security functions have:
- Required training  
- Azure security knowledge  
- FedRAMP Low awareness  
- Role-based security responsibilities  

Training logs stored here:  
`Portfolio/Training/Records.xlsx`

---

# **PM-14 – Testing, Training, and Monitoring (APJ)**

APJ performs:
- Annual Incident Response tabletop exercises (evidence in IR folder)  
- Logging and monitoring reviews  
- Sentinel rule tuning  
- Quarterly RBAC reviews  

Evidence stored in:  
`Portfolio/Incident_Response/`

---

# **PM-15 – Contacts With Security Groups (APJ)**

APJ maintains relationships with:
- Microsoft support  
- Government cloud security contacts  
- FedRAMP PMO (when applicable)  
- Industry ISAC notifications  

---

# **PM-16 – Threat Awareness Program (APJ)**

APJ uses:
- Microsoft threat intelligence feeds  
- Defender for Cloud recommendations  
- Sentinel threat analytics  
- Alerts from CISA and MS-ISAC  

Threat awareness reports stored in:  
`Portfolio/Threat_Intel/`

---

# End of PM Control Family
