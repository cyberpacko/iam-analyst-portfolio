# Conditional Access Hardening – Regulatory Mapping

## 1. Overview
This document maps each Conditional Access control to relevant regulatory and industry security requirements.

---

## 2. OSFI B-10 (Third-Party Risk)
| Control | Requirement | Alignment |
|---------|-------------|-----------|
| MFA for Contractors | Third-party authentication assurance | Fully aligned |
| Block Legacy Auth | Reduce exposure to credential attacks | Fully aligned |
| Device Compliance for Finance Apps | Protect sensitive financial data | Strong alignment |

---

## 3. PCI-DSS Requirement 8.4
| Control | Requirement | Alignment |
|---------|-------------|-----------|
| MFA for Contractors | MFA for all non-consumer access | Fully aligned |
| Admin Location Restriction | Strengthen privileged access | Strong alignment |

---

## 4. PIPEDA (Financial Data Protection)
| Control | Requirement | Alignment |
|---------|-------------|-----------|
| Device Compliance | Prevent unauthorized access to regulated data | Fully aligned |
| Legacy Auth Block | Prevent insecure authentication | Strong alignment |

---

## 5. Zero Trust Principles
| Principle | Control | Alignment |
|-----------|---------|-----------|
| Verify explicitly | MFA, device trust | Full |
| Use least privilege | Admin location restriction | Full |
| Assume breach | Block legacy auth | Full |
