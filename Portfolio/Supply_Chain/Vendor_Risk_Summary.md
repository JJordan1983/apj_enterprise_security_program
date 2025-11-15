# Vendor Risk Summary  
APJ SecureCloud – Supply Chain Risk Management

APJ SecureCloud relies on a small set of vetted third-party services and open-source components to operate its metadata-only SaaS platform hosted in Azure Government IL2. To keep the supply chain clean and predictable, every vendor and component goes through:

1. **Initial vetting**  
2. **A structured security review**  
3. **Weighted risk scoring**  
4. **SBOM entry creation**  
5. **KEV tracking**  
6. **Annual or quarterly risk reassessment**

---

# 1. Vendor Classifications

Vendors fall into three categories:

### **A. Core Cloud Provider**
- Microsoft Azure Government (IL2)

### **B. Supporting SaaS Tools**
- CI/CD, scanning tools, repository services

### **C. Open-Source Libraries**
- Only actively maintained components  
- Dependency scanning is enforced every build  

---

# 2. Weighted Risk Method

APJ rates each vendor or component based on six factors:

| Category | Weight |
|----------|--------|
| Security Posture | 30% |
| Vulnerability History | 20% |
| Operational Stability | 10% |
| Integration Risk | 15% |
| Dependency Criticality | 10% |
| Impact if Compromised | 15% |

Scores between **1.0 and 5.0** determine risk:

| Score | Risk Level |
|-------|------------|
| 1.0–2.0 | Low |
| 2.01–3.5 | Medium |
| 3.51–5.0 | High |

High-risk items require:
- formal mitigation plans  
- POA&M entries  
- leadership approval to continue  

---

# 3. KEV Monitoring

APJ checks all vendor components monthly against:
- **CISA KEV Catalog**  
- **MSRC advisories**  
- **NVD feeds**

If a component appears on the KEV list:
- It becomes **High Risk** immediately  
- A POA&M item is created  
- Patching or removal becomes the top priority  

---

# 4. Continuous Monitoring Activities

APJ performs:

- Monthly KEV checks  
- Quarterly vendor reviews  
- Annual full SCRM audit  
- Continuous dependency scanning in CI/CD  
- SBOM updates on every major release  

---

# 5. Evidence Locations

All documentation is under:

Portfolio/Supply_Chain/
Portfolio/POAM/
Portfolio/Risk/
Portfolio/DevSecOps/
