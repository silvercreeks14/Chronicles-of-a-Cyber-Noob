# PHP2Shell Update: Active Exploitation & CISA KEV Addition 

- **What happened:** Less than a week after the "PHP2Shell" vulnerabilities (CVE-2026-109618 & CVE-2026-109619) were patched, CISA confirmed they are being actively exploited in the wild. As a result, CISA added them to the Known Exploited Vulnerabilities (KEV) catalog on October 26 and issued a rare, extremely short deadline of October 29 for all federal agencies to apply the patches or take systems offline.
- **Why it matters:** The KEV catalog is the government's "Most Wanted" list for active threats. The fact that PHP2Shell went from disclosure to active, real-world exploitation in under a week highlights why relying on standard monthly patch cycles is no longer sufficient. 
- **The Takeaway:** A vulnerability's lifecycle is shrinking. The moment an exploit enters the KEV, organizations must pivot from scheduled maintenance to emergency incident response. If you didn't patch PHP2Shell immediately upon release, you must now assume your environment may have already been breached and begin hunting for leftover web shells or backdoors. 

**Source:** [CISA Alert: Critical Vulnerabilities in PHP Require Immediate Patching](https://www.cisa.gov/news-events/alerts/2026/10/21/critical-vulnerabilities-php-require-immediate-patching)
