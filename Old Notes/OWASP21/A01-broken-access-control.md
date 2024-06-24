# [A01:2021 – Broken Access Control](https://owasp.org/Top10/A01_2021-Broken_Access_Control/)
Broken Access Control refers to situations where users have access to view, create, modify, and/or destroy sensitive information which falls outside that user's normal access limits. This may be caused by simple mistakes like a user having the wrong role, or may be caused by users attempting to bypass security. 

Examples:
 - A user modifies the URL, say by changing an id to a different value, allowing them to view some resource they are normally not authorized for
 - A user has more access than would be required for the tasks they are meant to accomplish
 - An API has not been configured to disallow unauthenticated users from accessing one or more endpoints
 - A user tampers with or forges a JWT, cookie, or hidden field in order to elevate their privilages

## How to Prevent
 - Deny access to non-public resources by default
 - Implement access control mechanisms which are standardized throughout application
 - Access control for models (entities) should be based on record ownership rather than role
 - Rate limiting to minimize automated attacks
 - Follow oAuth 2.0 standards for tokens

Read more at [owasp.org](https://owasp.org/Top10/A01_2021-Broken_Access_Control/)
