133. [Amazon CloudWatch - Overview](#133)
134. [Analyze CloudWatch metrics - [Lab]](#134)
135. [Create a CloudWatch alarm - [Lab]](#135)
136. [Resource cleanup - [Lab]](#136)
137. [Interpreting CloudWatch logs - [Lab]](#137)
138. [Amazon CloudTrail - Overview](#138)
139. [Setup a CloudTrail - [Lab]](#139)
140. [AWS Personal Health Dashboard - Overview](#140)
141. [Exploring the AWS Personal Health Dashboard - [Lab]](#141)

---

<br>

### 133. Amazon CloudWatch - Overview<a id="133"></a>

<img src="notes/cloud monitoring 1.png" width="700">

<img src="notes/cloud monitoring 2.png" width="700">

<img src="notes/cloud monitoring 3.png" width="700">

<img src="notes/cloud monitoring 4.png" width="700">

### 134. Analyze CloudWatch metrics - [Lab]<a id="134"></a>

- Go to aws console, In auto search type "Cloudwatch", pin it on navigation bar
- click on "CloudWatch"

### 135. Create a CloudWatch alarm - [Lab]<a id="135"></a>

- Go to aws console, In auto search type "Cloudwatch", pin it on navigation bar
- click on "CloudWatch"
- Cloud watch --> Alarms-sidebar --> Create alarm

#### Specify metric and conditions

- Graph: select metric --> EC2 --> per-instance metrics --> ✅ CPUUtilization (click any) --> select metric

- Condition: default
- Scroll down --> Next

#### Configure actions

- Send a notification to the following SNS topic: ✅ Create new topic
- email endpoints: myemail@gmail.com
- click on "Create topic"
- check email and confirm
- Scroll down --> Next

#### Add name and description

- Alarm name: MyFirstSWAlarm
- Scroll down --> Next

#### Preview and create

- Scroll down --> Create alarm

#### How to attach alarm on EC2 instance

- Go to aws console, in auto search type "EC2" open it
- click on instance(running) --> Launch instance

#### Launch instance

- name and tags: MyEC2Instance

#### Application and OS image (Amazon Machine Image)

- Quick start: Amazon Linux
- default: Amazon Linux 2023 AMI (free tier eligible)

#### Instance type

- instance type: t2.micro (free tier eligible)

#### key pair (login)

- click on "create new key pair"
- key pair name: secret
- key pair type: RSA
- private key file format: .ppk (for windows)
- click "create key pair" to download file

#### Network settings

- Firewall (security group): Select existing security group
- ✔️ launch-wizard-1

#### Configure storage

- 8 GB gp3

#### Advance details

- User data: paste below code (HTML markup)

```sh
#!/bin/bash
# User data code
# Proceed to install httpd - (Amazon Linux 2 version)
yum update -y
yum install -y httpd
systemctl start httpd
systemctl enable httpd
echo "<h1> Hello from Mars!!! from $(hostname -f)</h1>" > /var/www/html/index.html
```

#### Summary

- click on "Launch Instance" --> "view all instance"

#### Instances

- select running instance, In Alarm column clink on "➕ No alarm"
- Add or edit alarm: ✅ edit an alarm
- Search for alarm: MyFirstCWAlarm
- Alarm notification: Default_cloudwatch_Alarms_topic2

<img src="notes/alarm threshold.png" width="700">

- Scroll down --> Update

### 136. Resource cleanup - [Lab]<a id="136"></a>

- Go to EC2 --> running instance --> instance --> ✅ MyEC2Instance
- Actions --> terminate

- Go to Amazon SNS --> Topics --> ✅ Default_cloudWatch_alarm_topic2 --> delete
- Go to Amazon SNS --> Subscription --> ✅ 56dfs5c6ds5f656fds --> delete

- Go to CloudWatch --> ALrams --> ✅ MyFirstCWalarm
- Actions --> Delete

### 137. Interpreting CloudWatch logs - [Lab]<a id="137"></a>

### 138. Amazon CloudTrail - Overview<a id="138"></a>

### 139. Setup a CloudTrail - [Lab]<a id="139"></a>

### 140. AWS Personal Health Dashboard - Overview<a id="140"></a>

### 141. Exploring the AWS Personal Health Dashboard - [Lab]<a id="141"></a>
