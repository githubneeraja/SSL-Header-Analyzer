 SSL-Header-Analyzer
Building SSL Header Analyzer


  SSL Header Analyzer — n8n Workflow

 Overview

TheSSL Header Analyzer** is ann8n workflow** that automatically scans websites for SSL/TLS configuration issues, HTTP security headers, and client-side vulnerabilities. It combinesAI-based analysis** (using Google Gemini and LangChain) withSSL Labs API integration** to generate a detailedsecurity audit report**.



 Features

SSL/TLS Analysis** – Connects to SSL Labs API to evaluate the target domain’s certificate grade, expiry date, and trust level.
HTTP Security Header Audit** – Identifies missing or misconfigured headers like CSP, HSTS, X-Frame-Options, and Referrer-Policy.
Client-Side Security Check** – Analyzes webpage HTML and scripts for potential vulnerabilities such as XSS or data leakage.
AI-Powered Reporting** – Uses Google Gemini (PaLM API) to intelligently analyze results and format them in readable reports.
Email Notifications** – Automatically sends detailed audit reports and SSL expiry alerts via Gmail.
Scoring System** – Grades the website’s overall security posture (A, B, C, or F).



 Workflow Components

| Node Name                                            | Description                                                 |
| - | -- |
|Landing Page URL (Form Trigger)**                  | Accepts website input from the user.                        |
|Scrape Website (HTTP Request)**                    | Fetches the webpage content and headers.                    |
|Extra Headers for Debug (Code)**                   | Extracts and formats response headers for analysis.         |
|Security Configuration Audit (LangChain Agent)**   | Analyzes header configurations for security best practices. |
|Security Vulnerabilities Audit (LangChain Agent)** | Reviews client-side vulnerabilities in HTML and JavaScript. |
|Check SSL (HTTP Request)**                         | Queries SSL Labs API for certificate and grading data.      |
|Expiry Alert (If Node)**                           | Detects SSL certificate expiry conditions.                  |
|Warning Email Formulate (LangChain Agent)**        | Crafts a professional SSL security summary email.           |
|Send alert email (Gmail)**                         | Sends SSL/TLS expiry alerts.                                |
|Send Security Report (Gmail)**                     | Sends the full HTML-based audit report.                     |



 AI Models Used

*Google Gemini (PaLM API)** for intelligent report writing.
*LangChain Agent Nodes** for structured analysis and summarization.



  Output

You’ll receive anemail report** that includes:

* Overall SecurityGrade (A–F)**
* List ofpresent/missing security headers**
*Cookie security findings**
*Client-side vulnerabilities**
*SSL/TLS certificate details**
*Recommendations** for fixes



  Example Use Case

* Enter a website URL (e.g., `https://example.com`)
* The workflow will:

  1. Check SSL/TLS validity and grade
  2. Fetch headers and HTML
  3. Run AI-driven audits
  4. Send results to your Gmail inbox



  Requirements

| Tool                         | Purpose                      |
| - | - |
|n8n**                      | Workflow automation platform |
|Google Gemini API**        | For AI analysis              |
|SSL Labs API**             | For SSL grading and status   |
|Gmail OAuth2 Credentials** | For sending email reports    |



 Installation

1. Clone this repository:

   bash
   git clone https://github.com/githubneeraja/SSL-Header-Analyzer.git
   
2. Openn8n** →Import Workflow** → select `SSL Header Analyze.json`
3. Configure credentials:

  Google Gemini (PaLM API)**
  Gmail OAuth2**
4. Activate the workflow.



  Example Email Report

```
Subject: Website Security Audit - example.com

URL: https://example.com
Grade: A
Timestamp: 2025-11-03T18:00:00Z

Configuration Audit:
- Missing Header: Content-Security-Policy
- Weak Referrer Policy

Vulnerability Audit:
- No client-side vulnerabilities found

SSL Grade: A+
Certificate Expiry: 2026-01-01


Future Enhancements

* AddDNSSEC validation**
* IncludeOWASP Top 10** scanning integration
* AddDashboard UI** for visual reports







