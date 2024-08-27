### Practice Exam 4
##### lines: 1902 - 2355

 1. A Developer is migrating existing applications to AWS. These applications use MongoDB as their primary data store, and they will be deployed to Amazon EC2 instances. Management requires that the Developer minimize changes to applications while using AWS services. Which solution should the Developer use to host MongoDB in AWS?
    - Install MongoDB on the same instance where the application is running.
    - Deploy Amazon DocumentDB in MongoDB compatibility mode.
    - Use Amazon API Gateway to translate API calls from MongoDB to Amazon DynamoDB.
    - Replicate the existing MongoDB workload to Amazon DynamoDB.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
    </details>

 2. A company requires that AWS Lambda functions written by Developers log errors so System Administrators can more effectively troubleshoot issues. What should the Developers implement to meet this need?
    - Publish errors to a dedicated Amazon SQS queue.
    - Create an Amazon CloudWatch Events event trigger based on certain Lambda events.
    - Report errors through logging statements in Lambda function code.
    - Set up an Amazon SNS topic that sends logging statements upon failure.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
    </details>

 3. A Developer is writing an application that runs on Amazon EC2 instances in an Auto Scaling group. The application data is stored in an Amazon DynamoDB table and records are constantly updated by all instances. An instance sometimes retrieves old data. The Developer wants to correct this by making sure the reads are strongly consistent. How can the Developer accomplish this?
    - Set ConsistentRead to true when calling Getltem.
    - Create a new DynamoDB Accelerator (DAX) table.
    - Set Consistency to strong when calling UpdateTable.
    - Use the GetShardIterator command.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
    </details>

 4. A Developer has an application that must accept a large amount of incoming data streams and process the data before sending it to many downstream users. Which serverless solution should the Developer use to meet these requirements?
    - Amazon RDS MySQL stored procedure with AWS Lambda.
    - AWS Direct Connect with AWS Lambda.
    - Amazon Kinesis Data Streams with AWS Lambda.
    - Amazon EC2 bash script with AWS Lambda.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
    </details>

 5. An application is experiencing performance issues based on increased demand. This increased demand is on read-only historical records pulled from an Amazon RDS-hosted database with custom views and queries. A Developer must improve performance without changing the database structure. Which approach will improve performance and MINIMIZE management overhead?
    - Deploy Amazon DynamoDB, move all the data, and point to DynamoDB.
    - Deploy Amazon ElastiCache for Redis and cache the data for the application.
    - Deploy Memcached on Amazon EC2 and cache the data for the application.
    - Deploy Amazon DynamoDB Accelerator (DAX) on Amazon RDS to improve cache performance.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
    </details>

 6. A Developer has an Amazon DynamoDB table that must be in provisioned mode to comply with user requirements. The application needs to support the following:  
   Average item size: 10 KB  
   Item reads each second: 10 strongly consistent  
   Item writes each second: 2 transactional  
   Which read and write capacity cost-effectively meets these requirements?
    - Read 10; write 2.
    - Read 30; write 40.
    - Use on-demand scaling.
    - Read 300; write 400.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B  
      Reads per item 4KB
      RCUs needed = 3
      Read capacity = 3 x 10 = 30 

      Writes per item 1KB
      WCUs = 1KB x 2 = 2KB
      Write capacity = 2KB x 10 = 20
      2 transactional writrs = 20 x 2 = 40

    </details>

 7. A company wants to containerize an existing three-tier web application and deploy it to Amazon ECS Fargate. The application is using session data to keep track of user activities. Which approach would provide the BEST user experience?
    - Provision a Redis cluster in Amazon ElastiCache and save the session data in the cluster.
    - Create a session table in Amazon Redshift and save the session data in the database table.
    - Enable session stickiness in the existing Network Load Balancer and manage the session data in the container.
    - Use an Amazon S3 bucket as data store and save the session data in the bucket.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C  

      A is the way to go according to latter link  
      A: Distributed session management  
      B: 
      C: Sticky sessions  
      D: 

      https://www.awsadvent.com/2016/12/17/session-management-for-web-applications-on-aws-cloud/  
      https://aws.amazon.com/caching/session-management/  
      https://www.reddit.com/r/aws/comments/hn5zoe/are_sticky_sessions_the_best_option_for/
    </details>

 8. An application is using a single-node Amazon ElastiCache for Redis instance to improve read performance. Over time, demand for the application has increased exponentially, which has increased the load on the ElastiCache instance. It is critical that this cache layer handles the load and is resilient in case of node failures. What can the Developer do to address the load and resiliency requirements?
    - Add a read replica instance.
    - Migrate to a Memcached cluster.
    - Migrate to an Amazon Elasticsearch Service cluster.
    - Vertically scale the ElastiCache instance.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A  

      A: Spread reads across nodes. When the primary fails, the primary fails over to a read replica instance.  
      B: Makes it easy to set up, manage, and scale a distributed in-memory data store  
      C: Benefits? fast time-to-value, high performance  
      D: Helps workload traffic  

      https://docs.aws.amazon.com/AmazonElastiCache/latest/red-ug/Replication.html
    </details>

 9. A Developer is investigating an application's performance issues. The application consists of hundreds of microservices, and a single API call can potentially have a deep call stack. The Developer must isolate the component that is causing the issue. Which AWS service or feature should the Developer use to gather information about what is happening and isolate the fault?
    - AWS X-Ray.
    - VPC Flow Logs.
    - Amazon GuardDuty.
    - Amazon Macie.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A  

      A: Monitor components and services that make up your cloud applications  
      B: Capture information about the IP traffic going to and from network interfaces in your VPC  
      C: GuardDuty is a threat detection service  
      D: Macie is a fully managed data security and data privacy service  
      https://docs.aws.amazon.com/xray/latest/devguide/aws-xray.html 
    </details>

 10. A Company runs continuous integration/continuous delivery (CI/CD) pipelines for its application on AWS CodePipeline. A Developer must write unit tests and run them as part of the pipelines before staging the artifacts for testing. How should the Developer incorporate unit tests as part of CI/CD pipelines?
    - Create a separate CodePipeline pipeline to run unit tests.
    - Update the AWS CodeBuild specification to include a phase for running unit tests.
    - Install the AWS CodeDeploy agent on an Amazon EC2 instance to run unit tests.
    - Create a testing branch in AWS CodeCommit to run unit tests.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B

      B: New feature of CodeBuild:  
      https://aws.amazon.com/pt/blogs/devops/test-reports-with-aws-codebuild/  
      D: More related to branching strategy rather than running unit test as part of CI/CD pipeline
    </details>

 11. An application has the following requirements: Performance efficiency of seconds with up to a minute of latency. The data storage size may grow up to thousands of terabytes. Per-message sizes may vary between 100 KB and 100 MB. Data can be stored as key/value stores supporting eventual consistency. What is the MOST cost-effective AWS service to meet these requirements?
    - Amazon DynamoDB.
    - Amazon S3.
    - Amazon RDS (with a MySQL engine).
    - Amazon ElastiCache.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A  

      A: Supports key/value and document data models   
      B: Object storage service  
      C: Relational database
    </details>

 12. A Developer must allow guest users without logins to access an Amazon Cognito-enabled site to view files stored within an Amazon S3 bucket. How should the Developer meet these requirements?
    - Create a blank user ID in a user pool, add to the user group, and grant access to AWS resources.
    - Create a new identity pool, enable access to authenticated identities, and grant access to AWS resources.
    - Create a new user pool, enable access to authenticated identifies, and grant access to AWS resources.
    - Create a new user pool, disable authentication access, and grant access to AWS resources.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D  

      Question is asking about guest users without logins. Therefore we want unauthenticated access.  

      https://docs.aws.amazon.com/location/latest/developerguide/authenticating-using-cognito.html
    </details>

 13. A Developer has written code for an application and wants to share it with other Developers on the team to receive feedback. The shared application code needs to be stored long-term with multiple versions and batch change tracking. Which AWS service should the Developer use?
    - AWS CodeBuild.
    - Amazon S3.
    - AWS CodeCommit.
    - AWS Cloud9.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
    </details>

 14. A Developer has discovered that an application responsible for processing messages in an Amazon SQS queue is routinely falling behind. The application is capable of processing multiple messages in one execution, but is only receiving one message at a time. What should the Developer do to increase the number of messages the application receives?
    - Call the ChangeMessageVisibility API for the queue and set MaxNumberOfMessages to a value greater than the default of 1.
    - Call the AddPermission API to set MaxNumberOfMessages for the ReceiveMessage action to a value greater than the default of 1.
    - Call the ReceiveMessage API to set MaxNumberOfMessages to a value greater than the default of 1.
    - Call the SetQueueAttributes API for the queue and set MaxNumberOfMessages to a value greater than the default of 1.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C  

      B: You can't set MaxNumberofMessages with this API   
      C: Specify the number of messages to receive from the queue (up to 10). Set the maximum number of messages to return  
      https://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_ReceiveMessage.html
    </details>

 15. A Developer registered an AWS Lambda function as a target for an Application Load Balancer (ALB) using a CLI command. However, the Lambda function is not being invoked when the client sends requests through the ALB. Why is the Lambda function not being invoked?
    - A Lambda function cannot be registered as a target for an ALB.
    - A Lambda function can be registered with an ALB using AWS Management Console only.
    - The permissions to invoke the Lambda function are missing.
    - Cross-zone is not enabled on the ALB.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C  

      When registering an AWS Lambda function as a target for an Application Load Balancer (ALB), you need to grant the ALB permission to invoke the Lambda function.  
      https://docs.amazonaws.cn/en_us/lambda/latest/dg/services-alb.html
    </details>

 16. A company provides APIs as a service and commits to a service level agreement (SLA) with all its users. To comply with each SLA, what should the company do?
    - Enable throttling limits for each method in Amazon API Gateway.
    - Create a usage plan for each user and request API keys to access the APIs.
    - Enable API rate limiting in Amazon Cognito for each user.
    - Enable default throttling limits for each stage after deploying the APIs.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D  

      https://docs.aws.amazon.com/apigateway/latest/developerguide/api-gateway-request-throttling.html
    </details>

 17. A Developer is preparing a deployment package using AWS CloudFormation. The package consists of two separate templates: one for the infrastructure and one for the application. The application has to be inside the VPC that is created from the infrastructure template. How can the application stack refer to the VPC created from the infrastructure template?
    - Use the Ref function to import the VPC into the application stack from the infrastructure template.
    - Use the export flag in the infrastructure template, and then use the Fn::ImportValue function in the application template.
    - Use the DependsOn attribute to specify that the application instance depends on the VPC in the application template.
    - Use the Fn::GetAtt function to include the attribute of the VPC in the application template.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A  

      A: When you pass the logical ID of this resource to the intrinsic Ref function, Ref returns the ID of the VPC  
      B: Fn::ImportValue is typically used to create cross-reference stacks  
      C: DependsOn lets you specify the creation of a resource follows another. Then, a resource is created only after the creation of the resource specified in the DependsOn attribute  
      D: Returns the value of an attribute from a resource in the template  
      https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-ec2-vpc.html
    </details>

 18. A Developer needs to create an application that supports Security Assertion Markup Language (SAML) and Facebook authentication. It must also allow access to AWS services, such as Amazon DynamoDB. Which AWS service or feature will meet these requirements with the LEAST amount of additional coding?
    - AWS AppSync.
    - Amazon Cognito identity pools.
    - Amazon Cognito user pools.
    - Amazon Lambda@Edge.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C  

      B: Provides temporary AWS credentials for users who are guests  
      C: User directory for web and mobile authentication  

      https://docs.aws.amazon.com/cognito/latest/developerguide/cognito-user-identity-pools.html  
    </details>

 19. A Developer is trying to monitor an application's status by running a cron job that returns 1 if the service is up and 0 if the service is down. The Developer created code that uses an AWS CLI put-metric-alarm command to publish the custom metrics to Amazon CloudWatch and create an alarm. However, the Developer is unable to create an alarm as the custom metrics do not appear in the CloudWatch console. What is causing this issue?
    - Sending custom metrics using the CLI is not supported.
    - The Developer needs to use the put-metric-data command.
    - The Developer must use a unified CloudWatch agent to publish custom metrics.
    - The code is not running on an Amazon EC2 instance.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B  

      A: Not true
      B: Publish a single data point for a new or existing metric  
      C: Unified CloudWatch agent lets you: gather metrics from EC2 instances, collect metrics from on-premises servers, retrieve custom metrics from your services or collect logs from Amazon EC2 instances and on-premises servers  

      https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/publishingMetrics.html
    </details>

 20. A Developer has written an application that runs on Amazon EC2 instances and generates a value every minute. The Developer wants to monitor and graph the values generated over time without logging in to the instance each time. Which approach should the Developer use to achieve this goal?
    - Use the Amazon CloudWatch metrics reported by default for all EC2 instances. View each value from the CloudWatch console.
    - Develop the application to store each value in a file on Amazon S3 every minute with the timestamp as the name.
    - Publish each generated value as a custom metric to Amazon CloudWatch using available AWS SDKs.
    - Store each value as a variable and add the variable to the list of EC2 metrics that should be reported to the Amazon CloudWatch console.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C  

      A: EC2 instances don't report to CloudWatch by default  
      B: S3 is not for monitoring values  
      C: We need custom metrics, best answer   
      D: As A)  

      https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/publishingMetrics.html
    </details>

 21. A Development team decides to adopt a continuous integration/continuous delivery (CI/CD) process using AWS CodePipeline and AWS CodeCommit for a new application. However, management wants a person to review and approve the code before it is deployed to production. How can the Development team add a manual approver to the CI/CD pipeline?
    - Use AWS SES to send an email to approvers when their action is required. Develop a simple application that allows approvers to accept or reject a build. Invoke an AWS Lambda function to advance the pipeline when a build is accepted.
    - If approved, add an approved tag when pushing changes to the CodeCommit repository. CodePipeline will proceed to build and deploy approved commits without interruption.
    - Add an approval step to CodeCommit. Commits will not be saved until approved.
    - Add an approval action to the pipeline. Configure the approval action to publish to an Amazon SNS topic when approval is required. The pipeline execution will stop and wait for an approval.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D  

      B: Question wants a manual approval  
      C: Question is asking how to implement approval before deployment to production rather than before updating the codebase. Therefore, approval action in the pipeline is required rather than an approval step in AWS CodeCommit repository.  
      D: Need one stage for approval in CodePipeline.  

      https://docs.aws.amazon.com/codepipeline/latest/userguide/approvals-action-add.html
    </details>

 22. A Developer is building a serverless application using AWS Lambda and must create a REST API using an HTTP GET method. What needs to be defined to meet this requirement? (Choose TWO)
    - A Lambda@Edge function.
    - An Amazon API Gateway with a Lambda function.
    - An exposed GET method in an Amazon API Gateway.
    - An exposed GET method in the Lambda function.
    - An exposed GET method in Amazon Route 53.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B, C  

      A: Compute service that lets you execute functions that customize the content that Amazon Cloudfront delivers  
      B, D: See below resource

      https://docs.aws.amazon.com/lambda/latest/dg/services-apigateway.html
    </details>

 23. A Developer is writing an application in AWS Lambda. To simplify testing and deployments, the Developer needs the database connection string to be easily changed without modifying the Lambda code. How can this requirement be met?
    - Store the connection string as a secret in AWS Secrets Manager.
    - Store the connection string in an IAM user account.
    - Store the connection string in AWS KMS.
    - Store the connection string as a Lambda layer.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A  

      A: This also gives the opportunity to rotate the credentials  
      https://docs.aws.amazon.com/secretsmanager/latest/userguide/intro.html 
    </details>

 24. A company is launching an ecommerce website and will host the static data in Amazon S3. The company expects approximately 1,000 transactions per second (TPS) for GET and PUT requests in total. Logging must be enabled to track all requests and must be retained for auditing purposes. What is the MOST cost-effective solution?
    - Enable AWS CloudTrail logging for the S3 bucket-level action and create a lifecycle policy to move the data from the log bucket to Amazon S3 Glacier in 90 days.
    - Enable S3 server access logging and create a lifecycle policy to expire the data in 90 days.
    - Enable AWS CloudTrail logging for the S3 bucket-level action and create a lifecycle policy to expire the data in 90 days.
    - Enable S3 server access logging and create a lifecycle policy to move the data to Amazon S3 Glacier in 90 days.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D  
      https://docs.aws.amazon.com/AmazonS3/latest/userguide/ServerLogs.html  
      https://docs.aws.amazon.com/AmazonS3/latest/userguide/lifecycle-transition-general-considerations.html
    </details>

 25. A Developer decides to store highly secure data in Amazon S3 and wants to implement server-side encryption (SSE) with granular control of who can access the master key. Company policy requires that the master key be created, rotated, and disabled easily when needed, all for security reasons. Which solution should be used to meet these requirements?
    - SSE with Amazon S3 managed keys (SSE-S3).
    - SSE with AWS KMS managed keys (SSE-KMS).
    - SSE with AWS Secrets Manager.
    - SSE with customer-provided encryption keys.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C  

      A: Best for users who want to ensure their data is encrypted at rest but do not require control over the encryption keys    
      B: Allows for key rotation, centralized key management, and detailed access control over who can use the keys.  
      C: Lets you retrieve, manage, and rotate database credentials, application credentials, OAuth tokens, API keys etc. throughout their lifecycles. 
      D: Encrypt data client-side before uploading it to S3. It's useful when the user wants complete control over the encryption process and keys, using AWS KMS for key management  
      https://docs.aws.amazon.com/secretsmanager/latest/userguide/intro.html
    </details>

 26. A Developer is migrating an on-premises application to AWS. The application currently takes user uploads and saves them to a local directory on the server. All uploads must be saved and made immediately available to all instances in an Auto Scaling group. Which approach will meet these requirements?
    - Use Amazon EBS and configure the application AMI to use a snapshot of the same EBS instance on boot.
    - Use Amazon S3 and rearchitect the application so all uploads are placed in S3.
    - Use instance storage and share it between instances launched from the same Amazon Machine Image (AMI).
    - Use Amazon EBS and file synchronization software to achieve eventual consistency among the Auto Scaling group.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
    </details>

 27. A Developer implemented a static website hosted in Amazon S3 that makes web service requests hosted in Amazon API Gateway and AWS Lambda. The site is showing an error that reads: 'No 'Access-Control-Allow-Origin' header is present on the requested resource. Origin 'null' is therefore not allowed access.' What should the Developer do to resolve this issue?
    - Enable cross-origin resource sharing (CORS) on the S3 bucket.
    - Enable cross-origin resource sharing (CORS) for the method in API Gateway.
    - Add the Access-Control-Request-Method header to the request.
    - Add the Access-Control-Request-Headers header to the request.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
    </details>

 28. A Developer is building an application that needs to store data in Amazon S3. Management requires that the data be encrypted before it is sent to Amazon S3 for storage. The encryption keys need to be managed by the Security team. Which approach should the Developer take to meet these requirements?
    - Implement server-side encryption using customer-provided encryption keys (SSE-C).
    - Implement server-side encryption by using a client-side master key.
    - Implement client-side encryption using an AWS KMS managed customer master key (CMK).
    - Implement client-side encryption using Amazon S3 managed keys.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
    </details>

 29. A Developer has written an Amazon Kinesis Data Streams application. As usage grows and traffic increases over time, the application is regularly receiving ProvisionedThroughputExceededException error messages. Which steps should the Developer take to resolve the error? (Choose TWO)
    - Use Auto Scaling to scale the stream for better performance.
    - Increase the delay between the GetRecords call and the PutRecords call.
    - Increase the number of shards in the data stream.
    - Specify a shard iterator using the ShardIterator parameter.
    - Implement exponential backoff on the GetRecords call and the PutRecords call.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C, E
    </details>

 30. A Developer is publishing critical log data to a log group in Amazon CloudWatch Logs, which was created 2 months ago. The Developer must encrypt the log data using an AWS KMS customer master key (CMK) so future data can be encrypted to comply with the company's security policy. How can the Developer meet this requirement?
    - Use the CloudWatch Logs console and enable the encrypt feature on the log group.
    - Use the AWS CLI create-log-group command and specify the key Amazon Resource Name (ARN).
    - Use the KMS console and associate the CMK with the log group.
    - Use the AWS CLI associate-kms-key command and specify the key Amazon Resource Name (ARN)

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
    </details>

 31. A Developer has code running on Amazon EC2 instances that needs read-only access to an Amazon DynamoDB table. What is the MOST secure approach the Developer should take to accomplish this task?
    - Create a user access key for each EC2 instance with read-only access to DynamoDB. Place the keys in the code. Redeploy the code as keys rotate.
    - Use an IAM role with an AmazonDynamoDBReadOnlyAccess policy applied to the EC2 instances.
    - Run all code with only AWS account root user access keys to ensure maximum access to services.
    - Use an IAM role with Administrator access applied to the EC2 instance.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
    </details>

 32. A Developer migrated a web application to AWS. As part of the migration, the Developer implemented an automated continuous integration/continuous improvement (CI/CD) process using a blue/green deployment. The deployment provisions new Amazon EC2 instances in an Auto Scaling group behind a new Application Load Balancer. After the migration was completed, the Developer began receiving complaints from users getting booted out of the system. The system also requires users to log in after every new deployment. How can these issues be resolved?
    - Use rolling updates instead of a blue/green deployment.
    - Externalize the user sessions to Amazon ElastiCache.
    - Turn on sticky sessions in the Application Load Balancer.
    - Use multicast to replicate session information.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
    </details>

 33. A Developer wants to insert a record into an Amazon DynamoDB table as soon as a new file is added to an Amazon S3 bucket. Which set of steps would be necessary to achieve this?
    - Create an event with Amazon CloudWatch Events that will monitor the S3 bucket and then insert the records into DynamoDB.
    - Configure an S3 event to invoke a Lambda function that inserts records into DynamoDB.
    - Create a Lambda function that will poll the S3 bucket and then insert the records into DynamoDB.
    - Create a cron job that will run at a scheduled time and insert the records into DynamoDB.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
    </details>

 34. A company has implemented AWS CodeDeploy as part of its cloud native CI/CD stack. The company enables automatic rollbacks while deploying a new version of a popular web application from in-place to Amazon EC2. What occurs if the deployment of the new version fails due to code regression?
    - The last known good deployment is automatically restored using the snapshot stored in Amazon S3.
    - CodeDeploy switches the Amazon Route 53 alias records back to the known good green deployment and terminates the failed blue deployment.
    - A new deployment of the last known version of the application is deployed with a new deployment ID.
    - AWS CodePipeline promotes the most recent deployment with a SUCCEEDED status to production.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
    </details>

 35. A Developer uses Amazon S3 buckets for static website hosting. The Developer creates one S3 bucket for the code and another S3 bucket for the assets, such as image and video files. Access is denied when a user attempts to access the assets bucket from the code bucket, with the website application showing a 403 error. How should the Developer solve this issue?
    - Create an IAM role and apply it to the assets bucket for the code bucket to be granted access.
    - Edit the bucket policy of the assets bucket to allow access from the code bucket.
    - Edit the bucket policy of the assets bucket to open access to all principals.
    - Change the code bucket to use AWS Lambda functions instead of static website hosting.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
    </details>

 36. A company has implemented AWS CodePipeline to automate its release pipelines. The Development team is writing an AWS Lambda function what will send notifications for state changes of each of the actions in the stages. Which steps must be taken to associate the Lambda function with the event source?
    - Create a trigger that invokes the Lambda function from the Lambda console by selecting CodePipeline as the event source.
    - Create an event trigger and specify the Lambda function from the CodePipeline console.
    - Create an Amazon CloudWatch alarm that monitors status changes in Code Pipeline and triggers the Lambda function.
    - Create an Amazon CloudWatch Events rule that uses CodePipeline as an event source.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
    </details>

 37. A Developer has built an application running on AWS Lambda using AWS Serverless Application Model (AWS SAM). What is the correct order of execution to successfully deploy the application?
    - 1. Build the SAM template in Amazon EC2. 2. Package the SAM template to Amazon EBS storage. 3. Deploy the SAM template from Amazon EBS.
    - 1. Build the SAM template locally. 2. Package the SAM template onto Amazon S3. 3. Deploy the SAM template from Amazon S3.
    - 1. Build the SAM template locally. 2. Deploy the SAM template from Amazon S3. 3. Package the SAM template for use.
    - 1. Build the SAM template locally. 2. Package the SAM template from AWS CodeCommit. 3. Deploy the SAM template to CodeCommit.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
    </details>

 38. A company wants to migrate an imaging service to Amazon EC2 while following security best practices. The images are sourced and read from a non-public Amazon S3 bucket. What should a Developer do to meet these requirements?
    - Create an IAM user with read-only permissions for the S3 bucket. Temporarily store the user credentials in the Amazon EBS volume of the EC2 instance.
    - Create an IAM user with read-only permissions for the S3 bucket. Temporarily store the user credentials in the user data of the EC2 instance.
    - Create an EC2 service role with read-only permissions for the S3 bucket. Attach the role to the EC2 instance.
    - Create an S3 service role with read-only permissions for the S3 bucket. Attach the role to the EC2 instance.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
    </details>

 39. A Development team wants to immediately build and deploy an application whenever there is a change to the source code. Which approaches could be used to trigger the deployment? (Choose TWO)
    - Store the source code in an Amazon S3 bucket. Configure AWS CodePipeline to start whenever a file in the bucket changes.
    - Store the source code in an encrypted Amazon EBS volume. Configure AWS CodePipeline to start whenever a file in the volume changes.
    - Store the source code in an AWS CodeCommit repository. Configure AWS CodePipeline to start whenever a change is committed to the repository.
    - Store the source code in an Amazon S3 bucket. Configure AWS CodePipeline to start every 15 minutes.
    - Store the source code in an Amazon EC2 instance's ephemeral storage. Configure the instance to start AWS CodePipeline whenever there are changes to the source code.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B, C
    </details>

 40. An application ingests a large number of small messages and stores them in a database. The application uses AWS Lambda. A Development team is making changes to the application's processing logic. In testing, it is taking more than 15 minutes to process each message. The team is concerned the current backend may time out. Which changes should be made to the backend system to ensure each message is processed in the MOST scalable way?
    - Add the messages to an Amazon SQS queue. Set up and Amazon EC2 instance to poll the queue and process messages as they arrive.
    - Add the messages to an Amazon SQS queue. Set up Amazon EC2 instances in an Auto Scaling group to poll the queue and process the messages as they arrive.
    - Create a support ticket to increase the Lambda timeout to 60 minutes to allow for increased processing time.
    - Change the application to directly insert the body of the message into an Amazon RDS database.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
    </details>

 41. A Software Engineer developed an AWS Lambda function in Node.js to do some CPU-intensive data processing. With the default settings, the Lambda function takes about 5 minutes to complete. Which approach should a Developer take to increase the speed of completion?
    - Instead of using Node.js, rewrite the Lambda function using Python.
    - Instead of packaging the libraries in the ZIP file with the function, move them to a Lambda layer and use the layer with the function.
    - Allocate the maximum available CPU units to the function.
    - Increase the available memory to the function.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
    </details>

 42. An online retail company has deployed a serverless application with AWS Lambda, Amazon API Gateway, Amazon S3, and Amazon DynamoDB using AWS CloudFormation. The company rolled out a new release with major upgrades to the Lambda function and deployed the release to production. Subsequently, the application stopped working. Which solution should bring the application back up as quickly as possible?
    - Redeploy the application on Amazon EC2 so the Lambda function can resolve dependencies.
    - Migrate DynamoDB to Amazon RDS and redeploy the Lambda function.
    - Roll back the Lambda function to the previous version.
    - Deploy the latest Lambda function in a different Region.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
    </details>

 43. A Developer is writing an application that will run on Amazon EC2 instances in an Auto Scaling group. The Developer wants to externalize session state to support the application. Which services will meet these needs? (Choose TWO)
    - Amazon DynamoDB.
    - Amazon Cognito.
    - Amazon ElastiCache.
    - Amazon EBS.
    - Amazon SQS.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A, C
    </details>

 44. A Developer has a legacy application that is hosted on-premises. Other applications hosted on AWS depend on the on-premises application for proper functioning. In case of any application errors, the Developer wants to be able to use Amazon CloudWatch to monitor and troubleshoot all applications from one place. How can the Developer accomplish this?
    - Install an AWS SDK on the on-premises server to automatically send logs to CloudWatch.
    - Download the CloudWatch agent to the on-premises server. Configure the agent to use IAM user credentials with permissions for CloudWatch.
    - Upload log files from the on-premises server to Amazon S3 and have CloudWatch read the files.
    - Upload log files from the on-premises server to an Amazon EC2 instance and have the instance forward the logs to CloudWatch.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
    </details>

 45. A company is developing an application that will be accessed through the Amazon API Gateway REST API. Registered users should be the only ones who can access certain resources of this API. The token being used should expire automatically and needs to be refreshed periodically. How can a Developer meet these requirements?
    - Create an Amazon Cognito identity pool, configure the Amazon Cognito Authorizer in API Gateway, and use the temporary credentials generated by the identity pool.
    - Create and maintain a database record for each user with a corresponding token and use an AWS Lambda authorizer in API Gateway.
    - Create an Amazon Cognito user pool, configure the Cognito Authorizer in API Gateway, and use the identity or access token.
    - Create an IAM user for each API user, attach an invoke permissions policy to the API, and use an IAM authorizer in API Gateway.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
    </details>

 46. A Developer is working on a serverless project based in Java. Initial testing shows a cold start takes about 8 seconds on average for AWS Lambda functions. What should the Developer do to reduce the cold start time? (Choose TWO)
    - Add the Spring Framework to the project and enable dependency injection.
    - Reduce the deployment package by including only needed modules from the AWS SDK for Java.
    - Increase the memory allocation setting for the Lambda function.
    - Increase the timeout setting for the Lambda function.
    - Change the Lambda invocation mode from synchronous to asynchronous.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A, D
    </details>

 47. A Developer is leveraging a Border Gateway Protocol (BGP)-based AWS VPN connection to connect from on-premises to Amazon EC2 instances in the Developer's account. The Developer is able to access an EC2 instance in subnet A, but is unable to access an EC2 instance in subnet B in the same VPC. Which logs can the Developer use to verify whether the traffic is reaching subnet B?
    - VPN logs.
    - BGP logs
    - VPC Flow Logs.
    - AWS CloudTrail logs.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
    </details>

48. A Developer has created a new AWS IAM user that has s3 putObject permission to write to a specific Amazon S3 bucket. This S3 bucket uses server-side encryption with AWS KMS managed keys (SSE-KMS) as the default encryption. Using the access key and secret key of the IAM user, the application received an access denied error when calling the PutObject API. How can this issue be resolved?
    - Update the policy of the IAM user to allow the s3 Encrypt action.
    - Update the bucket policy of the S3 bucket to allow the IAM user to upload objects.
    - Update the policy of the IAM user to allow the kms:GenerateDataKey action.
    - Update the ACL of the S3 bucket to allow the IAM user to upload objects.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
    </details>

 49. A company has a web application that uses an Amazon Cognito user pool for authentication. The company wants to create a login page with the company logo. What should a Developer do to meet these requirements?
    - Create a hosted user interface in Amazon Cognito and customize it with the company logo.
    - Create a login page with the company logo and upload it to Amazon Cognito.
    - Create a login page in Amazon API Gateway with the logo and save the link in Amazon Cognito.
    - Upload the logo to the Amazon Cognito app settings and point to the logo on a custom login page.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
    </details>

 50. A Developer is working on an AWS Lambda function that accesses Amazon DynamoDB. The Lambda function must retrieve an item and update some of its attributes, or create the item if it does not exist. The Lambda function has access to the primary key. Which IAM permissions should the Developer request for the Lambda function to achieve this functionality?
    - dynamodb:DeleteItem dynamodb:GetItem dynamodb:PutItem.
    - dynamodb:UpdateItem dynamodb:GetItem dynamodb:DescribeTable.
    - dynamodb:GetRecords dynamodb:PutItem dynamodb:UpdateTable.
    - dynamodb:UpdateItem dynamodb:GetItem dynamodb:PutItem.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
    </details>
