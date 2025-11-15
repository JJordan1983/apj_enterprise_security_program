# Audit Logging and Monitoring Policy  
APJ SecureCloud – Azure Government  
Version 1.0

## 1. Purpose
Defines requirements for collection, storage, protection, review, and analysis
of audit logs related to APJ SecureCloud’s SaaS-layer system activity.

## 2. Scope
Covers:
- Azure AD sign-in logs
- PIM logs
- Conditional Access logs
- Activity Logs
- Sentinel analytics
- App Service logs
- Log Analytics workspace
- CI/CD pipeline logs

## 3. Logging Requirements
APJ must log:
- Authentication events
- Authorization events
- Administrative actions
- Security alerts
- Resource changes
- Key Vault access
- App Service runtime errors
- CI/CD pipeline failures

Azure Gov infrastructure logging is inherited.

## 4. Log Storage & Retention
- Logs aggregated into Log Analytics + Sentinel
- Retention: **90 days online**, **1 year archival**
- Only authorized personnel may access logs

## 5. Protection of Logs
- Logs are immutable
- Access controlled with RBAC
- Reviewed quarterly

## 6. Monitoring
Sentinel analytic rules detect:
- Suspicious sign-ins
- PIM elevation anomalies
- API abuse
- Key Vault misuse
- Configuration tampering

## 7. Log Review
Daily:
- Identity Protection  
Weekly:
- Sentinel Incidents  
Quarterly:
- Full audit review  

Evidence stored under:  
`Portfolio/Dashboards/SIEM/`

## 8. Approval
Approved by APJ Security Program Lead.
