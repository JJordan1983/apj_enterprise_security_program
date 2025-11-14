📘 APJ SecureCloud – Authorization Boundary (FedRAMP Low)
1. Boundary Summary

The APJ SecureCloud authorization boundary includes all system components that store, process, transmit, or secure federal customer data within Azure Government (IL2) and Microsoft 365 GCC. This includes compute, storage, identity, monitoring, logging, and operational components required to deliver the SaaS platform to customers.

APJ SecureCloud uses a multi-tenant architecture, where each customer receives logically isolated data spaces, RBAC-scoped access, and dedicated access policies, while all tenants share the same underlying PaaS infrastructure. Tenant isolation is enforced through:
✔ Azure AD group segregation
✔ Application-layer tenant GUID routing
✔ SQL row-level security
✔ Tenant-specific storage containers
✔ Dedicated audit log tagging
✔ Strict RBAC boundaries

2. Components Inside the Authorization Boundary

All components required for the direct operation of APJ SecureCloud are inside the authorization boundary.

Application Layer

Azure App Service

Azure Functions

Azure API Management

Application configuration + secrets retrieval (through Key Vault)

Data Layer

Azure SQL Database (row-level security for multi-tenancy)

Storage Accounts: Blob/File containers

Container-level RBAC

SSE (Storage Service Encryption)

Identity & Access Control

Azure AD Gov tenant

Conditional Access

Entra ID RBAC roles

Tenant-level custom roles

Privileged Identity Management (PIM) for elevated accounts

Monitoring & Logging

Log Analytics workspace

Microsoft Sentinel workspace

Defender XDR integration

Purview Audit (Unified Audit Log)

Security Controls & Services

Azure Firewall / NSG baselines

Defender for Cloud (recommendations + compliance)

Managed Identities

Azure Key Vault

Azure Policy

3. Components Outside the Authorization Boundary
Customer-managed components (out of scope):

End-user endpoints (mobile/desktop)

Customer network or VPN

Customer device compliance enforcement

Customer-managed SIEM or SOAR tools

Microsoft-managed components (inherited controls):

Azure Gov physical infrastructure

Underlying hypervisor and fabric

Physical access, guards, cameras (PE controls)

Datacenter environmental protections

Azure AD authentication backend

Microsoft 365 GCC backend security controls

Global network infrastructure

Third-party or external interconnections (if used):

Ticketing or workflow integrations

Non-government SaaS providers (HTTPS only)

Customer API integrations

All external interconnections use:
✔ Mutual TLS or HTTPS
✔ API keys or OAuth 2.0
✔ IP/identity restrictions

4. Boundary Diagram (ASCII Version)

(A PNG + draw.io version will be delivered in the Diagrams folder)

                             +-------------------------------+
                             | Azure AD / Entra ID (Gov)     |
                             |  - MFA                         |
                             |  - RBAC                        |
                             |  - Conditional Access          |
                             +---------------+----------------+
                                             |
                                             v
        +-----------------------------------------------------------------------+
        |                        Azure Government (IL2)                          |
        |                                                                       |
        |   +------------------+        +----------------------+                |
        |   |  App Service     |<------>| Azure SQL Database   |                |
        |   | (Web/API)        |        |  (Row-Level Security)|                |
        |   +---------+--------+        +----------------------+                |
        |             |                                                     +---+
        |             v                                                     |
        |      +------------+       +-------------------+        +--------------------+
        |      |  Storage   |<----->| Azure Key Vault  |<------>| Managed Identities |
        |      | Blob/File  |       +-------------------+        +--------------------+
        |      +------------+                                                     |
        |             |                                                           |
        |             v                                                           |
        |      +---------------------+        +------------------------+          |
        |      | Log Analytics       |<------>| Microsoft Sentinel     |          |
        |      +---------------------+        +------------------------+          |
        |                                                                       |
        +-----------------------------------------------------------------------+
 

5. Multi-Tenant Isolation Controls

APJ SecureCloud enforces tenant separation through the following mechanisms:

Application-Layer Isolation

Tenant GUID embedded in every request

Middleware enforces tenant context

No shared user or data tables

Database Isolation

Row-Level Security (RLS)

Tenant-specific SQL schemas when applicable

Encryption at rest + in transit

No cross-tenant JOINs or stored procedures

Storage Isolation

Each tenant receives a dedicated container

SAS tokens scoped to tenant container only

Access logged with tenant-level audit tags

Logging Isolation

Logs tagged with tenantId property

Sentinel analytic rules enforce cross-tenant detection

RBAC Segmentation

Tenant-specific administrative roles

No cross-tenant namespace overlap

Tiered RBAC for internal staff (ISSO, SysAdmin, DevOps)

6. Boundary Rationale

The authorization boundary is limited to components where:

the system processes customer data

the system enforces security controls

APJ Enterprise maintains operational responsibility

audit logs are generated and protected

security functions are applied

Azure Gov + Microsoft 365 GCC backend systems remain inherited, consistent with FedRAMP doctrine.

7. Ports, Protocols, and Services (PPS)

APJ SecureCloud uses only approved FIPS-compliant and government-approved protocols:

Port	Protocol	Description
443	HTTPS/TLS 1.2+	All frontend + backend communication
1433	TLS Encrypted SQL	Azure SQL PaaS connection
443	HTTPS	API Management + Function App
443	HTTPS	Storage (Blob/File)
443	HTTPS	Key Vault access
443	HTTPS	Log ingestion to Sentinel
443	HTTPS	Defender/MDI/MDM telemetry

No inbound traffic originates from the public internet except through HTTPS to App Service.

8. Authorization Boundary Narrative (FedRAMP-Style)

APJ SecureCloud defines the system boundary as all application, identity, data, and security components required for the delivery of this cloud service. Azure Government is used for hosting, data storage, compute, and monitoring. Microsoft 365 GCC is used for identity, audit log retrieval, and O365-based security tooling (Defender, Purview, and unified audit log).

All tenant data is fully segregated via application-layer tenant enforcement, SQL row-level security, and container-level RBAC. System components not involved in storing, processing, or transmitting data—such as developer laptops, customer devices, and Azure Gov physical hardware—are explicitly out of scope or inherited.

Audit logs, monitoring signals, and security events flow through the boundary into Log Analytics and Sentinel, where they are analyzed and correlated into incidents for triage by APJ security analysts. The system boundary fully encompasses all functions APJ Enterprise is responsible for under FedRAMP.
