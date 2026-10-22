# PHP2Shell — CVE-2026-109618 & CVE-2026-109619

Plain-English brief and patch runbook for the two critical PHP core vulnerabilities disclosed
**21 October 2026**. Written for people who have to fix a server, not read a paper.

**Read it here: https://nwfella.github.io/php2shell-advisory/**

## What this covers

- Affected and fixed versions for every supported branch (8.2 – 8.5) and the EOL reality below that
- Risk by SAPI: mod_php, PHP-FPM, FrankenPHP, LSAPI, php-cgi
- Patch runbooks: Debian, Ubuntu, RHEL/Alma/Rocky, Alpine, Docker, cPanel/CloudLinux, Plesk, Windows, source
- How to verify the fix actually landed — including the worker-restart check most people skip
- Interim mitigations and, explicitly, why none of them is a fix
- Detection guidance and post-compromise checklist
- What to do if you're stuck on PHP 8.1 or older

## The two-minute version

1. Find every PHP binary that serves HTTP (not just `php -v`).
2. Update to **8.5.12 · 8.4.27 · 8.3.36 · 8.2.35**, or your distro's backported package.
3. **Restart every PHP worker.** A patched package with stale workers is still vulnerable.
4. Set `session.upload_progress.enabled=0` anyway.
5. Can't patch now? Take it off the public internet.

## Notes on sourcing

Every version number, errata ID and advisory quote is taken from the primary sources listed in
section 12 of the page — the PHP advisories and GitHub security advisories, NVD, CERT-EU, and the
Debian, Ubuntu and Red Hat trackers. Vendor state moves; re-check your own tracker.

Corrections welcome — open an issue.

## License

Content and page: MIT. Advisories and quotations remain the property of their respective authors.
Not affiliated with or endorsed by the PHP Group, the PHP Foundation, Wiz, or any vendor named.
