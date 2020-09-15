# CF_Task

This task create a basic EC2 Auto Scaling template with Cloud Formation. 



Parameters for defaults like AMI-ID, AppSubnet, ASGSecurityGroupList, etc
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
