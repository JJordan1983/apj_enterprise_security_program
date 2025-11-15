# 06. Control Implementations – MP: Media Protection  
APJ SecureCloud – FedRAMP Low (LI-SaaS)

APJ SecureCloud does not use, process, store, or distribute customer data or
content. Only system metadata (non-sensitive operational logs) passes through
the boundary. No removable media, no physical storage devices, and no portable
hardware exist within APJ SecureCloud’s operational environment.

All underlying storage and media protection controls are inherited from
Microsoft Azure Government (IL2), which provides FIPS-validated encryption,
media sanitization, and hardware destruction.

---

# **MP-1 – Media Protection Policy and Procedures**

APJ SecureCloud maintains a Media Protection Policy that defines:

- Media handling requirements  
- Restrictions on removable media  
- Requirements for cloud-based storage only  
- Inheritance of Azure Gov media protections  

Because APJ stores no customer content and uses no physical media, MP controls
are administrative only.

Policy located at:  
`Portfolio/M365_Security/Policies/Media_Protection_Policy.md`

---

# **MP-2 – Media Access (NOT APPLICABLE – Documented)**

### **Reason for N/A**
APJ SecureCloud maintains **no physical or digital media** outside Azure Gov.
There are:

- No USB drives  
- No external storage  
- No CDs/DVDs  
- No hardware appliances  
- No local servers  

Only Azure storage accounts and Log Analytics are used, and those are logically
isolated and RBAC protected.

**Conclusion:** Media access control is inherited from Azure Gov.

---

# **MP-3 – Media Marking (NOT APPLICABLE – Documented)**

### **Reason for N/A**
APJ does not create, store, or distribute media that requires marking.

- No physical media  
- No portable drives  
- No stored customer data  

Azure Gov handles media marking for datacenter assets.

---

# **MP-4 – Media Storage (NOT APPLICABLE – Documented)**

### **Reason for N/A**
APJ does not store any information on media outside of Azure Gov.

All metadata is stored in:

- Azure Storage  
- Key Vault  
- Log Analytics  
- Sentinel  

All of which are encrypted and part of Azure’s FedRAMP package.

No local or portable media is used.

---

# **MP-5 – Media Transport (NOT APPLICABLE – Documented)**

### **Reason for N/A**
APJ never transports media:

- No drives are moved  
- No tapes  
- No removable devices  
- No printouts  

Azure Gov handles all internal datacenter media transport with strict controls.

---

# **MP-6 – Media Sanitization**

Although APJ doesn’t manage physical media, APJ inherits Azure Gov’s
FIPS-validated sanitization processes.

Azure Gov performs:

- Secure drive wiping  
- Cryptographic erasure  
- Destruction of decommissioned hardware  
- Validation of sanitization events  

APJ maintains no physical components to sanitize.

Documentation reference: Azure Gov FedRAMP Security Package.

---

# **MP-7 – Media Use (NOT APPLICABLE – Documented)**

### **Reason for N/A**
APJ SecureCloud explicitly prohibits:

- USB devices  
- External hard drives  
- Smartphones used for data transfer  
- Any removable storage  

All administrative actions occur through secure Azure portals with RBAC + MFA.

Written prohibition is included in the Media Protection Policy.

---

# End of MP Control Family

