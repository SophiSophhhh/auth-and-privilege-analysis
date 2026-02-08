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
Multiple successful SSH authentications to a single user account from different source IPs within a short time window may indicate unauthorized access or credential compromise. If an attacker gains valid credentials, they can maintain access, escalate privileges, or move laterally within the environment. Detecting this behavior helps SOC teams identify potentially compromised accounts early and reduce the impact of further malicious activity.


Recommended Actions:
- Verify whether the affected user account is expected to authenticate from multiple locations or devices.
- Validate the source IP addresses to determine if they are known, authorized, or associated with VPN, proxy, or NAT infrastructure.
- Review authentication history for the user account to identify deviations from normal login behavior.
- Correlate with additional logs to assess post-authentication activity for signs of privilege escalation, persistence, or lateral movement.
- Escalate to Incident Response if the access pattern is determined to be unauthorized or if suspicious post-login activity is identified.

