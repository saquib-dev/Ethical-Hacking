# Module 19: Reporting and Documentation Examples

## 1. Example Executive Summary

**Overall Risk Assessment:** **Critical**

During the penetration test of the GlobalCorp network environment, the assessment team successfully compromised the external web server and pivoted into the internal Active Directory domain. The attack path culminated in full Domain Administrator privileges, granting the team total control over all domain resources, including sensitive customer databases.

**Key Findings:**
1. **Critical:** Unauthenticated Remote Code Execution on `web.globalcorp.local` via vulnerable Apache Struts instance.
2. **High:** Kerberoastable service account with weak password complexity allowing internal network privilege escalation.
3. **Medium:** Lack of network segmentation between the DMZ and internal domain controllers.

**Strategic Recommendations:**
- Implement a comprehensive patch management strategy for external-facing assets.
- Enforce a strict minimum length of 15 characters for all Active Directory service accounts.
- Restrict traffic between the DMZ and internal network to only essential ports and services.

---

## 2. Example Technical Finding

**Title:** Unauthenticated Remote Code Execution via Apache Struts (CVE-2017-5638)
**Severity:** Critical
**CVSS Score:** 10.0

**Description:**
The application hosted at `web.globalcorp.local` is running an outdated version of Apache Struts (2.3.31). This version is vulnerable to CVE-2017-5638, allowing an unauthenticated remote attacker to execute arbitrary OS commands by sending a maliciously crafted HTTP `Content-Type` header.

**Proof of Concept (PoC):**
1. The attacker sends the following HTTP request containing the OGNL payload in the `Content-Type` header:
   ```http
   GET /login.action HTTP/1.1
   Host: web.globalcorp.local
   Content-Type: %{(#_='multipart/form-data')...(#cmds={'whoami'})...}
   ```
2. The server processes the payload and returns the output of the `whoami` command in the response body.
   *(Insert Screenshot showing HTTP request and response with 'nt authority\system')*

**Impact:**
An attacker can completely compromise the web server, read or modify sensitive data, and use the server as a pivot point to attack the internal network.

**Remediation:**
Update Apache Struts to version 2.3.32 or 2.5.10.1 immediately. Additionally, implement a Web Application Firewall (WAF) to detect and block malicious OGNL expressions.
