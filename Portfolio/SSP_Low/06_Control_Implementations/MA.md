# 06. Control Implementations – MA: Maintenance  
APJ SecureCloud – FedRAMP Low (LI-SaaS)

APJ SecureCloud is a metadata-only SaaS platform hosted entirely within
Microsoft Azure Government (IL2). APJ does not manage physical infrastructure
or hardware. All underlying platform maintenance, patching, physical repair,
and datacenter servicing are inherited from Azure Gov’s FedRAMP authorization.

APJ SecureCloud performs maintenance ONLY on:
- Application code
- API integrations
- Logging pipelines
- Sentinel SIEM detections
- Infrastructure-as-Code templates
- Identity and access configurations

No local hardware, appliances, or system components exist to be physically serviced.

---

# **MA-1 – System Maintenance Policy and Procedures**

APJ SecureCloud maintains a Maintenance Policy establishing:

- Types of maintenance performed  
- Roles responsible for executing maintenance  
- Requirements for planned vs. emergency updates  
- Security review of maintenance actions  
- Change approval workflow via Azure DevOps  
- Logging and documentation requirements  
- Restrictions on remote maintenance  

Maintenance is executed exclusively via:
- Azure DevOps CI/CD pipelines  
- IaC templates (Bicep/Terraform)  
- Controlled role-based access (RBAC + PIM)  

Policy located at:  
`Portfolio/M365_Security/Policies/Maintenance_Policy.md`

---

# **MA-2 – Controlled Maintenance**

The following controls are implemented:

### **Allowed Maintenance Activities**
- Code updates to the SaaS application  
- Sentinel detection tuning  
- Log Analytics schema or retention adjustments  
- API key rotation  
- Service principal certificate renewal  
- Patching container images used by the ingestion pipeline  

### **Maintenance Controls**
- All maintenance must be approved via Azure DevOps Change Request  
- All actions require PIM elevation for the “Cloud Application Administrator” role  
- Maintenance tasks generate logs in:  
  - Azure Activity Logs  
  - Sentinel  
  - DevOps audit history  

### **Maintenance Windows**
- Planned maintenance occurs during low-impact hours  
- Emergency maintenance is allowed for:  
  - Security vulnerabilities  
  - Service outages  
  - Credential compromise events  

All maintenance is documented in ConMon reports as needed.

---

# **MA-3 – Maintenance Tools**

APJ uses only approved and secure maintenance tools:

### **Permitted Tools**
- Azure Portal (via RBAC + PIM)  
- Azure CLI (PIM-restricted)  
- Azure DevOps CI/CD  
- Bicep/Terraform IaC  
- GitHub Enterprise (private repos)  
- Microsoft Sentinel investigation tools  

### **Tool Restrictions**
- No external administrative tools permitted  
- No third-party remote access utilities  
- No portable storage devices  
- No local console access (cloud-only)  

### **Logging**
All tool usage is captured through:
- Activity Logs  
- Azure AD sign-ins  
- DevOps pull request history  
- Sentinel audit events  

---

# **MA-4 – Nonlocal Maintenance**

All maintenance is **nonlocal** and cloud-based.

### **Implementation**
- All administrative sessions originate from authenticated APJ devices  
- PIM elevation must be used for any privileged command  
- MFA enforced on all maintenance accounts  
- Session control policies restrict location and device compliance  
- Azure AD Identity Protection flags high-risk maintenance sessions  

### **Session Logging**
Every action during nonlocal maintenance is logged automatically:
- Resource Manager operations  
- PIM elevation logs  
- Identity Protection risk signals  
- Sentinel investigation actions  

### **Encrypted Channels**
All maintenance traffic uses:
- HTTPS / TLS 1.2+  
- Azure AD token-protected endpoints  
- Private network paths for internal operations  

---

# **MA-5 – Maintenance Personnel (NOT APPLICABLE – Documented)**

APJ SecureCloud performs **no physical maintenance**, and no personnel interact with hardware.

Therefore:

### **MA-5 is marked Not Applicable**  
because:

- APJ controls no physical
