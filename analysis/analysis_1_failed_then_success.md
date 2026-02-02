# Detection: Multiple Failed SSH Logins Followed by Success

## Scenario
5 failed login attempts for user1 from IP 198.51.100.23, followed by a successful login within 4 minutes.

## Analysis
Analysis of SSH authentication logs identified five failed login attempts followed by a successful authentication for user1 from the same source IP within four minutes, meeting detection criteria. This pattern may indicate brute force or credential misuse. Endpoint activity and intent are unknown. Recommended next steps include validating whether the source IP is authorized, reviewing login timing for anomalies, correlating with historical authentication patterns, and monitoring for repeated activity.


## Linux Commands Used
- grep "Failed password" fakelog | grep "user1"
- grep "Accepted password" fakelog | grep "user1"
- grep "user1" fakelog | grep "Failed" | grep -c 198.51.100.23
