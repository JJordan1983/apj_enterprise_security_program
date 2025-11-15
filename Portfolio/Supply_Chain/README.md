# Supply Chain Risk Management  
APJ SecureCloud

This folder contains all artifacts supporting APJ SecureCloud’s Supply Chain Risk Management (SCRM) program. These items help identify, evaluate, monitor, and manage third-party risks that may affect the security and reliability of the SaaS platform.

APJ’s SCRM approach is based on a simple model: verify, validate, and monitor. The goal is to catch risks early, avoid surprises, and keep the system clean and stable.

---

## 📁 Folder Contents

### 1. Vendor_Review_Template.md  
A structured template used to perform initial and annual reviews of any third-party product, API, service, open-source library, or cloud dependency.

### 2. SBOM_Template.md / SBOM_Template.csv  
A standard Software Bill of Materials used to track libraries, versions, sources, licenses, and vulnerability history. Supports CI/CD dependency scanning.

### 3. CISA_KEV_Tracking.xlsx  
A sheet used to track Known Exploited Vulnerabilities (KEVs) published by CISA. Items tied to APJ components are highlighted and assigned remediation deadlines.

### 4. Third_Party_Onboarding_Checklist.md  
A requirements checklist ensuring all vendors meet APJ’s minimal security expectations before onboarding.

### 5. Vendor_Scoring_Model.md (included below)  
Provides a consistent scoring method for vendors and components, helping rank third-party risks.

---

## 🔄 How to Use This Folder

### **New Vendor or Tool**
1. Complete the onboarding checklist  
2. Perform a vendor security review  
3. Add component(s) to the SBOM  
4. Add any related CVEs to the KEV file (if applicable)  
5. Assign a risk score using the scoring model  
6. Capture required mitigations in the POA&M, if needed  

### **Annual / Quarterly Tasks**
- Review vendor security documents  
- Update SBOM entries  
- Refresh KEV tracking  
- Re-score key suppliers  
- Update POA&M if weaknesses are found  

---

## 📚 Related Documentation

- **Supply_Chain_Risk_Management_Policy.md**  
  Governance policy outlining SCRM expectations.

- **RA Family**  
  All supply chain risks must flow into the Risk Register.

- **POA&M**  
  Weaknesses tied to vendors or components must be tracked to closure.

---

## ✔ Evidence for Audits
Auditors should review:
- Vendor review forms  
- SBOM  
- Latest KEV sheet  
- Onboarding checklists  
- POA&M entries mapped to supply chain issues  
- Dependency scanning reports from CI/CD  

This folder provides everything needed to validate APJ SecureCloud’s supply chain security posture.
