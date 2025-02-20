IAM / EC2 / EFS / VPC
EBS (volume) vs EFS (file system)
# ELB (Elastic Load Balancer)
ALB (Application Load Balancer) Layer 7
NLB (Network Load Balancer) Layer 4 (TCP, UDP)
GWLB (Gateway Load Balancer) Layer 3 (IP)
Server Name Indication (SNI) // multiple SSL certificates on a single IP address
ASG (Auto Scaling Group)
CloudWatch (Monitoring)
# RDS (Relational Database Service)
Aurora (MySQL, PostgreSQL)
MariaDB
Oracle
SQL Serverя
DB2
# NoSQL
ElastiCache (Redis, Memcached)
Keyspaces (Cassandra)
DynamoDB (NoSQL)
Graph (Neptune)
# ElastiCache (Redis, Memcached)
Write Through
Lazy Loading
Session Store
# Route 53 (DNS)
Routing Policy
Health Check
# Beanstalk (PaaS)
Docker / Multi-Container / Single-Container
# S3 (Simple Storage Service)
Versioning / Encryption / Replication
CRR (Cross-Region Replication) / SRR (Same-Region Replication)
S3 Batch Replication (replicate existing objects)
https://aws.amazon.com/s3/storage-classes/
S3 Event Notification]
S3 Retention Mode / Compliance Mode / Governance Mode
S3 Object Lambda (transform data as it is read from S3) / Redacting Lambda (remove sensitive data)
CloudFront (CDN)
Global Accelerator (Anycast IP) send traffic over the AWS global network to the closest edge location
Snowball (Data Transfer Appliance)
FSx (Windows File Server, Lustre, ONTAP, OpenZFS, Amazon FSx for NetApp ONTAP)
Storage Gateway (File Gateway, Volume Gateway, Tape Gateway)
AWS DataSync (Data Transfer Service)
SQS (Simple Queue Service) (FIFO, Standard)
SNS (Simple Notification Service) publish/subscribe

Kinesis (Data Streaming)
• Let's assume 100 trucks, 5 kinesis shards, I SQS FIFO
Kinesis Data Streams:
• On average you'll have 20 trucks per shard
• Trucks will have their data ordered within each shard
• The maximum amount of consumers in parallel we can have is 5
• Can receive up to 5 MB/s of data
SOS FIFO
• You only have one SQS FIFO queue
• You will have 100 Group ID
• You can have up to 100 Consumers (due to the 100 Group ID)
• You have up to 300 messages per second (or 3000 if using batching)

ECS (Elastic Container Service) / ECR (Elastic Container Registry)
EKS (Elastic Kubernetes Service)
Fargate (Serverless)
AWS App Runner (Fully Managed Container Service)
CloudFormation (Infrastructure as Code)
Lambda (Serverless)
connect to VPC by using VPC configuration
Invoke Lambda & Event Notification
RDS for PostgreSQL / Aurora Mysql (events to call lambda) - need access for call Lambda function 
Serverless Application Model (SAM)
* AWS CLI
* AWS SDK
* AWS Lambda / Lambda Snap Start (Java 11+) / Provisioned Concurrency / Lambda Extensions / default outside VPC
Lambda@Edge is a feature of CloudFront that lets you run code closer to your users, which improves performance and reduces latency.
* DynamoDB
* AWS Cognito (User Pools, Identity Pools)
* AWS S3 (Simple Storage Service)
* AWS SNS (Simple Notification Service)
* AWS SQS (Simple Queue Service)
* AWS SES (Simple Email Service)
* Kinesis Data Streams
* AWS API Gateway
* Aurora
* Step Functions
DynamoDB (NoSQL) / DAX (DynamoDB Accelerator)
API Gateway
Cognito (User Pools, Identity Pools)
* Cognito User Pools (User Directory)
* Cognito Identity Pools (Federated Identity)

# Data & Analytics
* Redshift (Data Warehouse)
* Athena (Query S3)
* OpenSearch Service (Elasticsearch)
* EMR (Elastic MapReduce)
* QuickSight (Business Intelligence) - Dashboard
* Glue (ETL - Extract, Transform, Load)
* Data Lake (S3 + Glue + Athena) - top level security
* MSK (Managed Streaming for Kafka)

# Machine Learning
* Rekognition (Image & Video) - Detect Labels, Faces, Text, Moderation, Celebrity, Pathing, Face Comparison
* Transcribe (Speech to Text)
* Polly (Text to Speech)
* Translate (Language Translation)
* Lex (Chatbot / Voice)
* Connect (Contact Center)
* Comprehend (Natural Language Processing) - Detect Sentiment, Entities, Key Phrases, Language, Structure data from text
* SageMaker (ML) - Build, Train, Deploy ML models
* Forecast (Time Series Forecasting)
* Kendra (Enterprise Search / Document Search)
* Personalize (Personalized Recommendations)
* Textract (OCR - Optical Character Recognition) - KYC (Know Your Customer)
* Fraud Detector

# Monitoring & Audit
* CloudWatch (Monitor Resources)
* CloudTrail (Audit API Calls)
* Config (Resource Inventory) - Compliance
* EventBridge (Event Bus, Cron Jobs)

# Security
* AWS Secrets Manager
* AWS Certificate Manager (ACM)
* Web Application Firewall (WAF)
* Firewall Manager
* Shield (DDoS Protection) - const 3000 $/month give 24/7 support
* Macie (Data Security & Privacy)
* GuardDuty (Threat Detection)
* Inspector (Security Assessment)

# Networking - VPC
* CIDR (Classless Inter-Domain Routing) - give IP addresses to devices on a network
* 0.0.0.0/{n} - n = 0-32 - bits #example 0.0.0.0/16 = 0.0.255.255 (65,536 IP addresses), 0.0.0.255/24 = 256 IP addresses
* VPC (Virtual Private Cloud) - Isolated Network
* Subnet (Availability Zone)
* Route Table (Route to Internet Gateway) - connect to subnet to Internet Gateway, need add route target IGW
* Internet Gateway (IGW) - on their own don't do anything, need to be attached to VPC
* Bastion Host (Jump Box) - allow SSH to private instances (from public subnet to private subnet)
* NAT Gateway (NAT Instance) - allow instances in private subnet to connect to the internet
* NAT Instance (Network Address Translation) - allow instances in private subnet to connect to the internet - outdated
* NAT Gateway (NATGW Network Address Translation) - highly available, managed by AWS, automatically scaled, not associated with security group,
, required IGW, required Elastic IP, required public subnet
* Security Group (Stateful) - allow traffic to and from instances
* Network Access Control List (NACL) (Stateless / Security Group Stateful) - allow traffic to and from subnets
* [x] NACL - allow traffic to and from subnets, 2 checks for Incoming and Outgoing traffic, Security Group allow return traffic automatically
* [x] Allow deny rules, 100 rules, 1-32766, 32767-65535, default allow all
* [x] Rules are evaluated in order, the first rule that matches a packet applies
* [x] Applies at the subnet level to all instances in the subnet
* Security Group - allow rules only
* Ephemeral Ports (Dynamic Ports) - 1024-65535 - Outgoing traffic from instance to the internet (response)
* VPC Peering - connect two VPCs (no transitive peering)
* VPC Endpoints - connect to AWS services from private network not public, remove the need IGW, NATGW (S3, DynamoDB, SNS, SQS, Kinesis, API Gateway, CloudWatch, CloudTrail, CodeBuild, CodeCommit, CodePipeline, EC2, SSM, Secrets Manager, STS, Lambda, Step Functions, S3, DynamoDB, SNS, SQS, Kinesis, API Gateway, CloudWatch, CloudTrail, CodeBuild, CodeCommit, CodePipeline, EC2, SSM, Secrets Manager, STS, Lambda, Step Functions)
* Interface Endpoint - powered by PrivateLink, provisions an ENI (Elastic Network Interface) in your subnet, for services hosted on AWS or by other AWS customers
* Gateway Endpoint - free, for S3 and DynamoDB, powered by route tables, for services hosted on AWS\
* Flow Logs - capture information about IP traffic going to and from network interfaces in your VPC
* VPN (Virtual Private Network) - connect on-premises network to AWS
* VPG (Virtual Private Gateway) - attach to VPC, connect to Customer Gateway
* CGW (Customer Gateway) - attach to on-premises network, connect to Virtual Private Gateway
* Route Propagation - enable route propagation on the route table associated with the subnet
* Direct Connect - dedicated network connection from on-premises to AWS
* DX (Direct Connect Gateway) - connect multiple VPCs to on-premises network
* Transit Gateway - connect multiple VPCs and on-premises networks
* VPC Traffic Mirroring - copy network traffic from EC2 instances within your VPC to security and monitoring appliances for use cases such as content inspection, threat monitoring, and troubleshooting
* Egress-Only Internet Gateway (Similar to NAT for IPv6) - allow IPv6 traffic from instances in your VPC to the internet, but prevent the internet from initiating an IPv6 connection with your instances
* AWS Network Firewall - managed firewall service that makes it easy to deploy essential network protections for all of your Amazon Virtual Private Clouds (VPCs)
* [x] uses AWS Gateway Load Balancer (GWLB) to inspect and filter traffic
* [x] Stateful inspection, intrusion prevention
* [x] From Layer 3 to Layer 7

Elastic Beanstalk / CodeDeploy / CodePipeline / CodeCommit / Glacier / Workspaces / Direct
# EC2
ssh -i EC2DevSsh.pem ec2-user@54.175.14.82
