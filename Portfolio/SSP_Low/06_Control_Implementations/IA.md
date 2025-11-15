# 06. Control Implementations – IA: Identification & Authentication  
APJ SecureCloud – FedRAMP Low (LI-SaaS)

APJ SecureCloud relies entirely on Azure Government’s FedRAMP-authorized identity services (Entra ID Gov IL2) for authentication, MFA, token issuance, session management, password policy enforcement, and privileged access management.  
No authentication secrets are stored or managed by APJ SecureCloud.

APJ SecureCloud operators authenticate against Entra ID Gov using MFA + Conditional Access + PIM.  
Customer tenants authenticate using their own Entra ID platform and grant read-only permissions to allow metadata ingestion into APJ SecureCloud.

---

## **IA-1 – Identification & Authentication Policy and Procedures**

APJ SecureCloud maintains a formal IA Policy defining:

- Identity proofing requirements  
- Authentication mechanisms  
- Use of MFA for all operator access  
- PIM elevation workflow  
- Requirements for service principals and managed identities  
- Password and token lifecycle expectations  
- Customer identity separation  
- Device compliance expectations for operators  

Procedures include:

- Onboarding and offboarding of APJ personnel  
- Privileged identity workflow approval  
- Credential revocation  
- Incident response steps for compromised identities  

Policy location:  
`Portfolio/M365_Security/Policies/Identity_And_Authentication_Policy.md`

---

## **IA-2 – Identification & Authentication (Organizational Users)**

APJ operator accounts must:

- Authenticate using Entra ID Gov IL2  
- Use MFA at every sign-in  
- Use compliant devices enforced via Conditional Access  
- Elevate privileges using PIM (no permanent admin accounts)  
- Rotate tokens per Azure Gov best practices  
- Follow APJ offboarding process within 24 hours of separation  

Key points:

- No passwords stored in APJ SecureCloud  
- No local accounts exist  
- All operator actions logged in Azure AD Sign-In Logs  
- API access uses certificate-based authentication  

Azure Gov enforces:

- Strong authentication  
- FIPS-validated crypto modules  
- Identity security across cloud boundaries  

---

## **IA-3 – Device Identification**

APJ SecureCloud does not identify customer devices.  
Customer endpoints are out-of-boundary.

APJ operator devices must:

- Be compliant with Conditional Access policies  
- Have endpoint protection enabled (Defender)  
- Meet corporate security baseline  
- Pass device health checks before authentication  

Azure Gov handles device identity signals using:

- Device Compliance policies  
- Azure AD Join / Hybrid Join  
- Conditional Access risk scoring  

---

## **IA-4 – Identifier Management**

Identifiers include:

### **APJ Operator Accounts**
- Unique Entra ID Gov UPN  
- Assigned per least privilege  
- Disabled or deleted when no longer required  
- Reviewed quarterly during access reviews  

### **Service Principals**
Used to authenticate ingestion pipelines using:

- Certificate-based authentication  
- Strict least privilege API permissions  
- Managed Identity where possible  

### **Customer Tenants**
Customer identities belong exclusively to the customer and are never managed by APJ SecureCloud.

Identifiers are never reused after deprovisioning.

---

## **IA-5 – Authenticator Management**

APJ SecureCloud does **not** manage passwords for any user.

Authenticator management is inherited from Microsoft Azure Gov:

- Password policy  
- MFA enforcement  
- Strong authentication requirements  
- Smart Lockout  
- Account recovery mechanisms  

APJ-specific mechanisms:

- Certificate rotation every 180 days for service principals  
- Managed Identities used in lieu of secrets  
- No long-lived secrets or API keys permitted  
- All credentials stored in Azure Key Vault (RBAC-restricted + private endpoint)  

---

## **IA-6 – Authenticator Feedback**

Azure Gov prevents disclosure of authentication failures through:

- Non-specific error messages  
- Smart Lockout and risk-based protections  
- Controlled feedback for MFA and password resets  

APJ SecureCloud UI does not provide user authentication; it reflects only the customer identity already validated by Entra ID.

---

## **IA-7 – Cryptographic Module Authentication**

Authentication relies on FIPS 140-2 validated cryptographic modules used by Azure Gov:

- TLS 1.2+  
- Token signing certificates  
- Key Vault HSM-backed keys (optional)  
- Managed identity tokens signed by Azure  

APJ SecureCloud inherits module-level controls from Microsoft’s FedRAMP authorization.

---

## **IA-8 – Identification & Authentication (Non-Organizational Users)**

APJ SecureCloud **does not create or manage identities for customer users**.

Authentication flow:

1. Customer logs into their own Entra ID tenant.  
2. Customer obtains OAuth2 authorization token.  
3. APJ SecureCloud uses delegated permissions to ingest metadata.  
4. APJ has no access to customer passwords, MFA, or secrets.  

APJ responsibilities:

- Enforce read-only API scopes  
- Never store customer credentials  
- Log all API-based access  
- Provide documentation for securely granting permissions  

Customer responsibilities:

- Manage their own IAM lifecycle  
- Enforce MFA and identity policies in their tenant  
- Grant and revoke API access as appropriate  

---

## **IA-8(1) – Acceptance of PIV Credentials**

Not applicable (FedRAMP Low).  
No PIV integration is required for SaaS access.

If future requirements include PIV/CAC, APJ SecureCloud will support Entra ID Gov integration.

---

## **IA-9 – Service Identification & Authentication**

Internal system-to-system authentication uses:

- Managed Identities (preferred)  
- Certificate-based authentication for pipelines  
- OAuth2 for API ingestion  
- Key Vault for secret storage  

No shared secrets.  
No long-lived API tokens.  
No plaintext credentials stored in code or configuration.

Service identity logs are stored in:

- Azure Activity Logs  
- Key Vault Access Logs  
- App Service Authentication logs  

---

## **IA-10 – Adaptive Authentication (Conditional Access)**

APJ operator accounts must pass Conditional Access, enforcing:

- MFA  
- Device compliance  
- Geolocation rules  
- Risk scoring from Microsoft Identity Protection  
- Prohibition of legacy authentication  

High-risk logins are blocked, logged, and generate Sentinel alerts.

---

## **IA-11 – Reauthentication**

Azure Gov session controls enforce:

- Reauthentication for PIM elevation  
- Token renewal every 1–24 hours depending on session type  
- Reauthentication after Conditional Access risk events  
- Reauthentication for privileged actions  

APJ SecureCloud UI sessions expire:

- After 15 minutes of inactivity  
- After browser close  
- After elevated role expiration  

---

# End of IA Control Family
