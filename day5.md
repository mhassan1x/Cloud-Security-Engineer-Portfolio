# Day 5 – Data Lifecycle, Encryption, and AWS KMS

## Data Lifecycle
- Create, Store, Use, Share, Archive, Destroy.
- Security controls for each stage.

## Encryption Types
- **At rest** – S3 SSE, EBS encryption.
- **In transit** – TLS.
- **In use** – Confidential computing (advanced).

## Hands-On Lab
- Created a symmetric KMS key.
- Encrypted a file using AWS CLI (`aws kms encrypt`).
- Decrypted the file (`aws kms decrypt`).
- Scheduled key deletion.

## Key Takeaway
- KMS is the foundation for encryption in AWS.
- Always encrypt sensitive data at rest and in transit.
- Manage key permissions carefully (least privilege).

## Next Steps
- Day 6: Container Security (Docker, Kubernetes basics).
