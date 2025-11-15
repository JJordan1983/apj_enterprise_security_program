# 06. Control Implementations – SA: System and Services Acquisition  
APJ SecureCloud – FedRAMP Low (LI-SaaS)

APJ SecureCloud acquires, builds, and maintains system components through
cloud-native Azure Government services using secure CI/CD pipelines,
Infrastructure-as-Code (IaC), and formalized acquisition procedures.

Azure Government (IL2) provides the underlying FedRAMP-authorized platform,
datacenter services, networking, compute, storage, logging, and identity
backbone. APJ manages only SaaS-layer components and inherits all
infrastructure-level controls.

---

# **SA-1 – System and Services Acquisition Policy and Procedures**

APJ maintains a System and Services Acquisition Policy defining:

- Required security reviews for new services  
- Required FedRAMP authorization for infrastructure components  
- SaaS-level architectural and security assessments  
- Vendor evaluation criteria (secure APIs, compliance posture)  
- Software composition and dependency scanning requirements  
- Contractual requirements for third-party services  

Policy stored at:  
`Portfolio/M365_Security/Policies/Acquisition_Policy.md`

Procedures cover:
- Adding new Azure services  
- Adding new dependencies to the SaaS stack  
- Reviewing licensing and subscriptions  
- Ensuring IaC templates enforce security controls  

---

# **SA-2 – Allocation of Resources**

APJ allocates resources for:

- Security engineering  
- DevSecOps functions  
- Code scanning  
- Sentinel/Defender analytics  
- Logging and monitoring  
- Security documentation and ConMon reporting  
- Zero Trust and PIM enforcement  

Azure Gov handles all infrastructure-level staffing and resources.

---

# **SA-3 – System Development Life Cycle (SDLC)**

APJ’s SDLC integrates:

### **Secure Development Practices**
- Threat modeling for new features  
- Code scanning (SAST)  
- Dependency scanning (SCA)  
- Secrets scanning  
- IaC validation (Terraform/Bicep security linting)  
- Sentinel rule testing in non-prod  

### **Pipeline Enforcement**
CI/CD pipelines enforce:
- Required approvals  
- PIM elevation for privileged operations  
- Branch protection  
- Code review by senior engineer  
- Security gates  

SDLC documentation stored in:  
`Portfolio/DevSecOps/SDLC.md`

---

# **SA-4 – Acquisition Process**

APJ acquires services using:

### **Approved Cloud Services**
- Only FedRAMP-authorized Azure Gov services  
- Marketplace services with FedRAMP alignment  
- APIs with validated security practices  

### **Vendor Assessment**
All vendors undergo review for:
- Security attestation  
- Shared responsibility alignment  
- API security posture  
- Logging and audit capabilities  

Records stored in:  
`Portfolio/Vendor_Management/`

---

# **SA-4(1) – Functional Properties of Security Controls**

For every new service introduced, APJ documents:

- Expected authentication method  
- Required logging and audit events  
- Minimum encryption standards  
- Identity model (managed identities / service principals)  
- Role-based access requirements  

Stored in:  
`Portfolio/SSP_Low/06_Control_Implementations/Service_Control_Profiles/`

---

# **SA-4(2) – Design / Implementation Information**

APJ provides design, diagrams, and implementation details for SaaS components:

- Data Flow Diagram  
- RBAC Model  
- Boundary Diagram  
- Logging Architecture  
- Sentinel Automation Flow  
- AI Component Flow (if applicable)

Location:  
`Portfolio/SSP_Low/Diagrams/`

---

# **SA-4(9) – Functions, Ports, Protocols, and Services**

APJ documents all required external connectivity including:

### **Primary Protocols**
- HTTPS/TLS 1.2+  
- OAuth 2.0 / OIDC tokens  
- Azure service endpoints  

### **No inbound ports**  
APJ SecureCloud is serverless/app-service based; no inbound open ports or direct exposure.

Documented in:  
`Portfolio/SSP_Low/Network/Ports_Protocols_Services.md`

---

# **SA-5 – Information System Documentation**

APJ provides the following documentation:

- System Security Plan (this SSP)  
- Architecture diagrams  
- Component inventory  
- RBAC model  
- Monitoring & logging plan  
- IR plan and tabletop results  
- ConOps  

Documentation stored across:  
`Portfolio/SSP_Low/`  
`Portfolio/M365_Security/`  
`Portfolio/Incident_Response/`

---

# **SA-8 – Security Engineering Principles**

APJ uses the following engineering principles:

### **Zero Trust**
- Least privilege  
- MFA everywhere  
- Continuous evaluation  
- PIM for privileged accounts  

### **Secure-by-Design**
- No customer content stored  
- Secrets stored in Key Vault  
- Logging mandatory for all services  
- TLS 1.2+ enforced  

### **Infrastructure-as-Code**
- No manual configuration drift  
- Automated security scanning  
- GitOps approval workflows  

Evidence stored in:  
`Portfolio/DevSecOps/`

---

# **SA-9 – External Information System Services**

External services used:

### Allowed:
- Azure Government IL2  
- Microsoft-hosted FedRAMP services  
- Secure API providers (evaluated through vendor review)  

### Not allowed:
- Public cloud resources  
- Consumer-grade SaaS  
- Data transfer or storage outside U.S.  

Azure Gov provides FedRAMP-authorized:
- Compute  
- Networking  
- Storage  
- Logging  
- Identity  

APJ manages SaaS logic on top of these services.

Vendor assessment results stored in:  
`Portfolio/Vendor_Management/`

---

# **SA-10 – Developer Configuration Management**

APJ enforces:

- Git repository branch protections  
- Pull request approvals  
- Secrets scanning  
- Version control tagging  
- Immutable audit history for all changes  

Documentation stored at:  
`Portfolio/DevSecOps/Configuration_Management.md`

---

# **SA-11 – Developer Testing and Evaluation**

APJ performs:

### **Static Analysis**
- SAST via pipeline scanners  

### **Dependency Scan**
- SCA for library vulnerabilities  

### **Runtime/Tenant Testing**
- Non-prod environments  
- Sentinel rule validation  
- API functional testing  

### **IaC Testing**
- Security linting  
- Policy-as-code checks  
- Drift detection  

Testing documentation stored in:  
`Portfolio/DevSecOps/Testing/`

---

# **SA-15 – Development Process, Documentation, and Configuration Management**

APJ manages:

- Code repositories  
- IaC repos  
- Dev/Test/Prod segregation  
- Automated secrets rotation  
- Change management via Azure DevOps  

### Documentation includes:
- Architecture  
- Design specifications  
- Testing plans  
- Deployment pipelines  
- Security controls  

---

# **SA-22 – Unsupported System Components**

APJ enforces:
- No unsupported libraries or runtimes  
- CI/CD scanning for deprecated packages  
- Immediate remediation when EOL components are detected  

Azure Government infrastructure never includes unsupported components.

---

# End of SA Control Family
