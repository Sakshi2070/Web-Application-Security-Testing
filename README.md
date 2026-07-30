# Web Application Security Testing using OWASP Juice Shop & Burp Suite

## Overview

This project demonstrates manual web application security testing using **OWASP Juice Shop** and **Burp Suite Community Edition**. The objective was to understand how HTTP requests and responses can be intercepted, analyzed, and modified while performing manual security assessments aligned with selected OWASP Top 10 categories.

The project focuses on practical testing of authentication, access control, request manipulation, HTTP security headers, and basic SQL Injection testing in a safe lab environment.

---

## Objectives

- Capture HTTP requests using Burp Suite
- Analyze HTTP requests and responses
- Test authentication mechanisms
- Examine authentication and authorization behaviour
- Examine HTTP response security headers
- Attempt SQL Injection payloads
- Document security observations

---

## Features

- HTTP request interception
- Request modification using Burp Repeater
- Authentication request analysis
- Authorization testing
- Security header inspection
- Manual web application testing
- OWASP Top 10 aligned assessment

## Tools Used

- OWASP Juice Shop
- Burp Suite Community Edition
- Firefox Browser
- Kali Linux (Virtual Machine)

---

## Environment

| Component | Details |
|-----------|---------|
| Operating System | Kali Linux |
| Target Application | OWASP Juice Shop |
| Proxy Tool | Burp Suite Community Edition |
| Browser | Firefox |
| Test Type | Manual Web Application Security Testing |

---

# Testing Performed

## 1. Authentication Request Analysis

The login request was intercepted using Burp Suite Proxy.

The captured request was examined to understand:

- HTTP request method
- Request headers
- JSON request body
- Authentication parameters

The request was then forwarded to Burp Repeater for manual testing.

---

## 2. Authentication Header Analysis (OWASP A02)

The captured requests were examined for security-related HTTP headers.

### Observed Headers

- X-Content-Type-Options: nosniff
- X-Frame-Options: SAMEORIGIN
- Feature-Policy
- Content-Type
- Connection
- Keep-Alive

### Observation

The application implements several defensive HTTP response headers that help mitigate common browser-based attacks.

---
## 3. Authorization Testing (OWASP A01)

Protected API endpoints were accessed to observe how the application handled unauthorized requests.

### Observation

Requests made without valid authentication received:

```
HTTP/1.1 401 Unauthorized
```

This indicates that authentication is required before protected resources can be accessed.

---

## 4. Injection Testing (OWASP A03)

The intercepted login request was modified using Burp Repeater.

Test payloads were inserted into request parameters to observe how the application processed unexpected input.

### Observation

A malformed request generated a server error because the JSON structure became invalid.

No successful SQL Injection or authentication bypass was observed during testing.

---

## 5. Response Analysis (OWASP A05)

Application responses were reviewed while performing request manipulation.

The objective was to observe how the application handled unexpected or malformed requests and whether meaningful error responses were returned.

---


---
# Findings Summary

| ID | Finding | Observation | Severity |
|----|---------|-------------|----------|
| A01 | Authorization Enforcement | Protected API endpoints returned **401 Unauthorized** when accessed without valid authentication, indicating that authorization checks were enforced for the tested endpoint. | Low |
| A02 | HTTP Security Header Analysis | HTTP requests and responses were analyzed, including security-related response headers such as **X-Frame-Options** and **X-Content-Type-Options**. | Informational |
| A03 | Injection Testing | Login requests were modified using Burp Repeater to test for SQL Injection. The application returned a JSON parsing error due to malformed input, and no successful SQL Injection was observed. | Informational |
| A05 | Response Handling | Application responses were reviewed while submitting modified requests to observe how unexpected input was handled. | Informational |


# OWASP Top 10 Mapping

| OWASP Category | Activity performed |
|---------------|--------|
| A01 Broken Access Control | Tested |
| A02 Cryptographic Failures | Header inspection performed |
| A03 Injection | Basic SQL Injection payload tested |
| A07 Identification & Authentication Failures | Login request analyzed |

---

# Screenshots

Include the following screenshots inside the **screenshots/** folder.

```
screenshots/

01_login_request_intercept.png
02_login_request_repeater.png
03_sql_payload_500_response.png
04_authorization_401_response.png
05_response_headers.png
```

---

# Skills Demonstrated

- Burp Suite
- HTTP Request Analysis
- HTTP Response Analysis
- Authentication Testing
- Authorization Testing
- SQL Injection Basics
- OWASP Top 10
- Web Application Security Testing
- Security Header Analysis

---

# Learning Outcomes

- Configured Burp Suite as an intercepting proxy.
- Captured and modified HTTP requests.
- Used Burp Repeater to replay requests.
- Understood authentication and authorization mechanisms.
- Examined security-related HTTP headers.
- Performed basic SQL Injection testing in a controlled environment.
- Documented findings according to web application security testing practices.

---

## Project Structure

```
Web-Application-Security-Testing/
│
├── README.md
└── screenshots/
   ├── 01_login_request_intercept.png
   ├── 02_successful_login_jwt.png
   ├── 03_authorization_401.png
   ├── 04_http_request_analysis.png
   ├── 05_response_headers.png
   ├── 06_security_misconfiguration.png
   └── 07_whoami_endpoint.png
---

## Disclaimer

This project was conducted in a controlled lab environment using **OWASP Juice Shop**, an intentionally vulnerable web application designed for security education and penetration testing practice. No testing was performed against unauthorized systems.
