## Detection Name:
Successful SSH Login Following Multiple Failed Attempts from Multiple Source IPs

## Description:
This detection identifies authentication activity where multiple failed SSH login attempts against a single user account originate from different source IP addresses and are followed by a successful authentication. This pattern may indicate credential compromise or unauthorized credential reuse and requires further investigation.

## Detection Logic:
- ≥ 5 failed SSH authentication attempts
- Originating from multiple distinct source IP addresses
- Targeting the same user account
- Followed by a successful SSH authentication to the same account from a source IP that previously generated failed authentication attempts
- All activity occurring within a 10-minute time window

## Potential False Positives:
- Automated scripts or services using a shared account across multiple hosts.
- Users connecting via rotating VPN endpoints or NAT devices, causing multiple IPs to appear.
- Shared service accounts legitimately accessed by multiple users or systems.
- Recent password rotations causing failed login attempts from multiple IPs.

## What Happened:
Multiple failed SSH authentication attempts were observed against a single user account from several source IP addresses. A successful authentication then occurred from a source IP that had previously generated multiple failed attempts, indicating potential credential guessing or compromise.

## Risk Level:
Medium–High — successful authentication following failed attempts from multiple source IPs may indicate credential compromise.

## Why SOC Cares:
This behavior may indicate unauthorized credential reuse or credential guessing against a single account. Early detection enables SOC teams to validate IP legitimacy, assess account exposure, and reduce the risk of account compromise or downstream activity such as lateral movement.

## Additional Context to Review
- Are the source IPs internal, external, or VPN-assigned?
- Are the IPs associated with known infrastructure or automation?
- Is the account a shared or service account?
- Does this user normally authenticate from multiple locations?

Recommended Actions:
- Validate whether the source IP addresses are known and expected for the user account.
- Correlate authentication logs to identify abnormal login patterns or repeated access attempts from multiple source IPs.
- Monitor for any successful authentication events and subsequent post-login activity, including privilege escalation or persistence mechanisms.


