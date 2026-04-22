# Day 8 – Cloud Disaster Recovery (DR)

## Key Concepts
- **RTO** (Recovery Time Objective) – max downtime allowed.
- **RPO** (Recovery Point Objective) – max data loss allowed.
- **SLA** – service level agreement.

## DR Strategies
- Backup & Restore (cheapest, slowest)
- Pilot Light (medium)
- Warm Standby (high)
- Multi‑Site (expensive, fastest)

## DR Plan Example
Designed a DR plan for a web app (S3, EC2, RDS) with RTO=2h, RPO=30min:
- RDS automated snapshots + cross‑region replication.
- Pilot Light EC2 in secondary region.
- S3 cross‑region replication.
- Route 53 failover with health checks.

## Cost Estimation
Used AWS Pricing Calculator to compare strategies. Backup & Restore is cheapest; Multi‑Site is costliest.

## Hands‑On
Created and restored an EBS snapshot to practice Backup & Restore.

## DR Plan Design

I designed a complete DR plan for a web application (S3, EC2, RDS, Route 53) with RTO=2h and RPO=30min.

👉 [View the full DR Plan](dr-plan-webapp.md)

## Next Steps
- Day 9: Cloud Auditing Tools (Prowler, ScoutSuite, Vulnerability Assessment).
