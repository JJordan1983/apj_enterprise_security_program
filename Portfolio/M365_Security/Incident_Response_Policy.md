# Incident Response Policy  
APJ SecureCloud – Azure Government Zero Trust  
Version 1.0

## 1. Purpose
This policy defines APJ SecureCloud’s requirements for detecting, reporting,
assessing, responding to, and recovering from security incidents affecting the
SaaS boundary hosted in Azure Government IL2.

## 2. Scope
Applies to:
- APJ employees
- Azure Gov resources supporting the SaaS
- Sentinel, Log Analytics, Activity Logs, PIM logs, and CA logs
- CI/CD pipeline security events
- Third-party vendors supporting security functions

Azure Gov underlying infrastructure IR is inherited from Microsoft’s FedRAMP P-ATO.

## 3. Definitions
- **Security Incident:** Unauthorized access, configuration tampering, anomalous activity, or system misuse.
- **Event:** Logged activity requiring analysis.
- **Major Incident:** Any event with potential customer impact or boundary compromise.

## 4. Detection Requirements
Detection tools include:
- Microsoft Sentinel analytic rules (UEBA + identity + access anomalies)
- Azure AD Identity Protection
- Defender for Cloud
- Activity Logs
- App Service diagnostic logs
- DevOps pipeline scanning failures

APJ must monitor these daily.

## 5. Reporting
Incidents must be:
- Reported within **1 hour**
- Recorded in the Incident Log
- Escalated if the incident indicates compromise

## 6. Response Workflow
1. Detect  
2. Validate  
3. Classify  
4. Contain  
5. Eradicate  
6. Recover  
7. Root Cause Analysis  
8. POA&M entry if required  

Workflow stored at:  
`Portfolio/Incident_Response/IR_Workflow.png`

## 7. Roles
- **IR Lead:** Coordinates all response & communication.
- **Security Engineer:** Performs triage and containment.
- **DevOps Lead:** Assists with code- or pipeline-related incidents.
- **Executive Contact:** Approves customer or agency notifications.

## 8. Evidence Retention
IR artifacts stored at:  
`Portfolio/Incident_Response/`

## 9. Training
All personnel must complete annual IR training and tabletop participation.

## 10. Annual Tabletop Exercise
APJ must conduct one tabletop exercise per year and store results under:  
`Portfolio/Incident_Response/Tabletop_Results_2025.pdf`

## 11. Continuous Improvement
All major incidents require RCA and policy updates.

## 12. Approval
Approved by APJ Security Program Lead.
