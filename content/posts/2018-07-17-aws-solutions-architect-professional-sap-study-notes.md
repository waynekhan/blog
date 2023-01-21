---
title: AWS Solutions Architect Professional (SAP) study notes
date: 2018-07-17T10:24:23+00:00
---

Completed this one on a wintry Sydney morning. Despite a lack of sleep, I felt much better prepared vs. DevOps Pro, and it showed in the grade, too:

Overall Score: 75%

## Topic Level Scoring

1. High Availability and Business Continuity: 72%
1. Costing: 75%
1. Deployment Management: 57%
1. Network Design: 42%
1. Data Storage: 72%
1. Security: 85%
1. Scalability & Elasticity: 90%
1. Cloud Migration & Hybrid Architecture: 85%

## Scratchpad

* ASG;
* CloudFormation, using YAML/JSON for solution architecture:
* Which Services are supported?;
* Templates vs Stacks;
* "Fn::getAtt": [ "WebServerHost", "PublicIp"];
* Chef/Puppet integration OK, or use bootstrapping for application-level dependencies/config;
* By default, automatic rollback on error (resource provisioning charges still apply);
* WaitCondition;
* Resource deletion policy;
* Resource update policy;
* IAM Role definition and assignment;
* VPC creation and customisation (and pretty much everything within a VPC);
* EIPs and private IPs;
* Multiple VPCs (for peering) within the same Account only;
* Create/update Route 53 hosted zones;
* CloudFront, web/RTMP, geo black-/white-list, SSL (SNI/dedicated), PPPD HTTP methods never cached (proxied to origin), CNAME?, Invalidation API, naked domain alias, dynamic content support (cookie), Origin Access Identity (OAI);
* CloudHSM, key GSM within a VPC, non fault-tolerant (needs to be clustered), accessible via peering;
* CloudSearch?;
* CloudTrail, from multiple Accounts to an S3 bucket;
* CloudWatch, indefinite by default, 14 days for alarm history;
* Data Pipeline, use on AWS (EC2/EMR)or on-premise, pipeline container, data node (end dest), activity, precondition, schedule;
* Direct Connect, 802.1q, can address both public/private environments by relying on an underlying VIV, sub-1/1/10 Gbps dark fibre to AWS vs establishing a VPN, CGW vs VGW, also configure BGP failover, US-only: 1 Direct Connect will work for all Regions;
* Directory Services, AD Connector (existing), Simple AD (new);
* DR as a part of BC (eg hardware/software failure, network/power outage, physical damage). Spectrum of options:
* Backup & Restore: (i) backup (to AWS), (ii) retention policies; and (iii) security measures; eg access policies, encryption.
* Pilot Light: (i) Pre-configure functional (eg app/web, database) servers as AMIs for various functions; (ii) fire drill; (iii) consider automation (via CloudFormation).
* Warm Standby: (i) Run apps in an ASG (and/or other infrastructure); and (ii) keep 'em up-to-date (eg patches, config files).
* Multisite/active-active: (i) Duplicate non-AWS environment; and (ii) Configure weighted routing (Route 53) to route traffic on-premise/AWS environments;
* DynamoDB (cross-Region replication);
* EBS point-in-time (eg using the CLI), attached to a single EC2 only;
* EC2;
* D (dense storage);
* I (IOPS);
* R (RAM);
* T (t2.micro);
* M (main choice);
* C (compute);
* G (graphics);
* F (FPGA);
* P (mining);
* X (HANA/Spark);
* ECS?;
* EFS?;
* ElasticCache, Memcached (scale out, multi-threaded) vs Redis (scale up, persistency, multi-AZ);
* Elastic Beanstalk (EB), relatively simple (vs CloudFormation);
* Applications vs environments;
* Supported languages:
* Docker (single-/multi-container);
* Go 1.6;
* Java w/ Tomcat;
* Java SE (7, 8);
* .NET (IIS 7.5+);
* Node.js;
* PHP;
* Python 2.6+;
* Ruby 1.9+;
* Supported AWS services include:
* CloudWatch;
* IAM;
* RDS;
* S3;
* VPC (within a Region only);
* Elastic Transcoder?;
* ELB, CLB (single/multiple AZs, health checks, associate SGs, SSL offload, sticky sessions, IPv{4,6}, CloudWatch metrics, optional logging to S3, CloudTrail support, layer 4) vs ALB (single AZ, content-/host-/path-based routing, ECS dynamic port integration, HTTP/2, Web Sockets, HA {2 or more AZs}, WAF support, delete protection, X-Amzn-Trace-Id, layer 7), Proxy Protocol;
* EMR?;
* ENI?;
* FSMO role?;
* Glacier, cheap/slow data archival (3+ hours);
* HA:
* MySQL (async. replication);
* Oracle Database (DataGuard, RAC);
* SQL Server (AlwaysOn Availability Groups, clustering, mirroring);
* HTTP Live Streaming (HLS);
* HPC, Jumbo (Ethernet) Frames via Enhanced Networking (selected HVM instance types), PGs within an AZ;
* IAM:
* Cross-Account access, segregation of access for Dev., vs Test via pre-configured inline policy.; ie no need to remember a separate Account ID/username/password, can also be used to store/deploy SSL (in lieu of ACM);
* IDS/IPS, watch the AlertLogic video;
* Kinesis Data Streams, real-time data streaming (1-7 days);
* KMS, to generate signed certificates on demand for a requesting instance;
* Multicast?;
* NAT scaling
* OpsWorks, Chef 11+ deployments on AWS;
* Stacks, Layers (eg apps, caching, databases, load balancers), and Recipes;
* ELBs must be separately started up and attached initially, but subsequently are managed via OpsWorks;
* ELBs and SGs must be separately torn down after layer/stack deletion;
* Instances may be: 24/7(default), Time-based, and Load-based;
* Organizations:
* All Features vs Consolidated Billing: the former merely enables policy-based service controls for Accounts (eg deny EC2 in a bid to encourage Serverless computing);
* Consolidated Billing; ie a single bill for multiple Accounts, and with volume discounting too (eg EC2 RIs, S3):
* Alerts can still be individually configured at either level of the hierarchy;
* CloudTrail must be configured individually, logging to a Cross-Account S3 bucket, though;
* Promiscuous?;
* RDS:
* Multi-AZ (sync., durable) vs RRs (async., scalable);
* Multi-AZ tech.: AWS (Aurora/MariaDB/MySQL, Oracle Database, PostgresSQL), vs Microsoft (SQL Server mirroring);
* RRs in another Region OK, except Oracle Database/SQL Server;
* RRs can also be configured as Multi-AZ;
* RRs of RRs for MySQL only, and this will increase replica lag;
* Supports snapshotting to a different Region;
* Redshift (snapshot to S3, or copy to another Region), WLM;
* RIs:
* EC2, reserve within an AZ:
* On Demand: Unpredictable;
* Dedicated;
* Spot: Flexible provisioning, only if the bid price is met only;
* Reserved (Standard, Convertible, Scheduled): up to 75% discounts for 1-/3-year terms, for steady-state use (eg Production):
* May be split into multiple instances if the footprint remains the same;
* Restricted within the same family (eg T2) unless Convertible;
* Restricted for Linux only, excl. RHEL and SUSE;
* RDS, reserve within a Region, supports Multi-AZ and RRs (same Region only);
* Route 53;
* Routing symmetrically vs asymmetrically (ie round-trip data path);
* RTO vs RPO;
* S3 (11 9s durability), can be a VPC endpoint;
* Scale up (ie vertical), vs out (ie horizontal). Latter is preferred to minimise downtime;
* SES;
* SG, cannot setup explicit deny rules (NACLs can);
* Snowball/Snowmobile, or previously (data) Import/Export;
* SNS;
* SQS;
* Storage Gateway (on-prem {ESXi/Hyper-V} bandwidth-throttled, or as an EC2; also works with Direct Connect):
* File (NFS), up to 5 TB per file;
* Tape (iSCSI):
* Library (S3: instant);
* Shelf (Glacier: 1d);
* Volume (iSCSI):
* Cached (subset only, most frequently used, up to 32 volumes {32 TB ea}; ie 1 PB);
* Stored (full set, up to 32 volumes {16 TB ea}; ie 512 TB);
* SR-IOV?;
* STS, AD-based identity federation for 1-36 hour access (to some resource, eg S3) without having to create new IAM creds, LDAP authentication first (then STS), 4 fields (access key, secret access key, token, duration);
* SWF?;
* Tags are key/value pairs attached to resources, usable in Resource Groups;
* VM Import/Export;
* VPC tenancy (default vs dedicated) and its impact on EC2 instances;
* Route table (created by default), subnet to AZ (1:1), private vs public subnets, assign a public IP within a public subnet to make an instance internet-facing (behind an ELB also works), 5 reserved IPs per subnet (.0-.3, .255), CIDR block; "local" route within a VPC, IGW to VPC (1:1), route table (for n subnets), IGW/NAT target (for destination 0.0.0.0/0) route, SGs can span multiple subnets but not the other way around, NAT instance disable source/destination check, VPC peering: use private IPs to address instances within the same Region (50-125 VPCs), 1:1 relationship, private DNS names won't resolve, routes/SGs/NACLs config required on both ends, multicast vs unicast?;
* WAF, managed layer 7 sandwich;
