# AWS SAA-C03 — Detailed Weekly Study Plan

Each week includes daily topics, learning objectives, hands-on labs, and review checkpoints. Weekdays assume 1-2 hours, weekends 2-3 hours.

---

## Week 1: IAM & Security Foundations

### Day 1 (Mon) — IAM Core Concepts
- IAM users, groups, and roles — when to use each
- Root account security: enable MFA, do not use for daily tasks
- IAM policies: JSON structure (Effect, Action, Resource, Condition)
- Difference between inline policies and managed policies (AWS-managed vs customer-managed)
- **Key takeaway**: Groups cannot be nested. Policies attach to groups, not users whenever possible.

### Day 2 (Tue) — IAM Policies Deep Dive
- Policy evaluation logic: explicit Deny > explicit Allow > implicit Deny
- Identity-based policies vs resource-based policies
- Permission boundaries — limit the maximum permissions a role/user can have
- AWS Organizations SCPs — deny-only guardrails across accounts
- **Practice**: Write a policy that allows S3 read-only access to a single bucket

### Day 3 (Wed) — IAM Roles & Federation
- Roles for EC2 instances (instance profiles) — never embed credentials
- Cross-account access with AssumeRole
- AWS STS: temporary credentials, session tokens
- Federation: SAML 2.0 with corporate IdP, Web Identity Federation with Cognito
- AWS SSO (IAM Identity Center) for multi-account access
- **Key takeaway**: Roles are always preferred over long-term access keys

### Day 4 (Thu) — Encryption & KMS
- Encryption at rest vs in transit
- KMS: customer managed keys (CMK), AWS managed keys, AWS owned keys
- Envelope encryption: KMS encrypts data key, data key encrypts data
- Key policies + IAM policies together control access to keys
- Key rotation: automatic (every year) vs manual
- **Practice**: Create a KMS key in the console, encrypt/decrypt a file using AWS CLI

### Day 5 (Fri) — Security Services Overview
- AWS CloudTrail — API call logging (management events vs data events)
- AWS Config — resource configuration history and compliance rules
- Amazon GuardDuty — threat detection from VPC Flow Logs, CloudTrail, DNS
- Amazon Inspector — vulnerability scanning for EC2, ECR images, Lambda
- Amazon Macie — S3 data classification, PII detection
- AWS Secrets Manager vs Systems Manager Parameter Store
- **Key takeaway**: CloudTrail = who did what. Config = what changed. GuardDuty = what's suspicious.

### Day 6 (Sat) — AWS Organizations & Multi-Account
- Organizational Units (OUs) and SCPs
- Consolidated billing — volume discounts, reserved instance sharing
- AWS Control Tower — automated multi-account setup with guardrails
- RAM (Resource Access Manager) — share resources across accounts
- **Hands-on**: Set up an AWS Organization with two accounts in Free Tier (optional)

### Day 7 (Sun) — Week 1 Review
- Re-read all notes from the week
- Take 20 IAM/security-focused questions from your practice tests
- Create a one-page cheat sheet covering: IAM policy evaluation, CMK vs AWS-managed keys, CloudTrail vs Config vs GuardDuty
- List any topics you found confusing — revisit those sections in the slides

---

## Week 2: Networking & VPC

### Day 1 (Mon) — VPC Fundamentals
- VPC = your private network in AWS, spans a single Region
- CIDR blocks: how to calculate subnets (know /16, /24, /28 ranges)
- Subnets are AZ-scoped: one subnet = one AZ
- Public subnet = has a route to an Internet Gateway (IGW)
- Private subnet = no direct internet route
- **Key takeaway**: AWS reserves 5 IPs per subnet (first 4 + last 1)

### Day 2 (Tue) — Internet Connectivity
- Internet Gateway (IGW) — one per VPC, horizontally scaled
- NAT Gateway — allows private subnets outbound internet access, AZ-scoped, deploy one per AZ for HA
- NAT Instance — self-managed, cheaper, must disable source/destination check
- Egress-Only Internet Gateway — IPv6 equivalent of NAT Gateway
- Elastic IP — static public IPv4 address, charges when not associated
- **Practice**: Build a VPC with one public and one private subnet, NAT Gateway for the private subnet

### Day 3 (Wed) — Security Groups & NACLs
- Security Groups: stateful, instance-level, allow rules only, default deny inbound / allow outbound
- NACLs: stateless, subnet-level, allow AND deny rules, processed in numerical order, default allow all
- SG can reference another SG (e.g., allow traffic from the ALB's SG)
- Ephemeral ports: NACLs must allow response traffic on ports 1024-65535
- **Key takeaway**: Use SGs for instance-level control (most questions). Use NACLs only when you need explicit deny rules (e.g., block a specific IP).

### Day 4 (Thu) — VPC Connectivity
- VPC Peering — 1:1 connection, no transitive routing, works cross-region
- Transit Gateway — hub-and-spoke, connects thousands of VPCs + on-premises, supports inter-region peering
- VPN: Site-to-Site VPN (over internet, IPsec) vs Direct Connect (dedicated physical connection)
- Direct Connect: 1 Gbps or 10 Gbps, takes weeks to set up, private + public VIF
- Direct Connect Gateway — connect to multiple VPCs across regions
- **Key takeaway**: Peering for a few VPCs. Transit Gateway for many. Direct Connect for consistent low-latency private connectivity.

### Day 5 (Fri) — VPC Endpoints & PrivateLink
- Gateway Endpoints: S3 and DynamoDB only, free, route table entry, no SG needed
- Interface Endpoints (PrivateLink): ENI with private IP, for all other AWS services, costs per hour + per GB
- Gateway Endpoints vs Interface Endpoints — this distinction is tested heavily
- PrivateLink: expose your service to other VPCs without peering or internet
- **Practice**: Create a gateway endpoint for S3 in your VPC, verify private access from EC2

### Day 6 (Sat) — DNS & Route 53
- Route 53: DNS service + domain registration + health checks
- Record types: A (IPv4), AAAA (IPv6), CNAME (alias to hostname, not zone apex), Alias (AWS-specific, works at zone apex, free for AWS resources)
- Routing policies: Simple, Weighted, Latency-based, Failover (active-passive), Geolocation, Geoproximity, Multi-value
- Health checks: endpoint, calculated, CloudWatch alarm-based
- **Key takeaway**: Alias records for AWS resources (ELB, CloudFront, S3 website). CNAME cannot be used at zone apex (naked domain).

### Day 7 (Sun) — Week 2 Review
- Re-read all notes
- Take 20 networking-focused questions from your practice tests
- Draw a diagram from memory: VPC with public/private subnets, IGW, NAT GW, route tables, SGs, NACLs
- Cheat sheet: SG vs NACL table, Gateway vs Interface endpoints, Route 53 routing policies

---

## Week 3: Compute & Containers

### Day 1 (Mon) — EC2 Instance Types & Purchasing
- Instance families: General (M/T), Compute (C), Memory (R/X/z), Storage (I/D/H), Accelerated (P/G/Inf)
- T instances: burstable, CPU credits, unlimited mode
- On-Demand: pay per second, no commitment
- Reserved Instances: 1 or 3 year, Standard (up to 72% off) vs Convertible (up to 54% off, can change family)
- Savings Plans: Compute (most flexible) vs EC2 Instance (biggest discount)
- Spot Instances: up to 90% off, 2-minute interruption notice, use for fault-tolerant workloads
- Dedicated Hosts: per-socket/core licensing (Windows Server, SQL Server), compliance
- Dedicated Instances: your hardware, but no socket/core visibility
- **Key takeaway**: Spot for batch/CI. Reserved/Savings Plans for steady baseline. On-Demand for spikes.

### Day 2 (Tue) — EC2 Storage & Networking
- Instance store: ephemeral, highest IOPS, data lost on stop/terminate
- EBS: persistent, can detach/attach, snapshots to S3
- EBS-optimized instances: dedicated throughput to EBS
- Enhanced networking: ENA (Elastic Network Adapter) for up to 100 Gbps
- Placement groups:
    - Cluster: same rack, lowest latency, HPC
    - Spread: each instance on different hardware, max 7 per AZ, critical instances
    - Partition: groups on separate racks, large distributed systems (HDFS, Kafka, Cassandra)
- **Practice**: Launch an EC2 instance, attach an EBS volume, take a snapshot, restore it

### Day 3 (Wed) — EC2 Advanced Features
- AMI: regional, can be copied cross-region, can be shared cross-account
- User data: bootstrap scripts (runs as root on first boot)
- Instance metadata: http://169.254.169.254/latest/meta-data/ (know this URL)
- Hibernate: RAM contents saved to EBS, faster startup, root volume must be encrypted
- EC2 status checks: system (AWS hardware) vs instance (your OS)
- **Key takeaway**: Hibernate preserves in-memory state. Stop/Start may move to new host.

### Day 4 (Thu) — Auto Scaling
- Launch Template (preferred) vs Launch Configuration (legacy, no versioning)
- Auto Scaling Group: min, max, desired capacity
- Scaling policies:
    - Target Tracking: maintain a metric at target (e.g., CPU at 50%) — simplest
    - Step Scaling: add/remove based on CloudWatch alarm thresholds
    - Scheduled: scale at specific times (predictable patterns)
    - Predictive: ML-based, forecasts traffic patterns
- Cooldown period: prevents rapid scale in/out (default 300s)
- Lifecycle hooks: run scripts before instance enters/leaves service
- Health checks: EC2 (default) or ELB (recommended when behind a load balancer)
- **Key takeaway**: Target tracking for most use cases. Step for fine-grained control. Scheduled for known patterns.

### Day 5 (Fri) — Elastic Load Balancing
- ALB (Layer 7): HTTP/HTTPS, path-based routing, host-based routing, supports Lambda targets, WebSocket, gRPC
- NLB (Layer 4): TCP/UDP/TLS, ultra-low latency, static IP per AZ, millions of requests/sec
- GLB (Layer 3): third-party virtual appliances (firewalls, IDS), GENEVE protocol
- Cross-zone load balancing: ALB (always on, free), NLB (off by default, charges if enabled)
- Connection draining (deregistration delay): time to complete in-flight requests before deregistering
- Health checks: path, port, thresholds, intervals
- SSL/TLS: ACM certificates on ALB/NLB, SNI for multiple certs on one ALB
- **Key takeaway**: ALB for HTTP routing decisions. NLB for extreme performance or static IPs. GLB for inline security appliances.

### Day 6 (Sat) — Containers & Serverless Compute
- ECS: AWS-native container orchestration
    - EC2 launch type: you manage EC2 instances
    - Fargate launch type: serverless, no infrastructure to manage
- EKS: managed Kubernetes on AWS (use when you need Kubernetes compatibility)
- ECR: container image registry
- Lambda: event-driven, 15-min timeout, 10 GB memory, 1000 default concurrent executions
- Lambda@Edge / CloudFront Functions: run code at edge locations
- AWS App Runner: fully managed container service from source code or image
- **Hands-on**: Deploy a simple container on Fargate using the ECS console

### Day 7 (Sun) — Week 3 Review
- Re-read all notes
- Take 20 compute-focused questions from practice tests
- Cheat sheet: instance purchasing options comparison, ALB vs NLB vs GLB, ECS EC2 vs Fargate vs Lambda decision tree
- Memorize: placement group types and when to use each

---

## Week 4: Storage & Data Transfer

### Day 1 (Mon) — S3 Storage Classes
- S3 Standard: frequently accessed, 99.99% availability, 11 nines durability
- S3 Standard-IA: infrequent access, cheaper storage, retrieval fee, 30-day minimum
- S3 One Zone-IA: single AZ, 20% cheaper than Standard-IA, for re-creatable data
- S3 Glacier Instant Retrieval: millisecond retrieval, 90-day minimum
- S3 Glacier Flexible Retrieval: minutes to hours (Expedited 1-5 min, Standard 3-5 hr, Bulk 5-12 hr), 90-day minimum
- S3 Glacier Deep Archive: cheapest, 12-48 hours retrieval, 180-day minimum
- S3 Intelligent-Tiering: auto-moves objects based on access patterns, small monitoring fee, no retrieval fee
- **Key takeaway**: Intelligent-Tiering when access patterns are unknown. Glacier Deep Archive for compliance archives.

### Day 2 (Tue) — S3 Features & Security
- Versioning: protects against accidental deletes, MFA Delete for extra protection
- Lifecycle policies: transition between storage classes, expire objects
- Replication: CRR (cross-region, DR/compliance) vs SRR (same-region, log aggregation), requires versioning
- S3 Transfer Acceleration: uses CloudFront edge locations for faster uploads
- S3 Select / Glacier Select: query with SQL, retrieve only needed data, save on transfer costs
- Bucket policies (resource-based) vs IAM policies (identity-based)
- Block Public Access: account-level and bucket-level settings
- Pre-signed URLs: temporary access to private objects
- **Practice**: Create a bucket with versioning, set up a lifecycle policy to transition to Glacier after 90 days

### Day 3 (Wed) — S3 Encryption & Advanced
- SSE-S3: AWS manages keys, AES-256, default since Jan 2023
- SSE-KMS: KMS key, audit trail via CloudTrail, envelope encryption, API call limits (GenerateDataKey)
- SSE-C: customer provides key with every request, AWS does not store the key
- Client-side encryption: you encrypt before uploading
- S3 Object Lock: WORM (Write Once Read Many), Governance mode vs Compliance mode
- S3 event notifications: trigger Lambda, SQS, SNS, or EventBridge on object events
- S3 Access Points: simplify managing access for shared datasets
- Multipart upload: required for >5 GB, recommended for >100 MB

### Day 4 (Thu) — EBS Deep Dive
- gp3: 3000 IOPS baseline, 125 MiB/s, can provision up to 16K IOPS / 1000 MiB/s independently
- gp2: 3 IOPS/GB, burst to 3000, max 16K IOPS (linked to size)
- io2 Block Express: up to 256K IOPS, 4000 MiB/s, sub-millisecond latency, critical databases
- st1: throughput-optimized HDD, 500 MiB/s max, big data/data warehouse, cannot be boot volume
- sc1: cold HDD, 250 MiB/s max, cheapest, infrequent access, cannot be boot volume
- Snapshots: incremental, stored in S3, can copy cross-region, can create AMI from snapshot
- Encryption: uses KMS, encrypting an unencrypted volume requires snapshot > copy (encrypted) > restore
- Multi-attach: io1/io2 only, same AZ, up to 16 instances
- **Key takeaway**: gp3 is the default choice. io2 for databases needing >16K IOPS. st1 for sequential throughput.

### Day 5 (Fri) — EFS, FSx & Other Storage
- EFS: managed NFS, Linux only, pay per use, scales automatically, multi-AZ
    - Performance modes: General Purpose (default, low latency) vs Max I/O (high throughput, higher latency)
    - Throughput modes: Bursting vs Provisioned vs Elastic
    - Storage classes: Standard, Infrequent Access (EFS-IA), lifecycle policies
- FSx for Windows File Server: SMB, NTFS, Active Directory integration, DFS Namespaces
- FSx for Lustre: HPC, ML training, integrates with S3 (hot data on Lustre, cold on S3)
- FSx for NetApp ONTAP: multi-protocol (NFS, SMB, iSCSI), data deduplication, compression
- FSx for OpenZFS: NFS, snapshots, up to 1M IOPS
- AWS Storage Gateway: hybrid cloud storage (File Gateway, Volume Gateway, Tape Gateway)

### Day 6 (Sat) — Data Transfer & Migration
- Snow Family:
    - Snowcone: 8-14 TB, edge computing + data transfer
    - Snowball Edge Storage Optimized: 80 TB, for large data transfers
    - Snowball Edge Compute Optimized: 42 TB + compute, for edge processing
    - Snowmobile: 100 PB, for exabyte-scale migration
- AWS DataSync: online data transfer, NFS/SMB to S3/EFS/FSx, scheduled, built-in encryption
- AWS Transfer Family: SFTP/FTPS/FTP to S3 or EFS
- AWS DMS (Database Migration Service): continuous replication, supports heterogeneous migrations with SCT
- **Key takeaway**: DataSync for online transfer. Snow Family for offline/large transfers. DMS for database migration.
- **Take Practice Test 1** (timed, 130 minutes)

### Day 7 (Sun) — Week 4 Review
- Score Practice Test 1, read all explanations
- Track wrong answers by topic
- Cheat sheet: S3 storage class comparison (durability, availability, min duration, retrieval time), EBS volume type comparison, Snow Family sizes
- Revisit any weak areas from the test

---

## Week 5: Databases

### Day 1 (Mon) — RDS Fundamentals
- Supported engines: MySQL, PostgreSQL, MariaDB, Oracle, SQL Server, Aurora
- Multi-AZ: synchronous standby replica, automatic failover (1-2 min), same region, not for read traffic
- Read Replicas: asynchronous, up to 5 (15 for Aurora), can be cross-region, can be promoted to standalone
- Automated backups: 1-35 day retention, point-in-time recovery, stored in S3
- Manual snapshots: persist until deleted, can be shared cross-account
- RDS Proxy: connection pooling, reduces failover time by 66%, enforces IAM auth, Lambda integration
- **Key takeaway**: Multi-AZ = high availability. Read Replica = read scaling. They serve different purposes.

### Day 2 (Tue) — Aurora
- MySQL and PostgreSQL compatible, 5x MySQL / 3x PostgreSQL performance
- Storage: 6 copies across 3 AZs, auto-grows 10 GB to 128 TB, self-healing
- Aurora Replicas: up to 15, automatic failover (priority tiers), reader endpoint for load balancing
- Aurora Serverless v2: scales compute automatically, good for unpredictable workloads
- Aurora Global Database: 1 primary region + up to 5 secondary regions, < 1 second replication, promote for DR
- Aurora Cloning: create a copy using copy-on-write, same storage initially, fast, good for testing
- Aurora Multi-Master: multiple write nodes (discontinued in favor of other patterns)
- **Key takeaway**: Aurora Global Database for cross-region DR. Aurora Serverless for variable workloads.

### Day 3 (Wed) — DynamoDB
- Fully managed NoSQL, single-digit ms latency, unlimited scale
- Tables, items (rows), attributes (columns), primary key (partition key or partition + sort key)
- Capacity modes: On-Demand (pay per request) vs Provisioned (specify RCU/WCU, auto-scaling available)
- RCU: 1 strongly consistent read/s for 4 KB, 2 eventually consistent reads/s for 4 KB
- WCU: 1 write/s for 1 KB
- GSI: alternate partition + sort key, eventual consistency only, has its own RCU/WCU, can add anytime
- LSI: same partition key + alternate sort key, strong or eventual consistency, must create at table creation, max 5 per table
- DAX: in-memory cache, microsecond reads, sits in front of DynamoDB
- DynamoDB Streams: ordered record of changes, integrates with Lambda for triggers
- DynamoDB Global Tables: multi-region, multi-active replication, requires Streams enabled
- **Key takeaway**: GSI for flexible queries. LSI only if you need strong consistency on alternate sort key.

### Day 4 (Thu) — ElastiCache, MemoryDB & Specialized Databases
- ElastiCache Redis: complex data types, Multi-AZ with auto-failover, persistence, encryption, pub/sub, sorted sets
- ElastiCache Memcached: simpler, multi-threaded, no persistence, no replication, for simple key-value caching
- MemoryDB for Redis: durable in-memory database (not just cache), microsecond reads, single-digit ms writes
- Use cases: session store (Redis), leaderboard (Redis sorted sets), caching DB queries, rate limiting
- **Key takeaway**: Redis for most exam answers. Memcached only when question says "simplest caching" or "multi-threaded".

### Day 5 (Fri) — Analytics & Other Databases
- Redshift: data warehouse, columnar, SQL, Spectrum for querying S3 directly, not for OLTP
- Athena: serverless SQL on S3, pay per query, uses Presto, integrates with Glue Data Catalog
- Neptune: graph database, social networks, recommendation engines, fraud detection
- DocumentDB: MongoDB compatible, fully managed
- Keyspaces: Apache Cassandra compatible, serverless
- QLDB: quantum ledger, immutable, verifiable history, financial transactions
- Timestream: time-series data, IoT, DevOps metrics
- **Key takeaway**: Athena for ad-hoc S3 queries. Redshift for complex analytics. Neptune for graph/relationships.

### Day 6 (Sat) — Database Migration & Choosing the Right DB
- DMS: continuous replication, minimal downtime migration
- SCT (Schema Conversion Tool): convert schema for heterogeneous migrations (Oracle to PostgreSQL)
- Decision framework:
    - Relational + transactions → RDS or Aurora
    - Key-value at scale → DynamoDB
    - Caching → ElastiCache
    - Graph → Neptune
    - Time-series → Timestream
    - Immutable ledger → QLDB
    - Analytics → Redshift or Athena
    - Document → DocumentDB
- **Hands-on**: Create an RDS instance with Multi-AZ, create a Read Replica, test failover

### Day 7 (Sun) — Week 5 Review
- Re-read all notes
- Take 20 database-focused questions from practice tests
- Cheat sheet: RDS Multi-AZ vs Read Replica, DynamoDB capacity calculations (RCU/WCU), Redis vs Memcached, when to use each database service

---

## Week 6: Application Integration & Serverless

### Day 1 (Mon) — SQS
- Standard Queue: unlimited throughput, at-least-once delivery, best-effort ordering
- FIFO Queue: 300 msg/s (3000 with batching), exactly-once processing, strict ordering, message group ID for parallel processing within FIFO
- Visibility timeout: time a message is hidden after consumer receives it (default 30s, max 12 hrs)
- Dead-letter queue (DLQ): messages that fail processing after N attempts, set maxReceiveCount
- Delay queue: postpone delivery of new messages (0-15 min)
- Long polling: reduces empty responses, set WaitTimeSeconds (1-20s), cheaper than short polling
- Message retention: 1 minute to 14 days (default 4 days)
- Max message size: 256 KB (use Extended Client Library + S3 for larger)
- **Key takeaway**: Standard for throughput. FIFO when ordering matters. DLQ for failed message handling.

### Day 2 (Tue) — SNS, EventBridge & Fan-Out
- SNS: pub/sub, push-based, one message to many subscribers
- Subscribers: SQS, Lambda, HTTP/S, Email, SMS, Kinesis Data Firehose
- SNS + SQS fan-out pattern: SNS topic pushes to multiple SQS queues for parallel independent processing
- SNS FIFO: works only with SQS FIFO subscribers
- SNS message filtering: subscriber filter policies reduce unnecessary processing
- EventBridge (CloudWatch Events successor): event-driven, rules match events to targets
    - Default event bus (AWS services), custom event bus, partner event bus
    - Schema registry: discover event schemas
    - Archive and replay events
- **Key takeaway**: SNS for simple fan-out. EventBridge for complex routing with rules and multiple sources.

### Day 3 (Wed) — Kinesis
- Kinesis Data Streams: real-time streaming, 1 MB/s per shard in, 2 MB/s per shard out, 1-365 day retention
    - Producers: SDK, KPL, Kinesis Agent
    - Consumers: SDK, KCL, Lambda, Kinesis Data Firehose
    - Capacity: provisioned (per shard) or on-demand
- Kinesis Data Firehose: near real-time delivery (60s buffer), fully managed, load data to S3/Redshift/OpenSearch/Splunk, auto-scaling
- Kinesis Data Analytics: SQL or Apache Flink on streaming data
- Kinesis vs SQS:
    - Kinesis: real-time, multiple consumers read same data, ordered per shard, replay capability
    - SQS: messaging, one consumer per message, no replay, simpler
- **Key takeaway**: Kinesis for real-time analytics and multiple consumers. SQS for decoupling and job queues.

### Day 4 (Thu) — API Gateway & Step Functions
- API Gateway: create REST and WebSocket APIs, throttling (10K rps default, 5K burst), caching, API keys, usage plans
- Integration types: Lambda proxy, HTTP proxy, AWS service, Mock
- Stages: dev, staging, prod with stage variables
- Authentication: IAM, Cognito User Pools, Lambda authorizer
- API Gateway + Lambda = fully serverless API
- Step Functions: orchestrate Lambda functions and AWS services
    - Standard workflows: up to 1 year, exactly-once, auditable
    - Express workflows: up to 5 minutes, at-least-once, high volume
    - States: Task, Choice, Parallel, Wait, Map, Pass, Succeed, Fail
- **Key takeaway**: API Gateway for throttling and request management. Step Functions for coordinating multi-step workflows.

### Day 5 (Fri) — Serverless Patterns & Cognito
- Common serverless stack: API Gateway → Lambda → DynamoDB
- S3 event → Lambda for image processing, log processing
- SQS → Lambda for async processing (batch size, concurrency)
- Cognito User Pools: authentication (sign-up, sign-in, MFA, tokens)
- Cognito Identity Pools: authorization (temporary AWS credentials for accessing AWS services)
- User Pools + Identity Pools together: authenticate first, then get AWS credentials
- AppSync: managed GraphQL API, real-time subscriptions, offline sync
- **Practice**: Build a simple API Gateway + Lambda + DynamoDB stack

### Day 6 (Sat) — Practice Tests 2 & 3
- Take Practice Test 2 (timed, 130 minutes)
- Score it, read all explanations
- Take Practice Test 3 (timed, 130 minutes)
- Score it, read all explanations
- Track all wrong answers by topic

### Day 7 (Sun) — Week 6 Review
- Compare wrong answers from Tests 2 and 3 to Test 1 — look for recurring weak areas
- Cheat sheet: SQS Standard vs FIFO, Kinesis vs SQS, SNS vs EventBridge, Cognito User Pools vs Identity Pools
- Revisit any topic you got wrong on two or more tests

---

## Week 7: Monitoring, DR & Cost Optimization

### Day 1 (Mon) — CloudWatch
- CloudWatch Metrics: CPU, Network, Disk (not RAM — requires CloudWatch Agent)
- Custom metrics: push via PutMetricData API
- CloudWatch Alarms: OK, ALARM, INSUFFICIENT_DATA states, trigger Auto Scaling, SNS, EC2 actions
- Composite alarms: combine multiple alarms with AND/OR
- CloudWatch Logs: log groups, log streams, metric filters, subscription filters
- CloudWatch Logs Insights: query logs with built-in query language
- CloudWatch Agent: collect RAM, disk space, custom logs from EC2 and on-premises servers
- **Key takeaway**: Default EC2 metrics are every 5 min. Detailed monitoring = 1 min. Custom metrics = up to 1 sec (high resolution).

### Day 2 (Tue) — CloudTrail, Config & Trusted Advisor
- CloudTrail: records AWS API calls, enabled by default (90-day management events)
    - Management events: control plane (CreateBucket, TerminateInstances)
    - Data events: data plane (GetObject, PutItem), disabled by default, high volume
    - Trail: deliver to S3 for long-term storage, can send to CloudWatch Logs
    - Organization trail: all accounts in the org
- AWS Config: records resource configurations over time
    - Config Rules: managed or custom (Lambda), evaluate compliance
    - Remediation: auto-fix non-compliant resources via SSM Automation
    - Aggregator: multi-account, multi-region view
- Trusted Advisor: checks for cost optimization, performance, security, fault tolerance, service limits
    - Basic: 7 core checks (S3 bucket permissions, MFA on root, etc.)
    - Business/Enterprise Support: full checks + API access
- **Key takeaway**: CloudTrail = audit log. Config = compliance. Trusted Advisor = best practices.

### Day 3 (Wed) — Disaster Recovery Strategies
- RPO (Recovery Point Objective): how much data can you afford to lose
- RTO (Recovery Time Objective): how long can you afford to be down
- Strategies (cheapest to most expensive):
    1. Backup & Restore: RPO hours, RTO hours. S3 CRR, EBS snapshots, RDS backups
    2. Pilot Light: RPO minutes, RTO tens of minutes. Core DB replicated, compute off, scale up on failure
    3. Warm Standby: RPO seconds, RTO minutes. Scaled-down full environment in DR region
    4. Multi-Site Active/Active: RPO ~0, RTO ~0. Full production in both regions, Route 53 failover
- Route 53 failover routing: health checks on primary, automatic DNS failover to secondary
- Aurora Global Database: < 1 sec RPO, < 1 min RTO for cross-region failover
- S3 Cross-Region Replication: asynchronous, new objects only (unless S3 Batch Replication)
- **Practice**: Design a DR architecture on paper for a three-tier web app

### Day 4 (Thu) — High Availability Patterns
- Multi-AZ deployments: RDS, ElastiCache, EFS, NAT Gateway (one per AZ)
- Auto Scaling across AZs: ASG spans multiple subnets/AZs
- ELB cross-zone: distribute evenly across all AZs
- S3: 11 nines durability, automatically distributed across 3+ AZs
- Stateless architecture: externalize state to ElastiCache/DynamoDB for seamless failover
- Health checks at every layer: Route 53 → ELB → EC2/container
- **Key takeaway**: HA = multiple AZs + auto scaling + health checks + decoupled components.

### Day 5 (Fri) — Cost Optimization
- EC2: Right-size with Compute Optimizer, use Savings Plans or Reserved for baseline, Spot for flexible workloads
- S3: Lifecycle policies, Intelligent-Tiering, S3 Analytics for access pattern visibility
- Data transfer: free inbound, free within AZ, cross-AZ costs money, VPC endpoints save NAT Gateway fees
- RDS: Reserved Instances, Aurora Serverless for variable workloads, stop dev/test instances on schedule
- Lambda: pay per invocation + duration, optimize memory for price-performance
- Cost management tools:
    - Cost Explorer: visualize and forecast spending
    - Budgets: set alerts on spend or usage thresholds
    - Cost Allocation Tags: tag resources to track costs by project/team
    - Savings Plans: Compute (flexible) vs EC2 Instance (deepest discount)

### Day 6 (Sat) — Practice Tests 4 & 5
- Take Practice Test 4 (timed, 130 minutes)
- Score it, read all explanations
- Take Practice Test 5 (timed, 130 minutes)
- Score it, read all explanations
- Track all wrong answers by topic

### Day 7 (Sun) — Week 7 Review
- Compare wrong answers from Tests 4-5 to Tests 1-3
- Cheat sheet: DR strategies with RPO/RTO, CloudWatch vs CloudTrail vs Config, cost optimization levers
- Deep dive into any topic you've gotten wrong 3+ times

---

## Week 8: Review & Final Prep

### Day 1 (Mon) — Practice Test 6 & Analysis
- Take Practice Test 6 (timed, 130 minutes)
- Score it, read every explanation carefully
- Compile all wrong answers from Tests 1-6 by domain:
    - Domain 1 (Security 30%): count wrong answers
    - Domain 2 (Resilient 26%): count wrong answers
    - Domain 3 (High-Performing 24%): count wrong answers
    - Domain 4 (Cost-Optimized 20%): count wrong answers
- Your weakest domain = highest priority for remaining study days

### Day 2 (Tue) — Weakest Domain Deep Dive
- Spend the full session on your weakest domain
- Re-read the relevant sections in the slide deck
- Review every wrong answer you got in this domain across all 6 tests
- Look for the pattern: are you confusing two similar services? Missing a key detail? Misreading the question?
- Write down the 5 most important lessons from your mistakes

### Day 3 (Wed) — Second Weakest Domain + Cross-Cutting Topics
- Spend half the session on your second weakest domain
- Spend the other half on cross-cutting topics that appear in every domain:
    - Encryption (at rest, in transit, KMS, SSE options)
    - High availability (Multi-AZ, Auto Scaling, health checks)
    - Least privilege (IAM, SGs, NACLs, resource policies)
    - Serverless vs managed vs self-managed (when to pick each)

### Day 4 (Thu) — Re-Take Practice Test 1
- Re-take Practice Test 1 (timed, 130 minutes)
- Compare your score to the first attempt
- Any question you got wrong both times = a critical gap, study that specific topic tonight
- You should see meaningful improvement — if not, focus remaining days on the weak areas

### Day 5 (Fri) — Rapid Review of All Cheat Sheets
- Review all weekly cheat sheets you created
- Rapid-fire mental quiz on these high-frequency topics:
    - S3 storage classes and when to use each
    - EBS volume types and IOPS limits
    - RDS Multi-AZ vs Read Replica
    - SG vs NACL
    - Gateway vs Interface endpoints
    - DR strategies and RPO/RTO
    - EC2 purchasing options
    - Kinesis vs SQS
    - CloudFront vs Global Accelerator
    - Cognito User Pools vs Identity Pools

### Day 6 (Sat) — Light Review & Logistics
- Light review only — do not cram new material
- Skim through the AWS Well-Architected Framework pillars (Operational Excellence, Security, Reliability, Performance Efficiency, Cost Optimization, Sustainability)
- Confirm exam logistics:
    - Test center: know the location and parking, or online proctoring setup tested
    - ID documents ready (two forms of ID for test center)
    - Arrive 15 minutes early
- Read the exam guide one final time on the AWS Certification site

### Day 7 (Sun) — Exam Day
- Get a full night's sleep (do NOT study the night before)
- Eat a good meal before the exam
- During the exam:
    - Read every question fully, focus on the last sentence (the actual ask)
    - Eliminate 2 wrong answers, then choose between the remaining 2
    - Flag hard questions, come back after finishing all 65
    - 2 minutes per question in the first pass, use remaining time for flagged questions
    - Trust your first instinct — change answers only with a clear reason
- After the exam: result is pass/fail immediately, detailed score within 5 business days
