Supply_Chain_Risk_Management_Policy

APJ SecureCloud
Version 1.0

1. Purpose

This policy explains how APJ SecureCloud manages the risks that come from third-party services, software, cloud providers, and open-source components. The goal is simple: keep the environment trustworthy and avoid surprises. Supply chain failures hit fast, so this policy makes sure we stay ahead of them.

2. Scope

This policy applies to:

All software, libraries, and dependencies used in the APJ SecureCloud SaaS platform

Azure Government IL2 services

Third-party APIs or integrations

CI/CD pipelines and DevOps tools

Any vendor or contractor supporting APJ

Any component that could affect security, integrity, or availability

Infrastructure supply chain responsibilities—hardware, hosting, firmware, networking, datacenter operations—are inherited from Microsoft Azure Government’s FedRAMP authorization.

3. Principles

APJ follows a traditional but proven approach:

Only use vendors you can verify

Never trust a dependency without scanning it

Monitor constantly

Document everything

Cut off anything that stops meeting security expectations

4. Roles and Responsibilities
Security Program Lead

Owns this policy

Reviews vendor risks quarterly

Approves new technology before adoption

DevSecOps Lead

Manages dependency scanning

Tracks SBOM-related data

Keeps CI/CD protections in place

Compliance Manager

Ensures suppliers meet FedRAMP Low expectations

Keeps documentation current for audits

Vendors

Must notify APJ of major changes or security issues

Must remain reputable and supported

5. Azure Government Inherited Controls

APJ relies on Microsoft Azure Government for:

Hardware lifecycle security

Datacenter protections

Hypervisor integrity

Firmware and supply-chain protections

Vendor vetting

FedRAMP documentation and assurance

APJ must review Azure Gov FedRAMP packages at least annually.

6. SaaS-Layer Supply Chain Requirements

APJ manages what it controls:

App code

Dependencies

Pipelines

Keys and secrets

Admin access

Log and telemetry pipelines

Supply chain actions APJ performs:

Dependency Scanning – every build

Container / App Vulnerability Review – monthly

SBOM maintenance (optional but recommended)

Monitoring Microsoft advisories

Tracking CISA KEV (Known Exploited Vulnerabilities)

Reviewing vendor SOC2 / FedRAMP materials when available

7. Approved and Forbidden Components
Approved

FedRAMP-authorized Azure Gov services

Reputable open-source libraries with ongoing support

Tools with active patch cycles

Forbidden

Abandoned or unmaintained libraries

Unsupported software

Any product failing vulnerability scanning

Products with unclear licensing

8. Vendor Evaluation Process

A vendor or tool must pass:

Security review

Functionality review

Licensing review

Risk scoring

Executive approval for high-impact tools

Evidence is stored under:

Portfolio/Supply_Chain/Vendor_Reviews/

9. Continuous Monitoring

APJ uses:

GitHub Dependabot or Azure DevOps scanning

Defender for DevOps

Sentinel alerts for suspicious API behavior

Monthly dependency checks

Quarterly vendor risk review

If a vendor or library becomes high-risk:

Replace it

Patch it

Add a POA&M item

Update risk register

10. Weaknesses & POA&M Tracking

Supply chain weaknesses must be tracked in:

Portfolio/POAM/POAM.xlsx


And evaluated monthly.

11. Response to Supply-Chain Compromise

If a library or vendor introduces risk:

Block the component

Patch or rollback

Scan for impact

Add IR ticket if compromise is suspected

Notify leadership

Document in POA&M

No exceptions.

12. Annual Review

This policy must be reviewed at least once per year or after:

A major vendor breach

A supply chain-related incident

A new architectural change

13. Approval

Approved by the APJ SecureCloud Security Program Lead.
Effective until replaced.
