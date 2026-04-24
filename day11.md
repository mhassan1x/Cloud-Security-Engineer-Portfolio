# Day 11 – Cloud Compliance, Incident Reporting, Audits

## Compliance Frameworks

### GDPR
- Protects personal data of EU residents.
- Right to be forgotten, 72‑hour breach notification, privacy by design.

### HIPAA
- Protects US health data (PHI).
- Requires technical safeguards, BAAs, breach notification within 60 days.

### PCI‑DSS
- Protects payment card data.
- Requires encryption, access restriction, regular scans.

## Incident Reporting Example
Scenario: Public S3 bucket exposed customer emails for 24 hours.
- Determine jurisdiction (EU residents?) → GDPR applies.
- Count affected records, notify authority within 72 hours.
- Remediate access, inform customers.

## Compliance Audits
- Internal: run Prowler, track findings.
- External: SOC2, ISO 27001.
- AWS Artifact portal provides AWS compliance reports.

## Next Steps
- Day 12: Certification Prep (CCSP, CCSK, AWS Security Specialty).
