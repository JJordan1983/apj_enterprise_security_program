# 06. Control Implementations – PS: Personnel Security  
APJ SecureCloud – FedRAMP Low (LI-SaaS)

APJ SecureCloud operates entirely within Microsoft Azure Government (IL2).  
APJ does not administer datacenter personnel, physical access, or hiring for infrastructure roles.  
These responsibilities are fully inherited from Azure Government’s FedRAMP authorization.

APJ personnel who administer the SaaS platform operate remotely, use only logical (cloud) access, and have no physical access to any datacenter.

---

# **PS-1 – Personnel Security Policy and Procedures (APJ + Inherited)**

### APJ Responsibilities
APJ maintains a Personnel Security Policy covering:
- Background check requirements for employees with privileged system access  
- Separation-of-duties for sensitive roles  
- Annual security training  
- Rules of Behavior compliance  
- Procedures for onboarding/offboarding logical access  

Policy stored here:  
`Portfolio/M365_Security/Policies/Personnel_Security_Policy.md`

### Inherited
Azure Gov handles:
- Datacenter personnel vetting  
- Datacenter background investigations  
- Physical access controls  

---

# **PS-2 – Position Risk Designation (APJ)**

APJ designates all system roles according to risk:

### **High-Risk Roles**
- Cloud Administrator  
- DevSecOps Engineer  
- Sentinel/Logging Administrator  

These roles require elevated review before access is granted.

### **Moderate-Risk Roles**
- Analysts  
- Security Program Lead  

### **Low-Risk Roles**
- Non-administrative support roles

Risk designation worksheet stored in:  
`Portfolio/SSP_Low/Role_Risk_Designations.xlsx`

---

# **PS-3 – Personnel Screening (APJ + Inherited)**

### APJ Responsibilities
Before granting administrative access:
- Employment verification  
- Reference checks  
- Identity verification  
- Agreement to APJ Rules of Behavior  
- Completion of Security Awareness Training  

### Inherited (Azure Gov)
Microsoft screens all datacenter personnel per FedRAMP requirements.

APJ does **not** require public trust or national security clearances because the service:
- Handles no classified data  
- Stores no PII  
- Is FedRAMP Low (LI-SaaS) boundary  

---

# **PS-4 – Personnel Termination (APJ)**

APJ maintains strict processes for employees leaving the organization or changing roles:

### Termination Actions
- Immediate deactivation of Entra ID accounts  
- PIM role removal  
- Removal from Azure DevOps and GitHub repos  
- Sentinel and Log Analytics access revocation  
- Audit verification within 24 hours  

Termination checklist file:  
`Portfolio/M365_Security/Procedures/Access_Termination_Checklist.md`

---

# **PS-5 – Personnel Transfer (APJ)**

When APJ staff move between roles:
- Access privileges are reevaluated  
- Excess permissions are removed  
- PIM roles are reassigned or revoked  
- Training requirements are refreshed  

Transfers generate:
- An updated access review entry  
- Updates in the quarterly RBAC Review package  

Documentation stored here:  
`Portfolio/Access_Reviews/Q4_2025.xlsx`

---

# **PS-6 – Access Agreements (APJ)**

All APJ staff with privileged access must sign:
- APJ Rules of Behavior (RoB)  
- Acceptable Use Policy  
- Confidentiality statement  
- AI usage & data handling rules (if applicable)  

Copies kept in:  
`Portfolio/Training/Access_Agreements/`

---

# **PS-7 – External Personnel Security (Inherited)**

Azure Gov is responsible for:
- Screening datacenter operators  
- Vetting third-party personnel  
- Controlling physical access  

APJ has no ability to sponsor, manage, or authorize personnel at Microsoft facilities.

---

# **PS-8 – Personnel Sanctions (APJ)**

APJ enforces sanctions for violation of:
- Security policies  
- Access rules  
- Behavior expectations  

Sanctions may include:
- Access revocation  
- Formal warning  
- Role reassignment  
- Termination  

APJ documents all sanctions privately; no artifacts stored in the public repository.

---

# **PS-9 – Position Categorization (APJ)**

APJ categorizes system roles in alignment with:
- FedRAMP Low requirements  
- Risk impact to SaaS boundary  
- Privileged vs. standard access requirements  

Role matrix stored in:  
`Portfolio/SSP_Low/Role_Categorization_Matrix.xlsx`

---

# **PS-10 – Personnel Security Official (APJ)**

APJ designates a **Personnel Security Officer** responsible for:
- Reviewing access requests  
- Ensuring all personnel complete training  
- Managing policy acknowledgements  
- Overseeing background verification  

This is typically the **Security Program Lead**.

---

# End of PS Control Family
