# Cloud Formation Task

**Answers to Invincible Brands Interview Task questions – AWS Cloud Engineer**
---

This task creates a basic EC2 Auto Scaling template with Cloud Formation. 

Question 1.
---

a. Create a Cloud Formation template that accomodates parameters for defaults like AMI-ID, AppSubnet, ASGSecurityGroupList, etc

b. AutoScaling Configuration Parameters:
- "ScalingCreateTimeOut",
- "ScalingUpdateTimeOut",
- "ScalingMin",
- "ScalingTermination",
- "EC2ScaleUpCooldown"
- "EC2ScaleDownCooldown",
- "EC2ScaleUpAdjustment",
- "EC2ScaleDownAdjustment",
- "HealthCheckGracePeriod",
- "HealthCheckType",
- "ScalingNotificationTopic",
- "DesiredCapacity",
- "MinInstancesInService",
- "TerminatedInstances",
- "ScalingMax",

c. “NFSLocation” Parameter:
- Default:“nfs.example.com:/data”

d. “AppSubnet” Parameter

e. “ASGSecurityGroupList” Parameter


**Answer**:
Code can be reference in task-ec2-autoscaling.yml


Question 2: 
---

### To accommodate huge spikes of traffic, for example - thousands of users online within a couple of minutes. What recommendations can I proffer for the Autoscaling Group to serve as little 50x errors as possible when scaling aggressively?

**Answer:**  Mostly, 50x errors associated with the Autoscaling Group configurations are usually a result of insufficient capacity, the ASG not scaling fast enough to meet demand. The load balancer, EC2 instances, and Autoscaling work together to allow applications scale in the most efficient way.

a)	The first recommendation would be to monitor metrics from the ELB, as well as from the Load balancers e.g. real time health check fails, request counts when there is a spike. This would inform the Auto Scaling Group Configurations, such as tweaking values like cooldown, HealthCheckGracePeriod etc.

b)	If the load changes/ spikes are predictable – In a case whereby the spikes experienced by the company are traceable to specific or repeated occurrences e.g. a traffic surge on Wednesday, steady through till Friday. Then, a recommendation would be to rely on a scheduled scaling policy. The aggressive scaling out can be preempted proactively such that the application is prepared for the surge by temporarily increasing capacity. In this case, the instances are fully in “running” state when the traffic spike hits. Hence reducing number of possible 50x errors.

c)	Target Tracking scaling policies: A predefined metric like ALBRequestCountPerTarget, ASGAverageCPUUtilization, ASGAverageNetworkOut monitored via Amazon CloudWatch and used to determine when to trigger the scaling in or out of the application tier (Auto Scaling Group) can be really helpful to keeping 50x errors to a minimum.



Question 3.
---

### Define and describe a method in detail to use a Redis Cluster via ElastiCache as central PHP Session storage for the AutoScalingGroup above.

https://aws.amazon.com/getting-started/hands-on/building-fast-session-caching-with-amazon-elasticache-for-redis/2/

This short example explains handing and storing server-side sessions in a key-value store such as Redis. It enables the PHP environment to enjoy a distributed system of session storage such that the sessions are not dependent on the specific instance serving the session. If one EC2 instance fails, the session is not lost.


