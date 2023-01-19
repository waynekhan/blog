---
title: "AWS: SysOps Administrator (SOA) study notes"
date: 2018-04-19T04:08:07+00:00
---

Hello, world. Penned down some keywords after passing my recent AWS SOA exam, and then expanded on 'em below. Perhaps you'll find 'em useful then.

--
**EBS**
RAID 0 (striped) vs. 1 (mirrored); i.e., the lower the number, the higher the risk, see <https://www.diffen.com/difference/RAID_0_vs_RAID_1>.

Just like EC2 instances, EBS volumes reside in a specific AZ of a Region; i.e., they can only be attached to a running instances within the same AZ. To switch AZs, use snapshots, see <https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AmazonEBS.html>.

**EC2**
AMIs can be referred to as being backed by EBS, or ephemeral/instance store. Ephemeral/instance AMIs are stored in S3; i.e., terminating an EC2 instance running the S3-based AMI means that data in the root volume is gone forever, see <https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ComponentsAMIs.html>.

EBS optimized; i.e., minimizing contention between EBS I/O and other traffic from your EC2 instance, see <https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EBSOptimized.html>.

Cluster-type placement groups: low-latency grouping (of EC2 instances) within a single AZ, see <https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/placement-groups.html>.

**RDS**
Automated Backups allow users to restore to data within about 5 minutes of the current time, see <https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_PIT.html>.

**S3**
TA, as its name suggests, allows users to accelerate file transfers to S3, for when users are underutilizing available Internet bandwidth at upload time, see <https://docs.aws.amazon.com/AmazonS3/latest/dev/transfer-acceleration.html>.

**VPC**
Tenancy is typically default (i.e., shared) tenancy. Users cannot change from default to dedicated/host, and vice-versa, see <https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/dedicated-instance.html#change-tenancy-vpc>.

IPv4 CIDR blocks can range from large (/16 netmask, 65k addresses) to small (/28 netmask, 16 addresses), see <https://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/VPC_Subnets.html>.

Direct Connect, use private (virtual interface) to connect to your VPC, public for services that aren't in a VPC (e.g., Glacier), see <https://docs.aws.amazon.com/directconnect/latest/UserGuide/WorkingWithVirtualInterfaces.html>.

Within VPCs, there is a "local" route allowing communication between subnets using private IP addresses only, see <https://medium.com/@mda590/aws-routing-101-67879d23014d, https://acloud.guru/forums/aws-certified-solutions-architect-professional/discussion/-KGl5vgVKjHuXcpWM0S6/communication_between_subnets>.

**Windows**
Active Directory and AWS, see <https://aws.amazon.com/blogs/security/how-to-connect-your-on-premises-active-directory-to-aws-using-ad-connector/, https://docs.aws.amazon.com/directoryservice/latest/admin-guide/ms_ad_tutorial_setup_trust.html>.

Windows EC2 instances can be configured using EC2Config (2.2.10+) to export data to CloudWatch, see <https://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/ec2config-service.html>.
