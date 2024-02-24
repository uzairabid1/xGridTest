The design diagram explains the high level design of the newsfeed system.
The communication between the Front-End and Back-End would be done using various APIs according to the business needs. We'll use Microservices for every task that should be implemented, the communication between the Microservices would be done through a message broker like RabbitMQ or Amazon MQ and the whole management would be done using Kuberentes. The database schema would consist of tables like User and Post and any other table that we require, we could use AWS RDS for this.
The system will show the new posts to the user which are posted by their friends/followers/groups/pages according to the ranking that would be calculated by the system.

Some APIs could be:
- POST /v1/comment
- POST /v1/like
- POST /v1/post_new
- POST /v1/login

For the Functional requirements:
1. We'll use APIs for content generation and the users would be ablt to see them.
2. For different content we'll be storing objects in a AWS S3 bucket.
3. For ranking positions we'll use a method that would calculate the ranking by how many times the user has interacted with a resource, so the new posts would appear according to the highest interacted resource and also the latest ones.

For the Non-functional requirements:
1. For high scalability we'll use AWS ASG and AWS ALB for autoscaling and load balancing to balance the load from the incoming users.
2. For fault tolerance we'll deploy our system in multiple AZs and back-up the data over different zones. Using an IAC tool like AWS CloudFormation or Terraform could be viable too so if any case of emergency we could start again easily.
3. For high availability and durability we could deploy using AWS EKS and carefully think out deployment strategies and what strategy would be the best for the system and users.
4. For low latency we'll use AWS CloudFront to server our content rapidly.