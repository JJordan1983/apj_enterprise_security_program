APJ Enterprise Security Program

A complete, audit-ready federal cloud security portfolio demonstrating FedRAMP, NIST SP 800-53 Rev5, SOC 2, ISO 27001, Zero Trust, and AI governance maturity.

🔹 Executive Summary

APJ Enterprise Security Program is a full-scale demonstration of a modern federal security architecture, built to reflect the capabilities of a seasoned cloud security engineer and GRC consultant.
It includes:

a FedRAMP Low SSP

Azure Government baseline

Microsoft 365 security hardening

comprehensive continuous monitoring

AI governance aligned to the NIST AI RMF

incident response lifecycle

risk and compliance artifacts

complete POA&M workflows

audit-ready documentation and evidence models

This portfolio shows end-to-end control ownership, engineering capability, governance planning, and operational execution.

🔹 Architecture Overview

APJ Enterprise adopts a hybrid Zero Trust architecture across:

Azure Government

Microsoft 365 GCC/GCC-High

Defender XDR + Sentinel

Azure Monitor + Log Analytics

Conditional Access + Identity Governance

FedRAMP-aligned configuration baselines

Data movement, identity boundaries, network zones, and telemetry pipelines are modeled using industry-standard diagrams stored in the Diagrams folder.

🔹 FedRAMP Low Security Program (SSP)

Located in:
Portfolio/SSP_Low

Includes:

system overview and boundary

data flow diagrams

component inventory

security responsibility matrix

full control implementation statements

audit logging, monitoring, and incident response

configuration management program

access control + identity governance

risk assessments

SSP narrative aligned to NIST SP 800-18

This SSP is built in the same structure used by federal ATO packages.

🔹 Continuous Monitoring (ConMon)

Located across:
Portfolio/SSP_Low, Scripts, M365_Security, AzureGov

This program demonstrates:

automated log exports (Sentinel + Defender + Azure)

RBAC drift detection

policy compliance scanning

POA&M ingestion workflows

vulnerability + patch tracking

monthly control evidence collection

audit-ready dashboarding

Scripts used for governance automation are in the Scripts directory.

🔹 Microsoft 365 Security Engineering

Located in:
Portfolio/M365_Security

Includes:

Conditional Access MFA enforcement

Device Compliance baseline

Purview DLP sample rules

Insider Risk baseline

Defender XDR configuration

Sentinel KQL detection pack

audit log retention guidance

Zero Trust identity segmentation

This is a practical, real-world enterprise M365 hardening standard.

🔹 Azure Government Landing Zone

Located in:
Portfolio/AzureGov

Includes:

subscription baseline

RBAC + role scoping standards

secure networking patterns

Azure Policy baseline

Key Vault, Storage, and resource security

logging, diagnostic settings, and SIEM integration

This folder models how to deploy a federal-ready Azure Gov environment.

🔹 POA&M (Plan of Action & Milestones)

Located in:
Portfolio/POAM

Includes:

a FedRAMP-style CSV

realistic weaknesses

remediation milestones

accountable roles

severity + risk scores

status and completion tracking

This demonstrates an understanding of federal remediation management.

🔹 AI Governance – NIST AI RMF

Located in:
Compliance/AI_Impact_Assessment.md

Includes:

AI use case inventory

bias, harm, and transparency evaluation

model risk scoring

human-in-the-loop policies

logging and monitoring requirements

alignment to NIST AI RMF (Govern, Map, Measure, Manage)

This is an advanced element rarely included in public security portfolios.

🔹 Evidence & Audit Artifacts

Located in:
Evidence/

Includes example evidence for:

access reviews

configuration baselines

vulnerability scans

audit log exports

monthly monitoring summaries

IR findings

This folder shows practical audit preparation and evidence management.

🔹 Diagrams

Located in:
Portfolio/Diagrams

Includes:

RBAC model

network boundary diagram

data flow diagram

security monitoring pipeline

component architecture

Each diagram represents an enterprise-ready reference architecture.

🔹 Scripts & Automation

Located in:
Scripts/

Included scripts:

Azure-RBAC-Audit.ps1 — role drift detection

Export-ConMonMetrics.ps1 — compliance export

Sentinel-Detection-Pack.kql — KQL analytics rules

upcoming: Defender evidence packaging scripts

Automation shows maturity beyond documentation alone.

🔹 Repository Navigation Guide

Portfolio/ – program artifacts
Portfolio/SSP_Low – FedRAMP Low SSP
Portfolio/POAM – POA&M
Portfolio/AzureGov – Azure Gov baseline
Portfolio/M365_Security – Microsoft 365 hardening
Portfolio/Diagrams – architecture diagrams
Compliance/ – SOC2, ISO27001, AI governance
Scripts/ – automation
Evidence/ – real-world audit samples

If you are evaluating this repository for hiring, subcontracting, or consulting opportunities, begin with the SSP_Low folder for governance and Scripts folder for automation depth.

🔹 Author

Jeanette Jordan
Cloud Security Engineer | GRC Consultant | FedRAMP & NIST Practitioner
APJ Enterprise LLC

🔹 License

This project is released for professional demonstration and educational use.
