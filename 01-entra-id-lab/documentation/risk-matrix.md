# Conditional Access Hardening – Risk Matrix

## 1. Overview
This matrix compares authentication risks before and after implementing Conditional Access controls.

---

## 2. Risk Matrix

| Risk Scenario | Before Hardening | After Hardening | Residual Risk |
|---------------|------------------|------------------|----------------|
| Contractor password compromised | High – full SaaS access | Low – MFA + device trust | Low |
| Legacy auth password spray | Critical – MFA bypass | Eliminated | None |
| Admin login from foreign IP | High | Blocked | Very Low |
| Finance data accessed from personal laptop | High | Low – compliant device required | Low |
| Regulatory exposure (OSFI, PCI-DSS) | High | Low | Low |

---

## 3. Key Observations
- Legacy authentication was the single largest risk vector.
- Privileged accounts had excessive exposure due to unrestricted locations.
- Device trust significantly reduces data leakage risk for regulated workloads.

---

## 4. Recommendations
- Add Identity Protection risk-based policies
- Implement PIM for JIT admin access
- Expand device compliance to all high-risk users
