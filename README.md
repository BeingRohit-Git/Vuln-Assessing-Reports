<div align="center">

# 🛡️ Vulnerability Assessment & Penetration Testing Reports

<img src="https://img.shields.io/badge/Security-Testing-FF4B4B?style=for-the-badge&logo=security&logoColor=white" alt="Security Testing" />
<img src="https://img.shields.io/badge/Web_App-Sec-0077B5?style=for-the-badge&logo=owasp&logoColor=white" alt="Web App Sec" />
<img src="https://img.shields.io/badge/Network-Recon-000000?style=for-the-badge&logo=linux&logoColor=white" alt="Network Recon" />

<p align="center">
  A curated collection of professional vulnerability assessment reports demonstrating practical experience in network reconnaissance, web application security testing, and vulnerability documentation.
</p>

</div>

---

## ⚠️ Legal & Ethical Disclaimer
**All assessments documented in this repository were conducted strictly on publicly authorized, intentionally vulnerable environments specifically designed for security testing and educational purposes.** No unauthorized systems, networks, or applications were targeted or exploited. 

---

## 🛠️ Tools & Technologies Utilized

The following industry-standard tools were utilized across these assessments for traffic interception, enumeration, and automated/manual exploitation:

* **Web Proxy & Interception:** Burp Suite Professional
* **Network Reconnaissance:** Nmap, Wireshark
* **Vulnerability Scanners:** Nikto
* **Exploitation Frameworks:** SQLmap
* **Methodologies:** OWASP Top 10, CVSS v3.1 Scoring

---

## 📑 Assessment Reports Index

Below is the index of the completed vulnerability assessment reports. Click on the report names to view the full technical documentation, Proof of Concepts (PoCs), and remediation strategies.

### 1. [Web Application Security: Error-Based SQL Injection (SQLi)](./VA_Report_TestPHP_SQLi.md)
* **Target:** Acunetix Intentionally Vulnerable Web Application (`testphp.vulnweb.com`)
* **Vulnerability:** Critical (CVSS 9.8) - Error-Based SQL Injection
* **Summary:** Identified and exploited an unauthenticated SQL injection vulnerability allowing direct interaction with the backend MySQL database. Demonstrated database enumeration using SQLmap and provided remediation steps for implementing parameterized queries.

### 2. [Network Infrastructure Reconnaissance & Vulnerability Scan](./VA_Report_ScanMe_Nmap.md)
* **Target:** Nmap Security Testing Subnet (`scanme.nmap.org`)
* **Vulnerability:** Medium / Low - Cleartext Protocols & Information Disclosure
* **Summary:** Conducted comprehensive network reconnaissance identifying exposed TCP ports and outdated web server services (Apache 2.4.7). Documented the risks of unencrypted HTTP traffic and server header leakage, providing hardening recommendations.

### 3. [Web Application Security: Reflected Cross-Site Scripting (XSS)](./VA_Report_AltoroMutual_XSS.md)
* **Target:** Altoro Mutual Banking Portal (`demo.testfire.net`)
* **Vulnerability:** Medium (CVSS 6.1) - Reflected XSS
* **Summary:** Identified a failure to sanitize user input in a search parameter, allowing the execution of malicious JavaScript within the victim's browser context. Detailed the potential for session hijacking and recommended strict output encoding.

---

## 👨‍💻 About the Assessor

**Rohit Bhosale**
* Cybersecurity Enthusiast & Full-Stack Developer
* **Connect:** [LinkedIn](https://www.linkedin.com/in/rohitbhosale6)
