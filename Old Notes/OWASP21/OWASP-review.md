# OWASP Top 10 2021 Review
For each review item below identify which of the top 10 categories the issue falls under, and how you might prevent it.

 - A client doesn't normally allow users to access certain URLs unless they are authenticated as an admin. However, the user simply makes their browser target those URLs, and they are not denied access by the server.
 - A library used in an application has been comprimised, thus comprimising your application and allowing attackers to execute custom code remotely.
 - An e-commerce business doesn't try to stop bots and automated purchasing, so their highly in-demand product (Video cards, event tickets, etc) sells out to re-sellers before actual end-users can ever make a purchase.
 - A user inputs a username when registering which contains valid code that could destroy parts of the database if executed.
 - A user modifies the value held in browser memory to send any user id they want in a request that responds with sensitive information.
 - A restaurant takes online reservations without human validation. An attacker writes a simple script to make reservations automatically so that no real reservations can be made, denying service to paying customers.
 - The password database uses MD5 hashing algorithm to encrypt passwords. A copy of this database is stolen and the passwords are easily decrypted.
 - An application encrypts credit card data before storing it, but decrypts the data when queried, allowing someone exploiting some other security flaw to see unencrypted credit card details.
 - Attackers release a fake update for your router firmware which your router fails to notice is illigitimate. This update contains a backdoor so that the attackers can intercept and modify all traffic.
 - When the client gets a 500 server error the response also contains the full stack trace.
 - Your application doesn't do anything to delay or monitor repeated login attempts, so an attacker has grabbed a list of known usernames and passwords and is automatically testing every combination as quickly as possible to find ones that work.
 - A framework used in your application depends on a library which depends on a library which depends on a library that hasn't been updated in 5 years. An exploit was discovered and fixes were released last year, but the transitive dependency hasn't been patched since before 0 day.
 - Users who forgot their passwords are given a process to recover the account by answering security questions. An attacker who knows about the person who's account they are trying to breech is able to answer these questions and reset the password.
 - A user accesses their account with your application on a public computer, then forgets to logout. A week later someone comes along and notices they are logged into that user's account.
 - Someone notices that Spring Boot Actuator endpoints are enabled and open, so they send the server a shutdown command during peak hours.