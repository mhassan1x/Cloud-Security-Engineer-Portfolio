# Day 10 – Cloud Security Automation (EventBridge + Lambda)

## Why Automation?
- Speed, consistency, reduces human error.
- Auto‑remediate common issues like public S3 buckets.

## Hands‑On Lab
- Created IAM role for Lambda with S3 permissions.
- Wrote a Python Lambda function that:
  - Lists all S3 buckets.
  - Checks ACL for `AllUsers` (public‑read).
  - Changes the bucket to `private` if found.
- Tested with a public bucket – successfully fixed.
- Scheduled the function to run hourly via EventBridge.

## Code Snippet
```python

import boto3

def lambda_handler(event, context):
    s3 = boto3.client('s3')
    
    # List all buckets
    buckets = s3.list_buckets()['Buckets']
    
    fixed_buckets = []
    for bucket in buckets:
        bucket_name = bucket['Name']
        try:
            # Get bucket ACL
            acl = s3.get_bucket_acl(Bucket=bucket_name)
            # Check if any grantee has public-read permission
            for grant in acl['Grants']:
                if 'URI' in grant['Grantee'] and 'AllUsers' in grant['Grantee']['URI']:
                    # Change to private
                    s3.put_bucket_acl(Bucket=bucket_name, ACL='private')
                    fixed_buckets.append(bucket_name)
                    print(f"Fixed public bucket: {bucket_name}")
                    break
        except Exception as e:
            print(f"Error processing {bucket_name}: {e}")
    
    return {
        'statusCode': 200,
        'body': f'Fixed buckets: {fixed_buckets}'
    }
```
## Next Steps
- Day 11: Compliance (GDPR, HIPAA) and Incident Reporting.
