# 03. Data Flow Diagram (DFD)

This section describes how data moves through the APJ SecureCloud SaaS platform.  
APJ SecureCloud is classified as a **metadata-processing LI-SaaS system**.  
It does **not** store or process customer PHI/PII data.  
Only telemetry, audit metadata, resource configuration metadata, and security events are transmitted.

---

## 1. Data Types Processed

APJ SecureCloud only processes:

- Azure AD / Entra ID user metadata  
- Audit and activity logs  
- Resource configuration metadata  
- Alert metadata (Defender, Sentinel)  
- Compliance state data  
- API request/response metadata  
- Health/telemetry metrics  
- Incident metadata  

**No customer business data** (documents, emails, files, records, PHI/PII) flows through or is stored within APJ SecureCloud.

---

## 2. Logical Data Flow (Level 0 DFD)

+------------------+ HTTPS/TLS +-----------------------+
| Customer Tenant| ----------------------> | APJ SecureCloud |
| (Azure / M365) | | API Ingestion Layer |
+------------------+ +-----------+-----------+
|
v
+-----------------------+
| Processing Engine |
| (Normalization, |
| Correlation, Rules) |
+-----------+-----------+
|
v
+-----------------------+
| Analytics Output |
| Dashboards/Reports |
+-----------+-----------+
|
v
+-----------------------+
| Customer Browser/UI |
+-----------------------+


---

## 3. Level 1 Detailed Data Flow

[1] Entra ID/Azure AD Metadata

Customer Tenant
|
|---> App Registration (API Permissions)
|
APJ SecureCloud Ingestion (HTTPS/TLS 1.2+)
|
|---> Normalize (JSON → Internal Schema)
|---> Correlate (Rules Engine)
|
Analytics UI (Read-only dashboards)

[2] Activity & Audit Logs

Azure AD → Export API → APJ SecureCloud
Defender for Cloud → Alerts API → APJ SecureCloud
Sentinel → Metadata API → APJ SecureCloud

[3] Output / Visualizations

APJ SecureCloud → Browser UI (HTTPS)
|---> Risk Summaries
|---> Access Insights
|---> Resource Compliance Status
|---> Audit Trails (Metadata Only)

No data is pushed back into the customer tenant.


---

## 4. Trust Boundaries

### **Boundary A: Customer Tenant → APJ SecureCloud**
- API tokens stored in Azure Key Vault
- OAuth2 App Registration required
- Traffic is encrypted (TLS 1.2+)
- Customer identity boundary remains under Azure AD

### **Boundary B: APJ SecureCloud Internal Processing**
- All components reside in Azure Government (IL2)
- No multi-customer data mixing (metadata partitioning enforced)
- All processing uses short-lived tokens
- Logs stored in Azure storage with encryption at rest (SSE)

### **Boundary C: APJ SecureCloud → Customer Browser**
- HTTPS encrypted channel
- Read-only dashboards
- No download of raw customer data

---

## 5. Diagram Files Included

The following diagram image files should be uploaded to:

Portfolio/Diagrams/

- `dfd_level0.png`
- `dfd_level1.png`
- `boundary_diagram.png`
- `rbac_model.png`

Upload them after they are generated.

---

## 6. FedRAMP Control Mapping

| Control | Mapping | Notes |
|--------|---------|-------|
| AC-4   | Boundary protection | TLS 1.2+ enforced for all APIs |
| AC-6   | Least privilege | API permissions limited to metadata only |
| AU-2   | Audit events | Only audit metadata is ingested |
| AU-6   | Audit review | Customer retains ownership of audit review |
| SC-7   | Boundary defense | Ingress restricted via Azure Gov WAF |
| SC-13  | Cryptographic protection | FIPS 140-2 validated crypto |
| SC-28  | Protection of data | Metadata only; encrypted at rest and in transit |
| SR-12  | Supply chain | Inheritance from Azure Government IL2 |

---

## 7. Notes on Data Minimization

APJ SecureCloud intentionally implements **data minimization**, processing only:

- Identity metadata  
- Logs  
- Compliance posture signals  
- Alerts  

This ensures:

- Lower authorization impact  
- No sensitive customer data retention  
- Faster FedRAMP review  
- Clear shared responsibility delineation  

---

