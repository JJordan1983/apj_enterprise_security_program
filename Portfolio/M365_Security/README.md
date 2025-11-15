# M365 Security Policies – APJ SecureCloud

This folder contains all system-level security policies that support the FedRAMP
Low system boundary for APJ SecureCloud. These policies align with the architecture
described in the SSP and implement Zero Trust, least privilege, and continuous
monitoring as required by FedRAMP and NIST SP 800-53 Rev5.

## How to Use This Folder (Auditors & Reviewers)

### 1. **Policies mapped to SSP control families**
Each policy here directly aligns with your SSP sections:

- AC – Access_Control_Policy.md  
- AT – Training_Policy.md (optional)  
- AU – Logging_Policy.md  
- CM – Configuration_Management_Policy.md  
- IA – Identity_Policy.md (optional, combined in AC for LI-SaaS)  
- IR – Incident_Response_Policy.md  
- MA – Maintenance_Policy.md  
- MP – Media_Protection_Policy.md  
- PE – Physical_Environmental (inherited from Azure Gov)  
- PL – Security_Planning_Policy.md  
- PM – Security_Program_Plan.md  
- PS – Personnel_Security_Policy.md  
- RA – Risk_Assessment_Policy.md  
- SA – Acquisition_Policy.md  
- SC – System_and_Communications_Protection_Policy.md  
- SI – System_Integrity_Policy.md  
- SR – Supply_Chain_Risk_Management_Policy.md  

### 2. **Azure Gov Shared Responsibility**
Azure Government IL2 provides:
- Physical protections  
- Datacenter controls  
- Hypervisor and host patching  
- Hardware lifecycle  
- Networking architecture  
- FedRAMP Authorization (P-ATO)  

APJ provides:
- SaaS-layer identity  
- Access controls  
- Logging  
- Sentinel detection rules  
- DevSecOps governance  
- Policies + procedures  
- ConMon reporting  

### 3. **How reviewers can validate compliance**
Auditors can cross-reference:
- Policies in this folder  
- Procedures under `/Portfolio/DevSecOps/`  
- Diagrams under `/Portfolio/SSP_Low/Diagrams/`  
- IR artifacts under `/Portfolio/Incident_Response/`  
- POA&M at `/Portfolio/POAM/`  
- Risk Register at `/Portfolio/Risk/`  

### 4. **Zero Trust Access Architecture**
This policy set enforces:
- MFA everywhere  
- PIM for elevated roles  
- Conditional Access for device compliance  
- No standing privileges  
- “Verify explicitly, least privilege, assume breach”  
- Role-based access to all cloud resources  

### 5. Evidence Locations
Evidence referenced by these policies exists in:
Portfolio/Access_Reviews/
Portfolio/ConMon/
Portfolio/Incident_Response/
Portfolio/DevSecOps/
Portfolio/Risk/
Portfolio/POAM/
Portfolio/SSP_Low/Diagrams/


This README serves as the auditor’s guide to your security governance framework.

---

