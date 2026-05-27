# Project 2: Automated User Provisioning & Deprovisioning with PowerShell

## Company context
Packo Financial Group is a publicly traded Canadian bank operating across 12 subsidiaries with 45,000 employees. It is regulated under OSFI, PIPEDA, and PCI-DSS. The IAM Access Request Provisioning team supports ~8,000 access requests monthly across RSA Token, Microsoft Entra ID, VPN, and privileged systems.
## Scenario
Packo's internal audit found 112 "ghost accounts".  Active Directory accounts that were still enabled 30+ days after the employee's HR termination date. Three of these accounts had logged in after termination, a potential insider threat indicator. Manually processing the daily HR feed (averaging 45 joiners, 30 movers, 20 leavers per day) took two analysts 3 hours each morning and was error-prone.
