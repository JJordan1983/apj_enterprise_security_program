# 06. Control Implementations – CM: Configuration Management  
APJ SecureCloud – FedRAMP Low (LI-SaaS)

APJ SecureCloud maintains a disciplined, automated configuration management program using Azure Gov services, GitHub repository controls, and IaC (Terraform/Bicep) templates. All infrastructure changes flow through controlled pipelines with audit logging, approval workflows, and IaC drift detection.

Only system metadata is processed. No customer content enters the boundary.

---

# **CM-1 – Policy and Procedures**

APJ SecureCloud maintains a Configuration Management Policy defining:

- Roles and responsibilities  
- CM lifecycle (request → review → approval → implementation → audit)  
- Configuration baselines  
- Source control requirements  
- IaC enforcement  
- Automated testing and validation  
- Change approvals (two-person rule for production)  
- Emergency change process  
- Reporting requirements for FedRAMP ConMon  

Procedure documents include:

- IaC deployment checklist  
- Pull request workflow  
- Pipeline integrity validation steps  
- Monthly drift detection procedure  

Policy located at:  
`Portfolio/M365_Security/Policies/Configuration_Management_Policy.md`

---

# **CM-2 – Baselines**

APJ SecureCloud maintains secure baseline configurations for:

### **Azure Platform Baselines**
- Azure AD security baseline  
- Azure App Service hardened baseline  
- Azure SQL baseline  
- Storage Account secure baseline (HTTPS-only, private endpoints)  
- NSG baseline rules  
- Defender for Cloud recommendations baseline  

### **Application Baselines**
- API configuration baseline  
- App Service Authentication baseline (Entra ID)  
- App Service diagnostic logs baseline  
- CI/CD pipeline baseline  

### **Infrastructure-As-Code Baselines**
All baselines are expressed using:

- **Terraform modules** or  
- **Azure Bicep templates**

Stored in the repo:
Portfolio/AzureGov/Baselines/

Baselines are reviewed **quarterly** and validated during deployments.

---

# **CM-3 – Configuration Change Control**

All changes follow strict workflow:

1. Developer submits Pull Request (PR)  
2. Automated scanning runs (GitHub Advanced Security, IaC checks)  
3. Cloud Security Analyst reviews for compliance  
4. Change Advisory Board (CAB) approval required for production  
5. Pipeline deploys change to staging  
6. Sentinel, Log Analytics, and Defender signals monitored  
7. Final approval before production release  

Emergency changes require:

- Security Officer approval  
- Retrospective review within 72 hours  
- Inclusion in ConMon report  

All PRs remain permanently logged in GitHub.

---

# **CM-4 – Security Impact Analysis**

Before any change is merged, GitHub Actions automatically performs:

### **Automated Analysis**
- Static code analysis  
- IaC misconfiguration scanning  
- Dependency vulnerability scanning  
- Policy-as-code validation  
- Terraform plan review  

### **Manual Security Review**
Performed by APJ SecureCloud Cloud Security Analyst:

- Review changes for RBAC impacts  
- Evaluate PIM elevation logs  
- Ensure diagnostic logs remain enabled  
- Check Key Vault access policies  
- Validate any Conditional Access or Identity changes  

Changes that materially affect security require updated:

- Diagrams  
- SRM entries  
- POA&M notes  
- SSP sections  

---

# **CM-5 – Access Restrictions for Changes**

APJ SecureCloud limits system changes via:

### **GitHub**
- Protected branches  
- Required reviewer checks  
- Required status checks  
- Signed commits  
- PR-only merges  
- No direct pushes to `main`  

### **Azure Government**
- PIM enforcement for all privileged roles  
- Just-In-Time (JIT) role approval  
- No standing admin accounts  
- Key Vault secrets locked behind RBAC + private endpoints  
- App Service managed identity used for automation  

No developer has direct production write access.

---

# **CM-6 – Configuration Settings**

Configuration settings enforced via:

- Azure Policy (built-in + custom)  
- Azure Blueprints (where applicable)  
- Terraform/Bicep modules  
- CI/CD pipeline validation  
- AppService configuration enforcement  
- Defender for Cloud hardening controls  

Settings include:

- HTTPS-only resources  
- TLS 1.2+  
- Logging always enabled  
- Private endpoints for sensitive resources  
- Storage encryption (SSE)  
- SQL auditing and threat detection  
- Restrictions on local auth  

Non-compliant resources trigger Sentinel alerts + Defender recommendations.

---

# **CM-7 – Least Functionality**

APJ SecureCloud minimizes functionality by:

- Disabling unneeded Azure services  
- Enforcing minimal NSG rules  
- Disabling public network access unless required  
- Restricting API endpoints  
- Using Managed Identities instead of service accounts  
- Removing unused App Service features  

Monthly review validates:

- No unnecessary ports  
- No unused roles  
- No stale API keys  
- No legacy deployment methods enabled  

---

# **CM-8 – Information System Component Inventory**

(Already captured in your Section 04 file)  
This control references:

Portfolio/SSP_Low/04_Component_Inventory.md

Inventory includes:

- Resource type  
- Resource ID  
- Owner  
- Purpose  
- Sensitivity  
- Logging status  
- Dependencies  
- Tags  
- RBAC roles  

Inventory updated automatically via:

- Azure Resource Graph Queries  
- Weekly GitHub Action exporting to CSV  

---

# **CM-9 – Configuration Management Plan**

The CM Plan is included in:

Portfolio/M365_Security/Policies/Configuration_Management_Policy.md

Plan includes:

- Baseline lifecycle  
- Monitoring strategy  
- Drift detection schedule  
- IaC enforcement strategy  
- Change workflow  
- Metrics (e.g., failed deployments, misconfiguration rate)  
- Reporting requirements aligned to FedRAMP ConMon  

---

# **CM-10 – Software Usage Restrictions**

APJ SecureCloud uses:

- Approved open-source libraries only  
- GitHub Dependabot for automated version control  
- Licensing checks for OSS packages  
- Code signing for deployment artifacts  

Unapproved software or libraries blocked by pipeline rules.

---

# **CM-11 – User-Installed Software**

Not applicable—APJ SecureCloud is cloud-hosted and users cannot install software.

Azure Gov resources are read-only to tenants and do not allow unapproved installation.

---

# End of CM Control Family

