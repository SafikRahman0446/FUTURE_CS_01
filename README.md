# FUTURE_CS_01
Task 1: Web Application Security Testing with DVWA, Burp Suite, and OWASP ZAP


🔐 FUTURE_CS_01 – Web Application Vulnerability Assessment (DVWA)

📌 Overview
This repository contains the work completed for Task 1 of the Cyber Security Internship under the Future Interns Program. The objective of this task was to conduct a vulnerability assessment of a deliberately insecure web application (DVWA) using industry-standard tools and methodologies. The findings simulate a real-world penetration test and demonstrate practical ethical hacking skills.

🎯 Objectives
- Identify common web application vulnerabilities (e.g., SQL Injection, XSS, CSRF)
- Perform both manual and automated testing
- Generate a detailed security report with recommendations
- Map findings to the OWASP Top 10 vulnerabilities

🛠️ Tools Used
| Tool        | Purpose                                          |
|-------------|--------------------------------------------------|
| Kali Linux  | Penetration testing OS                           |
| DVWA        | Test environment with real vulnerabilities       |
| OWASP ZAP   | Automated scanning and alerting                  |
| Burp Suite  | Manual payload injection and request analysis    |
| Firefox     | Browser-based interaction with DVWA              |





 🔍 Vulnerabilities Identified

|    | Vulnerability            | Type   | Severity |
|----|--------------------------|--------|----------|
| 1  | SQL Injection            | Manual | 🔴 High   |
| 2  | Reflected XSS            | Manual | 🟠 Medium |
| 3  | CSRF (Password Reset)    | Manual | 🔴 High   |
| 4  | Missing Security Headers | ZAP    | 🟠 Medium |
| 5  | Cookie Misconfiguration  | ZAP    | 🟠 Medium |
| 6  | Server Version Disclosure| ZAP    | 🔵 Info   |




📢 Disclaimer
This project was conducted on a local and intentionally vulnerable environment (DVWA) for educational purposes only. No real systems or services were harmed or tested.

