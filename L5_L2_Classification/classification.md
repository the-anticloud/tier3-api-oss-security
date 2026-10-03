# L5 Narrow / L2 General Classification — api-oss-security
**Platform:** Anticloud | **PAX:** 27B | **IP:** USPTO pending 2026, Anticloud FZ LLE
**Domain:** Sovereign security scanning: SAST, dependency audit, secrets detection for Anticloud

## L5 Narrow
api-oss-security specializes in sovereign security scanning: sast, dependency audit, secrets detection for anticloud within the Anticloud sovereign deployment boundary. All operations stay local — no cloud services, no external APIs, no data exfiltration. The narrow scope ensures deterministic, auditable behavior that PAX 27B can reason about precisely.

## L2 General
L2 General means api-oss-security is available to all 9 Anticloud tiers without per-tier configuration. The same API serves hospital, defense, robotics, and research deployments.

## PAX Integration
PAX 27B provides remediation guidance: given a bandit or safety finding, PAX generates the specific code fix and explains the security impact in context.

## AIOSS Audit Relevance
Every security scan result (target hash + findings hash + severity counts + remediation suggestions hash) is AIOSS-chained: H_n = SHA3-256(H_{n-1} || entry_hash_n || timestamp_n).
Tamper-evident, offline-verifiable, zero cloud dependency.

## Regulatory / Compliance
OWASP Top 10, NIST SP 800-53 SA-11 (developer security testing), CWE/CVE
