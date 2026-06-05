#  Project 1: Entra ID Conditional Access Hardening Lab

## 1. Overview
This project simulates Packo Financial’s contractor identity environment and implements a hardened Conditional Access (CA) architecture to address a CAP‑1 audit finding. The lab demonstrates how to enforce MFA, block legacy authentication, restrict privileged access by location, and require compliant devices for regulated applications — all using Entra ID Free capabilities.

## 2. Business Problem
A security audit found that 340 contractor accounts had:
- No MFA enforcement  
- No device trust  
- No location restrictions  
- Legacy authentication still enabled  

This violated:
- OSFI B‑10 (third‑party risk)  
- PCI‑DSS 8.4 (MFA for all non‑consumer access)  
- PIPEDA (regulated financial data protection)  

A compromised contractor password could grant full SaaS access with no controls.

## 3. Objectives
- Enforce MFA for all contractor identities  
- Block legacy authentication globally  
- Require compliant devices for Finance applications  
- Restrict privileged admin roles to corporate IP ranges  
- Reduce regulatory exposure and authentication attack surface  

## 4. Conditional Access Policies Implemented

| Policy | Purpose | Security Principle |
|--------|---------|--------------------|
| Require MFA for Contractors | Contractors = highest risk | Defense‑in‑depth |
| Block Legacy Authentication | Legacy protocols bypass MFA | Attack surface reduction |
| Require Compliant Device for Finance Apps | Finance data is regulated | Device‑based least privilege |
| Admin Location Restriction | Admins should only log in from corporate IPs | Least exposure |

## 5. Architecture Diagram
```mermaid
flowchart LR
    Contractor[Contractor User] --> Login[Login Request]
    Login --> CA[Conditional Access Engine]

    CA -->|Password Only| BlockLegacy[Block Legacy Auth]
    CA -->|Unmanaged Device| BlockDevice[Block Finance App Access]
    CA -->|Foreign IP| BlockLocation[Block Admin Access]
    CA -->|Standard Login| MFA[Require MFA]

    MFA --> Allow[Access Granted]
