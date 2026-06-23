# Network Infrastructure Vulnerability Assessment

**Date of Assessment:** June 23, 2026  
**Target Organization:** Nmap Security Testing Subnet  
**Target IP/Domain:** `scanme.nmap.org` (45.33.32.156)  
**Assessor:** Rohit Bhosale
**Assessment Type:** Network Reconnaissance and Infrastructure Scanning  

---

## 1. Executive Summary
A proactive vulnerability assessment and network reconnaissance scan were executed against `scanme.nmap.org`. The objective was to identify exposed attack surfaces, open ports, and outdated services running on the perimeter infrastructure. The assessment identified exposed ports running cleartext protocols (HTTP) and SSH services, alongside web server version disclosure. While no critical Remote Code Execution (RCE) vulnerabilities were discovered, hardening recommendations are provided to improve the overall security posture and reduce the external attack surface.

## 2. Scope and Methodology
* **In-Scope Target:** `scanme.nmap.org`
* **Tools Utilized:** Nmap, Nikto
* **Methodology:**
  1. Host discovery and comprehensive TCP port scanning.
  2. Service version detection and OS fingerprinting to identify legacy software.
  3. Web server configuration vulnerability scanning utilizing Nikto.

---

## 3. Detailed Findings

### 3.1. Cleartext Communication Protocol (HTTP)
* **Severity:** Medium
* **Port/Service:** Port 80 / TCP (HTTP)

#### 3.1.1. Vulnerability Description
The target server is exposing port 80 running an Apache web server without enforcing encryption. Traffic transmitted over HTTP is sent in cleartext, meaning any data transmitted (including potential administrative credentials, API keys, or sensitive session tokens) is susceptible to interception and packet sniffing via Man-in-the-Middle (MITM) attacks. 

#### 3.1.2. Proof of Concept (PoC)

**Nmap Version Scan:**
```bash
nmap -sV -p 80 scanme.nmap.org
```

*Terminal Output:*
```text
Starting Nmap 7.93 ( [https://nmap.org](https://nmap.org) ) 
Nmap scan report for scanme.nmap.org (45.33.32.156)
Host is up (0.045s latency).

PORT   STATE SERVICE VERSION
80/tcp open  http    Apache httpd 2.4.7 ((Ubuntu))
```

### 3.2. Outdated Web Server Information Disclosure
* **Severity:** Low
* **Port/Service:** Port 80 / TCP (HTTP)

#### 3.2.1. Vulnerability Description
A vulnerability scan revealed that the web server's HTTP response headers explicitly disclose the exact version of the Apache server (`Apache/2.4.7`) and the underlying operating system (`Ubuntu`). This information disclosure severely reduces the time and effort required for an attacker to profile the infrastructure and search for specific Common Vulnerabilities and Exposures (CVEs) related to this legacy software.

#### 3.2.2. Proof of Concept (PoC)

**Nikto Vulnerability Scan:**
```bash
nikto -h [http://scanme.nmap.org](http://scanme.nmap.org)
```

*Terminal Output:*
```text
- Nikto v2.1.6
---------------------------------------------------------------------------
+ Target IP:          45.33.32.156
+ Target Hostname:    scanme.nmap.org
+ Target Port:        80
+ Start Time:         2026-06-23
---------------------------------------------------------------------------
+ Server: Apache/2.4.7 (Ubuntu)
+ Server may leak inodes via ETags, header found with file /, inode: 147, size: 54c22b9bcbbbc, mtime: gzip
+ Allowed HTTP Methods: GET, HEAD, POST, OPTIONS 
```

---

## 4. Remediation Recommendations
1. **Enforce HTTPS (TLS Encryption):** Deprecate cleartext HTTP. Redirect all traffic on port 80 to port 443 (HTTPS) to ensure all data in transit is encrypted using TLS 1.2 or TLS 1.3. Procure and install a valid SSL/TLS certificate.
2. **Server Header Obfuscation:** Reconfigure the Apache web server to limit the amount of version information disclosed to the public. Modify the `apache2.conf` file with the following directives:
   * `ServerTokens Prod`
   * `ServerSignature Off`
3. **Patch Management Program:** The identified Apache version (2.4.7) is significantly outdated. Upgrade the Ubuntu host and the Apache service to their latest stable releases to mitigate known CVEs associated with legacy versions.
