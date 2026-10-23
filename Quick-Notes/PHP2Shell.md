# PHP2Shell: Critical PHP Vulnerabilities (CVE-2026-109618 & CVE-2026-109619)
**Date of news:** 2026-10-20

- **What happened:** The PHP project just released emergency patches for "PHP2Shell," two critical vulnerabilities that allow attackers to remotely execute code and take full control of web servers without needing a password. 
- **New Concepts & Root Cause:** I learned about low-level memory vulnerabilities like **Use-After-Free (UAF)** and **Out-of-Memory (OOM)** corruption. The root cause is PHP mismanaging server memory. By intentionally forcing PHP to crash (OOM) or tricking it during a file upload (UAF), attackers confuse the server's internal cleanup routine, causing it to accidentally execute malicious code instead of throwing bad data away.
- **Remediation:** Because the flaw is in the core engine itself, updating a website's CMS (like WordPress) won't protect you. You must patch the core PHP engine directly on the server. If patching is delayed, strict Web Application Firewall (WAF) rules are required to block the malicious uploads.
- **Why it caught my attention:** PHP powers nearly 70% of the internet, so the blast radius is massive. What's crazier is that attackers began attempting to exploit this four days *before* the vulnerabilities were publicly disclosed. 
- **The Takeaway:** The window between a vulnerability being discovered and it being actively exploited is shrinking to zero. Defense-in-depth and rapid incident response are mandatory because you can no longer just wait for the official patch to drop.

**Source:** [Tenable Research: PHP2Shell FAQ](https://www.tenable.com/blog/php2shell-cve-2026-109618-cve-2026-109619-frequently-asked-questions-about-critical-php-remote)

## Concept Breakdown: Memory Vulnerabilities
To understand this attack, you need to understand two core memory concepts:
* **Use-After-Free (UAF):** Think of server memory like a hotel room. UAF happens when a program "checks out" (frees memory) but accidentally keeps the room key (a pointer). An attacker can use that old key to access the space and inject malicious code.
* **Out-of-Memory (OOM) Corruption:** When a server is pushed past its memory limits, it panics and aborts its current task. If an attacker intentionally triggers this panic at the exact right moment, the server's emergency cleanup routine gets confused by half-finished data, creating a loophole for exploitation.
