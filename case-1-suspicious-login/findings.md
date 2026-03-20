# Case 1: Suspicious Login Investigation

## Executive Summary
Multiple failed login attempts were observed on a non-administrative account, followed by a successful login. Shortly after, an administrative account logged in, triggering Event ID 4672 (privileged access).

## Tools Used
- Windows Event Viewer
- PowerShell
- EVXT logs exported from lab vm

## Timeline of Events
| Time        | Event ID | User         | Result     | Logon Type | Notes                    |
|-------------|----------|--------------|------------|------------|--------------------------|
| 9:13:30 AM  | 4625     | hacker123    | Failure    | 2          | Multiple failed attempts |
| 10:00:10 AM | 4624     | hacker123    | Success    | 2          | Suspicious login         |
| 10:01:53 AM | 4624     | Win10-Victim | Success    | 2          | Admin login              |
| 10:01:53 AM | 4672     | Win10-Victim | Privileged | 2          | Elevated Privileges      |


## Findings
- Brute-force-like pattern observed on hacker123 account
- Administrative access detected after suspicious login activity
- No lateral movement or other anomalies observed in this session

## Recommendations
- Enable account lockout policies after multiple failed attempts
- Implement strong passwords and two-factor authentication
- Monitor administrative logins closely for anomalies
