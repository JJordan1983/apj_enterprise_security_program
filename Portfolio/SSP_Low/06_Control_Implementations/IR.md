# 06. Control Implementations – IR: Incident Response  
APJ SecureCloud – FedRAMP Low (LI-SaaS)

APJ SecureCloud maintains a formalized Incident Response (IR) capability aligned to NIST SP 800-61r2 and FedRAMP requirements. IR integrates:

- Azure Gov inherited platform incident management  
- Sentinel-based detection and triage  
- APJ SecureCloud IR runbooks and escalation workflows  
- Evidence preservation  
- Customer communication paths  
- IR tabletop exercises (annual)  
- Monthly FedRAMP Continuous Monitoring reporting

The system processes **only metadata**, reducing incident scope and classification complexity.

---

# **IR-1 – Incident Response Policy and Procedures**

APJ SecureCloud maintains an Incident Response Policy that defines:

- Roles and responsibilities  
- Incident definitions and categories  
- Required response timelines  
- Escalation process  
- Evidence collection and chain of custody  
- Customer notification thresholds  
- Root cause analysis (RCA)  
- Post-incident reporting requirements  

Procedures follow the NIST lifecycle:

1. **Preparation**  
2. **Detection & Analysis**  
3. **Containment**  
4. **Eradication**  
5. **Recovery**  
6. **Post-Incident Review & Lessons Learned**  

Policy located in:  
`Portfolio/M365_Security/Policies/Incident_Response_Policy.md`

---

# **IR-2 – Incident Response Training**

All APJ operators with IR duties must complete:

### **Annual IR Training**  
- NIST 800-61 fundamentals  
- Sentinel incident handling  
- Azure Gov incident workflow  
- Metadata-only SaaS incident classification  

### **Quarterly Micro-Training**  
- New Sentinel detection use cases  
- Zero-day threat briefings  
- Cloud log correlation improvements  

### **Role-Based Training (IR Team)**  
- KQL investigation techniques  
- Log Analytics deep dives  
- Key Vault access investigation  
- PIM elevation abuse detection  
- MITRE ATT&CK cloud tactics  

Training records stored in an IL2 SharePoint Gov site.

---

# **IR-3 – Incident Response Testing (Tabletop Exercises)**

APJ SecureCloud performs **annual tabletop exercises** covering:

- API credential compromise  
- Failed ingestion pipeline  
- Suspicious PIM activity  
- Sentinel high-severity correlation alerts  
- Metadata integrity anomalies  
- Unauthorized access attempts to Key Vault  

Outputs include:

- Test results  
- Lessons learned  
- Updated runbooks  
- IR maturity improvements  

Artifacts stored in:

