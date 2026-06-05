# Conditional Access Hardening – Deployment Guide

## 1. Overview
This guide provides step-by-step instructions for deploying four Conditional Access (CA) policies that harden contractor and privileged access in Microsoft Entra ID. These controls enforce MFA, block legacy authentication, restrict admin access by location, and require compliant devices for regulated applications.

---

## 2. Prerequisites
- Entra ID tenant (Free or higher)
- Global Administrator or Conditional Access Administrator role
- Defined groups:
  - Contractors
  - Finance-App-Users
  - Privileged-Admins
- Known corporate IP ranges (for admin location restriction)
- Finance application registered in Entra ID

---

## 3. Policy 1 — Require MFA for Contractors
### Steps
1. Go to **Entra ID → Security → Conditional Access → New Policy**  
2. Name: `CA - Require MFA for Contractors`
3. Assignments:
   - Users → Include → *Contractors group*
4. Cloud apps: All cloud apps
5. Grant:
   - Require MFA
6. Enable policy

---

## 4. Policy 2 — Block Legacy Authentication
### Steps
1. Create new policy: `CA - Block Legacy Authentication`
2. Assignments:
   - Client apps → Select:
     - Exchange ActiveSync
     - Other clients (legacy protocols)
3. Grant:
   - Block access
4. Enable policy

---

## 5. Policy 3 — Require Compliant Device for Finance Apps
### Steps
1. Create new policy: `CA - Require Compliant Device for Finance Apps`
2. Assignments:
   - Cloud apps → Include → Finance application
3. Conditions:
   - Device state → Require compliant device
4. Grant:
   - Require device to be marked as compliant
5. Enable policy

---

## 6. Policy 4 — Restrict Admin Roles to Trusted Locations
### Steps
1. Create new policy: `CA - Admins Trusted Locations`
2. Assignments:
   - Users → Include → Directory roles:
     - Global Administrator
     - Privileged Role Administrator
3. Conditions:
   - Locations:
     - Include → *Trusted Locations*
     - Exclude → *All locations*
4. Grant:
   - Block access (if not from trusted location)
5. Enable policy

---

## 7. Validation
- Test contractor login from unmanaged device
- Test legacy auth (IMAP/SMTP) → should be blocked
- Test Finance app access from personal laptop → blocked
- Test admin login from foreign IP → blocked
- Review sign-in logs and CA insights

---

## 8. Rollback Plan
- Disable policies individually if misconfiguration occurs
- Maintain break-glass account excluded from all CA policies

