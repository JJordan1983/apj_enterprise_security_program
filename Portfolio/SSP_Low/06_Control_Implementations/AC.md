# 06. Control Implementations – AC: Access Control  
APJ SecureCloud – FedRAMP Low (LI-SaaS)  
Metadata-Only SaaS • No Customer PHI/PII • Azure Gov IL2

APJ SecureCloud enforces access control through Azure Government, Entra ID Gov IL2, RBAC, and SaaS-level authorization.  
Customer tenants maintain control of their own users and API permissions.  
APJ SecureCloud operators use PIM, MFA, and Conditional Access.

---

## **AC-1 – Access Control Policy & Procedures**
APJ SecureCloud maintains documented Access Control Policy and Procedures aligned with:
- NIST SP 800-53 Rev5 AC family  
- FedRAMP LI-SaaS requirements  
- Azure Gov IL2 inherited identity controls  

Key elements:
- SaaS RBAC model (Admin, Analyst, Viewer)
- Operator controls using Entra ID Gov + PIM
- All privileged actions logged in Azure Activity Log
- Quarterly access reviews performed by APJ

Procedures stored in:  
`Portfolio/M365_Security/Access_Control_Policy.md`

---

## **AC-2 – Account Management**
APJ SecureCloud DOES NOT manage customer accounts.  
All customer identities remain within the customer’s Azure AD tenant.

APJ responsibilities:
- Maintain operator accounts in Entra Gov IL2
- Use PIM for elevation
- Perform quarterly privileged access reviews
- Enforce Conditional Access for operators
- Log all operator authentication and access events

Azure Gov provides:
- Identity platform security  
- MFA enforcement engine  
- Authentication tokens and session protection  

Customer responsibilities:
- Grant API permissions to APJ SecureCloud app registration  
- Manage and review their own users  
- Disable unused identities  

---

## **AC-3 – Access Enforcement**
APJ SecureCloud enforces access through:
- SaaS RBAC model  
- Role separation (Admin, Analyst, Viewer)  
- API-level scopes (read-only metadata ingestion)  
- Application Gateway + NSG inbound restrictions  
- Operator access enforced with PIM + CA policies  

No direct data modification occurs within the SaaS; read-only metadata analytics only.

---

## **AC-5 – Separation of Duties**
- Admins cannot modify ingestion logic  
- Analysts cannot modify RBAC  
- Viewers have read-only dashboard access  
- Developers cannot approve production changes (DevOps separation)  
- PIM logs track each elevation and reviewer approval  

Azure Gov separates platform duties.

---

## **AC-6 – Least Privilege**
Implemented through:
- Fine-grained RBAC roles  
- PIM for privileged role elevation  
- Just-in-time (JIT) access  
- Conditional Access requiring MFA  
- Key Vault using RBAC + private endpoints  
- System components run with managed identities (least privilege)  

Customer users have no write access in SaaS.

---

## **AC-7 – Unsuccessful Login Attempts**
APJ SecureCloud inherits from Entra Gov IL2:
- Lockout policies  
- Smart lockout  
- Brute-force protections  
- Login anomaly detection  

SaaS accounts cannot be brute-forced because no local credential store exists.

---

## **AC-8 – System Use Notification**
User login banner displayed via:
- APJ SecureCloud login page  
- Terms of Use presented before first login  
- Periodic banner acknowledgement required for Admin role  

---

## **AC-9 – Previous Logon Notification**
Inherits from Entra ID Gov:
- Last sign-in details displayed in portal  
- Authentication details logged in Azure Core Logs  

---

## **AC-11 – Session Lock**
UI automatically locks after **15 minutes** of inactivity.

---

## **AC-12 – Session Termination**
Sessions terminate:
- When browser tab closes  
- After 30 minutes absolute timeout  
- After PIM elevation expires  
- When Conditional Access signals risk anomaly  

---

## **AC-14 – Permitted Actions Without Identification**
None.  
All access requires authentication via Entra ID.

---

## **AC-17 – Remote Access**
Remote operator access:
- Enforced via Conditional Access  
- Restricted to U.S. IP ranges (optional customer requirement)  
- Requires MFA + compliant device  
- Logged in Audit Logs  

Customer access is always through HTTPS from browser.

---

## **AC-18 – Wireless Access**
No wireless components exist within the SaaS boundary.  
Operators manage components via Azure Portal over HTTPS.

---

## **AC-19 – Access Control for Mobile Devices**
No APJ-managed mobile devices.  
Access governed by Conditional Access.

---

## **AC-20 – Use of External Information Systems**
Customer systems considered *external* to the SaaS boundary.

APJ SecureCloud:
- Does not depend on external unmanaged systems  
- Ingests metadata only through secure OAuth2 APIs  

---

## **AC-21 – Information Sharing**
APJ SecureCloud shares no customer data; only metadata is ingested.  
No inter-agency data sharing occurs.

---

## **AC-22 – Publicly Accessible Content**
APJ SecureCloud provides no public-facing content.

---

# **End of AC Family**
