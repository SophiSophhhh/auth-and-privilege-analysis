# Detection: Multiple Failed SSH Logins Followed by Success

## Scenario
5 failed login attempts for user1 from IP 198.51.100.23, followed by a successful login within 4 minutes.

## Analysis
An alert fired because user1 experienced multiple failed logins followed by a success from the same IP in 4 minutes, meeting detection criteria. This pattern may indicate brute force or credential misuse. Endpoint activity and intent are unknown. 
Recommended next steps: verify if IP is authorized, check login time, correlate with historical patterns, and monitor for repeated activity.

## Linux Commands Used
- grep "Failed password" fakelog | grep "user1"
- grep "Accepted password" fakelog | grep "user1"
- grep "user1" fakelog | grep "Failed" | grep -c 198.51.100.23
