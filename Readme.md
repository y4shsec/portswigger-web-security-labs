# SQL Injection – Hidden Data

## 1. Lab Overview

**Platform:** PortSwigger Web Security Academy
**Vulnerability:** SQL Injection (SQLi)
**Lab:** SQL Injection – Hidden Data
**Testing Tool:** Burp Suite
**Difficulty:** Apprentice
**Status:** Completed

---

## 2. Objective

The objective of this lab was to identify and exploit a SQL Injection vulnerability in a web application's product filtering functionality.

The testing demonstrated how attacker-controlled input can modify the application's backend SQL query and cause unintended database records to be returned.

---

## 3. Vulnerability Description

SQL Injection occurs when an application incorporates untrusted user input directly into a database query without using appropriate parameterization or input handling.

An attacker may manipulate the application's SQL query logic by supplying specially crafted input.

In this lab, the vulnerable functionality was associated with a product category parameter.

---

## 4. Security Classification

| Attribute               | Details         |
| ----------------------- | --------------- |
| Vulnerability           | SQL Injection   |
| CWE                     | CWE-89          |
| OWASP Category          | A03: Injection  |
| Severity                | High            |
| Attack Vector           | Web Application |
| Authentication Required | No              |
| User Interaction        | None            |

---

## 5. Tools Used

* Burp Suite
* Firefox
* PortSwigger Web Security Academy
* HTTP/HTTPS
* Burp Proxy
* Burp Repeater

---

## 6. Testing Methodology

The following methodology was used during the assessment:

```text
Access Application
        ↓
Identify Product Filtering Functionality
        ↓
Observe HTTP Request
        ↓
Intercept Request Using Burp Suite
        ↓
Identify User-Controlled Parameter
        ↓
Test Parameter for SQL Injection
        ↓
Modify SQL Query Logic
        ↓
Analyze Server Response
        ↓
Confirm Unauthorized Data Retrieval
        ↓
Capture Evidence
        ↓
Verify Lab Completion
```

---

## 7. Exploitation Process

### Step 1 – Identify the Application Functionality

The application was accessed through the PortSwigger Web Security Academy environment.

The product category functionality was examined to understand how the application processed user-supplied input.

### Step 2 – Intercept the HTTP Request

Burp Suite Proxy was used to intercept the request generated when selecting a product category.

The intercepted request was analyzed to identify parameters that were controlled by the user.

### Step 3 – Identify the Vulnerable Parameter

The category parameter was identified as the relevant input point.

Because the parameter value was incorporated into the application's backend database query, it was selected for SQL Injection testing.

### Step 4 – Test for SQL Injection

The parameter was modified using a SQL Injection payload designed to alter the application's query logic.

The modified request was sent to the server and the resulting HTTP response was analyzed.

### Step 5 – Validate the Vulnerability

The application returned records that were not expected from the original category selection.

This confirmed that the supplied input was influencing the backend SQL query.

The successful response provided evidence that the application was vulnerable to SQL Injection.

---

## 8. Evidence

The following screenshots provide evidence of the testing process.

### Evidence 01 – Normal Application

Shows the application's normal product/category functionality before exploitation.

![Normal Application](evidence/01-normal-application.png)

---

### Evidence 02 – Burp Suite Request

Shows the HTTP request intercepted using Burp Suite and identifies the user-controlled parameter.

![Burp Request](evidence/02-burp-request.png)

---

### Evidence 03 – SQL Injection Payload

Shows the modified parameter containing the SQL Injection test payload.

![SQL Injection Payload](evidence/03-sql-injection-payload.png)

---

### Evidence 04 – Hidden Data Retrieved

Shows the application's response after the SQL Injection payload was processed, demonstrating unintended data retrieval.

![Hidden Data Retrieved](evidence/04-hidden-data-retrieved.png)

---

### Evidence 05 – Lab Completion

Shows successful completion of the PortSwigger laboratory.

![Lab Completion](evidence/05-lab-solved.png)

---

## 9. Impact

A successful SQL Injection vulnerability can have significant security consequences depending on the application's database privileges and architecture.

Potential impacts include:

* Unauthorized access to database information
* Exposure of sensitive application data
* Authentication bypass
* Modification of database records
* Deletion of database records
* Extraction of confidential information
* Potential compromise of other application functionality

In this lab, the demonstrated impact was **unauthorized retrieval of application data through manipulation of the SQL query**.

---

## 10. Root Cause

The underlying security issue is the application's failure to safely separate user-controlled input from SQL query logic.

Directly incorporating untrusted input into SQL statements can allow an attacker to change the intended meaning of the query.

---

## 11. Remediation

The following controls should be implemented to prevent SQL Injection:

### Parameterized Queries

Use prepared statements and parameterized queries instead of dynamically constructing SQL statements.

### Input Validation

Validate user-controlled input against an appropriate allowlist where possible.

### Least-Privilege Database Access

The application's database account should have only the permissions required for normal application functionality.

### Secure Error Handling

Do not expose detailed database errors or SQL statements to users.

### Secure Development Practices

Developers should follow secure coding practices and conduct security testing throughout the software development lifecycle.

### Security Testing

Perform regular:

* SAST
* DAST
* Penetration Testing
* Code Review
* Dependency and configuration reviews

---

## 12. OWASP Mapping

**OWASP Top 10: A03 – Injection**

SQL Injection is categorized under Injection because attacker-controlled input can alter the structure or interpretation of a backend command.

---

## 13. Key Learning

This lab demonstrated the importance of analyzing HTTP requests and identifying parameters that interact with backend database queries.

Key takeaways:

* User-controlled parameters should always be considered potential attack surfaces.
* Burp Suite can be used to intercept and manipulate HTTP requests.
* SQL Injection can be validated by observing changes in application behavior and responses.
* Parameterized queries are a primary defense against SQL Injection.
* Security findings should be supported by clear, reproducible evidence.

---

## 14. Evidence Files

```text
01-sql-injection-hidden-data/
│
├── README.md
│
├── evidence/
│   ├── E01-Normal-Application
│   ├── E02-Normal-Burp-Request
│   ├── E03-SQLi-Payload
│   ├── E04-Hidden-Data-Retrieved
│   └── E05-lab-solved
│
└── requests/
    ├── 01-normal-request
    └── 02-SQLi-exploited-request
```

---

## 15. Disclaimer

This security testing activity was performed exclusively against the intentionally vulnerable environment provided by PortSwigger Web Security Academy for educational purposes.

No unauthorized systems, applications, or infrastructure were targeted.
