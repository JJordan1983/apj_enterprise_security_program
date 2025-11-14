# 04. Component Inventory  
APJ SecureCloud – FedRAMP Low (LI-SaaS)  
Metadata-Processing SaaS (No Customer PHI/PII)

This section describes all system components—logical, physical, software, network, and boundary components—that make up the APJ SecureCloud platform.  
APJ SecureCloud operates exclusively within Azure Government (IL2), inherits platform controls from Microsoft, and processes only **metadata**, not customer-provided business data.

---

## 1. Component Inventory Overview

APJ SecureCloud consists of the following categories of components:

### • Compute components  
### • Storage components  
### • Network & boundary components  
### • Identity & access components  
### • Logging & monitoring components  
### • Cryptographic components  
### • Security & compliance components  

All components are provisioned and managed through Azure Government using Azure Resource Manager (ARM) or Infrastructure-as-Code (IaC) pipelines.

---

## 2. Logical Component List

| Component | Type | Purpose | FedRAMP Role | Customer Impact |
|----------|------|---------|--------------|-----------------|
| API Ingestion Service | App Service (PaaS) | Collect metadata via OAuth APIs | System processing boundary | None (read-only ingestion) |
| Processing Engine | Function App | Normalize, correlate metadata | System processing boundary | None |
| Analytics UI | App Service | Display dashboards & insights | Customer-facing SaaS | Read-only |
| Azure Key Vault | Key mgmt | API credential storage | Cryptographic boundary | Customer secrets never stored |
| Log Storage (Metadata Only) | Storage Account | Ingestion logs, correlation table | System log boundary | Metadata only |
| Configuration DB | Azure SQL / Azure Table | Store normalized metadata | System boundary | No PII data stored |
| Identity Provider | Entra ID Gov IL2 | Operator and tenant auth | Inherited | Customer identity managed externally |
| Monitoring Stack | Azure Monitor, Sentinel | Health, performance, alerts | Security boundary | Customer receives insights only |

---

## 3. Physical Components  
(As required by FedRAMP SSP Section 9)

APJ SecureCloud uses no on-premises physical infrastructure.  
All compute, storage, network, and platform services reside in:

### **Azure Government (IL2) Operating Regions**
- US Gov Virginia  
- US Gov Texas  

Microsoft maintains physical security of these datacenters (per FedRAMP ATO / NIST SP 800-53 PE controls).

---

## 4. Software Components

| Component Name | Version | Category | Purpose | Notes |
|----------------|---------|----------|---------|-------|
| APJ SecureCloud Portal | Latest | Front-end UI | Displays analytics | Stateless |
| APJ Processing Engine | Latest | Back-end | Correlation & normalization | Stateless, autoscaling |
| Azure SDK | Latest | Integration | Secure calls to Azure Gov APIs | Inherited from Microsoft |
| Defender/Sentinel Connectors | Microsoft-native | Integration | Security metadata ingestion | Metadata only |
| OAuth2 Client | Built-in | Auth | Tenant app registration auth | No customer secrets stored |
| IaC Pipelines | Latest | Deployment | Build, test, release | DevOps-only environment |

---

## 5. Network Components

| Component | Type | FedRAMP Purpose | Notes |
|----------|------|-----------------|-------|
| App Service Environment (IL2) | PaaS | Compute & isolation | Autoscaling |
| Virtual Network (Gov) | Network | Segmentation | NSGs restrict east-west traffic |
| Application Gateway (WAF) | Boundary | TLS termination, Layer 7 filtering | FIPS 140-2 validated |
| Private Endpoints | Network | Secure PaaS connections | No public storage access |
| Firewall / NSG Rules | Policy | Restrict inbound API traffic | Only HTTPS allowed |
| Azure Front Door (optional) | CDN/security | DDoS protection | Inherited at edge |

None of these components directly store customer business data.

---

## 6. Storage Components

APJ SecureCloud stores **only metadata** for analytics and audit support.

| Storage Type | FedRAMP Boundary | Data Type Stored | Notes |
|--------------|------------------|------------------|-------|
| Azure Storage (Gov) | Audit/Processing | Metadata logs | SSE enabled |
| Azure SQL Gov | Processing | Normalized metadata | TDE enabled |
| Azure Key Vault | Cryptographic | API credentials for ingestion | No customer secrets |
| Azure Monitor Logs | Telemetry | System health metrics | Inherited from Azure |

**No PHI/PII or customer content is stored.**

---

## 7. Identity & Access Components

| Component | Purpose | Boundary |
|----------|----------|----------|
| Entra ID Gov IL2 | Operator IAM | Inherited from Microsoft |
| APJ SecureCloud RBAC Model | SaaS user authorization | Within SaaS boundary |
| PIM (Privileged Identity Mgmt) | Elevation for operators | Admin-only |
| Conditional Access Policies | Secure access enforcement | Applied to operators |

Customer user identities **remain in their own tenant**.  
APJ SecureCloud **never** stores customer passwords or authentication secrets.

---

## 8. Logging & Monitoring Components

| Component | Type | Purpose |
|----------|------|---------|
| Azure Monitor | Telemetry | System performance and health |
| Azure Activity Logs | Cloud operations | Security-relevant events |
| Sentinel Workspace | SIEM | Metadata correlation & detections |
| APJ SecureCloud Logs | SaaS logs | App logs, ingestion logs |

All logs retained per FedRAMP Low requirements.

---

## 9. Cryptographic Components

| Component | Purpose | FedRAMP Standard |
|----------|----------|------------------|
| Azure Key Vault (Gov) | Encryption key storage | FIPS 140-2 validated |
| Azure Storage SSE | Encrypt data at rest | AES-256 |
| TLS 1.2+ | Encrypt data in transit | FIPS-validated modules |

---

## 10. Inherited vs. System Components Summary

### **Inherited from Azure Government**
- Physical datacenters (all PE family controls)
- Virtualization layer
- Hypervisor
- Storage fabric
- Network fabric
- Identity platform (Entra ID Gov)
- Native logging pipelines
- DDoS protection
- Hardware crypto modules

### **APJ SecureCloud System Components**
- API ingestion pipeline
- Processing engine
- UI portal
- SaaS RBAC model
- Metadata correlation rules
- Monitoring dashboards
- Metadata storage
- Access control (within SaaS boundary)

### **Customer Components (Out-of-Boundary)**
- Customer’s Azure or M365 tenant
- Customer identity lifecycle
- Customer device/browser
- Customer network perimeter

---

## 11. Diagram References


Referenced filenames:

- `dfd_level0.png`
- `dfd_level1.png`
- `boundary_diagram.png`
- `rbac_model.png`

Each diagram corresponds to logical and physical elements in Section 04.

---



