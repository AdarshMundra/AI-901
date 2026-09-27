# AWS SAA-C03 Preparation Guide

## Exam Overview

The AWS Certified Solutions Architect – Associate (SAA-C03) validates your ability to design cost-optimized, resilient, high-performing, and secure architectures on AWS. It is one of the most popular cloud certifications globally.

| Detail | Info |
| --- | --- |
| Exam Code | SAA-C03 |
| Format | 65 questions, multiple choice & multiple response |
| Duration | 130 minutes |
| Passing Score | 720 out of 1000 |
| Cost | $150 USD |
| Validity | 3 years |
| Delivery | Pearson VUE (test center or online proctored) |
| Prerequisites | None (1+ year hands-on experience recommended) |

## Domain Breakdown & Weightage

The exam tests four domains. Design Secure Architectures and Design Resilient Architectures together account for over half the exam.

| Domain | Weight | Key Focus |
| --- | --- | --- |
| 1. Design Secure Architectures | 30% | IAM, encryption, VPC security, compliance, network controls |
| 2. Design Resilient Architectures | 26% | Multi-AZ, DR strategies, decoupling, auto scaling, backups |
| 3. Design High-Performing Architectures | 24% | Compute selection, storage optimization, caching, database scaling |
| 4. Design Cost-Optimized Architectures | 20% | Pricing models, right-sizing, storage tiering, cost allocation |

## 8-Week Study Plan

This plan assumes 1-2 hours of study per day on weekdays and 2-3 hours on weekends. Adjust the pace based on your existing AWS experience.

| Week | Focus Area | Activities |
| --- | --- | --- |
| 1 | IAM & Security Foundations | IAM users, groups, roles, policies (inline vs managed). STS, federation. MFA. Study slides + hands-on in AWS Free Tier |
| 2 | Networking & VPC | VPC, subnets, route tables, IGW, NAT Gateway. Security groups vs NACLs. VPC peering, Transit Gateway, VPC endpoints (gateway vs interface). Build a multi-tier VPC in the console |
| 3 | Compute & Containers | EC2 instance types, placement groups, tenancy. Auto Scaling (target tracking, step, scheduled). ELB types (ALB vs NLB vs GLB). Lambda concurrency. ECS vs EKS vs Fargate |
| 4 | Storage & Data Transfer | S3 storage classes, lifecycle policies, versioning, replication, encryption. EBS volume types (gp3, io2, st1, sc1). EFS vs FSx. Snow Family, DataSync, Transfer Family. Take Practice Test 1 |
| 5 | Databases | RDS Multi-AZ vs Read Replicas. Aurora (global databases, serverless). DynamoDB (partition keys, GSI/LSI, DAX, streams). ElastiCache (Redis vs Memcached). Redshift, Neptune, DocumentDB |
| 6 | Application Integration & Serverless | SQS (standard vs FIFO), SNS, EventBridge, Step Functions. API Gateway throttling. Kinesis (Data Streams vs Firehose). Decoupling patterns. Take Practice Tests 2 & 3 |
| 7 | Monitoring, DR & Cost | CloudWatch (metrics, alarms, logs). CloudTrail. AWS Config. DR strategies (backup/restore, pilot light, warm standby, multi-site). Cost Explorer, Budgets, Savings Plans, Reserved vs Spot instances. Take Practice Tests 4 & 5 |
| 8 | Review & Final Prep | Take Practice Test 6. Review all incorrect answers across tests. Revisit weak domains. Re-read the slide deck sections you struggled with. Rest the day before the exam |

## Core Services Deep Dive

These are the services most heavily tested on the SAA-C03, based on analysis of your six practice tests. Master these before anything else.

### Compute

- **EC2**: Know every instance family purpose (general, compute, memory, storage, accelerated). Understand placement groups (cluster = low latency, spread = fault isolation, partition = large distributed workloads like HDFS/Kafka). Know dedicated hosts vs dedicated instances. Understand hibernation vs stop.
- **Auto Scaling**: Target tracking (simplest, e.g. keep CPU at 50%), step scaling (react to CloudWatch alarms), scheduled (predictable load). Cooldown periods. Launch templates over launch configurations.
- **Lambda**: 15-minute max timeout, 10 GB memory, concurrency limits (reserved vs provisioned). Cold starts. Integration with API Gateway, S3 events, DynamoDB Streams, SQS.
- **ELB**: ALB = HTTP/HTTPS, path/host-based routing, supports Lambda targets. NLB = TCP/UDP, ultra-low latency, static IP. GLB = third-party appliances. Sticky sessions, connection draining, cross-zone load balancing.

### Storage

- **S3**: Storage classes (Standard > IA > One Zone-IA > Glacier Instant > Glacier Flexible > Glacier Deep Archive > Intelligent-Tiering). Lifecycle policies automate transitions. Cross-Region Replication (CRR) vs Same-Region Replication (SRR). S3 Transfer Acceleration. Pre-signed URLs. Bucket policies vs ACLs. Server-side encryption (SSE-S3, SSE-KMS, SSE-C). Event notifications to SNS/SQS/Lambda.
- **EBS**: gp3 (baseline 3000 IOPS, cheapest general purpose), io2 Block Express (up to 256K IOPS, critical databases), st1 (throughput-optimized HDD, big data), sc1 (cold HDD, cheapest). Snapshots are incremental and stored in S3. Multi-attach only for io1/io2.
- **EFS vs FSx**: EFS = managed NFS for Linux. FSx for Windows = SMB protocol, Active Directory. FSx for Lustre = HPC, machine learning. FSx for NetApp ONTAP = multi-protocol.

### Databases

- **RDS**: Multi-AZ = synchronous standby for HA, automatic failover, not for read scaling. Read Replicas = asynchronous, for read scaling, can be cross-region. Up to 15 read replicas for Aurora, 5 for other engines. IAM database authentication.
- **Aurora**: 6 copies of data across 3 AZs. Aurora Serverless for unpredictable workloads. Aurora Global Database for cross-region DR (< 1 second replication). Aurora cloning for testing.
- **DynamoDB**: Single-digit ms latency at any scale. Partition key design is critical. GSI (eventual consistency, any attribute) vs LSI (strong consistency, same partition key, must be created at table creation). DAX = in-memory cache for DynamoDB. DynamoDB Streams for change capture. On-demand vs provisioned capacity.
- **ElastiCache**: Redis = complex data types, replication, persistence, pub/sub. Memcached = simple caching, multi-threaded. Use for session stores, leaderboards, real-time analytics.

### Networking

- **VPC**: Public subnet = route to IGW. Private subnet = route to NAT Gateway for outbound internet. NAT Gateway is AZ-scoped, deploy one per AZ for HA.
- **Security Groups vs NACLs**: SGs are stateful (return traffic auto-allowed), instance-level, allow rules only. NACLs are stateless (must allow both inbound and outbound), subnet-level, allow and deny rules, processed in order.
- **VPC Endpoints**: Gateway endpoints (S3, DynamoDB) = free, route table entry. Interface endpoints (everything else) = ENI with private IP, costs per hour + per GB.
- **Transit Gateway**: Hub-and-spoke to connect thousands of VPCs and on-premises networks. Replaces complex peering meshes. Supports inter-region peering.
- **CloudFront**: Edge caching for static and dynamic content. Origin failover with origin groups. Field-level encryption. OAC (Origin Access Control) for S3.
- **Global Accelerator**: Static anycast IPs, routes traffic to optimal endpoint via AWS backbone. Use for non-HTTP (TCP/UDP) or when you need static IPs and instant regional failover.

### Security

- **IAM**: Least privilege. Policy evaluation: explicit deny > explicit allow > implicit deny. Resource-based policies (S3 bucket policy, SQS queue policy) vs identity-based policies. Cross-account access via roles.
- **KMS**: Customer managed keys vs AWS managed keys. Automatic key rotation (1 year). Envelope encryption (KMS encrypts data key, data key encrypts data). Key policies + IAM policies together control access.
- **WAF**: Layer 7 protection, attach to ALB/CloudFront/API Gateway. Rate-based rules for DDoS. AWS Shield Standard (free, layer 3/4) vs Shield Advanced (paid, DDoS response team).
- **GuardDuty**: Threat detection from VPC Flow Logs, CloudTrail, DNS logs. Macie = S3 data classification (PII detection). Inspector = vulnerability scanning for EC2/ECR/Lambda.

## Key Concepts & Patterns to Memorize

These recurring patterns appear across many exam questions. Recognizing them quickly saves time.

### Architecture Patterns

- **Decoupling**: SQS between tiers absorbs traffic spikes and survives component failures. SNS fans out to multiple SQS queues for parallel processing. EventBridge for event-driven routing with rules.
- **Stateless design**: Store session data in ElastiCache or DynamoDB, not on EC2 instances. This lets Auto Scaling add/remove instances freely.
- **Caching layers**: CloudFront at the edge, ElastiCache in front of the database, DAX in front of DynamoDB. Each reduces load on the tier behind it.
- **Read scaling**: Read Replicas for RDS/Aurora. ElastiCache for repeated queries. CloudFront for static assets. DynamoDB GSI for alternate query patterns.

### Disaster Recovery Strategies (by cost, low to high)

1. **Backup & Restore**: Cheapest. RPO/RTO in hours. S3 cross-region replication, EBS snapshots, RDS automated backups.
2. **Pilot Light**: Core systems always running (e.g., database replication). Scale up compute on failover. RPO minutes, RTO tens of minutes.
3. **Warm Standby**: Scaled-down full copy running in another region. Scale up on failover. RPO seconds, RTO minutes.
4. **Multi-Site Active/Active**: Full production in multiple regions. Route 53 health checks for failover. RPO near-zero, RTO near-zero. Most expensive.

### Migration Strategies (the 7 Rs)

1. **Retire** — decommission
2. **Retain** — keep on-premises for now
3. **Rehost** — lift and shift (AWS Application Migration Service)
4. **Relocate** — move to AWS without changes (VMware Cloud on AWS)
5. **Repurchase** — move to SaaS
6. **Replatform** — lift, tinker, shift (e.g., move MySQL to RDS MySQL)
7. **Refactor/Re-architect** — redesign for cloud-native

### Cost Optimization Cheat Sheet

- **EC2 pricing**: On-Demand > Reserved (1 or 3 year, up to 72% off) > Savings Plans (flexible across instance families) > Spot (up to 90% off, can be interrupted)
- **S3 cost reduction**: Lifecycle policies to move old data to Glacier. Intelligent-Tiering for unpredictable access. S3 Select/Glacier Select to retrieve only needed data.
- **Data transfer**: Transfer within the same AZ is free. Cross-AZ costs money. VPC endpoints avoid NAT Gateway data processing charges for S3/DynamoDB.
- **Right-sizing**: Use AWS Compute Optimizer and Cost Explorer recommendations. Graviton (ARM) instances are cheaper for compatible workloads.

### Encryption Rules

- **At rest**: S3 (SSE-S3 default, SSE-KMS for audit trail, SSE-C for client-managed keys). EBS volumes encrypted via KMS. RDS encryption must be enabled at creation (encrypt an unencrypted DB by creating an encrypted snapshot copy, then restore).
- **In transit**: TLS everywhere. ACM (Certificate Manager) for free public certificates on ALB/CloudFront/API Gateway. Between VPCs use VPC peering or Transit Gateway (traffic stays on AWS backbone).
- **Key point**: An encrypted RDS snapshot shared cross-account must use a customer-managed KMS key (not the default AWS key).

## Practice Test Analysis

Your six practice tests (~65 questions each, ~390 questions total) cover the full SAA-C03 exam scope. Here are the most heavily tested services and the patterns to watch for.

### Top 10 Most Tested Services

| Rank | Service | What to Know Cold |
| --- | --- | --- |
| 1 | EC2 | Instance types, placement groups, tenancy, hibernation, Auto Scaling policies |
| 2 | S3 | Storage classes, lifecycle rules, replication, encryption options, bucket policies, event notifications |
| 3 | RDS & Aurora | Multi-AZ vs Read Replicas, Aurora Global Database, IAM auth, encryption of unencrypted databases |
| 4 | IAM | Policy evaluation logic, cross-account roles, resource vs identity policies, federation |
| 5 | VPC & Networking | Subnets, SG vs NACL, VPC endpoints (gateway vs interface), peering vs Transit Gateway |
| 6 | ELB (ALB/NLB) | Routing rules, health checks, cross-zone, sticky sessions, security group configuration |
| 7 | Lambda | Concurrency, timeout limits, event source mappings, integration with API Gateway and S3 |
| 8 | CloudFront | Origin failover, OAC, field-level encryption, cache behaviors |
| 9 | SQS & SNS | Standard vs FIFO, visibility timeout, dead-letter queues, fan-out pattern with SNS + SQS |
| 10 | DynamoDB | Partition key design, GSI vs LSI, DAX, Streams, on-demand vs provisioned |

### Common Exam Traps

- **CloudFront vs Global Accelerator**: CloudFront caches content at the edge (HTTP). Global Accelerator routes TCP/UDP traffic over the AWS backbone without caching. Questions will try to make you pick the wrong one.
- **Multi-AZ vs Read Replica**: Multi-AZ is for availability (automatic failover, no reads served). Read Replicas are for performance (serve read traffic, manual promotion). Many questions blur this line.
- **Gateway Endpoint vs Interface Endpoint**: S3 and DynamoDB use gateway endpoints (free, route table). Everything else uses interface endpoints (ENI, costs money). Questions often test this distinction.
- **SQS Standard vs FIFO**: Standard = unlimited throughput, at-least-once, best-effort ordering. FIFO = 300 msg/s (3000 with batching), exactly-once, strict ordering. Choose based on the question's requirement for ordering or deduplication.
- **Stateful vs Stateless**: If a question mentions session data on EC2 instances and asks about scaling, the answer almost always involves moving sessions to ElastiCache or DynamoDB.

### How to Use Your Practice Tests

1. Take each test timed (130 minutes, no notes) to simulate exam conditions
2. Score yourself, then read every explanation — even for questions you got right
3. Track wrong answers by domain to identify your weakest areas
4. Re-take tests 1-3 in week 8 to measure improvement
5. Any topic you get wrong twice across different tests deserves focused study

## Exam Day Tips & Strategy

- **Time management**: 130 minutes for 65 questions = 2 minutes per question. Flag difficult questions and come back to them. Do not spend more than 3 minutes on any single question in the first pass.
- **Elimination method**: Most questions have two obviously wrong answers and two plausible ones. Eliminate the two wrong answers first, then reason about the remaining pair.
- **Read the ask carefully**: "Most cost-effective" and "best performance" lead to very different answers for the same scenario. The qualifying phrase is usually in the last sentence.
- **"Least operational overhead"**: This phrase almost always points toward managed/serverless services (Aurora Serverless, Fargate, Lambda, DynamoDB) over self-managed alternatives.
- **"Minimal changes"**: Favor solutions that modify the least infrastructure. A rehost is less change than a refactor. Adding a Read Replica is less change than re-architecting the database layer.
- **When two answers seem correct**: Pick the one that is more specific to the scenario. AWS prefers the simplest architecture that meets all stated requirements — nothing more.
- **Non-English speakers**: You can request an extra 30 minutes as an ESL accommodation through your AWS Certification account before scheduling.
- **Before you submit**: Use remaining time to review flagged questions. Change answers only if you have a clear reason — your first instinct is usually correct.
