# Vendor Scoring Model  
APJ SecureCloud

This model gives each vendor or component a numerical score based on security posture, operational stability, vulnerability exposure, and impact on APJ SecureCloud. Lower scores indicate lower risk.

---

# 1. Scoring Scale

Each category receives a score of **1 to 5**:

- **1 = Low Risk**
- **3 = Moderate Risk**
- **5 = High Risk**

A perfect vendor scores near 8–12.  
High-risk vendors score above 20.

---

# 2. Categories & Definitions

## **A. Security Posture**
- 1 – Documented security program, current SOC 2, active patching  
- 3 – Some documentation, slow patching  
- 5 – No documentation or outdated practices  

## **B. Vulnerability History**
- 1 – No critical/high vulnerabilities in past 12 months  
- 3 – Some medium/high vulnerabilities, regular fixes  
- 5 – Known exploited vulnerabilities (KEV) or major security incidents  

## **C. Operational Stability**
- 1 – Strong uptime history, reliable support  
- 3 – Occasional outages or slow support  
- 5 – Frequent outages or abandoned product  

## **D. Integration Risk**
- 1 – Easy identity/logging integration, low blast radius  
- 3 – Requires special handling or custom configuration  
- 5 – No MFA, weak logging, or poor access controls  

## **E. Dependency Criticality**
- 1 – Non-critical utility or optional tool  
- 3 – Used in multiple workloads  
- 5 – Core dependency affecting authentication or security  

## **F. Impact if Compromised**
- 1 – Minimal exposure, isolated  
- 3 – Moderate impact to operations  
- 5 – Could disrupt authentication, logs, or core SaaS components  

---

# 3. Scoring Table

| Category | Score (1–5) | Notes |
|----------|-------------|-------|
| Security Posture | | |
| Vulnerability History | | |
| Operational Stability | | |
| Integration Risk | | |
| Dependency Criticality | | |
| Impact if Compromised | | |

**Total Score:**  
**Risk Level:** Low / Medium / High  

---

# 4. Risk Level Thresholds

| Total Score | Risk Level |
|-------------|------------|
| 6–12 | Low |
| 13–20 | Medium |
| 21–30 | High |

High-risk vendors must be:
- Mitigated  
- Monitored more closely  
- Tracked in the POA&M  

---

# 5. Remediation Actions by Risk Level

### **Low**
- No immediate action required  
- Review annually  

### **Medium**
- Add mitigation controls  
- Review quarterly  
- Document in risk register  

### **High**
- Add to POA&M  
- Consider alternative solutions  
- Review monthly  
- Executive approval required to use or continue  

---

# 6. Storage Location
Completed scoring sheets should be stored under:

