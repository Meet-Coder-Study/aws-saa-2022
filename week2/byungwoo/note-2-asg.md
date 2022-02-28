## ASG (Auto Scaling Group)
- scale-out  to match increased load
- scale-in to match decreased load
- Automatically Register new instances to LB

## ASG in AWS

- minimum size
- actual size / desired capacity
- maximum size

## ASG with LC/LT

- LC (Launch Configuration)
    - AMI, Instnace Type
    - EC2 User Data
    - EBS Volumes
    - Security Groups
    - SSH Key Pair
- Min Size / Max Size / Initial Capacity
- Network + Subnets Information
- Scaling Policies

## Auto Scaling Alarms

- ASG based on CloudWatch alarms
- alarm monitors a metric (such as avg CPU)
- metrics are computed for overall ASG instances
- based on alarm, we can create scale-in/out policies

## Auto Scaling New Rules

- “better” rules
- Target Avg CPU Usage
- Number of requests on ELB per instance
- Avg Network In
- Avg Network Out

## Auto Scaling Custom Metric

- ex. number of connected users
1. send custom metric from app on EC2 to CloudWatch (PutMetric API)
2. create ClougWatch alarm as scaling policy for ASG

## ASG Brain Dump (Good to Know)

- Scaling policies can be based on CPU, Network and custom metric, or schedule
- ASG use LC or LT
- to update ASG, must provide new LC or LT
- IAM roles attached to ASG get assigned to EC2
- ASG is free. you pay for EC2 behind
- if EC2 terminated, ASG automatically create new ones as a replacement, extra safety!
- ASG can terminate instances marked as unhealthy by an LB

## ASG - Dynamic Scaling Policies

### Target Tracking Scaling

- simple & easy
- ex) I want to avg ASG CPU to stay arount 40%

### Simple / Step Scaling

- ex) when a CloudWatch alarm is triggered (CPU > 70%), add 2 units
- ex) when a CloudWatch alarm is triggered (CPU < 30%), remote 1 unit

### Scheduled Actions

- ex) increase min capacity to 10 at 5pm Fridays

## ASG - Predictive Sacling

- predictive scaling: forecast loat and schedule scaling ahead
- based on ML

## Good metrics to scale in

- CPU Utilization: avg CPU across EC2
- RequestCountperTarget: number of requests per EC2 is stable
- Avg Network In / Out: if app is network bound (ex) upload, download)
- Any custom metric (using CloudWatch PutMetric API)

## ASG - Scaling Cooldowns

- after scaling activity cooldown period begins (default 300s)
- during cooldown period, ASG will not scale-in/out (to allow for metrics to stabilize)
- Advice: Use read-to-use AMI to reduce configuration time in order to serve request faster and reduce cooldown period

## ASG for SA (Solution Architects)

### ASG default termination policy

1. find AZ has most EC2
2. delete one with oldest LC
- ASG tries to balance the number of EC2 across AZ

### ASG Lifecycle Hooks

- as soon as instance is launchd in ASG, it’s in service
- you can perform extra steps before instance goes in service (pending state)
- you can perform extra steps before instance goes is terminated (terminating state)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e072ac7b-198e-48d2-b4e6-3c9204c314fe/Untitled.png)

## LT vs. LC

### Both

- ID of AMI, instance type, key pair, sg, tags, EC2 user-data...

### LC (legacy)

- must be re-created every-time

### LT (new, recommanded)

- can have multiple versions
- create parameter subsets (for re-use and inheritance)
- provision using both on-demand and spot instances (or mix)
- can use T2 unlimited burst feature