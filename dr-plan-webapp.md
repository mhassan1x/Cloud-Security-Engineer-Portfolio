# Disaster Recovery Plan – Simple Web Application

**Application Name:** MyWebApp  
**RTO:** 2 hours  
**RPO:** 30 minutes  
**Primary Region:** us-east-1 (N. Virginia)  
**DR Region:** us-west-2 (Oregon)  
**Date:** [22-April-2026] 

## Components and Recovery Strategies

### 1. S3 (Static Files)
- **Risk:** Accidental deletion or region outage.
- **DR Strategy:** Cross-Region Replication (CRR).
- **RPO:** Near zero (replication happens in minutes).
- **RTO:** Near zero (files already exist in DR region; just update CloudFront origin).

### 2. EC2 (Web Servers)
- **Risk:** Instance failure or region outage.
- **DR Strategy:** Pilot Light.
- **How:** Keep one small EC2 instance (t2.micro) running in DR region with the application code pre-installed. On disaster, scale up to full capacity using a launch template.
- **RTO:** ~20 minutes (to launch additional instances).
- **RPO:** Not applicable (stateless servers).

### 3. RDS (Database)
- **Risk:** Data corruption or region outage.
- **DR Strategy:** Automated snapshots + cross-region copy + binary logs.
- **How:** Take automated snapshots every 60 minutes, copy them to DR region. Enable binary logging for point-in-time recovery.
- **RTO:** ~45 minutes (restore snapshot and apply logs).
- **RPO:** Up to 30 minutes (restore to a point just before disaster).

### 4. Route 53 (DNS)
- **Risk:** Primary endpoint becomes unhealthy.
- **DR Strategy:** Failover routing with health checks.
- **How:** Create failover record. Primary points to load balancer in us-east-1; secondary points to DR region. Health check monitors primary; on failure, traffic automatically routes to secondary.
- **RTO:** Seconds (automatic).
- **RPO:** 0 (no data loss).

- ## Recovery Procedure (When Primary Region Fails)

1. **DNS fails over automatically** – Route 53 detects health check failure and switches traffic to DR region within 90 seconds.

2. **Restore the database in DR region**:
   - Go to RDS console in us-west-2.
   - Find the latest snapshot (copied from primary).
   - Restore snapshot to a new RDS instance.
   - Apply binary logs to recover up to 30 minutes before failure.
   - Estimated time: 45 minutes.

3. **Scale up the web servers**:
   - In EC2 (us-west-2), use the pre-configured launch template.
   - Launch an Auto Scaling group with 2–3 instances.
   - Attach to the DR region load balancer.
   - Estimated time: 20 minutes.

4. **Update CloudFront origin** (if S3 is used):
   - Change CloudFront origin to the DR S3 bucket (already replicated).
   - Estimated time: 5 minutes.

5. **Verify application is working**:
   - Test the DR endpoint (or use Route 53 domain).
   - Estimated time: 5 minutes.

**Total estimated recovery time:** ~75 minutes (well within 2-hour RTO).

## Testing and Maintenance

- **Quarterly tabletop exercise** – Review the plan with the team.
- **Annual live failover test** – During low traffic hours, manually fail over to DR region and measure actual RTO/RPO.
- **Monitor replication** – Check S3 CRR and RDS snapshot copy status weekly.
- **Update AMIs** – Rebuild the pilot light EC2 instance every month with latest security patches.
