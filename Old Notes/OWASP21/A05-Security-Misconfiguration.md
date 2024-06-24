# A05:2021 – Security Misconfiguration
Not to be confused with A04 and A02, A05 is misconfiguration. A04 is about approaching the design of your application in a secure way, and A02 is about using up-to-date cryptographic tools. A05 occurs when we engage in bad practices, when we are careless, or when we lack expertise. Some examples include:
 - Unnecessary features are enabled, like spring boot actuator endpoints
 - Default credentials still active and unchanged
 - Stack traces are exposed to users
 - Improperly configured permissions

## How to Prevent
 - Remove, disable, or uninstall unnecessary features, libraries, and frameworks
 - Vet and frequently review configurations and permissions, especially when updating
 - Have automated processes to verify the effectiveness of configurations and settings (automated testing)

Read more at [owasp.org](https://owasp.org/Top10/A05_2021-Security_Misconfiguration/)