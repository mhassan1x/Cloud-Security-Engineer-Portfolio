# Day 9 – Cloud Auditing Tools & Incident Response

## Auditing Concepts
- CIS Benchmarks, NIST, PCI‑DSS – frameworks for security configuration.
- Prowler and ScoutSuite automate auditing via read‑only API calls.

## Hands‑On Lab
- Installed and ran Prowler in AWS CloudShell.
- Generated an HTML report with CIS benchmark results.
- (Optional) Ran ScoutSuite for a second perspective.
- Learned that many best‑practice checks fail in a lab account – that's normal.

## Incident Response Basics
- Four phases: Preparation, Detection, Containment, Eradication & Recovery.
- Cloud benefits: quick IAM revocation, network isolation, forensic snapshots.

## Example IR Scenario
*If an IAM access key is leaked:*  
1. **Detection** – GuardDuty alerts on anomalous API calls.  
2. **Containment** – Immediately deactivate the key and rotate it.  
3. **Eradication** – Determine what the attacker accessed via CloudTrail logs.  
4. **Recovery** – Restore any tampered resources from backup.

## Next Steps
- Day 10: Cloud Security Automation (EventBridge + Lambda).
