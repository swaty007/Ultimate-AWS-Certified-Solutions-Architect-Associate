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
* AWS Cognito
* AWS S3
* AWS SNS
* AWS SQS
* AWS SES
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
* Shield (DDoS Protection)
* Macie (Data Security & Privacy)
* GuardDuty (Threat Detection)
* Inspector (Security Assessment)

Elastic Beanstalk / CodeDeploy / CodePipeline / CodeCommit / Glacier / Workspaces / Direct
# EC2
ssh -i EC2DevSsh.pem ec2-user@54.175.14.82
