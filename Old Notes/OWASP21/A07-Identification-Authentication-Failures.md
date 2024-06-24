# A07:2021 – Identification and Authentication Failures
This category covers a wide variety of identification, authentication, and session management problems. This is sort of a catch-all for problems not included in other similar categories. A07 includes issues such as:
 - Permitting brute force and/or credential surfing attacks
 - Allowing weak or well known passwords
 - Having weak or exploitable workflows for forgotten passwords
 - Storing plain text passwords
 - Missing multi-factor authentication

## How to Prevent
 - Use multi-factor authentication
 - Check for weak and known common passwords
 - Change or disable all default credentials like admin/admin or root/postgres
 - Limit or delay authentication attempts to avoid automated attacks, log failures, and detect automated attacks
 - Use the same message for all auth outcomes to harden against giving bad actors any information they can use


Read more at [owasp.org](https://owasp.org/Top10/A07_2021-Identification_and_Authentication_Failures/)