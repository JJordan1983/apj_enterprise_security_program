# Access Control Policy  
APJ SecureCloud – Azure Government Zero Trust Model  
Version 1.0

## 1. Purpose
This Access Control Policy defines how APJ SecureCloud governs identity,
authentication, authorization, and privileged access within its FedRAMP Low
metadata-only SaaS boundary hosted entirely on Microsoft Azure Government (IL2).

The policy enforces:
- Zero Trust access principles  
- MFA for all accounts  
- PIM for all privileged roles  
- Role-based access control (RBAC)  
- Conditional Access  
- Least privilege  
- Logging and monitoring of all administrative operations  

---

## 2. Scope
This policy applies to:
- APJ SecureCloud employees  
- Administrators with access to Azure Gov resources  
- CI/CD service principals  
- Managed Identities  
- Any third-party administrator supporting APJ SecureCloud  

The scope covers SaaS-layer access only. Azure Gov infrastructure access is
inherited from Microsoft’s FedRAMP authorization.

---

## 3. Zero Trust Principles
APJ SecureCloud enforces:

1. **Verify explicitly**  
   - MFA required  
   - Device compliance required  
   - CA location restrictions  

2. **Least privilege access**  
   - RBAC roles assigned minimally  
   - No standing admin accounts  
   - PIM activation required  

3. **Assume breach**  
   - Continuous monitoring via Sentinel  
   - Session risk scoring via Identity Protection  
   - Terminate risky sessions automatically  

---

## 4. Identification and Authentication (IA Integration)
All identities (users, service principals, managed identities) must authenticate
via secure Azure Gov identity controls:

- Azure AD (Entra ID)  
- MFA (Authenticator app preferred)  
- CA enforcing compliant devices  
- Token-based authentication for APIs  
- Certificate-based authentication for automation  

Password use is minimized; key or certificate-based auth is recommended.

---

## 5. Authorization and RBAC Requirements
Authorization is enforced using RBAC with the following required practices:

### Required RBAC Principles
- Grant the **least privilege** needed  
- Use **built-in roles** when possible  
- Use **custom roles** only when required and approved  
- Review roles quarterly  
- Document all role mappings  

### Privileged Roles (must use PIM)
- Owner  
- Contributor  
- User Access Administrator  
- Security Administrator  
- Global Administrator  
- Sentinel Contributor  

No user may permanently hold these roles.

---

## 6. Privileged Identity Management (PIM)
### PIM Requirements
- Admin roles are disabled by default  
- Admin must request elevation  
- Justification required  
- Approval required for high-impact roles  
- Time-bound access enforced  
- Session logging required  
- Risk-based conditional access enforced  

### PIM Logs  
PIM elevation logs must be monitored daily through:
- Sentinel  
- Azure Activity Logs  
- Risky Sign-In Dashboard  

---

## 7. Conditional Access (CA)
APJ enforces CA policies requiring:

- MFA for all logins  
- Device compliance checks  
- Block legacy authentication  
- Block anonymous sessions  
- Block high-risk sign-ins  
- Require passwordless technology for admins  
- Only allow logins from approved countries (US-only if required)  

CA policies must be reviewed quarterly.

---

## 8. Session Control
Sessions must terminate under:

- PIM elevation expiry  
- Elevated session after 60 minutes of inactivity  
- High-risk sign-in  
- Device compliance failure  
- Identity Protection high risk  

---

## 9. Service Accounts & Managed Identities
### Service Accounts
Service principals must:
- Use certificate authentication  
- Rotate certificates annually  
- Have least privilege roles  
- Never authenticate with passwords stored in code  
- Be monitored via Sentinel for anomalies  

### Managed Identities
Must be used whenever possible for:
- Azure Functions  
- App Service  
- Key Vault access  

---

## 10. Access Reviews
Quarterly access reviews must include:

- User access to all Azure Gov resources  
- Privileged roles  
- Service principals  
- GitHub/Azure DevOps access  
- Sentinel & Log Analytics access  

Evidence stored in:
`Portfolio/Access_Reviews/`

---

## 11. Logging & Monitoring Requirements
All access events must generate logs via:

- Azure AD Sign-In Logs  
- PIM logs  
- Activity Logs  
- Sentinel KQL detections  
- Conditional Access insights  
- Identity Protection alerts  

Any anomalous behavior must initiate the IR workflow.

---

## 12. Violation of Policy
Any violation may result in:
- Immediate access removal  
- Security investigation  
- Sanctions up to termination  

---

## 13. Approval
This policy is approved by the APJ SecureCloud Security Program Lead and reviewed annually.

---
