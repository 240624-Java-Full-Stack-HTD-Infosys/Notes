# A09:2021 – Security Logging and Monitoring Failures
Without proper monitoring, security breeches may take longer to detect, if they are detected at all. This category may be underrepresent how common these issues are, as these issues lead to a lack of evidence and detection. It is critically important to be aware of the security situation at all times, and maintain a record for detection, and forensic purposes. Events that should be closely monitored include: 
 - Authentication, especially failed attempts
 - High-value transactions
 - API activity, specifically any activity which seems out of the ordinary or suspicious

A common security practice to do is preform penetration testing, where someone tries to find weaknesses in security in order to fix them. If your monitoring and alerting tools don't detect penetration testing as it occurs, these tools might not help when real attacks occur.

## How to Prevent
 - Ensure validation and authentication failures are logged with enough context to identify suispicious activity, and are kept long enough for later forensic analysis
 - Logs should be easy to consume
 - Logging also need to be secure, so attackers can't hide their activity
 - High-value transactions should be audited and scrutinized especially carefully
 - Establish effective monitoring and response procedures to detect and act on attacks as swiftly as possible

Read more at [owasp.org](https://owasp.org/Top10/A09_2021-Security_Logging_and_Monitoring_Failures/)