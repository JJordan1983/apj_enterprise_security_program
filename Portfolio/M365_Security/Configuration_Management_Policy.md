# Configuration Management Policy  
APJ SecureCloud  
Version 1.0

## 1. Purpose
Establishes how APJ manages secure configurations, baselines, changes, and
infrastructure-as-code for the SaaS boundary.

## 2. Scope
Covers:
- App Service configurations
- Key Vault configuration
- API management
- Terraform/Bicep templates
- Sentinel configuration
- CI/CD pipelines
- Conditional Access and PIM
- Logging architecture

Azure Gov host configuration is inherited.

## 3. Baselines
APJ maintains baselines for:
- App Service settings
- Key Vault access policies
- Sentinel analytic rule set
- Conditional Access policies
- RBAC assignments
- CI/CD pipelines
- Storage accounts
- Log Analytics workspace settings

Stored at:
`Portfolio/DevSecOps/Config_Baselines/`

## 4. Change Control
Changes must:
- Be reviewed via pull request
- Include justification
- Pass CI/CD security scanning
- Log deployment operations in Activity Logs

High-risk changes require approval.

## 5. Configuration Enforcement
- Policy-as-Code implemented for drift detection
- Key Vault secrets auto-rotate
- Zero Trust enforced through CA rules
- All changes recorded for audit

## 6. Approval
Approved by APJ Security Program Lead.
