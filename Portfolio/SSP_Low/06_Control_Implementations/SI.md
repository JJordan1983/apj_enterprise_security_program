# 06. Control Implementations – SI: System and Information Integrity  
APJ SecureCloud – FedRAMP Low (LI-SaaS)

APJ SecureCloud operates a metadata-only SaaS in Azure Government IL2 with no
customer content. SI controls focus on monitoring, alerting, and safeguarding
system metadata, SaaS code components, logging pipelines, APIs, and identity
infrastructure. All infrastructure-layer protections—including host patching,
malware scanning, hypervisor integrity, and network controls—are inherited
from Azure Government’s FedRAMP authorization.

---

# **SI-1 – System and Information Integrity Policy and Procedures**

APJ maintains a System and Information Integrity Policy addressing:

- Identification of anomalous activity  
- Allowable monitoring tools (Sentinel, Defender, Identity Protection)  
- Incident escalation requirements  
- Anti-malware expectations (inherited from Azure Gov)  
- Patch management for SaaS components  
- Log integrity protection  
- CI/CD and IaC scanning requirements  

Stored at:  
`Portfolio/M365_Security/Policies/System_Integrity_Policy.md`

---

# **SI-2 – Flaw Remediation**

### APJ Responsibilities  
APJ SecureCloud remediates flaws in SaaS-level components:

- Application code (scanned in CI/CD)  
- Libraries and dependencies (SCA scans)  
- App Service and Function configuration flaws  
- Sentinel and Log Analytics rules or connector issues  

### Timelines  
- **Critical:** 24–72 hours  
- **High:** 7 days  
- **Medium:** 30 days  

### Azure Gov Inherited  
- Host OS patching  
- Hypervisor patching  
- Physical system maintenance  
- Infrastructure firmware updates  

All findings are documented in the POA&M:  
`Portfolio/POAM/POAM.xlsx`

---

# **SI-3 – Malicious Code Protection (Inherited + APJ)**

### Inherited  
Azure Gov provides anti-malware protection on managed hosts using:

- Microsoft Antimalware  
- Defender for Cloud  
- Hypervisor-level protection  

### APJ SaaS-Layer Protections  
- CI/CD scanning for malicious packages  
- Dependency scanning  
- Blocklisted library detection  
- Sentinel alerts on suspicious API calls  
- No ability for executable uploads (no customer content)  

APJ does not run custom VMs, so no endpoint AV management is required.

---

# **SI-4 – Information System Monitoring**

APJ SecureCloud continuously monitors system activity using:

### **Microsoft Sentinel**
- Anomalous PIM activation  
- Repeated failed logins  
- Impossible travel detections  
- Audit log gaps  
- Defender for Cloud signals  
- Key Vault secret access anomalies  
- High-privileged role assignments  
- API abuse patterns  

### **Azure Activity Logs**
- Administrative changes  
- App Service configuration modifications  
- Resource deployments  
- Key Vault operations  

### **Identity Protection**
- Risky user signals  
- Compromised credentials  
- Token anomalies  

### Audit Dashboards
Stored in:  
`Portfolio/Dashboards/SIEM/`

---

# **SI-4(4) – Automated Tool Integration**

APJ integrates:

- Sentinel automation rules  
- Playbooks (Logic Apps)  
- Defender for Cloud automated recommendations  
- Service Health Alerts  
- GitHub/Azure DevOps scanning  

Automation outputs feed risk assessments and POA&M updates.

---

# **SI-4(5) – System-Wide Intrusion Detection**

System-wide detection is achieved through:

- Azure Gov intrusion detection systems  
- Sentinel UEBA (User and Entity Behavior Analytics)  
- Identity Protection risk scoring  
- Defender for Cloud host/network signals (inherited)  

APJ inherits infrastructure-level IDS but manages SaaS-level anomaly detection.

---

# **SI-5 – Security Alerts / Advisories / Directives**

APJ receives and processes:

- Microsoft Defender alerts  
- CISA KEV notices  
- Azure Security Center recommendations  
- Microsoft Security Response Center (MSRC) advisories  
- Sentinel analytic rule alerts  

APJ’s Security Program Lead triages and documents required actions,
including POA&M entries where applicable.

---

# **SI-7 – Software, Firmware, and Information Integrity**

APJ ensures integrity of:

### **Code & Dependencies**
- Git commit signatures  
- Branch protections  
- Mandatory pull request reviews  
- CI/CD scanning for tampering  

### **IaC Templates**
- Drift detection  
- Policy-as-Code enforcement  
- Terraform/Bicep validation  

### **Azure Resources**
- Activity log monitoring  
- Sentinel anomaly rules  

Azure Gov ensures infrastructure and hypervisor integrity.

---

# **SI-7(1) – Integrity Checks**

APJ performs:

- CI/CD integrity checks  
- SHA hash validation for critical files  
- Sentinel alerts on unauthorized modifications  
- Key Vault audit log monitoring  
- Application settings monitoring (App Service)  

Evidence stored in:  
`Portfolio/DevSecOps/Integrity_Checks/`

---

# **SI-8 – Spam Protection (NOT APPLICABLE)**

APJ SecureCloud:
- Does not send email externally  
- Does not operate messaging systems  
- Does not process inbound communications from customers  

SI-8 is Not Applicable.

---

# **SI-10 – Information Input Validation**

Although APJ stores no customer content, the application validates:

- API inputs  
- Authentication tokens  
- Metadata payload formats  
- Schema integrity for ingestion  
- Log EDM/structure validation in Log Analytics  

Defensive coding practices apply.

---

# **SI-11 – Error Handling**

APJ enforces:

- No sensitive data in error messages  
- Sanitized system exceptions  
- Logging of errors for auditability  
- App Service diagnostic logs enabled  

Errors cannot leak internal system details.

---

# **SI-12 – Information Output Handling and Retention**

Since APJ SecureCloud handles **metadata only**, output is restricted to:

- Health dashboards  
- Authentication insights  
- Sentinel and Log Analytics visualizations  
- Application operational metrics  

Retention is controlled by Log Analytics policies.

No PII or customer content exists in outputs.

---

# **SI-16 – Memory Protection (Inherited)**

Azure Gov provides:

- Kernel isolation  
- Hypervisor protections  
- Buffer overflow mitigations  
- Host memory protection  

APJ runs no custom VMs and inherits all memory protections.

---

# **SI-17 – Fail-Safe Procedures**

If system components fail, APJ ensures:

- Sentinel alerts for pipeline failure  
- Automatic retry behavior in Functions  
- Key Vault fallback mechanisms  
- Default-deny access behavior  
- Logging retained intact  

Fail-safe events trigger the IR workflow.

---

# End of SI Control Family
