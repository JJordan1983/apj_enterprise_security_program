# Supply Chain Risk Management Policy  
APJ SecureCloud  
Version 1.0

## 1. Purpose
Provides requirements for vetting and monitoring external services,
dependencies, and cloud providers.

## 2. Azure Government Inheritance
Azure Gov provides:
- Hardware vetting  
- Vendor controls  
- Supply chain assurances  
- FedRAMP P-ATO  

## 3. APJ SaaS-Layer Responsibilities
APJ must:
- Approve third-party libraries  
- Enforce dependency scanning  
- Track vendor security advisories  
- Maintain SBOM (optional for Low)  
- Verify cloud provider FedRAMP status  

## 4. Monitoring
Use:
- GitHub Dependabot / DevOps scanning  
- Defender for DevOps  
- Microsoft advisories  
- CISA KEV catalog  

## 5. Approval
Approved by APJ Security Program Lead.
