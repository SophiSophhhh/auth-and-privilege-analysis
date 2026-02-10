## Detection Name: Multiple Successful SSH Logins to Single-User Account from Different Source IPs

## Scenario
A single-user SSH account experienced multiple successful authentication events from different source IP addresses within a short time window, suggesting potential credential compromise.

## Analysis
Log review shows three successful SSH logins to the same single-user account from distinct IP addresses within one minute. Given the account is intended for individual use, this pattern is inconsistent with expected behavior and may indicate credential reuse or compromise. The absence of session termination logs prevents confirmation of concurrent sessions. Review of the filtered log output shows multiple successful authentication events for the same single-user account from different source IP addresses within one minute.

## Next Steps / Analyst Actions
- Validate account ownership
- Check MFA status
- Review post-login commands
- Correlate with VPN or identity logs

## Linux Commands Used
- grep "Accepted password for user1" fakelog4.log
- grep "Failed password for user1" fakelog4.log
- grep -c "Failed password for user1" fakelog4.log
