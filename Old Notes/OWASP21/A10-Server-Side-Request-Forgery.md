# A10:2021 – Server-Side Request Forgery (SSRF)
SSRF occurs when fetching a remote resource without validating user-supplied URLs. This allows attackers to coerce the application into sending crafted requests in an unexpected way. For instance, you make requests to a gateway server which can access resources in a network that the client doesn't have direct access to. The attacker changes the parameters of the request to trick the server into acting in a way it normally doesn't, such as making requests on the wrong ports. The attacker can watch for responses with error info, or time the responses to learn about the network they don't have access to.

## How to Prevent
 - Deny traffic by default, allowing only essential traffic to be responded to
 - Sanitize and validate user input
 - Do not send raw responses to clients
 - Disable HTTP Redirects

OWASP advises security teams to not mimigate these attacks with a [denylist](https://encyclopedia.kaspersky.com/glossary/blacklist/#:~:text=Denylist%20(sometimes%20referred%20as%20blocklist,email%20addresses%20for%20sending%20adware.), which is not an effective strategy anymore.

Read more at [owasp.org](https://owasp.org/Top10/A10_2021-Server-Side_Request_Forgery_%28SSRF%29/)