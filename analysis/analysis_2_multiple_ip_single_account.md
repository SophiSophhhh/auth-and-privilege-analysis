## Detection Name : Multiple Failed SSH Logins Followed by Successful Authentication

## Scenario
Multiple failed SSH authentication attempts were observed for account user2 from several external source IP addresses within a short time window. Successful authentication events for the same account were later observed from two source IPs.
## Analysis
Review of SSH authentication logs shows multiple failed login attempts against the account user2 originating from several distinct source IP addresses within a short time window. The failed 
attempts were followed by successful authentication events for the same account.
A successful login was observed from source IP 198.51.100.11, which had previously generated failed authentication attempts. An additional successful login was observed from source IP 
198.51.100.14, which authenticated successfully on its first attempt.
This activity explains why the detection triggered, as it meets the defined criteria of multiple failed authentication attempts from different source IPs followed by successful authentication
to the same account. Based on authentication logs alone, it is not possible to confirm whether the activity was malicious or expected, and additional context is required to determine intent.

## Next Steps / Analyst Actions
- Validate whether source IPs 198.51.100.11 and 198.51.100.14 are known, trusted, or associated with VPN or expected infrastructure.
- Confirm whether user2 is a personal account or a shared/service account to determine expected authentication behavior.
- Review authentication timestamps to assess whether the activity occurred during normal usage hours.
- Monitor subsequent authentication and session activity for repetition of the pattern or additional anomalies.

## Linux Commands Used
- grep "sshd" auth.log
- grep "Failed password" auth.log
- grep "Accepted password" auth.log
- grep "user2" auth.log
- grep "198.51.100.11" auth.log | wc -l
- grep "203.0.113.46" auth.log | wc -l
- grep "Feb  4 14:22" auth.log
