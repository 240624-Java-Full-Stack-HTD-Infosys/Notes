# A02:2021 – Cryptographic Failures
Previously called "sensitive data exposure" this item includes failed cryptographic implementations or lack thereof. Some security vulnerabilities which are considered cryptographics failures include:
 - Use of hard-coded passwords
 - Broken or risky cryptography algorithms
 - Insufficent entropy (not random enough)

Examples: 
 - HTTP, SMTP, FTP protocols transmitting data unencrypted
 - Using old/weak cryptographic algorithms (including in transitive and direct dependencies) such as MD5, SHA1, PKCS v1.0 & v1.5
 - Exposing passwords or keys in code repositories
 - Use of randomness or psuedo-randomness which is insufficent for cryptographic purposes

## How to Prevent
- Classify data, and identify sensitive data
- Don't store sensitive data unless necessary
- Encrypt sensitive data at rest as well as during transit
- Implement up-to-date standards, practices, keys, protocols, and algorithms
- Disable caching of sensitive data
- Ensure that randomness sufficent for cryptography is used, and has not been seeded in a predictable way
- Avoid deprecated cryptographic functions like MD5, SHA1, PKCS v1.0 & v1.5


Read more at [owasp.org](https://owasp.org/Top10/A02_2021-Cryptographic_Failures/)