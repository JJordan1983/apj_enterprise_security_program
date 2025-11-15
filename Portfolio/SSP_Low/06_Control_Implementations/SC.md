# 06. Control Implementations – SC: System and Communications Protection  
APJ SecureCloud – FedRAMP Low (LI-SaaS)

APJ SecureCloud operates as a metadata-only SaaS built entirely on Microsoft
Azure Government (IL2). APJ inherits Azure Gov’s encryption, network
segmentation, boundary protection, and platform security while implementing
SaaS-layer protections including identity controls, secure APIs, logging, and
CI/CD-based configuration management.

---

# **SC-1 – Policy and Procedures**

APJ SecureCloud maintains a System & Communications Protection Policy defining:

- Encryption requirements  
- Secure network design  
- Identity boundary protection  
- Key Vault secret management  
- Logging and metadata handling  
- TLS enforcement  
- API security requirements  

Policy located at:
`Portfolio/M365_Security/Policies/System_and_Communications_Protection_Policy.md`

---

# **SC-2 – Application Partitioning**

APJ SecureCloud is logically segmented across:

- App Service (SaaS logic)
- Serverless components (Functions)
- Log ingestion pipeline (Sentinel / Log Analytics)
- Key Vault for secrets
- Storage accounts for low-impact metadata

Azure Gov provides underlying tenant, region, and service isolation.

---

# **SC-4 – Information in Shared Resources**

APJ SecureCloud **does not store customer content**.  
All processing occurs on:

- Metadata streams  
- API outputs  
- Audit and operational logs  

Shared resources (App Service Plans, Storage, Log Analytics) use:

- Azure RBAC  
- Private identities  
- Key Vault tokens  

No customers share runtime execution or data paths.

---

# **SC-5 – Denial-of-Service Protection**

Denial-of-service resilience is provided through:

### **Azure Gov Inheritance**
- DDoS Protection  
- Global edge filtering  
- Network-layer throttling  
- Azure infrastructure resilience  

### **APJ SaaS Measures**
- Function and App Service autoscaling  
- Sentinel alerting on abnormal traffic patterns  
- API throttling via API Management (if enabled)  

---

# **SC-7 – Boundary Protection**

Boundary protection relies on:

### **Azure Gov Network Controls (Inherited)**
- Virtual network isolation  
- Hypervisor isolation  
- Managed firewalls  
- Azure DDoS Protection  
- Private endpoints  

### **APJ Zero Trust Controls**
- MFA  
- PIM  
- Conditional Access  
- Device compliance checks  
- No inbound open ports  
- All API access restricted to HTTPS  

Boundary Diagram stored at:  
`Portfolio/SSP_Low/Diagrams/Boundary_Diagram.png`

---

# **SC-7(5) – Boundary Protection: Deny-by-Default**

All traffic follows:

- **Default deny** ACL behavior  
- Explicitly allowed resource calls  
- App Service inbound restrictions to HTTPS  
- Private endpoints for supported services  

No public inbound traffic is used for higher-risk components.

---

# **SC-8 – Transmission Confidentiality and Integrity**

All data in transit uses:

- TLS 1.2 or higher  
- HTTPS endpoints only  
- Azure AD OAuth 2.0 tokens  
- Managed identity authentication  

APJ does not support plaintext protocols.

---

# **SC-10 – Network Disconnect**

Sessions automatically terminate when:

- PIM elevation ends  
- Device compliance changes  
- Conditional Access blocks detected  
- Admin console sessions time out  
- Risk-based session revocation occurs via Identity Protection  

---

# **SC-12 – Cryptographic Key Establishment and Management**

APJ relies on:

### **Azure Gov Managed Key Services**
- FIPS 140-2 validated Key Vault HSMs  
- Automated key rotation (configurable)  
- Certificate lifecycle management  

### **APJ Responsibilities**
- Storing secrets in Key Vault  
- Enforcing rotation policies  
- Preventing hard-coded secrets  
- Using Managed Identity where possible  

Documentation stored in:
`Portfolio/M365_Security/Key_Management/`

---

# **SC-13 – Cryptographic Protection**

APJ uses the following encryption standards:

### **In Transit**
- TLS 1.2+ for all HTTP/S traffic  
- OIDC/OAuth tokens (signed + encrypted)  

### **At Rest**
- Azure Storage Service Encryption (SSE)  
- Transparent Data Encryption (TDE)  
- Key Vault HSM encryption  

Azure Gov handles physical and disk-level crypto.

---

# **SC-15 – Collaborative Computing Devices (NOT APPLICABLE)**

APJ does not use:

- Cameras  
- Microphones  
- Built-in collaboration hardware  

SC-15 is documented as Not Applicable.

---

# **SC-18 – Mobile Code (APJ)**

APJ uses mobile code only in:

- Web UI JavaScript  
- Dashboard visualization layers (e.g., charts)  

Controls include:
- No untrusted code execution  
- No cross-domain content inclusion  
- Dependency scanning in CI/CD  

---

# **SC-19 – Voice Over IP (NOT APPLICABLE)**

APJ SecureCloud does not use VoIP technologies.

---

# **SC-20 – Secure Name/Address Resolution (Recursive or Caching Resolver)**

Azure Gov provides DNS services with:

- DNSSEC support  
- Secure recursive resolution  
- Redundant DNS endpoints  

APJ inherits all DNS-level protections.

---

# **SC-21 – Secure Name/Address Resolution (Authoritative Source)**

Azure Gov DNS ensures:
- Signed DNS responses  
- Protected authoritative servers  
- Anti-spoofing protections  

APJ does not operate its own DNS outside Azure.

---

# **SC-22 – Architecture and Provisioning for Name/Address Resolution Service**

Azure Gov ensures:
- Isolation of tenant DNS  
- Resolution path protection  
- Monitoring of DNS events  

APJ inherits.

---

# **SC-23 – Session Authenticity**

Session integrity is enforced by:

- Azure AD token verification  
- MFA  
- Conditional Access session controls  
- PIM ephemeral elevation  
- Termination after timeouts or risk triggers  

---

# **SC-28 – Protection of Information at Rest**

Although APJ retains **no customer content**, the following metadata is encry
