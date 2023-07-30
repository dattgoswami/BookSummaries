# AWS Fundamentals Cheat Sheet

## Key Takeaways and Summary for Software Engineers

### **1. Account Creation & Security**
- For account creation, an email address, phone number, and a credit/debit card (for validation only) are required.
- Use AWS IAM (Identity and Access Management) for account protection.
- Enable multi-factor authentication (MFA) for increased security.
- Use AWS IAM users for daily tasks, not root user credentials.

### **2. AWS Core Services**
- **Compute**: Use EC2 for virtual machines, ECS and Fargate for managing and orchestrating containers, and Lambda for running code without managing servers.
- **Database & Storage**: RDS for managed SQL databases, DynamoDB for scalable applications, and S3 for object storage.
- **Messaging**: Use SQS for message queues, SNS for pub/sub systems, and EventBridge for an event-driven architecture.
- **Networking**: Use API Gateway to expose applications' endpoints, Route 53 for high availability, VPC for resource isolation, and CloudFront for content distribution.

### **3. AWS Cost Management**
- Understand the AWS Free Tier and Pricing Calculators.
- Use AWS Budgets and Cost Explorer for cost tracking.
- Implement cost allocation tags and restrict IAM permissions to prevent accidental costly operations.

### **4. AWS Shared Responsibility Model**
- AWS is responsible for security "of" the cloud (infrastructure).
- Users are responsible for security "in" the cloud (configuration of AWS services).

### **5. AWS IAM and Policies**
- Use IAM users, groups, and roles to manage access to AWS resources.
- Understand and implement policies (identity-based, resource-based, managed policies, and inline policies).
- Leverage tools like IAM Access Analyzer and AWS Policy Simulator.

## Service-specific key takeaways:

### **6. Amazon EC2**
- EC2 instances can be controlled via network and security options to protect from external threats.
- Understand various purchase options: On-Demand, Reserved/Savings Plan, Spot, Dedicated Instances & Hosts, On-Demand Capacity Reservations.
- Utilize system status checks and instance status checks for troubleshooting.
- Use pre-configured AMIs from the AWS Marketplace for various requirements.
- Use Auto-Scaling to manage instances in response to varying workloads.
- The default storage is ephemeral unless you select EBS, S3, or EFS for persistent storage.

### **7. Amazon Elastic Container Service (ECS)**
- ECS provides orchestration for Docker containers. Key terms include: Containers, Task Definition, Task, Service, Cluster, and Launch Types.
- ECS Launch Types include: EC2, Fargate, and External.
- Scheduling is a crucial part of assigning tasks within a cluster.
- Use AWS Elastic Container Registry (ECR) for hosting and sharing images and artifacts.
- Understand the steps involved in creating an ECS Service and the Docker commands for ECR.
- Understand the lifecycle states of a task and how to run standalone tasks on demand.
- Remember to clean up resources after use.

### **8. Fargate**
- A serverless option within ECS that manages the underlying infrastructure. You only need to specify the task definition, cluster, and number of tasks.

### **9. AWS Lambda**
- Lambda is a serverless compute service that abstracts away infrastructure management.
- Understand the differences between 'Event' and 'RequestResponse' invocation types.
- Functions can be invoked synchronously (blocking) and asynchronously.
- Understand the function configuration process and how to integrate with VPC.
- Lambda integrates with CloudWatch for monitoring.

### **10. Migration to AWS and Database Solutions**
- Proficient knowledge of migrating applications to AWS with minimal interruptions.
- Understand how to switch database solutions such as shifting data from an on-premise directory to DynamoDB.

## General AWS Tips for Software Engineers
- Follow the principle of least privilege for permissions.
- Rotate access keys regularly.
- Use MFA and do not use root account for daily tasks.
- Understand and use IAM for managing access to AWS resources.
- Leverage serverless solutions for event-driven workloads and EC2 for steady, high-computing requirements.
- Understand and manage AWS costs efficiently.
- Use proper instance types and storage options in EC2 according to the requirements.
- Leverage the benefits of Infrastructure as Code (IaC) for effective resource management.
- Always monitor costs and terminate instances when no longer needed.
- Make use of the Marketplace for specific AMIs.
- Pay attention to additional usage fees when using the Marketplace.
- Utilize the target group's health monitoring feature effectively.
- Remember, AWS provides several services. Knowing how to use them effectively is a core skill for modern software engineers.

## More in-depth key takeaways:

### Lambda
1. Creating a Node.js function can be done directly in the AWS console.
2. Dependencies can be externalized into a Lambda layer for optimized deployment.
3. A Lambda function can invoke another function given the correct permissions.
4. Lambda functions can be exposed to the internet via API Gateway or Function URLs.
5. EFS provides durable storage, but requires the function to be attached to a VPC.
6. Use Lambda@Edge to run code closer to clients.
7. Lambda cost depends on memory settings, execution times, and ephemeral storage.

### Lambda Best Practices
1. Keep functions stateless and idempotent.
2. Monitor key metrics with CloudWatch Alarms.
3. Choose a compatible database solution, such as DynamoDB.
4. Use Step Functions for complex workflows and Lambda Layers for shared dependencies.
5. Environment variables help keep function code independent of the environment.
6. Build event-driven, resilient architectures and use structured logging.
7. Minimize cold start times by optimizing external dependencies, using warm-up requests, bootstrapping code outside the handler, and optimizing memory allocation.

### Databases & Storage
1. Amazon RDS is a fully-managed SQL database service.
2. Amazon S3 provides durable storage for unstructured data.
3. Amazon DynamoDB is a NoSQL database optimized for low-latency, high-throughput access.
4. Managed AWS services help focus on application development and offer features like encryption and backups for data security and protection.

### Amazon RDS and DynamoDB
1. AWS data centers are divided into regions and availability zones for optimized performance and resilience.
2. Multi-AZ databases in RDS increase resilience by automatic replication.
3. Read Replicas increase performance for read-heavy workloads.
4. RDS supports automated backups and AES-256 encryption.
5. RDS pricing is based on instance class, number of nodes, pricing mode, storage, and backups.

### DynamoDB
1. Key concepts: Primary Key, Composite Keys, Scalar Types, Document Types, Set Types.
2. Operations include creating a table, scan, query, and batch operations.
3. DynamoDB doesn't enforce a schema, allows for many empty fields, and cannot do Joins across tables.
4. Marshalers return the "normal" JSON object from the DynamoDB JSON.

### DynamoDB Advanced
1. DynamoDB assigns data to partitions based on the partition key for scalability.
2. Global Secondary Indexes define a new primary key; Local Secondary Indexes add sort keys.
3. Expression Attributes prevent the use of reserved variables.
4. DynamoDB supports inserting, removing, and updating items.
5. On-Demand capacity is best for unknown traffic patterns; Provisioned capacity is cheaper for predictable traffic.

### Amazon S3
1. S3 provides object storage with any amount of data.
2. S3 Lifecycle Policies manage objects within a bucket based on their age.
3. Bucket Policies grant permissions to your bucket and all objects inside it.
4. Batch operations cluster operations into a single API request.
5. Object Locks ensure data integrity; Object Versioning allows rollback to previous states.
6. S3 pricing depends on storage class, requests, data transfer, and usage of advanced features

## Networking

**Amazon Route 53**
1. Scalable and highly available Domain Name System (DNS) service.
2. Translates domain names into numeric IP addresses.
3. Utilizes Alias Records for routing traffic to AWS resources.
4. Enables Multi-answer Routing for flexibility in IP selection.

**Amazon Virtual Private Cloud (VPC)**
1. Enables launching of AWS resources in an isolated virtual network.
2. Provides control over the accessibility of resources.
3. Key components: subnets, security groups, network access control lists (ACLs), routing tables, and Classless Inter-Domain Routing (CIDR) blocks.
4. Supports VPC Peering and VPC Sharing for increased routing flexibility.
5. Uses Flow Logs for monitoring IP traffic.
6. Provides internet access for resources in public subnets via Internet Gateways.

**CloudFront**
1. Globally distributed Content Delivery Network (CDN) providing faster performance and reliability.
2. Supports multiple origins, AWS Web Application Firewall (WAF), and integrates with CloudWatch for monitoring.
3. Can run custom code directly on CloudFront’s edge nodes.

**API Gateway**
- A managed service for creating, deploying, and managing APIs.
- Supports RESTful, HTTP, and WebSocket API types.
- Features include endpoint creation, access control, integrations, request validation, data transformations, gateway responses, CORS, API deployment, caching, monitoring.
- Offers authentication and authorization via OAuth2, OpenID Connect, Lambda Authorizers, and Mutual TLS (mTLS).
- Usage plans restrict the number of API calls per client.
- Supports basic request validation and data transformation using Velocity Template Language (VTL).
- Custom responses can be defined for error handling.
- Custom domain names can be used for endpoint deployment.

## AWS Message Queuing

**SQS - Simple Queue Service**
1. At-Least-Once and Exactly-Once delivery principles govern the delivery of messages in SQS.
2. Idempotency ensures that an operation can be performed multiple times without changing the result beyond the initial application.
3. Standard Queues offer high throughput with no guarantee of message order, while FIFO Queues guarantee message order and Exactly-Once Delivery.
4. FIFO queues tend to be more costly but support Exactly-Once Delivery, reducing the need for application-level idempotency.
5. DLQs are used to handle failures and retries, providing insights into these failures.
6. Various parameters govern SQS's operations, including Retention Period, Visibility Timeout, Delivery Delay, and polling method (Long Polling vs Short Polling).

**SNS - Simple Notification Service**
1. SNS uses a pub/sub model to send messages to topics and receive them from subscribers.
2. It supports both Application-to-Application and Application-to-Person communications.
3. The Fanout Pattern helps in event handling by distributing events to multiple consumers.
4. Access to topics can be controlled via IAM topic policies.
5. SNS offers Standard and FIFO topics, Deduplication IDs, Message Archives, Message Filtering, Delivery Retries, and DLQs for server-side errors.

**AWS EventBridge**
1. EventBus manages events, with three types: Default Bus, Custom Bus, and Partner Event Bus.
2. Event Rules route events based on match patterns.
3. Targets are the consumers of events.
4. Events are JSON messages with 'detail', 'detail-type', and 'source' fields.
5. EventBridge supports scheduling tasks with EventBridge Scheduler.
6. Archive & Replay functionality allows saving all events and replaying them to the Event Bus.
7. Schema Bindings define the objects & attributes of your events, providing a clear description of event properties.
8. EventBridge provides Schema Discovery, Code Bindings, DLQs for Target Delivery, a Subscription Pattern for flexible subscription management, and security features.

## Continuous Integration and Continuous Delivery (CI/CD)

**AWS CodeBuild**
1. Executes application building and scripts.
2. Uses Build Images & Containers, and Build Specs for building jobs.
3. Build outputs can be archived and saved at S3.

**AWS CodePipeline**
1. Orchestrates build jobs and deployments.
2. Constructs Pipelines and allows for Approval Steps.
3. Works with CodeBuild for robust CI/CD processes.

**CI/CD with AWS CodeBuild and CodePipeline**
1. CodeBuild compiles source code, runs tests, produces software packages, and deploys them.
2. CodePipeline builds delivery pipelines from checking out source code to deploying infrastructure.

## Infrastructure Monitoring and Tracing

**CloudWatch**
- Used for collecting, monitoring, and visualizing data from AWS resources and applications.
- Logs provide insights into a distributed application's behavior, support complex reports, aggregations, and advanced queries.
- Metrics act as a metric repository, collecting data about service usage, performance, and behavior.
- Alarms notify when a system or service reaches a pre-defined threshold.
- CloudWatch dashboards present an overview of various metrics and alarms, useful for sharing insights across an organization.
- CloudWatch Synthetics can create canaries for regular health checks of web applications.

**AWS X-Ray**
- Used to trace user requests throughout a distributed system, useful for understanding user interaction with the system and debugging user sessions.

## Infrastructure as Code (IaC)

**AWS CloudFormation**
- Allows declarative infrastructure management, resource provisioning, handling errors, and rolling back states.
- Concepts include Templates, Stacks, and Change Sets.

**AWS CDK**
- Infrastructure as Code tool that uses a familiar programming language, such as Python or TypeScript, to define infrastructure.
- Concepts include Constructs, Stacks, and Apps.
- Comes with its own CLI for initializing, synthesizing, and deploying your app.
- IAM Management in CDK simplifies working with IAM by providing capabilities to grant permissions to roles or users easily.
- Constructs Hub is a platform for sharing different types of CDK constructs.

**Serverless Framework**
- Abstraction tool for AWS services, offering a simpler way to configure and deploy Lambda functions and other AWS resources.
- Can be installed globally or locally via NPM or YARN.
- Configuration is defined in a serverless.yml file, also supporting other formats.
- Supports the creation of custom resources directly in the Serverless configuration file.
- Offers integration with other Infrastructure-as-Code tools like Terraform.
- Provides plugins to extend its functionality.

## Other Key Points
1. SQS, SNS, and EventBridge all play crucial roles in building event-driven architectures, improving application robustness and error tolerance.
2. Both SNS and EventBridge operate based on usage, making it essential to understand your usage to manage costs.
3. As a software engineer, understanding and leveraging these AWS services will help you design and implement more scalable, decoupled, and resilient systems. Always consider the type of service and its respective features that best suit your application's needs.

## Best Practices
- Iterate your architecture and code.
- Choose solutions that best suit your application.
- Continuously improve your software.
- Reduce boilerplate code and avoid bugs by using API Gateway.
- Consider using Swagger to create an API Gateway.
- Utilize API Gateway stage variables for storing and retrieving runtime variables.
- Use mock integration types to create a gateway without specifying a backend integration.
- Directly register domains with Route 53 or delegate administration to Route 53 from any DNS provider.
- Understand the type of data you need to log

## Pricing
- CloudWatch: Pricing varies based on the chosen feature. Logs - $0.50 per GB ingested, $0.03 per GB archived, $0.02 per GB of queried data. Dashboards - $3 per dashboard per month. Alarms - $0.10 per standard alarm, $0.30 per high-resolution alarm.
- X-Ray: $5 per 1 million traces recorded, $0.50 per 1 million traces retrieved or scanned. Additional charges for Insights feature.
- AWS CloudFormation and CDK: Free service, but charges apply for resources managed through these tools.
- Serverless Framework: Free tier available, with higher plans offering additional benefits.

This cheatsheet can serve as a refresher for AWS features and services, a quick reference guide while designing or troubleshooting systems, or as a starting point for deep-dives into AWS services and practices. Happy learning and building!

Remember to always read the latest AWS documentation to stay updated with any changes or updates to these services. Also, feel free to share this with your fellow developers or teams to help them speed up their understanding of AWS services and how to leverage them effectively. 
