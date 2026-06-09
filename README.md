# Detection and Analysis of Web Application Attacks Using Splunk and DVWA

## Project Overview

In modern Security Operations Centers (SOCs), web application attacks remain one of the most common attack vectors targeting organizations. This project demonstrates how Security Information and Event Management (SIEM) solutions can be leveraged to detect, investigate, and analyze web application attacks through centralized log monitoring and threat detection.

To simulate a realistic attack environment, I deployed Damn Vulnerable Web Application (DVWA) on an Apache web server hosted through XAMPP and integrated the generated web server logs into Splunk Enterprise. Using this setup, I conducted controlled attacks including SQL Injection (SQLi) and Cross-Site Scripting (XSS), captured the resulting log data, and developed detection queries to identify malicious activity.

The project highlights practical skills in SIEM operations, log analysis, web application security monitoring, attack detection, threat hunting, and security event investigation.

---

## Key Objectives

* Deploy a vulnerable web application environment for security testing.
* Simulate real-world web application attacks in a controlled lab environment.
* Collect and centralize Apache web server logs.
* Ingest and analyze logs using Splunk Enterprise.
* Detect SQL Injection and Cross-Site Scripting attacks using SPL queries.
* Investigate attacker activity through log correlation and event analysis.
* Demonstrate SOC analyst workflows for web attack detection and monitoring.

---

## Technologies Used

| Category               | Technology                                          |
| ---------------------- | --------------------------------------------------- |
| SIEM                   | Splunk Enterprise                                   |
| Web Server             | Apache (XAMPP)                                      |
| Vulnerable Application | DVWA (Damn Vulnerable Web Application)              |
| Operating System       | Windows                                             |
| Log Source             | Apache Access Logs                                  |
| Attack Simulation      | SQL Injection, Cross-Site Scripting (XSS)           |
| Analysis Methodology   | Log Analysis, Threat Detection, Security Monitoring |

---

## Security Architecture

```text
Attacker
    │
    ▼
DVWA Web Application
    │
    ▼
Apache Web Server
    │
    ▼
Apache Access Logs
    │
    ▼
Splunk Enterprise
    │
    ▼
Threat Detection & Security Analysis
```

---

## Attack Scenarios and Detection

### SQL Injection (SQLi)

A SQL Injection attack was performed against the vulnerable DVWA application to demonstrate how malicious user input can manipulate backend database queries.

Payload Used:

```sql
' OR 1=1#
```

The attack successfully bypassed intended query restrictions and returned multiple database records.

Detection was achieved by monitoring Apache access logs within Splunk and identifying requests targeting the SQL Injection module.

---

### Cross-Site Scripting (XSS)

A reflected Cross-Site Scripting attack was executed against the DVWA XSS module to demonstrate client-side script injection.

Payload Used:

```html
<script>alert('XSS')</script>
```

The payload execution was successfully recorded in Apache access logs and analyzed through Splunk search queries.

---

## Detection Queries

### SQL Injection Detection

```spl
index=apache "/DVWA/vulnerabilities/sqli"
```

### SQL Injection Activity Analysis

```spl
index=apache "/DVWA/vulnerabilities/sqli"
| stats count by clientip
```

### XSS Detection

```spl
index=apache "/DVWA/vulnerabilities/xss_r"
```

### XSS Activity Analysis

```spl
index=apache "/DVWA/vulnerabilities/xss_r"
| stats count by clientip
```

---

## Key Findings

* Successfully deployed and configured a web application attack simulation environment.
* Centralized Apache web server logs into Splunk Enterprise.
* Detected and analyzed SQL Injection attack activity.
* Detected and analyzed Cross-Site Scripting attack activity.
* Developed custom SPL-based detection logic.
* Demonstrated practical SIEM workflows for threat detection and investigation.
* Performed security event analysis using real attack-generated telemetry.

---

## Skills Demonstrated

### Security Operations (SOC)

* Security Monitoring
* Threat Detection
* Incident Investigation
* Event Correlation
* Log Analysis
* Security Event Analysis

### SIEM Engineering

* Splunk Administration
* Data Ingestion
* Index Management
* Search Processing Language (SPL)
* Detection Engineering
* Dashboard Development

### Web Application Security

* SQL Injection Analysis
* Cross-Site Scripting (XSS) Analysis
* Vulnerability Assessment
* Web Application Threat Monitoring

### Cybersecurity Fundamentals

* Threat Hunting
* Attack Simulation
* Security Analytics
* Security Operations
* Blue Team Methodologies

---

## Future Enhancements

* Sysmon Integration for Endpoint Visibility
* Zeek Integration for Network Traffic Analysis
* Command Injection Detection
* Brute Force Attack Monitoring
* Real-Time Splunk Alerting
* Security Dashboard Development
* Detection Rule Tuning and Optimization

---

## Author

**Bharanidaran S**

Cybersecurity Student | SOC Analyst Aspirant | SIEM & Threat Detection Enthusiast

Passionate about Security Operations, Threat Detection, Log Analysis, Digital Forensics, Incident Response, and Blue Team Security Engineering. Continuously building hands-on cybersecurity projects to develop practical experience in real-world defensive security operations.
