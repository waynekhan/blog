---
title: "AWS: DevOps Pro study notes"
date: 2018-06-04T10:50:52+00:00
---

So I covered my eyes for a bit when I clicked 'Finish' (the test attempt), as this was the toughest exam I'd faced thus far, and I was maybe 70% satisfied with my body of work. Fortuitously, I passed, albeit with an overall score of 65%:-

## Topic Level Scoring

1. Continuous Delivery and Process Automation: 47%
1. Monitoring, Metrics, and Logging: 93%
1. Security, Governance, and Validation: 75%
1. High Availability and Elasticity: 83%

I really need to backtrack, figure out this CI/CD thing, then.

## Scratchpad

* ASG (lifecycle hooks {Terminating > Terminating:Wait}, span AZs evenly by default, Launch Configs cannot be edited, suspense AddToLoadBalancer and subsequent manual reg., Termination Policy {Default|OldestInstance});
* CI tooling (e.g., Jenkins) can perform syntax/build tests;
* CloudFormation (CreationPolicy {post-config}, ::CustomResource, {RDS} DeletionPolicy=Retain, nested stacks, UpdatePolicy=AutoScalingRollingUpdate);
* CloudTrail;
* CloudWatch (dimensions {per-ASG}, retention period, aggregation, Logs {agent}, Log Filters, subscriptions);
* DynamoDB (cache S3 object metadata);
* EB (Applications > Versions > Environments, Container Commands {leader-only}, Docker containers, Saved Configs., Swap URLs, .ebextensions);
* EBS (unencrypted to encrypted, pre-warming);
* ECS (Dockerrun.aws.json);
* ElastiCache;
* Elasticsearch?;
* IAM (Database Authentication {Aurora|MySQL}, Instance Profile > Role);
* Kinesis Streams (real time);
* OpsWorks; i.e., Chef+ (Configure {custom cookbook});
* RDS (Multi-AZ, Read Replicas, sharding);
* S3 (key-based naming scheme, store developer's public keys, MFA Delete);
* SNS;
* SQS;
* WiF (via some IdP {e.g., Google});
