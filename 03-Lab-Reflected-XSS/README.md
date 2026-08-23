# Cross-Site Scripting (XSS) – Web Security Labs

## Lab Overview

| Field | Details |
|---|---|
| Platform | PortSwigger Web Security Academy |
| Project Section | Lab 3 |
| Vulnerability Class | Cross-Site Scripting (XSS) |
| Testing Tool | Burp Suite / Web Browser |
| Difficulty | Apprentice-level practice |
| Status | Completed |

---

## 1. Objective

The objective of this laboratory section was to gain practical experience identifying and validating **Cross-Site Scripting (XSS)** vulnerabilities in intentionally vulnerable web applications.

The exercises covered different XSS injection points and contexts, including search functionality, comments, and reflected application output.

The assessment focused on:

- Identifying user-controlled input.
- Observing how application input is reflected or stored.
- Intercepting and analyzing HTTP requests.
- Testing input handling with controlled XSS payloads.
- Identifying the context in which attacker-controlled input is processed.
- Validating JavaScript execution or reflected output.
- Collecting technical evidence.
- Verifying successful laboratory completion.
- Understanding appropriate remediation techniques.

---

## 2. Vulnerability Description

**Cross-Site Scripting (XSS)** is a web application vulnerability that occurs when attacker-controlled input is included in a web page without sufficient output encoding or other appropriate security controls.

Depending on how the input is processed, XSS can occur in different forms, including:

- Reflected XSS
- Stored XSS
- DOM-based XSS

An XSS vulnerability may allow attacker-controlled JavaScript or HTML to execute in the security context of a victim's browser.

Potential consequences can include:

- Unauthorized actions performed in a victim's session
- Access to data available to client-side scripts
- Session or token exposure in vulnerable applications
- Manipulation of page content
- Phishing or user-interface manipulation
- Redirection to malicious resources

The exact impact depends on the application architecture, browser protections, authentication model, and location of the injection.

---

## 3. Security Classification

| Attribute | Details |
|---|---|
| Vulnerability | Cross-Site Scripting (XSS) |
| CWE | CWE-79 |
| CWE Name | Improper Neutralization of Input During Web Page Generation |
| OWASP Category | A03 – Injection |
| Attack Surface | Web Application |
| Testing Method | Controlled XSS payload injection |
| Authentication | Depends on the individual exercise |
| User Interaction | Depends on the individual exercise |

---

## 4. Tools Used

- Burp Suite
- Burp Proxy
- Burp Repeater
- Firefox / Web Browser
- PortSwigger Web Security Academy
- HTTP / HTTPS

---

## 5. Assessment Methodology

The XSS exercises were approached using a structured web application security testing workflow.

```text
                    Start
                      |
                      v
             Access Application
                      |
                      v
            Identify Input Point
                      |
                      v
           Observe Normal Behavior
                      |
                      v
           Intercept HTTP Request
                      |
                      v
          Identify Reflection/Storage
                      |
                      v
           Test Controlled Payload
                      |
                      v
          Analyze Application Output
                      |
                      v
          Validate XSS Behavior
                      |
                      v
             Capture Evidence
                      |
                      v
          Verify Lab Completion
                      |
                      v
                     End
```

---

# 6. XSS Exercises and Evidence

The supplied project evidence contains **five XSS exercises**, organized as L01 through L05.

The original evidence filenames are preserved exactly as collected.

---

## Exercise L01 – Search Function XSS

### Evidence Available

- `L01-E01-Normal-search-page.png`
- `L01-E02-Normal-search-burp-request.png`
- `L01-E03-XSS-script-inject.png`
- `L01-E04-XSS-lab-solved.png`

### Testing Process

The search functionality was first observed under normal conditions.

The corresponding HTTP request was then inspected using Burp Suite to identify the user-controlled search parameter.

A controlled XSS payload was inserted into the search input and the resulting application behavior was observed.

The successful execution/processing of the injected payload demonstrated the XSS vulnerability in the laboratory environment.

### Evidence

#### Normal Search Page

![Normal Search Page](03-Lab-Reflected-XSS/L01-E01-Normal-search-page.png)

**Evidence:** `L01-E01-Normal-search-page.png`

#### Normal Search Request

![Normal Search Burp Request](03-Lab-Reflected-XSS/L01-E02-Normal-search-burp-request.png)

**Evidence:** `L01-E02-Normal-search-burp-request.png`

#### XSS Payload Injection

![XSS Payload](03-Lab-Reflected-XSS/L01-E03-XSS-script-inject.png)

**Evidence:** `L01-E03-XSS-script-inject.png`

#### Lab Completion

![Lab Solved](03-Lab-Reflected-XSS/L01-E04-XSS-lab-solved.png)

**Evidence:** `L01-E04-XSS-lab-solved.png`

---

## Exercise L02 – Comment/Blog XSS

### Evidence Available

- `L02-E01-XSS-Normal-View-Post-Page.png`
- `L02-E02-XSS-script-inject-comment-section.png`
- `L02-E03-XSS-lab-solved.png`

### Testing Process

The post/comment functionality was reviewed to identify a user-controlled content field.

The comment section was tested with a controlled XSS payload.

The resulting behavior demonstrated that attacker-controlled content could be processed by the application in an unsafe manner.

### Evidence

#### Normal Post Page

![Normal Post Page](03-Lab-Reflected-XSS/L02-E01-XSS-Normal-View-Post-Page.png)

**Evidence:** `L02-E01-XSS-Normal-View-Post-Page.png`

#### XSS Payload in Comment Section

![XSS Comment Payload](03-Lab-Reflected-XSS/L02-E02-XSS-script-inject-comment-section.png)

**Evidence:** `L02-E02-XSS-script-inject-comment-section.png`

#### Lab Completion

![Lab Solved](03-Lab-Reflected-XSS/L02-E03-XSS-lab-solved.png)

**Evidence:** `L02-E03-XSS-lab-solved.png`

> Note: This exercise appears to involve stored/user-generated content based on the evidence filename. It should not automatically be classified as reflected XSS without confirming the exact PortSwigger lab behavior.

---

## Exercise L03 – Search Input XSS Filtering/Context Test

### Evidence Available

- `L03-E01-XSS-Normal-page.png`
- `L03-E02-XSS-search-random-alphanumberic-string.png`
- `L03-E03-XSS-search-script-output.png`
- `L03-E03-XSS-lab-solved.png`

### Testing Process

The search functionality was examined to understand how the application processed and returned user-controlled input.

A random alphanumeric string was first submitted to establish how the input was reflected.

Further testing was then performed using a controlled XSS payload.

The resulting output was analyzed to determine whether the injected content could execute in the application's response context.

### Evidence

#### Normal Page

![Normal Page](03-Lab-Reflected-XSS/L03-E01-XSS-Normal-page.png)

**Evidence:** `L03-E01-XSS-Normal-page.png`

#### Random Alphanumeric Search

![Random Search](03-Lab-Reflected-XSS/L03-E02-XSS-search-random-alphanumberic-string.png)

**Evidence:** `L03-E02-XSS-search-random-alphanumberic-string.png`

#### XSS Search Output

![XSS Search Output](03-Lab-Reflected-XSS/L03-E03-XSS-search-script-output.png)

**Evidence:** `L03-E03-XSS-search-script-output.png`

#### Lab Completion

![Lab Solved](03-Lab-Reflected-XSS/L03-E03-XSS-lab-solved.png)

**Evidence:** `L03-E03-XSS-lab-solved.png`

> Note: Two different files use the `L03-E03` prefix. Both original filenames are intentionally preserved.

---

## Exercise L04 – Search Context XSS

### Evidence Available

- `L04-E01-XSS-Normal-page.png`
- `L04-E02-XSS-script-inject-search-section.png`
- `L04-E03-XSS-search-script-output.png`
- `L04-E04-XSS-lab-solved.png`

### Testing Process

The search functionality was examined to identify the location where user-controlled input was incorporated into the application response.

The input was tested using a controlled XSS payload.

The resulting response was analyzed to validate whether the injected content was interpreted as executable client-side content.

### Evidence

#### Normal Page

![Normal Page](03-Lab-Reflected-XSS/L04-E01-XSS-Normal-page.png)

**Evidence:** `L04-E01-XSS-Normal-page.png`

#### XSS Payload in Search

![XSS Search Injection](03-Lab-Reflected-XSS/L04-E02-XSS-script-inject-search-section.png)

**Evidence:** `L04-E02-XSS-script-inject-search-section.png`

#### XSS Search Output

![XSS Search Output](03-Lab-Reflected-XSS/L04-E03-XSS-search-script-output.png)

**Evidence:** `L04-E03-XSS-search-script-output.png`

#### Lab Completion

![Lab Solved](03-Lab-Reflected-XSS/L04-E04-XSS-lab-solved.png)

**Evidence:** `L04-E04-XSS-lab-solved.png`

---

## Exercise L05 – Feedback/Search Input XSS

### Evidence Available

- `L05-E01-XSS-Normal-Feedback-page.png`
- `L05-E02-XSS-normal-slash.png`
- `L05-E03-XSS-search-script-output.png`
- `L05-E04-XSS-lab-solved.png`

### Testing Process

The feedback functionality was reviewed to identify how user-controlled input was processed.

Normal input was first tested to establish the application's behavior.

The input context was then analyzed and tested using a controlled XSS payload.

The resulting output was inspected to validate the security impact.

### Evidence

#### Normal Feedback Page

![Normal Feedback Page](03-Lab-Reflected-XSS/L05-E01-XSS-Normal-Feedback-page.png)

**Evidence:** `L05-E01-XSS-Normal-Feedback-page.png`

#### Normal Slash Input

![Normal Slash](03-Lab-Reflected-XSS/L05-E02-XSS-normal-slash.png)

**Evidence:** `L05-E02-XSS-normal-slash.png`

#### XSS Search Output

![XSS Search Output](03-Lab-Reflected-XSS/L05-E03-XSS-search-script-output.png)

**Evidence:** `L05-E03-XSS-search-script-output.png`

#### Lab Completion

![Lab Solved](03-Lab-Reflected-XSS/L05-E04-XSS-lab-solved.png)

**Evidence:** `L05-E04-XSS-lab-solved.png`

---

# 7. Evidence Summary

| Exercise | Evidence Count | Focus |
|---|---:|---|
| L01 | 4 | Search input XSS |
| L02 | 3 | Comment/user-generated content XSS |
| L03 | 4 | Search input/context testing |
| L04 | 4 | Search input XSS |
| L05 | 4 | Feedback/search input XSS |
| **Total** | **19** | **XSS testing evidence** |

---

# 8. Vulnerability Impact

Successful XSS exploitation can allow attacker-controlled client-side code to execute within a victim's browser context.

Potential impact may include:

- Unauthorized actions performed using the victim's browser session
- Access to information available to client-side scripts
- Manipulation of application content
- Phishing or UI redressing
- Redirection to attacker-controlled resources
- Theft of sensitive browser-accessible information
- Compromise of user trust in the affected application

The practical impact depends on the injection context, browser security controls, authentication model, and privileges available to the affected user.

---

# 9. Root Cause Analysis

The root cause of XSS is generally the application's failure to safely handle untrusted input before placing it into an HTML, JavaScript, attribute, URL, or other browser-interpreted context.

A vulnerable flow can be represented as:

```text
User Input
    |
    v
Application Processing
    |
    v
Unsafe Output
    |
    v
Browser Interprets Input
    |
    v
Potential Script Execution
```

A secure implementation should instead ensure that untrusted data is appropriately encoded for the output context before it reaches the browser.

---

# 10. Remediation Recommendations

## 10.1 Context-Aware Output Encoding

Encode untrusted data according to the context in which it is inserted.

Different contexts require different handling, including:

- HTML context
- HTML attribute context
- JavaScript context
- CSS context
- URL context

---

## 10.2 Use Safe Framework APIs

Use framework features that automatically escape or encode untrusted data.

Avoid APIs that directly interpret user input as HTML or executable script unless there is a strong, reviewed requirement.

---

## 10.3 Input Validation

Validate input according to the application's expected data format.

Input validation should be treated as an additional security layer and not as the primary defense against XSS.

---

## 10.4 Content Security Policy

Implement a strong **Content Security Policy (CSP)** to reduce the impact of successful XSS exploitation.

CSP should be designed to minimize unsafe script execution and avoid unnecessary use of:

```text
unsafe-inline
```

and

```text
unsafe-eval
```

where practical.

---

## 10.5 Cookie Security

For authentication cookies, use appropriate security attributes such as:

- `HttpOnly`
- `Secure`
- `SameSite`

These controls do not fix XSS, but they can reduce the impact of some exploitation scenarios.

---

## 10.6 Secure HTML Handling

Avoid inserting untrusted input through dangerous DOM APIs such as `innerHTML` when a safe alternative is available.

Prefer APIs that treat data as text rather than executable markup.

---

## 10.7 Security Testing

Include XSS testing in:

- Secure code review
- SAST
- DAST
- Penetration testing
- Regression testing
- API and web application security testing

---

# 11. OWASP and CWE Mapping

## OWASP Top 10

**A03 – Injection**

Cross-Site Scripting is commonly categorized under Injection because attacker-controlled input can be interpreted as executable browser-side content.

## CWE

**CWE-79 – Improper Neutralization of Input During Web Page Generation ('Cross-site Scripting')**

---

# 12. Detection Indicators

During authorized security testing, common XSS test patterns may include controlled inputs such as:

```text
<script>alert(1)</script>
```

Other context-specific payloads may be required when the application filters tags or places input inside an HTML attribute, JavaScript block, or other context.

Payloads should only be tested against systems where explicit authorization has been obtained.

---

# 13. Defensive Testing Recommendations

Organizations should verify that:

1. User input is not inserted into HTML without appropriate encoding.
2. HTML attributes are safely encoded.
3. JavaScript contexts use safe data-handling mechanisms.
4. User-generated content is sanitized when HTML is intentionally supported.
5. Dangerous DOM APIs are avoided for untrusted input.
6. CSP is configured as a defense-in-depth control.
7. Authentication cookies use appropriate security attributes.
8. XSS regression tests are included in the software development lifecycle.

---

# 14. Key Learning Outcomes

This laboratory section provided practical experience with multiple XSS injection points and browser interpretation contexts.

### Technical Learnings

- User-controlled input is a major web application attack surface.
- Burp Suite can be used to intercept and manipulate HTTP requests.
- XSS behavior depends heavily on the context in which input is reflected or stored.
- Testing should begin with benign/random input to understand application behavior.
- Payload selection must account for application filtering and output context.
- Successful exploitation should be supported by clear evidence.

### Security Engineering Learnings

- Context-aware output encoding is a primary XSS defense.
- Input validation alone is not sufficient.
- Safe framework APIs should be preferred.
- CSP provides useful defense in depth.
- Secure cookie attributes can reduce some potential impact.
- Security testing should be incorporated into the development lifecycle.

---

# 15. Skills Demonstrated

This laboratory demonstrates practical experience with:

- Web application security testing
- Cross-Site Scripting testing
- HTTP request analysis
- Burp Suite Proxy
- Burp Suite Repeater
- Parameter manipulation
- Search input testing
- User-generated content testing
- Payload analysis
- Browser-side behavior validation
- Vulnerability evidence collection
- Impact assessment
- Root cause analysis
- Security remediation
- Technical security documentation

---

# 16. Repository Structure

```text
03-Lab-Reflected-XSS/
│
├── README.md
│
└── Evidence/
    ├── L01-E01-Normal-search-page.png
    ├── L01-E02-Normal-search-burp-request.png
    ├── L01-E03-XSS-script-inject.png
    ├── L01-E04-XSS-lab-solved.png
    │
    ├── L02-E01-XSS-Normal-View-Post-Page.png
    ├── L02-E02-XSS-script-inject-comment-section.png
    ├── L02-E03-XSS-lab-solved.png
    │
    ├── L03-E01-XSS-Normal-page.png
    ├── L03-E02-XSS-search-random-alphanumberic-string.png
    ├── L03-E03-XSS-lab-solved.png
    ├── L03-E03-XSS-search-script-output.png
    │
    ├── L04-E01-XSS-Normal-page.png
    ├── L04-E02-XSS-script-inject-search-section.png
    ├── L04-E03-XSS-search-script-output.png
    ├── L04-E04-XSS-lab-solved.png
    │
    ├── L05-E01-XSS-Normal-Feedback-page.png
    ├── L05-E02-XSS-normal-slash.png
    ├── L05-E03-XSS-search-script-output.png
    └── L05-E04-XSS-lab-solved.png
```

---

# 17. Lab Completion

**Status: Completed**

The supplied evidence demonstrates completion of five XSS-related laboratory exercises in the authorized PortSwigger Web Security Academy environment.

A total of **19 evidence screenshots** were collected.

The original filenames are preserved to maintain traceability between the GitHub documentation and the evidence collected during the practical exercises.

---

# 18. Disclaimer

This security testing activity was performed exclusively against intentionally vulnerable environments provided by PortSwigger Web Security Academy for educational and authorized security-training purposes.

No unauthorized systems, applications, infrastructure, or third-party services were targeted.

The techniques documented in this repository are intended for authorized security testing, education, and defensive security research only.

---

## Author

**Yashdeep Sankhla**

Cybersecurity | Network Security | Web Application Security

GitHub: [@y4shsec](https://github.com/y4shsec)
