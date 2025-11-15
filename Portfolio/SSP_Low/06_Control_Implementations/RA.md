# 06. Control Implementations – RA: Risk Assessment  
APJ SecureCloud – FedRAMP Low (LI-SaaS)

APJ SecureCloud performs ongoing risk assessments covering system components,
identity configurations, metadata ingestion flows, CI/CD pipelines, and
dependencies inherited from Microsoft Azure Government (IL2).

The system does not process, store, or transmit customer content—APJ only
handles operational metadata. Risk assessments focus on the SaaS layer and not
the underlying infrastructure (inherited from Azure Gov’s FedRAMP authorization).

---

# **RA-1 – Risk Assessment Policy and Procedures**

APJ SecureCloud maintains a Risk Management Policy that defines:
- How risks are identified and categorized  
- Likelihood and impact scoring methodology  
- How risks enter the POA&M  
- Roles and responsibilities  
- Review cycles (quarterly + annually)  
- AI risk assessment alignment (NIST AI RMF)  

Policy location:  
`Portfolio/M365_Security/Policies/Risk_Assessment_Policy.md`

Procedures outline:
- How risks are logged in the Risk Register  
- When escalations occur  
- Documentation required for POA&M entries  

---

# **RA-2 – Security Categorization (FedRAMP Low)**

APJ SecureCloud is categorized as:

### **FIPS-199 Security Impact Level: LOW**
Justification:
- No customer content  
- No PII  
- Metadata-only insights  
- Cloud resources in Azure Gov IL2  
- SaaS only influences analytics and dashboards  

### **Information Types**
- System Metadata  
- Audit Logs  
- Operational Health Indicators  

Categorization reviewed annually and after:
- Major feature releases  
- New ingestion sources  
- Integration with third-party services  
- Introduction of ML/AI features  

Documentation stored in:  
`Portfolio/SSP_Low/03_System_Characteristics/`

---

# **RA-3 – Risk Assessment**

APJ performs formal risk assessments:

### **Quarterly**
- Review of new vulnerabilities  
- Sentinel/Defender analytics reports  
- PIM elevation anomalies  
- Failed login trends  
- IaC drift analysis  
- Audit log integrity checks  

### **Annually**
- Full system-wide risk posture review  
- Revalidation of FIPS-199 categorization  
- Update of AI Impact Assessment (if ML used)  

Risk sources include:
- Threat Intelligence (CISA + MSFT)  
- Azure Defender for Cloud  
- Sentinel analytics  
- CI/CD pipeline scanning  
- GitHub repository scanning (if applicable)  

Assessment artifacts stored here:  
`Portfolio/Risk/Assessments/`

---

# **RA-3(1) – Supply Chain Risk Assessment (APJ + Inherited)**

### APJ Responsibilities
- Assess third-party components included in the SaaS product  
- Review library vulnerabilities (SCA scans)  
- Validate Azure Marketplace or API dependencies  

### Inherited
Azure Gov handles:
- Hardware supply chain  
- Datacenter equipment sourcing  
- Infrastructure vendor management  

Results documented in:  
`Portfolio/Risk/Supply_Chain_Review.xlsx`

---

# **RA-4 – Risk Assessment Update**

APJ updates risk assessments:

- After major architecture changes  
- After significant vulnerability disclosures  
- After IaC pipeline security changes  
- After any SaaS-level incident  
- After fedRAMP or customer audit findings  

Version history maintained in:  
`Portfolio/Risk/Register.xlsx`

---

# **RA-5 – Vulnerability Monitoring & Scanning**

### **APJ Performs**
- Dependency scanning through CI/CD  
- Container image scanning (if used)  
- Code scanning for secrets and vulnerabilities  
- Sentinel/Defender detection of suspicious activity  

### **Azure Gov Provides**
- Host OS and hypervisor scanning  
- Network boundary vulnerability management  
- Infrastructure-level patching  

### **Sources**
- Microsoft Defender for Cloud  
- GitHub Advanced Security (if enabled)  
- Azure Security Center  
- CISA Known Exploited Vulnerabilities (KEV) feed  

### Remediation Requirements
- Critical: 24–72 hours  
- High: 7 days  
- Medium: 30 days  

All findings tracked in the POA&M:
`Portfolio/POAM/POAM.xlsx`

---

# **RA-7 – Risk Response**

APJ implements the following responses:

### **Risk Acceptance**
- Only permitted for Low severity  
- Requires justification in the Risk Register  

### **Risk Mitigation**
Common mitigation activities include:
- CI/CD fix  
- Sentinel rule adjustment  
- Key Vault rotation  
- Access revocation  
- App Service configuration hardening  

### **Risk Avoidance**
Where appropriate, APJ disables high-risk optional features.

### **Risk Transfer**
Not commonly used for SaaS systems, but supported via:
- Microsoft cloud shared responsibility  
- Vendor service contracts  

Documented in:  
`Portfolio/Risk/Register.xlsx`

---

# **RA-8 – Privacy Impact Assessment (Low Baseline – Not Required)**

Because APJ SecureCloud:
- Stores no PII  
- Processes no personal content  
- Analyzes only operational metadata  

A Privacy Impact Assessment (PIA) is **not required** under FedRAMP Low.

If this status changes, APJ will conduct a PIA aligned with NIST SP 800-122.

---

# End of RA Control Family
