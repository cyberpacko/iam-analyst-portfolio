# Project 1: Entra ID Conditional Access Hardening Lab


## 1\. The Real Problem

Meridian's security audit found that 340 contractor accounts had no Conditional Access policies enforced — meaning a contractor working from an unmanaged device in a foreign country could authenticate with just a password. This directly violated OSFI's B-10 guideline on third-party risk and PCI-DSS Requirement 8.4 (MFA for all non-consumer access).

## 2\. What Was Built (The Lab Environment)

## 3\. Architecture Overview 

  ┌─────────────────────────────────────────────────────────────────┐
│              Microsoft Entra ID — Meridian Financial Group       │
│                                                                   │
│  ┌───────────────────────────────────────────────────────────┐   │
│  │              Conditional Access Engine                     │   │
│  │                                                             │   │
│  │  CA-01: Require MFA — All Contractors        [B-10, B-13] │   │
│  │  CA-02: Block Legacy Authentication — All    [B-13, PCI]  │   │
│  │  CA-03: Compliant Device — Finance/CDE Apps  [PCI v4.0]   │   │
│  │  CA-04: Location Restriction — Admin Roles   [B-13 s3.2]  │   │
│  └──────────────────────┬────────────────────────────────────┘   │
│                          │ Evaluated on every sign-in token       │
│         ┌────────────────┼────────────────────┐                   │
│         ▼                ▼                    ▼                   │
│  ┌────────────┐  ┌──────────────┐  ┌──────────────────┐         │
│  │Contractor  │  │Finance /     │  │Global Admin /    │         │
│  │Group       │  │CDE App Users │  │Privileged Role   │         │
│  │(340 accts) │  │              │  │Admin accounts    │         │
│  └────────────┘  └──────────────┘  └──────────────────┘         │
│                                                                   │
│  Named Locations (OSFI B-13 — corporate perimeter definition):   │
│  ┌──────────────────────────────────────────────────────────┐    │
│  │  Toronto HQ:   203.0.113.0/24                            │    │
│  │  Montreal:     198.51.100.0/24                           │    │
│  │  Vancouver:    192.0.2.0/24                              │    │
│  │  Calgary:      192.0.3.0/24                              │    │
│  └──────────────────────────────────────────────────────────┘    │
│                                                                   │
│  Break-Glass Accounts (excluded ALL CA — OSFI BCP requirement):  │
│  BG-ADMIN-01@meridian.onmicrosoft.com  ← Physical safe, Toronto  │
│  BG-ADMIN-02@meridian.onmicrosoft.com  ← Physical safe, Montreal │
└─────────────────────────────────────────────────────────────────┘

