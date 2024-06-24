# A03:2021 – Injection
Injection occurs whenever someone inputs interpretable or executable code expressions into an application to have those expressions be executed or interpreted by the application. A perfect example would be XKCD's [Bobby Tables](https://xkcd.com/327/) where the user's name contains valid SQL expressions intended to cause destruction of database tables. In that example we can imagine the following SQL expression being concatinated directly with user input:
```SQL
INSERT INTO students (first_name, last_name) VALUES ('<FIRST_NAME_INPUT>', '<SECOND_NAME_INPUT>')
```
Concatinating the unsanitized user input would create the following expression:
```SQL
INSERT INTO students (first_name, last_name) VALUES ('Robert,'); DROP TABLE students;--', 'Tables' )
```
This turns the intended INSERT statement into two valid statements, the second of which is:
```SQL
DROP TABLE students;
```
This allows unscrupulous actors to add their own code to be executed by our secure systems, bypassing other security measures by being embedded in normal user input. SQL is not the only form of injection, any user input which might get interpreted or executed by the system is at risk for this type of attack. 

Prevent injection by keeping data and behavior totally separate, and sanitizing user input.

## How to Prevent
 - Client-side and server-side validation for special characters that might be used to "escape" the input such as ```"```, ```'```, ```\```, ```/```, ```-```, ```!```, and ```;```
 - Parameterized interfaces which would sanitize the parameters (such as JDBC's PreparedStatement)
 - Use ```LIMIT``` and other SQL controls within queries to reduce impact of successful attacks

Read more at [owasp.org](https://owasp.org/Top10/A03_2021-Injection/)
