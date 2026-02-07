Detection Name:
Multiple Successful SSH Logins from Different Source IPs to the Same User Account

What Happened:
Multiple successful SSH authentication events were observed for the same user account originating from different source IP addresses within a short time window. The timing of the logins suggests potential overlapping access to the account, which is unusual for a single user account and warrants further investigation.

Detection Logic:
- Successful SSH authentication events
- Targeting the same user account
- Originating from two or more distinct source IP addresses
- Occurring within a defined time window (e.g., 10 minutes)

Potential False Positives:
- VPN or NAT usage causing legitimate source IP changes
- Users accessing the same account from multiple approved devices or host
- Proxy or jump host routing differences making the same user appear to log in from different IPs

Risk Level:
Medium – multiple successful logins from different source IPs targeting the same user account may indicate potential unauthorized access; however, no malicious post-login activity has been observed.

Why SOC Cares
Multiple successful SSH authentications from different source IPs to the same user account could indicate credential compromise and may enable privilege escalation, persistence, or lateral movement within the environment.

Recommended Actions:
- Validate whether the affected user account is a shared or service account and confirm that concurrent access is expected.
- Verify whether the source IP addresses are authorized, recognized, and consistent with normal user behavior.
- Correlate authentication logs to identify repeated access patterns or abnormal login behavior involving the same account.
- Monitor post-login activity for indicators of privilege escalation, persistence, or lateral movement.
  Escalate to Incident Response if the account is non-shared and the access pattern is determined to be unauthorized.

