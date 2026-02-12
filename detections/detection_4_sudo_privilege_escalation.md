Detection Name: Immediate Privilege Elevation via Sudo Following SSH Login

Detection Concept:
Successful sudo command execution by a non-root user shortly after authentication, where privilege elevation may be inconsistent with normal user behavior.

What Happened:
A successful SSH login to a non-root user account was followed by sudo command execution within a short time window.

Detection Logic:
- A successful SSH authentication event is recorded for user X.
- A sudo command execution event is recorded for the same user X.
- The sudo event occurs within a defined short time window (e.g., 5–10 minutes) following the successful SSH login.
- The account is not designated as a root account.
- Sudo usage is evaluated against the user’s expected role and historical behavior.

Potential False Positives:
- Authorized users with sudo privileges performing legitimate administrative tasks shortly after login.
- Automated scripts, configuration management tools, or scheduled jobs executing sudo commands using approved service or user accounts.
- Incident response or troubleshooting activity requiring immediate privilege elevation.

Risk Level:
- Medium – Authorized sudo usage by a non-root user shortly after login with no additional suspicious behavior
- High – Sudo usage by an unexpected user, execution of high-risk commands, or correlation with other suspicious activity 

Why SOC cares:
Sudo execution shortly after authentication indicates potential post-compromise privilege escalation, granting elevated access that can enable persistence, lateral movement, and broader system compromise if unauthorized.

High-Risk Sudo Commands to Review:
- User management (useradd, usermod, passwd)
- Persistence (crontab, systemctl, modifying /etc/sudoers)
- Network changes (iptables, ufw)
- Credential access (cat /etc/shadow)
- Package installation (apt, yum, dnf)

Additional Context to Review:
- Does the user normally execute sudo commands?
- Is sudo usage consistent with the user’s historical behavior?
- Is the account newly granted sudo privileges?
- Has the account been involved in recent authentication anomalies?

Recommended Actions:
- Validate whether the user is authorized to execute sudo commands and whether the activity aligns with expected job responsibilities.
- Review the specific commands executed with sudo to assess potential impact.
- Correlate authentication and sudo logs to identify additional suspicious activity related to the account.
- Monitor for indicators of persistence, lateral movement, or further privilege escalation.
- Escalate to Incident Response if sudo usage is unauthorized or if malicious post-authentication activity is identified.

