# Day 7 – SecDevOps: CI/CD Security, IaC Scanning, Secrets Management

## Concepts
- Security as Code – policies and tests automated in pipelines.
- Shift Left – find vulnerabilities early.
- CI/CD pipeline security: static analysis for IaC (tfsec), container scanning (Trivy).

## Hands‑On Lab
- Created a GitHub repository with a Terraform file (public S3 bucket) and a Dockerfile.
- Added GitHub Actions workflow using `tfsec` and `trivy-action`.
- Pipeline failed due to insecure Terraform configuration (`acl = "public-read"`).
- Fixed to `private` and pipeline passed.
- Learned about GitHub Secrets (store API keys, etc.) and AWS Secrets Manager.

## Secrets Management
- Never hardcode secrets in code.
- Use GitHub Secrets for CI/CD variables.
- Use AWS Secrets Manager for application secrets (database passwords, API keys) with KMS encryption and rotation.

## Next Steps
- Day 8: Cloud Disaster Recovery (DR) strategies, RTO/RPO, DR plan.
