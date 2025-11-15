# 06. Control Implementations – SR: Supply Chain Risk Management  
APJ SecureCloud – FedRAMP Low (LI-SaaS)

APJ SecureCloud operates a metadata-only SaaS hosted entirely on Microsoft Azure
Government (IL2). APJ inherits all infrastructure, hardware, networking, and
datacenter supply chain protections from Azure Gov’s FedRAMP authorization.
APJ manages only SaaS-layer supply chain elements—software libraries, API
dependencies, CI/CD integrations, and cloud-native components used by the
platform.

---

# **SR-1 – Supply Chain Risk Management Policy and Procedures**

APJ maintains a Supply Chain Risk Management (SCRM) Policy that defines:

- Vendor assessment criteria  
- Requirements for FedRAMP-authorized IaaS/PaaS services  
- Secure acquisition practices  
- SBOM generation and dependency management  
- CI/CD code scanning requirements  
- Review and approval process for new third-party services  
- Risk escalation and POA&M documentation  

Policy location:  
`Portfolio/M365_Security/Policies/Supply_Chain_Risk_Management_Policy.md`

Procedures include:

- When vendor reviews are required  
- Required configuration and security documentation from suppliers  
- Acceptable use of open-source components  
- Steps for documenting supply chain findings in the Risk Register  

---

# **SR-2 – Supply Chain Risk Management Plan**

APJ’s SCRM Plan covers:

### **Scope**
- SaaS codebase  
- Application libraries  
- Secure CI/CD pipelines  
- Software dependencies  
- Third-party APIs  
- Marketplace services  
- Identity & logging integrations  

### **Plan Components**
- Annual supplier review  
- Quarterly dependency risk analysis  
- Sentinel-based anomaly monitoring  
- Azure Advisor and Defender for Cloud recommendations  
- Requirement to use only FedRAMP services for hosting  

Plan file:  
`Portfolio/SSP_Low/06_Control_Implementations/SCRM_Plan.md`

---

# **SR-3 – Supplier Agreements**

APJ ensures supplier agreements include:

- Security expectations  
- Logging and auditability  
- Support for incident notification  
- Requirements for vulnerability disclosure  
- Data handling restrictions  
- U.S. hosting requirements (where applicable)  

Azure Gov supplier agreements are inherited from Microsoft.

APJ maintains its own vendor records in:
`Portfolio/Vendor_Management/Vendor_List.xlsx`

---

# **SR-4 – Provenance**

APJ verifies the origin and trustworthiness of components including:

### **Open-Source Libraries**
- Checked through dependency scanning  
- Verified signatures when available  
- Reviewed for licensing compatibility  

### **CI/CD Tools**
- Azure DevOps (FedRAMP) or GitHub Enterprise  
- Pipeline security gates  

### **APIs**
- Must use secure authentication  
- Must provide documentation for audit  
- Must operate within U.S. boundaries (when applicable)  

Provenance review logs stored in:
`Portfolio/Vendor_Management/Provenance_Checks/`

---

# **SR-5 – Supply Chain Assessments**

APJ conducts:

### **Annual SCRM Review**
- Vendor risk ratings  
- Dependency vulnerability review  
- SBOM refresh  
- Cloud service shared-responsibility revalidation  

### **Quarterly Technical Reviews**
- SCA (Software Composition Analysis)  
- Secrets scanning  
- License audits  
- Sentinel monitoring for unusual dependency usage  

Assessment documents stored in:
`Portfolio/Risk/Supply_Chain_Review.xlsx`

---

# **SR-6 – Supplier Monitoring and Performance**

APJ monitors supplier performance via:

### **Azure Gov Signals (Inherited)**
- Regional service health  
- Outage notifications  
- Compliance changes  
- FedRAMP package updates  

### **APJ SaaS Monitoring**
- API response integrity  
- Unexpected permission changes  
- Security advisories from vendors  
- Changes in dependency risk ratings  
- Sentinel alerts on abnormal behavior of third-party integrations  

---

# **SR-7 – Supply Chain Operations Security**

APJ secures supply chain operations by:

### **CI/CD Security**
- Signed commits  
- Branch protection  
- Immutable audit logs  
- Approval workflows  
- Pipeline security gates  

### **IaC Protections**
- Drift detection  
- Template validation  
- Policy-as-Code enforcement  

### **Identity Controls**
- PIM for admin access  
- Least privilege roles  
- Managed Identity for service-to-service calls  

---

# **SR-8 – Notification Requirements**

APJ requires suppliers to notify APJ for:

- Security incidents  
- Compromised credentials  
- Significant architecture changes  
- Vulnerabilities impacting the SaaS boundary  

Microsoft provides this via the Azure Service Health & MSRC advisories.

---

# **SR-9 – Tamper Resistance and Detection (Inherited + APJ)**

Azure Gov provides:

- Hardware tamper detection  
- Secure boot  
- Firmware protections  
- Sensor-based detection for datacenter equipment  

APJ implements SaaS-layer tamper detection through:

- Sentinel alerts for unexpected config changes  
- Key Vault audit log review  
- Integrity checks in CI/CD  

---

# **SR-10 – Inspection of Supply Chain Components**

APJ performs software-level inspections:

- SBOM review  
- Dependency risk scoring  
- Signature validation  
- Code scanning  

Microsoft handles hardware-level inspection (inherited).

---

# **SR-11 – Component Disposal (Inherited)**

Azure Gov manages:

- Drive sanitization  
- Cryptographic erasure  
- Hardware destruction  
- Asset lifecycle disposal  

APJ does not manage physical assets.

---

# **SR-12 – Component Authenticity**

APJ ensures:

- Codebase integrity (via Git commit verification)  
- IaC template authenticity  
- Key Vault certificate chain validation  
- Dependency package authenticity (via vendor source & checksum)  

Azure Gov ensures authenticity of infrastructure components.

---

# **SR-13 – Supply Chain Security Training**

APJ personnel with development or acquisition roles receive training covering:

- Dependency management  
- Secure library usage  
- Vendor evaluation  
- Cloud shared responsibility  
- Secure CI/CD practices  

Records stored in:  
`Portfolio/Training/Training_Log.xlsx`

---

# **SR-14 – Criticality Analysis**

APJ performs criticality analysis of:

### **Critical SaaS Components**
- Key Vault  
- Log Analytics Workspace  
- App Service Platform  
- Sentinel SIEM  
- CI/CD pipelines  

### **Non-Critical Components**
- Helpdesk tools  
- Optional visualization libraries  
- Non-sensitive internal dashboards  

Criticality analysis stored in:  
`Portfolio/Risk/Criticality_Analysis.xlsx`

---

# End of SR Control Family
