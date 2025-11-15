# System and Communications Protection Policy  
APJ SecureCloud  
Version 1.0

## 1. Purpose
Defines encryption, communication protection, and boundary defense requirements.

## 2. Encryption
- TLS 1.2+ mandatory  
- Encryption at rest enabled  
- Key Vault required for secrets  

## 3. Communications Protection
- Private endpoints where supported  
- No public exposure of administrative interfaces  
- Network filtering inherited from Azure Gov  

## 4. Key Management
- Keys rotated annually  
- Access restricted via RBAC + CA

## 5. Approval
Approved by APJ Security Program Lead.
