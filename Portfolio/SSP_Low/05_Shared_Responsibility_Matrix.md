# 05. Shared Responsibility Matrix (SRM)
APJ SecureCloud – FedRAMP Low (LI-SaaS)
Metadata-Processing SaaS • No Customer PHI/PII • Azure Gov IL2

This section defines the shared security responsibilities among:

- **Microsoft Azure Government (IL2)** — Inherited Controls (IAAS/PAAS)
- **APJ SecureCloud** — SaaS Provider Controls
- **Customer** — External Tenant Controls

APJ SecureCloud processes **metadata only** (audit metadata, configuration metadata, identity metadata, alerts).  
No customer content, PHI, PII, or proprietary data is stored within the platform.

---

# 1. Responsibility Alignment Summary

APJ SecureCloud follows the **FedRAMP LI-SaaS shared model**:

| Area | Azure Gov | APJ SecureCloud | Customer |
|------|-----------|------------------|----------|
| Physical Security | ✔️ Inherited | ❌ | ❌ |
| Infrastructure Security | ✔️ Inherited | ❌ | ❌ |
| Platform Maintenance | ✔️ Inherited | ❌ | ❌ |
| SaaS Application Security | ❌ | ✔️ | ❌ |
| Metadata ingestion | ❌ | ✔️ | ❌ |
| Identity & Access (Operators) | ❌ | ✔️ | ❌ |
| Identity & Access (Tenant Users) | ❌ | ❌ | ✔️ |
| API Permissions | ❌ | ✔️ (app registration docs) | ✔️ (granting permissions) |
| Audit log review | ❌ | ✔️ (platform logs) | ✔️ (business logs) |
| Incident Reporting | ❌ | ✔️ | ✔️ |
| Customer Data Protection | ❌ | ❌ (no data stored) | ✔️ |

---

# 2. SRM by Control Family

## **AC – Access Control Responsibilities**

**Azure Government (Inherited)**  
- Provides Entra ID Gov IL2 platform  
- Enforces MFA at operator identity plane  
- Provides network segmentation, NSGs, private endpoints  

**APJ SecureCloud (SaaS Provider)**  
- Implements RBAC roles within SaaS (Admin, Analyst, Viewer)  
- Enforces least privilege for operators using PIM  
- Manages Conditional Access for operator accounts  
- Maintains API-level session management  
- Ensures token lifetime & timeouts  

**Customer**  
- Manages their own Azure AD users  
- Grants API permissions through App Registration  
- Performs user lifecycle actions for tenant users  
- Reviews their access to APJ SecureCloud dashboards  

---

## **AT – Awareness & Training Responsibilities**

**Azure Government**  
- Provides security training for MS Azure operators  

**APJ SecureCloud**  
- Trains APJ operators on FedRAMP, IR, privileged operations  
- Ensures awareness for access review and audit processes  

**Customer**  
- Trains users who log into the APJ SecureCloud SaaS  
- Ensures end-user security practices in their tenant  

---

## **AU – Audit & Accountability Responsibilities**

**Azure Government**  
- Maintains audit logs for cloud infrastructure  
- Protects integrity & retention of platform logs  

**APJ SecureCloud**  
- Produces ingestion logs, API logs, correlation logs  
- Monitors anomaly events in metadata  
- Maintains audit logs for SaaS application components  

**Customer**  
- Reviews tenant-level events, identity events, and resource updates  
- Consumes APJ SecureCloud dashboards for insights  

---

## **CM – Configuration Management Responsibilities**

**Azure Government**  
- Manages secure baselines, patches, and platform images  

**APJ SecureCloud**  
- Uses IaC pipelines to deploy validated version-controlled components  
- Performs dependency scanning / code scanning  
- Maintains configuration drift alerts  
- Ensures WAF, firewall rules, API policies remain compliant  

**Customer**  
- Manages their tenant configurations (Entra ID, resources, logs)  
- Maintains their own Azure/M365 CM policies  

---

## **IA – Identification & Authentication Responsibilities**

**Azure Government**  
- Provides the identity platform (Entra ID Gov IL2)  
- Enforces MFA at the platform access boundary  

**APJ SecureCloud**  
- Configures operator access (RBAC, PIM, CA)  
- Ensures secure OAuth2 client use  
- Does **not** store customer credentials  

**Customer**  
- Manages user identities within their Azure/M365 tenant  
- Approves API access permissions  

---

## **IR – Incident Response Responsibilities**

**Azure Government**  
- Handles infrastructure-level incidents  
- Provides IR per FedRAMP ATO  

**APJ SecureCloud**  
- Detects and responds to SaaS incidents (IR-6)  
- Reports security-relevant events affecting the service  
- Coordinates communication to the customer  

**Customer**  
- Responds to incidents within their own Azure/M365 tenant  
- Reports suspected anomalous events or misconfigurations  

---

## **RA – Risk Assessment Responsibilities**

**Azure Government**  
- Conducts risk assessments for all Gov cloud components  

**APJ SecureCloud**  
- Conducts annual risk assessments for SaaS application  
- Documents risks, mitigations, and POA&M entries  
- Performs vendor risk evaluations for integrated services  

**Customer**  
- Assesses risks within their own environment  

---

## **SC – System & Communications Protection Responsibilities**

**Azure Government**  
- Provides TLS 1.2+ boundary protection  
- Provides DDoS and WAF baseline protections  

**APJ SecureCloud**  
- Enforces HTTPS-only communications  
- Implements data minimization and metadata-only ingestion  
- Protects all metadata at rest with SSE & TDE  
- Ensures API keys stored in Azure Key Vault  

**Customer**  
- Ensures their outbound API calls originate from secure devices  
- Protects their own resource configurations  

---

## **SI – System & Information Integrity Responsibilities**

**Azure Government**  
- Provides platform integrity monitoring  
- Applies patches to hypervisors and hosts  

**APJ SecureCloud**  
- Implements correlation rules for metadata anomalies  
- Uses Defender + Sentinel for threat detection  
- Monitors system health, ingestion errors, API anomalies  

**Customer**  
- Validates alerts and insights provided by APJ SecureCloud  
- Takes corrective actions in their own tenant  

---

## **SR – Supply Chain Risk Management Responsibilities**

**Azure Government**  
- Manages supply chain for hardware and infrastructure  

**APJ SecureCloud**  
- Manages supplier risk for third-party integrations  
- Maintains vendor documentation and compliance status  

**Customer**  
- Reviews APJ SecureCloud documentation as part of vendor due diligence  

---

# 3. Summary Table (Condensed)

| Area | Azure Gov | APJ SecureCloud | Customer |
|------|-----------|------------------|----------|
| Physical & Infra Security | ✔️ Inherited | ❌ | ❌ |
| Platform Security | ✔️ Inherited | ❌ | ❌ |
| SaaS Application | ❌ | ✔️ | ❌ |
| Metadata Processing | ❌ | ✔️ | ❌ |
| Customer Business Data Handling | ❌ | ❌ (not processed) | ✔️ |
| IAM (Operators) | ❌ | ✔️ | ❌ |
| IAM (Customer Users) | ❌ | ❌ | ✔️ |
| API Permissions | ❌ | ✔️ | ✔️ |
| Audit Log Review | ❌ | ✔️ | ✔️ |
| Incident Response | ✔️ Infra-level | ✔️ SaaS-level | ✔️ Tenant-level |
| Configuration Management | ✔️ Platform | ✔️ SaaS | ✔️ Tenant |
| Risk Assessment | ✔️ | ✔️ | ✔️ |

---

# 4. Alignment to SRM Excel File

This narrative SRM mirrors the structure of:

Portfolio/SSP_Low/SRM/SRM_APJ_SecureCloud.xlsx


The Excel file includes:

- Tab 1: SRM Master  
- Tab 2: FedRAMP Mapping  
- Tab 3: Risk Notes  
- Tab 4: Diagram References  

---
