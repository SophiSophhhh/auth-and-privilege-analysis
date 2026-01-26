## auth-and-privilege-analysis

## Overview
This project demonstrates the analysis of Linux authentication activity from a SOC analyst perspective. The focus is on identifying suspicious authentication behavior, assessing risk, and determining appropriate response actions based on observed events.

## Scope
- **Log Source:** Linux authentication logs (`auth.log`-style events)
- **Analysis Context:** SSH-based authentication activity
- **Perspective:** SOC analyst performing alert triage

### Focus Areas
- Authentication successes and failures
- Privilege escalation attempts (`sudo`)
- Lateral movement via SSH between internal hosts
- Persistence mechanisms such as SSH key creation and new user accounts

## Skills Demonstrated
- Interpreting Linux authentication logs for security events
- Assessing severity and risk of authentication-related activity
- Identifying indicators of brute force, credential misuse, and privilege escalation
- Making SOC triage decisions (monitor, investigate, escalate)
