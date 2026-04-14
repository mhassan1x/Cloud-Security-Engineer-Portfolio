# Day 2 – Linux Permissions & IAM (RBAC vs ABAC)

## Linux Permissions Learned
- `chmod 600` – private file (owner read/write)
- `chmod 644` – public readable file
- `chmod 755` – executable for owner, read/exec for others
- `umask` – default permission mask

## IAM Concepts
- RBAC: Permissions tied to roles. Example: `S3ReaderRole` can list buckets.
- ABAC: Permissions tied to tags. Example: user tag `project=alpha` accesses bucket `alpha`.

## Lab Completed
- Created an IAM policy and role (RBAC).
- Understood ABAC policy structure.
- Attached/detached a policy to my IAM user.
