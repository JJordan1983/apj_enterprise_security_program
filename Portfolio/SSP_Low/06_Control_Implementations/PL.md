# 06. Control Implementations – PL: Planning  
APJ SecureCloud – FedRAMP Low (LI-SaaS)

APJ SecureCloud maintains a structured security planning program aligned to:
- FedRAMP Low requirements
- NIST SP 800-53 Rev5 planning controls
- NIST AI RMF (where applicable)
- Azure Government IL2 shared responsibility models

The Security Plan (this SSP) documents system characteristics, environments,
roles, responsibilities, and inherited controls from Azure Gov.

---

# **PL-1 – Security Planning Policy and Procedures**

APJ SecureCloud maintains a Security Planning Policy that defines:

- Purpose of the security plan  
- Required components of the SSP  
- Documentation responsibilities  
- Review frequency (annual or after major change)  
- SSP update approval workflow  
- Mapping to FedRAMP and NIST requirements  

Procedures include:

- How updates to the SSP are requested  
- How control owners provide evidence  
- How new service features are added into scope  

Policy location:  
`Portfolio/M365_Security/Policies/Security_Planning_Policy.md`

---

# **PL-2 – System Security and Privacy Plans**

APJ SecureCloud maintains an SSP that includes:

### **System Description**
- Metadata-only SaaS boundary  
- Azure Gov IL2 hosting  
- No customer content stored  

### **Security Controls**
- Full 800-53 Rev5 Low baseline  
- Azure Gov inheritance  
- APJ SaaS-specific configurations  

### **Diagrams**
Stored in:  
`Portfolio/SSP_Low/Diagrams/`

Includes:
- Network Boundary Diagram  
- RBAC Model  
- Data Flow Diagram  

### **Privacy Plan (FedRAMP Low)**
Not required for Low baseline systems that **do not process PII**.  
APJ SecureCloud processes **no PII**, only metadata.

### **Review Requirements**
- Annual leadership review  
- Review after any major architecture change  
- Review triggered by new compliance frameworks  

The SSP you are building is the formal documentation for PL-2.

---

# **PL-4 – Rules of Behavior**

APJ SecureCloud enforces rules of behavior for all personnel with system access:

### **Rules Include**
- Mandatory MFA  
- PIM for privileged access  
- No local media usage  
- No customer content access  
- Acceptable Use requirements  
- Restrictions on development in production  
- Secure device compliance checks  

Users acknowledge rules during onboarding.

Document location:  
`Portfolio/M365_Security/Policies/Rules_of_Behavior.md`

---

# **PL-7 – Concept of Operations (CONOPS)**

APJ maintains a Concept of Operations describing:

### **System Overview**
APJ SecureCloud provides metadata-driven insights and dashboards without
collecting or storing customer content.

### **Users**
- Security Officers  
- Cloud Administrators  
- Analysts  
- FedRAMP auditors  

### **Operating Model**
- Azure Gov IaaS/PaaS hosting  
- SaaS logic delivered through serverless components and App Service  
- CI/CD for deployments  
- Sentinel for monitoring  
- Zero Trust identity enforcement  

### **Lifecycle**
1. Requirements definition  
2. Secure architecture design  
3. IaC deployment  
4. Logging & detection onboarding  
5. Continuous monitoring  
6. Incident response  
7. Reporting & audits  

### **Support Model**
- Tier 1–3 support  
- FedRAMP compliance oversight  
- Change control via DevOps  

CONOPS document stored here:  
`Portfolio/SSP_Low/02_ConOps/`

---

# **PL-8 – Security and Privacy Architectures**

APJ SecureCloud implements a unified architecture incorporating:

### **Zero Trust Principles**
- Verify explicitly (MFA, PIM, device compliance)  
- Least privilege through RBAC  
- Assume breach (Sentinel analytics)  

### **Data Protection**
- No customer data stored  
- Metadata only  
- All storage is encrypted via Azure Gov  

### **AI Governance (for metadata ML modules)**
- AI lifecycle governed by NIST AI RMF  
- No automated decision-making that affects customers  
- ML/analytics limited to system health and anomaly detection  

### **Architecture Artifacts**
Located at:  
`Portfolio/SSP_Low/Diagrams/`

Includes:
- System Boundary Diagram  
- Identity & Access Flow  
- Logging Pipeline Diagram  
- AI Impact Flow (if applicable)  

### **Updates**
Architecture is reviewed:
- Annually
- After major technology changes
- After incident response lessons learned

---

# End of PL Control Family
