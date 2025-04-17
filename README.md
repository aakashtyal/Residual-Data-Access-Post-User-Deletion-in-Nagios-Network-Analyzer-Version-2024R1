# Residual Data Access Post User Deletion in Nagios Network Analyzer Version 2024R1.0.3

## Overview  
A vulnerability in Nagios Network Analyzer Version 2024R1.0.3 allows deleted users to retain access to system resources due to improper session invalidation and stale token handling. When an administrator deletes a user account, the backend fails to terminate active sessions and revoke associated API tokens, enabling unauthorized access to restricted functionalities.

Attackers can exploit this issue to:

Retrieve sensitive system data via /xxx/xx/sources even after deletion.
Modify user profile details using /xxx/xx/update-profile.
Execute privileged actions such as creating new queries through /xxx/xx/create-query.

This vulnerability results from the absence of proper backend validation of user account status during API request handling and insufficient cleanup of user session metadata upon deletion.

## Severity  
- **Impact:** High  
- **CWE:** CWE-613 (Insufficient Session Expiration)  
- **CVSS Score:** AV:N/AC:L/PR:L/UI:N/S:U/C:H/I:H/A:N  

## Affected Components  
- **User session management**  
- **Token invalidation process**  
- **Backend API authorization checks**

## Affected Vendor/Product
- **Product Name**- Nagios Network Analyzer
- **Affected Version**: 2024R1.0.3
- **Fixed Version**: 2024R2.0.1

## Summary of the Issue  
When an administrator deletes a user, their session remains active, leading to:  
- Access to system data via `/XXX/XX/sources`  
- Privilege abuse, e.g., updating their profile via `/XXX/XX/update-profile`  
- Creation of new queries via `/XXX/XX/create-query`  

## Mitigation Recommendations  
1. Immediately invalidate all sessions and tokens upon account deletion.  
2. Implement server-side validation for user status before processing API requests.  
3. Enforce token revocation policies.  

## Disclosure Timeline  
- **[2024-12-30]**: Vulnerability discovered  
- **[2024-12-30]**: Reported to vendor  
- **[2025-01-04]**: Vendor verified the vulnerability
- **[2025-01-21]**: Vendor patched the vulnerability with a new release
- **[2025-04-17]**: Assign CVE 

---
📌 *This repository is intended solely for vulnerability reporting and CVE reference.*
