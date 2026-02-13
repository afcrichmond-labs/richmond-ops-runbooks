# Incident Response: ALB / Load Balancer Issues

**Owner:** Will Kitman (DevOps)
**Last Updated:** 2026-01-27

## When to Use
When ALB health checks fail or listener rules are misconfigured.

## Quick Diagnosis
1. Check ALB target group health: `aws elbv2 describe-target-health`
2. Check listener rules: `aws elbv2 describe-rules`
3. Check recent Terraform applies: `terraform show`

## Rollback Procedure
1. Identify last known good Terraform state
2. Run `terraform plan` to verify expected changes
3. Run `terraform apply` with explicit approval
4. Verify health checks recover

## Prevention
- Always pin Terraform provider versions
- Run `terraform plan` diff validation in CI
- Never apply Terraform changes outside CI/CD
