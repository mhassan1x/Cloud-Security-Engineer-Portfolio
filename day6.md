# Day 6 – Container Security (Docker & Kubernetes)

## Docker Security Best Practices
- Run as non‑root user.
- Use read‑only root filesystem.
- Drop all capabilities; add only needed ones.
- Scan images for vulnerabilities (Trivy).

## Hands‑On Lab
- Pulled Alpine image.
- Ran container as non‑root (`adduser -D -u 1000 appuser`).
- Tested `--read-only` flag.
- Dropped all capabilities, added only `NET_ADMIN`.
- Scanned `alpine:latest` with Trivy.

## Kubernetes Security Concepts
- Pod Security Standards (Privileged, Baseline, Restricted).
- Network Policies (pod‑to‑pod firewall).
- RBAC (Role‑Based Access Control).
- Secrets Management (K8s Secrets, not env vars).
- Security Context (`runAsNonRoot`, `readOnlyRootFilesystem`).

## Next Steps
- Day 7: SecDevOps – CI/CD Security, Infrastructure as Code Scanning.
