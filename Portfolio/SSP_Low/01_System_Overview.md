📘 APJ SecureCloud – System Overview & Authorization Boundary

System Name: APJ SecureCloud
System Acronym: ASC
Impact Level: FedRAMP Low
Deployment Model: SaaS
Hosting Environment: Microsoft Azure Government + Microsoft 365 GCC
System Owner: APJ Enterprise LLC

1. System Purpose & Mission

APJ SecureCloud is a cloud-native SaaS platform designed to provide secure document storage, workflow automation, monitoring dashboards, and compliance reporting for small-to-mid-sized organizations supporting federal missions. The system supports low-impact federal data, including: public information, administrative data, training records, audit logs, and non-sensitive operational metadata.

The platform enables customers to centralize case management, analytics, and monitoring functions while inheriting core compliance capabilities from Azure Government and Microsoft 365 GCC. APJ SecureCloud follows zero-trust principles by enforcing identity-based access, encryption, continuous monitoring, and strict least-privilege RBAC.

2. System Environment

APJ SecureCloud operates entirely within Azure Government and Microsoft 365 GCC, leveraging the following services:

Azure Government Components

Azure App Service (PaaS)

Azure SQL (elastic pool)

Azure Storage (Blob + Files)

Azure Functions

Azure Key Vault

Azure Virtual Network (subnet-level segmentation)

Azure API Management

Azure Monitor / Log Analytics

Azure Policy

Azure AD (Entra ID Gov)

Microsoft 365 GCC Components

Exchange Online (audit logging only)

SharePoint Online for document handling

Teams (for IR coordination)

Microsoft Defender XDR

Microsoft Defender for Endpoint

Sentinel (SIEM)

Purview Audit (Unified Audit Log)

3. System Users
Internal Users

Cloud Engineers

ISSO / ISSM

Security Analysts

System Administrators

Developers

External Users

Customer administrative personnel

Customer standard users

Customer auditors

All access is authenticated through Azure AD/Entra ID using:

✔ MFA
✔ Conditional Access
✔ Device compliance (where applicable)
✔ Role-based access control

4. Data Types Stored or Processed

APJ SecureCloud processes only Low-impact data per FIPS-199:

Allowed Data Types

Public-facing information

Administrative metadata

Audit logs

Case notes

Ticket metadata

Operational analytics

Training materials

Low-risk research data

Nonsensitive content uploaded by customers

Explicitly NOT allowed

❌ Controlled Unclassified Information (CUI)
❌ PII beyond business contact information
❌ PHI
❌ HIPAA data
❌ FTI
❌ Confidential proprietary data
❌ Classified information

Azure Gov data classification policies enforce this through:

SharePoint upload restrictions

Azure Storage lifecycle rules

Purview data loss prevention (DLP) policies

5. FIPS-199 Categorization

APJ SecureCloud follows FedRAMP Low baseline categorization:

Security Objective	Rating	Rationale
Confidentiality	Low	System does not process CUI or sensitive data. Access is controlled via identity and MFA.
Integrity	Low	Integrity protections provided by Azure SQL, Storage Service Encryption, and audit logging.
Availability	Low	Service interruptions have limited impact; redundant PaaS architecture provides resilience.

Overall Impact Level: LOW

6. Authorization Boundary Description

The APJ SecureCloud authorization boundary includes:

Inside the Boundary

All application code (API backend, web frontend)

Azure Gov PaaS hosting environment

Azure SQL database

Storage accounts

Key Vault

Log Analytics workspace

Sentinel workspace

CI/CD pipelines

Authentication & authorization (Azure AD)

Monitoring & alerting

M365 GCC compliance components

Outside the Boundary

Customer endpoints and devices

External customer networks

Azure Gov underlying hypervisor + fabric (inherited)

Microsoft 365 GCC underlying infrastructure (inherited)

Third-party API providers

Interconnections

Microsoft 365 GCC

Azure Gov PaaS fabric

Optional customer-built APIs (HTTPS only)

No classified or moderate/high systems

7. System Components (High-Level Inventory)
Component	Type	Location	Purpose	Inheritance
Azure App Service	PaaS	Azure Gov	Runs ASC backend	Shared/Inherited
Azure SQL	PaaS	Azure Gov	Stores system metadata	Shared/Inherited
Azure Storage	PaaS	Azure Gov	User files, logs	Shared/Inherited
Key Vault	PaaS	Azure Gov	Secrets, certs, keys	Shared/Inherited
Azure AD Gov	IAM	GCC	Identity + MFA	Inherited
Defender XDR	Security	GCC	Endpoint + cloud workload protection	Shared
Sentinel	SIEM	Azure Gov	SIEM + analytics	Customer
Purview Audit	Compliance	GCC	Logs + investigations	Customer
Log Analytics	Monitoring	Azure Gov	Log ingestion	Customer
8. Technology Stack

Frontend: HTML/JS, running via Azure App Service
Backend: .NET and Python Functions
Database: Azure SQL + Storage
Identity: Azure AD Gov (Entra ID)
SIEM: Sentinel
XDR: Microsoft Defender
Pipeline: GitHub Actions or Azure DevOps

9. Security Services Used

APJ SecureCloud inherits or uses federal-compliant capabilities:

Azure AD MFA

Conditional Access (CA)

Platform encryption (FIPS 140-2 validated crypto modules)

Storage Service Encryption (SSE)

TDE for SQL

Defender for Cloud baseline recommendations

Sentinel Analytics Rules

Purview Audit

Azure Firewall / NSGs

Policy compliance monitoring
10. Logical Network Diagram (ASCII)
                         +------------------------------+
                         |       Azure AD / Entra ID     |
                         |  Authentication + MFA + RBAC   |
                         +------------------------------+
                                     |
                                     v
             +---------------------------------------------------+
             |               Azure Government (IL2)               |
             |                                                   |
             |  +----------------+     +-----------------------+ |
             |  |  App Service   |<--->|   Azure SQL Database  | |
             |  +----------------+     +-----------------------+ |
             |         |                          ^             |
             |         v                          |             |
             |   +--------------+         +-------------------+ |
             |   |  Blob/File   |<------->| Key Vault (Secrets)| |
             |   |   Storage    |         +-------------------+ |
             |   +--------------+                              |
             |         |                                       |
             |         v                                       |
             |   +-----------------+      +-------------------+ |
             |   | Log Analytics   |<---->| Microsoft Sentinel | |
             |   +-----------------+      +-------------------+ |
             |                                                   |
             +---------------------------------------------------+
11. Data Flow Diagram (Level 1)
 Users ---> Browser/UI ---> App Service ---> SQL/Storage ---> Logs ---> Sentinel ---> Analysts

 12. Inherited & Shared Controls

APJ SecureCloud inherits controls from:

Azure Government

Physical environment

Hypervisor

Fabric security

Host monitoring

Network backbone

FIPS-validated cryptographic modules

Microsoft 365 GCC

Email security

Purview audit

Identity platform protections

CASB/Defender capabilities
