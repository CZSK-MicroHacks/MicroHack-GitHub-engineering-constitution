# Service Runbooks

This document contains operational procedures for maintaining the service in production.

## On-Call Quick Reference
- **PagerDuty Service**: [Link]
- **Critical Dashboards**: [Link]
- **Logs**: [Link]

## Common Incidents

### High Latency / 429 Errors
**Symptoms**:
- Alert `HighLatency` fires.
- Users report slow loading.

**Diagnosis**:
1. Check dependency health (see `contracts/consumers.md`).
2. Check database CPU usage.

**Mitigation**:
- [ ] Scale up replicas if CPU is high.
- [ ] Enable circuit breaker if dependency is failing.

### Failed Deployment
**Symptoms**:
- Smoke tests failing after rollout.

**Mitigation**:
- [ ] Execute rollback pipeline: `[Link to Job]`

## Maintenance Tasks

### Rotating Secrets
1. Generate new key in KeyVault.
2. Update configuration `SERVICE_API_KEY`.
3. Restart service.

### Data Backfill
*Instructions for re-processing events...*
