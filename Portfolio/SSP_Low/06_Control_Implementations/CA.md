# 06. Control Implementations – CA: Security Assessment and Authorization  
APJ SecureCloud – FedRAMP Low (LI-SaaS)

APJ SecureCloud undergoes continuous assessment through monitoring, logging,
and vulnerability evaluation of its SaaS-layer components. Azure Government
(IL2) provides the underlying FedRAMP-authorized infrastructure, including
networking, identity, compute, and storage services. All infrastructure-level
controls are inherited from Azure Gov’s FedRAMP package.

APJ maintains SaaS-layer controls, evidence, POA&M entries, and ConMon
deliverables to support Low-Impact SaaS authorization.

---

# **CA-1 – Security Assessment and Authorization Policies and Procedures**

APJ maintains a Security Assessment & Authorization Policy that defines:

- The process for creating and maintaining the SSP  
- Required supporting documentation (inventory, diagrams, risk register)  
- Assessment responsibilities for SaaS components  
- Expectations for working with FedRAMP PMO and 3PAO (if pursuing authorization)  
- Annual and ongoing assessment requirements  
- POA&M management  
- Evidence retention requirements  

Policy stored in:  
`Portfolio/M365_Security/Policies/Security_Assessment_and_Authorization_Policy.md`

---

# **CA-2 – Security Assessments**

APJ conducts recurring security assessments:

### **Annual SaaS Assessment**
- Review SSP accuracy  
- Validate control implementations  
- Update risk posture  
- Capture new threats or design changes  

### **Quarterly Reviews**
- Dependency vulnerabilities  
- Sentinel analytic rule effectiveness  
- PIM usage patterns  
- Log ingestion integrity  
- CI/CD pipeline security scans  
- Identity Protection signals  

### **Automated Assessments**
Using:
- Microsoft Defender for Cloud  
- Azure Advisor  
- Sentinel analytic rules  
- GitHub/Azure DevOps code scanning  

Assessment artifacts stored at:  
`Portfolio/Assessments/Annual/`  
`Portfolio/Assessments/Quarterly/`

---

# **CA-2(1) – Independent Assessors**

When required (e.g., for FedRAMP authorization):

- A 3PAO is engaged for independent evaluation  
- APJ provides SSP, POA&M, diagrams, and evidence  
- APJ supports interviews and technical walkthroughs  
- Azure Gov evidence is provided separately from Microsoft’s FedRAMP package  

Until APJ pursues authorization, this control is satisfied through readiness testing.

---

# **CA-3 – System Interconnections**

APJ documents all interconnections in:

`Portfolio/SSP_Low/05_Shared_Responsibility_Matrix/`  
`Portfolio/SSP_Low/Diagrams/Data_Flow_Diagram.png`

### **Allowed Interconnections**
- Azure Gov identity services (Entra ID)  
- Azure Storage  
- Key Vault  
- Log Analytics  
- Sentinel  
- Azure DevOps / GitHub (for CI/CD)

### **Not Allowed**
- External systems storing content  
- Third-party unmanaged databases  
- Unvetted integration services  

No customer systems interconnect directly with APJ SecureCloud.

---

# **CA-5 – Plan of Action and Milestones (POA&M)**

APJ maintains a fully structured POA&M:

- Uses FedRAMP-style fields and scoring  
- Tracks vulnerabilities, misconfigurations, and control gaps  
- Includes SaaS-layer remediation plans  
- Reviews remediation status monthly  
- Updates tied to quarterly ConMon submissions  

POA&M stored at:  
`Portfolio/POAM/POAM.xlsx`

Sample entries include:
- Outdated library vulnerabilities  
- Sentinel analytic rule tuning backlog  
- IaC policy-as-code drift findings  
- Configuration issues detected by Defender for Cloud  

---

# **CA-6 – Security Authorization**

As a SaaS provider operating on Azure Gov IL2:

### **Azure Gov Authorization**
- Already FedRAMP authorized  
- Provides inherited security controls  
- Covers physical, environmental, and infrastructure protections  

### **APJ Authorization (When applicable)**
- APJ prepares SSP and supporting artifacts  
- Submits package to Agency or FedRAMP PMO (for LI-SaaS)  
- Responds to reviewer comments  
- Tracks remediation in POA&M  
- Provides monthly ConMon reporting  

At this stage, APJ is preparing for authorization (“pre-assessment posture”).

---

# **CA-7 – Continuous Monitoring**

APJ implements continuous monitoring across:

### **Identity**
- Daily review of Risky Users  
- PIM elevation anomalies  
- Conditional Access failures  

### **Infrastructure (Inherited)**
- Azure Gov health and compliance  
- Built-in Defender for Cloud signals  

### **SaaS Layer**
- Sentinel log coverage  
- Log ingestion gaps  
- Detection rule quality  
- API usage anomalies  
- RBAC review (quarterly)  
- Dependency vulnerability scanning  
- IaC drift detection  
- Secret expiration and rotation monitoring  

### **Monthly ConMon Submission Elements**
- Executive summary  
- Updated POA&M items  
- New vulnerabilities  
- Major detections/incidents  
- Evidence package (screenshots, exports)  

All ConMon reports stored at:  
`Portfolio/ConMon/Monthly/`

---

# **CA-7(1) – Automation Support for Continuous Monitoring**

APJ uses:

- Sentinel Automation Rules  
- Logic Apps (Respond + Notify)  
- Microsoft Defender for Cloud automated recommendations  
- DevOps/GitHub CI alerts  
- Azure Monitor alerts  
- Automated drift detection (Terraform/Bicep)  
- Key Vault secret expiration alerts  

Automation outputs feed directly into:  
`Portfolio/POAM/POAM.xlsx`  
`Portfolio/Risk/Register.xlsx`

---

# **CA-8 – Penetration Testing (NOT REQUIRED for LI-SaaS)**

FedRAMP LI-SaaS does **not require formal penetration testing**.

However, APJ performs:

### SaaS-layer security testing
- Static Code Analysis (SAST)  
- Dependency Scanning (SCA)  
- CI/CD pipeline integrity testing  
- Sentinel detection tuning  

Azure Gov infrastructure pen-testing is covered under Microsoft’s FedRAMP package.

External penetration testing can be performed if required by an Agency sponsor.

---

# **CA-9 – Internal System Connections**

APJ documents all internal SaaS connections:

- App Service ↔ Key Vault  
- App Service ↔ Log Analytics  
- Sentinel ↔ Log Analytics  
- Sentinel ↔ Azure Monitor  
- CI/CD ↔ Azure Resource Manager  
- App Service ↔ Azure Identity (Managed Identity)

These connections are represented in:  
`Portfolio/SSP_Low/Diagrams/Data_Flow_Diagram.png`

Connections must satisfy:
- TLS 1.2+  
- Managed Identity or certificate auth  
- Private endpoints when supported  

---

# End of CA Control Family
