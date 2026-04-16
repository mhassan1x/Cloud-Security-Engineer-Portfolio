# Day 4 – DDoS Protection, AWS WAF, and Cloud Security Standards

## DDoS Protection
- **AWS Shield Standard** – free, automatic, protects against layer 3/4 attacks.
- **AWS Shield Advanced** – paid, adds layer 7 protection, cost protection, 24/7 DRT.
- **AWS WAF** – web application firewall, blocks SQLi, XSS, rate limiting, geo-blocking.

## Hands-On Lab
- Created S3 bucket with static website.
- Created CloudFront distribution with S3 origin.
- Created WAF web ACL with SQL injection protection rule.
- Attached WAF to CloudFront and verified blocking.

## Cloud Security Standards
- **ISO/IEC 27017** – cloud-specific controls for providers and customers.
- **ISO/IEC 27018** – protection of PII in public clouds.
- **NIST SP 800-144** – US government guidelines for public cloud security.

## Next Steps
- Day 5: Data Lifecycle, Encryption, and Key Management (KMS).
