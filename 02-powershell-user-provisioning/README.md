# Project 2: Automated User Provisioning & Deprovisioning with PowerShell

## Company context
Packo Financial Group is a publicly traded Canadian bank operating across 12 subsidiaries with 45,000 employees. It is regulated under OSFI, PIPEDA, and PCI-DSS. The IAM Access Request Provisioning team supports ~8,000 access requests monthly across RSA Token, Microsoft Entra ID, VPN, and privileged systems.
## Scenario
Packo's internal audit found 112 "ghost accounts".  Active Directory accounts that were still enabled 30+ days after the employee's HR termination date. Three of these accounts had logged in after termination, a potential insider threat indicator. Manually processing the daily HR feed (averaging 45 joiners, 30 movers, 20 leavers per day) took two analysts 3 hours each morning and was error-prone.

## Solution

## What Was Built

- A PowerShell automation pipeline that:

- Pulls the daily HR delta feed (CSV export from the HR system)

- Compares it against Active Directory using Get-ADUser

- Creates, updates, or disables accounts based on HR status

- Assigns group memberships from a role-to-group mapping table

- Writes a signed, timestamped audit log to a write-once network share

## Business Value Added

- Reduces leaver processing time from same-day manual to within 15 minutes of HR system update — critical for high-risk departures (terminated-for-cause employees)

- Eliminates ghost account risk — each ghost account is a potential persistent threat actor foothold

- Frees 6 analyst-hours per day (1,560 hours/year) for higher-value IAM work

- Audit log satisfies OSFI and internal audit evidence requirements for access lifecycle controls

## Security Best Practices Applied

- Principle of least privilege on the script itself: The service account running the script has only the AD permissions required (Create User, Modify User, Disable Account) — not Domain Admin. This limits damage if the service account is ever compromised

-  Write-once audit log: Logs are written to a WORM (Write Once Read Many) network share. Attackers who compromise the provisioning system cannot erase their tracks

-  Leavers are disabled, not deleted: Accounts are disabled and moved to a quarantine OU for 90 days before deletion. This preserves forensic evidence if a leaver dispute or investigation arises

-  Four-eyes on privileged leavers: Accounts with admin roles trigger a ServiceNow approval to the IAM Team Lead before disablement, preventing accidental lockout of key personnel

