## Detection Name
Sudo Execution by Non-Root User Shortly After Authentication

## Scenario
A successful SSH login was observed for user analyst1 from source IP 203.0.113.50. Within approximately two minutes of authentication, the same user executed multiple sudo commands:
- /usr/bin/id
- /bin/cat /etc/shadow
- /usr/bin/useradd backupadmin
- The activity occurred in a short, continuous sequence following authentication.

## Analysis
The short time interval between authentication and privileged command execution suggests intentional post-login administrative activity. While immediate sudo usage can be legitimate for authorized administrators, the specific commands executed significantly elevate risk.
The command id likely served to confirm effective privileges and group membership after login.
The command cat /etc/shadow accessed the system file containing password hashes for all local user accounts. Exposure of password hashes introduces the risk of offline password cracking. If successful, cracked credentials could enable unauthorized access to additional accounts, privilege escalation, or reuse of credentials across other systems.
The command useradd backupadmin created a new local user account. Creation of new identity objects increases attack surface and introduces potential persistence risk if the account is unauthorized or undocumented.
Based solely on log data, it cannot be confirmed whether:
- The activity aligns with the user’s job responsibilities
- The commands were part of an approved change
- Password hashes were exfiltrated
- The newly created account was granted elevated privileges
- While sudo usage alone is not inherently malicious, the combination of credential access and new account creation shortly after login warrants validation.

## Next Steps / Analyst Actions
- Validate whether analyst1 is authorized to perform administrative tasks on this system.
- Confirm whether the activity corresponds to an approved change request or ticket.
- Review historical sudo usage for analyst1 to determine whether this behavior is consistent with past activity.
- Verify whether the backupadmin account is documented and required.
- Inspect /etc/sudoers and group memberships to determine if the new account was granted elevated privileges.
- Review network logs to assess whether /etc/shadow contents were potentially exfiltrated.
- Escalate to Incident Response if activity is unauthorized or inconsistent with expected behavior.
