### Report Title:

```
Web Application Security Assessment Report
Target: DVWA (Damn Vulnerable Web App)
```

---

### **Project Overview**

In today's digital landscape, web applications have become the backbone of businesses, from startups to large-scale enterprises. With this increasing reliance comes a growing risk—cyber threats that exploit weak points in application security. This project was undertaken to simulate a real-world penetration test on a vulnerable web application, with the goal of identifying security flaws before malicious actors can exploit them.

Using a combination of manual testing techniques and industry-standard tools such as OWASP ZAP and Burp Suite, the test environment was carefully analyzed to uncover vulnerabilities often overlooked in development. The exercise not only reflects how attackers operate but also how defenders must think—strategically, methodically, and with a deep understanding of the OWASP Top 10 framework.

---

###  **Objective**

The primary objective of this assessment was to evaluate the security posture of a deliberately vulnerable web application in a controlled environment. The focus was to uncover and document real vulnerabilities—such as SQL injection, cross-site scripting (XSS), and CSRF—while gaining practical experience in ethical hacking methodologies. Each finding is backed with visual evidence, technical impact, and clear mitigation steps. This hands-on task bridges the gap between theory and practice, building the skills needed to assess and secure modern web applications.

---

## 2. **Scope of Work**

* **Target Application:** DVWA on localhost
* **Testing Tools:** OWASP ZAP, Firefox with proxy
* **Testing Type:** Black-box vulnerability scanning and manual verification
* **Environment:** Kali Linux (Localhost)

---

### Vulnerability 1: SQL Injection

* **OWASP Category**: A1 – Injection
* **Risk Level**: High
* **Page Affected**: Login Page (`/login.php`)
* **Tools Used**: Manual + OWASP ZAP
* **Payload**: ' OR '2'='2 --
* **Impact**: Bypasses authentication
* **Remediation**: Use prepared statements (parameterized queries), input validation, and stored procedures.

---

### Vulnerability 2: Stored Cross-Site Scripting (XSS)

* **OWASP Category**: A7 – Cross-Site Scripting
* **Risk Level**: Medium
* **Page Affected**: `vulnerabilities/xss_s/`
* **Tools Used**: Manual
* **Payload**: `<script>alert("XSS")</script>`
* **Impact**: Allows attacker to execute JavaScript in victims’ browsers
* **Remediation**: Sanitize input/output, use HTML encoding libraries, use Content Security Policy (CSP).

---

### Vulnerability 3: CSRF (Cross-Site Request Forgery)

* **OWASP Category**: A5 – Broken Access Control
* **Risk Level**: Medium
* **Page Affected**: Change password form
* **Tools Used**: OWASP ZAP CSRF PoC Generator
* **Impact**: Attacker can trick user into changing their password
* **Remediation**: Implement anti-CSRF tokens in all state-changing forms, check referrer headers.

---

### Vulnerability 4: File Inclusion / Directory Traversal

* **OWASP Category**: A6 – Security Misconfiguration
* **Risk Level**: Medium
* **Payload**: `?page=../../../../etc/passwd`
* **Impact**: Access to sensitive system files
* **Remediation**: Validate file paths strictly, disable user-controlled includes.

---

## 4. **OWASP Top 10 Checklist Mapping**

| OWASP Category                 | Found? | Vulnerability Name |
| ------------------------------ | ------ | ------------------ |
| A01: Injection                 | ✅      | SQL Injection      |
| A02: Broken Authentication     | ✅      | Weak login logic   |
| A05: Broken Access Control     | ✅      | CSRF               |
| A06: Security Misconfig        | ✅      | File Inclusion     |
| A07: Cross-Site Scripting      | ✅      | XSS                |

---

## 5. **Conclusion & Recommendations**
> The DVWA test environment revealed multiple critical vulnerabilities that would pose serious risks in a real-world application. It's recommended to implement input validation, sanitize all user data, use prepared statements for database access, enforce proper session and CSRF protection, and follow secure coding practices aligned with OWASP guidelines.

---
