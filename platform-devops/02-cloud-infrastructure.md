# Cloud Infrastructure and Platform Architecture

Choose infrastructure according to workload, resilience, security, team capability, and total operating cost.

## Core design concerns

- Identity and least-privilege access.
- Network segmentation and private connectivity.
- Secrets and key management.
- Compute, storage, database, and queue lifecycle.
- Availability zones/regions and recovery strategy.
- Encryption, backup, retention, and deletion.
- Monitoring, cost allocation, and ownership.

## Containers and orchestration

Containers improve packaging consistency, but orchestration introduces scheduling, networking, storage, upgrades, and operational complexity. Use a managed platform or simpler compute where it meets requirements. Kubernetes is not a default prerequisite for a web application.

## Infrastructure as code

Keep infrastructure definitions version-controlled, reviewed, tested, and reproducible. Separate plan from apply, restrict production permissions, protect state, and detect drift. Avoid unmanaged console changes.

## Resilience and recovery

Define RTO (recovery time objective) and RPO (recovery point objective) per business capability. Multi-zone deployment does not protect against every regional, account, data, or operator failure. Test restore and failover procedures.

## Cost management

Tag or attribute resources to teams and products. Monitor idle capacity, data transfer, storage growth, log volume, and managed-service pricing. Use budgets and anomaly alerts. Optimize cost without violating reliability or security requirements.

## Checklist

- [ ] Identity and network boundaries are explicit.
- [ ] Infrastructure is reproducible as code.
- [ ] Secrets and encryption keys are managed securely.
- [ ] RTO/RPO are defined and tested.
- [ ] Cost ownership and budgets exist.
- [ ] Resource lifecycle and decommissioning are planned.
