# PortSwigger Web Security Academy – Web Application Security Labs

![PortSwigger](https://img.shields.io/badge/Platform-PortSwigger%20Web%20Security%20Academy-blue)
![Burp Suite](https://img.shields.io/badge/Tool-Burp%20Suite-orange)
![Web Security](https://img.shields.io/badge/Focus-Web%20Application%20Security-red)
![Labs](https://img.shields.io/badge/Labs-5-success)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

## Overview

This repository documents hands-on web application security testing performed using the **PortSwigger Web Security Academy** and **Burp Suite**.

The project focuses on identifying, analyzing, exploiting, validating, and documenting common web application vulnerabilities through controlled security laboratory exercises.

The objective was to develop practical skills in HTTP request analysis, parameter manipulation, vulnerability identification, exploitation, evidence collection, impact assessment, and security remediation.

---

## Project Objectives

- Understand common web application vulnerabilities.
- Perform practical vulnerability identification and validation.
- Analyze HTTP requests and responses using Burp Suite.
- Manipulate application parameters and requests.
- Develop controlled proof-of-concept exploits.
- Collect and organize technical evidence.
- Assess potential security impact.
- Recommend appropriate security controls and remediation measures.
- Document findings using a professional security assessment structure.

---

## Labs Completed

| # | Vulnerability | PortSwigger Lab | Status |
|---|---|---|---|
| 01 | SQL Injection | SQL Injection – Hidden Data | ✅ Completed |
| 02 | Path Traversal | Path Traversal | ✅ Completed |
| 03 | Reflected XSS | Reflected Cross-Site Scripting | ✅ Completed |
| 04 | Broken Access Control | Broken Access Control | ✅ Completed |
| 05 | CSRF | Cross-Site Request Forgery | ✅ Completed |

---

## Security Testing Methodology

The labs were approached using the following security testing workflow:

```text
                    Start
                      │
                      ▼
              Application Review
                      │
                      ▼
              Identify Attack Surface
                      │
                      ▼
             Intercept HTTP Requests
                      │
                      ▼
             Analyze Parameters/Input
                      │
                      ▼
             Vulnerability Testing
                      │
                      ▼
              Payload Manipulation
                      │
                      ▼
                Exploitation
                      │
                      ▼
             Impact Verification
                      │
                      ▼
              Evidence Collection
                      │
                      ▼
              Remediation Analysis
                      │
                      ▼
                     End
