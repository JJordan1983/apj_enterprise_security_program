# 06. Control Implementations – AU: Audit & Accountability  
APJ SecureCloud – FedRAMP Low (LI-SaaS)

APJ SecureCloud uses Azure Government’s native logging stack (Azure Monitor, Log Analytics, and Microsoft Sentinel) to collect, analyze, store, and protect audit logs for all system activity.  
The system ingests **no customer content**, only metadata required to operate APJ SecureCloud services.

All AU controls rely on:
- Azure Gov IL2 inherited controls  
- Log Analytics workspace with secure retention  
- Sentinel analytic rules for detection  
- Defender for Cloud audit signals  
- APJ SecureCloud audit procedures (see Portfolio/M365_Security/Policies/Logging_Policy.md)

---

## **AU-1 – Policy and Procedures**

APJ SecureCloud maintains a Logging & Monitoring Policy that defines:

- Audit log categories  
- Minimum events captured  
- Retention periods  
- Responsibilities (Security Officer, Cloud Ops, Analysts)  
- Review and reporting processes  
- Sentinel alert expectations  
- Log integrity and access restrictions  

Procedures cover:

- How audit logs are generated  
- Daily Sentinel log health checks  
- Manual investigations  
- Evidence handling for FedRAMP audits  

Policy location:  
`Portfolio/M365_Security/Policies/Logging_Policy.md`

---

## **AU-2 – Audit Events**

APJ SecureCloud captures all significant events from:

### **Azure AD / Entra ID**
- Authentication events  
- MFA prompts  
- Privileged identity activation (PIM)  
- Conditional Access decisions  

### **Azure Gov Resources**
- Key Vault access attempts  
- Storage account operations  
- App Service configuration changes  
- SQL audit logs  
- Virtual network / NSG rule modifications  

### **Sentinel SIEM**
- KQL detections  
- Anomaly rules  
- Correlated alerts  
- Watchlist evaluations  

### **Application Layer**
- Admin portal logins  
- API token usage  
- Configuration updates  
- Deployment pipeline activity  

Event coverage follows the FedRAMP Low baseline and Azure CIS benchmarks.

---

## **AU-3 – Content of Audit Records**

Each audit log includes:

- Event type  
- Timestamp (UTC)  
- Source service  
- User/Service principal ID  
- IP address (if applicable)  
- Correlation ID  
- Operation success/failure  
- Resource ID  

Azure Gov ensures immutability and provides tamper-resistant logging.

---

## **AU-4 – Audit Storage Capacity**

APJ SecureCloud ensures adequate storage by:

- Allocating a dedicated Log Analytics workspace  
- Auto-expanding retention per Microsoft Gov policies  
- Monitoring log ingestion volume and health  
- Alerting when high-volume anomalies occur  

Storage capacity is reviewed quarterly.

---

## **AU-5 – Response to Audit Processing Failures**

Azure Monitor and Sentinel generate alerts when:

- Log ingestion stops  
- Alerts fail to fire  
- Workspace reaches quota  
- Data connectors disconnect  

APJ SecureCloud response procedure:

1. Analyst receives Sentinel alert  
2. Validate ingestion pipeline health  
3. Restart or reauthorize connector  
4. Document incident in IR system  
5. Report in monthly ConMon summary if required  

---

## **AU-6 – Audit Review, Analysis, and Reporting**

Log review occurs:

### **Daily**
- Sentinel health checks  
- Ingestion status  
- Correlated alert review  

### **Weekly**
- Access review anomalies  
- PIM usage logs  
- Failed login trend analysis  

### **Monthly**
- FedRAMP ConMon audit package validation  
- Reporting to system owner  

### **Quarterly**
- Full RBAC & Conditional Access review  
- SIEM analytics tuning  
- Review with APJ Security Officer  

Evidence stored in:  
`Portfolio/M365_Security/Reports/ConMon/`

---

## **AU-7 – Audit Reduction and Report Generation**

Analysts use:

- **KQL queries**  
- **Workbooks**  
- **Custom dashboards**  
- **Watchl**
