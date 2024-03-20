57. [Elastic Load Balancing (ELB) - Overview](#57)
58. [Create an application load balancer - [Lab]](#58)
59. [Testing our application load balancer - [Lab]](#59)
60. [Auto Scaling Groups (ASG) - Overview](#60)
61. [Specify a launch template - [Lab]](#61)
62. [Create an auto scaling group - [Lab]](#62)
63. [Auto scaling groups - Deep dive - [Lab]](#63)
64. [Testing our auto scaling group - [Lab]](#64)
65. [ELB/ASG - Resource cleanup - [Lab]](#65)

---

<br>

### 57. Elastic Load Balancing (ELB) - Overview<a id="57"></a>

<img src="notes/elb 1.png" width="700">

<img src="notes/elb 2.png" width="700">

<img src="notes/elb 3.png" width="700">

<img src="notes/elb 4.png" width="700">

<img src="notes/elb 5.png" width="700">

<img src="notes/elb 6.png" width="700">

<img src="notes/elb 7.png" width="700">

<img src="notes/elb 8.png" width="700">

<img src="notes/elb 9.png" width="700">

### 58. Create an application load balancer - [Lab]<a id="58"></a> Part-1

We have to create 2 instance to apply, Elastic(application) load balancer

- Go to aws console --> EC2 --> running instance --> Launch instance

#### Launch instance

- name and tags: Server 1

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

- Firewall (security group): select existing security group
- Security group: launch-wizard-1

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

---

- Now create second instance

- Go to aws console --> EC2 --> running instance --> Launch instance

#### Launch instance

- name and tags: Server 2

#### Application and OS image (Amazon Machine Image)

- Quick start: Amazon Linux
- default: Amazon Linux 2023 AMI (free tier eligible)

#### Instance type

- instance type: t2.micro (free tier eligible)

#### key pair (login)

- we can use previous key pair OR we can create new one

- click on "create new key pair"
- key pair name: secret
- key pair type: RSA
- private key file format: .ppk (for windows)
- click "create key pair" to download file

#### Network settings

- Firewall (security group): select existing security group
- Security group: launch-wizard-1

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

---

- On left side click hamburger icon, select Load Balancing-dropdown --> Load balancers

#### Load balancers

- click on "Create load balancer"

#### Load balancers types

- Application: create

#### Basic configuration

- load balancer name: demoAppLB
- scheme: internet-facing
- Ip address type: IPv4

#### Network mapping

- VPC: default
- Mappings: us-east-2a, us-east-2b

#### Security group

- remove the default one
- Open on new tab by click on "create new security group"

##### Basic details

- Security group name: demoAppLB-SG
- Description: demoAppLB-SG
- VPC: default

##### Inbound rules

- type: http, source: anywhere(0.0.0.0/0)
- Scroll down in the end click on "Create security group"

#### Security group (continue..)

- security group: DemoAppLB-SG

#### Listeners and routing

- Open in new tab by clicking on "Create target group"

##### Basic configuration

- choose a target type: instances
- Target group name: DemoAppTG
- Scroll down till end click on "Next"

##### Register target

- select server1 & server2, click on "Include as pending below"

##### Review target

- default
- Scroll down till end click on "Create target group"

#### Listening and routing (continue)

- Default action: DemoAppTG
- Scroll down till end click on "Create load balancer"

#### Create Application Load Balancer

- click on "View load balancer"

### 59. Testing our application load balancer - [Lab]<a id="59"></a> Part-2

#### Create Application Load Balancer

- click on "View load balancer"
- Check the status: Active (this will take 5 min)
- copy DNS: DemoAppLB8.64....., paste to chrome url, refresh and notice private-ipv4-address is changing

---

- Go to aws console --> EC2 --> running instance
- Open all running instance, stop server 1, then refresh chrome to notice only server 2 ip address is active

Note- Every time we stop and start server the public and private ip changes

### 60. Auto Scaling Groups (ASG) - Overview<a id="60"></a>

<img src="notes/asg 1.png" width="700">

<img src="notes/asg 2.png" width="700">

<img src="notes/asg 3.png" width="700">

<img src="notes/asg 4.png" width="700">

<img src="notes/asg 5.png" width="700">

<img src="notes/asg 6.png" width="700">

<img src="notes/asg 7.png" width="700">

<img src="notes/asg 8.png" width="700">

### 61. Specify a launch template - [Lab]<a id="61"></a> Part-1

- Go to EC2 dashboard, under Instance-dropdown --> Launch templates --> "Create launch template"

#### Launch template name and description

- Launch template name: MyTemplate
- Template version description: MyTemplate

#### Application and OS Image (Amazon Machine Image)

- Quick start: Amazon Linux

#### Instance type

- instance type: t2.micro

#### Key pair login

- create new key pair OR use old one

#### Network settings

- Firewall (security group): select existing security group
- security group: launch-wizard-1

#### Advanced details

- user data: paste this code in user data

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

#### summary

- click on "Create launch template" --> view launch template

### 62. Create an auto scaling group - [Lab]<a id="62"></a> Part-2

- Go to EC2 dashboard, under Auto Scaling-dropdown--> Auto scaling Groups --> "Create Auto scaling group"

#### Name

- Auto scaling group name: MyFirstASG

#### Launch template

- Launch template: Mytemplate
- clink "Next"

#### Network

- Availability zone and subsets: select alphabetically in order, 2a, 2b, 2c
- Scroll down click "Next"

#### Load balancing

- use the option below to attach...: Attach tp existing load balancer

#### Attach to an existing load balancing

- existing load balancer target groups: DemoAppTg

#### Health checks

- ✔️ Turn on elastic load balancing health check
- Scroll down till end click "Next"

#### Group size

- Desired capacity: 2
- Minimum capacity: 1
- Maximum capacity: 3
- Scroll down till end click on "Next"

#### Add notification

- default
- click on "Next"

#### Add tags

- default
- click on "Next"

#### Review

- default
- Scroll down till end, click on "Create Auto Scaling group"

### 63. Auto scaling groups - Deep dive - [Lab]<a id="63"></a> Part-3

- Select auto scaling groups, and in bottom click on "^" to open menu
- click on each tab for reviewing and configuring and making changes

### 64. Testing our auto scaling group - [Lab]<a id="64"></a> Part-4

- Go to EC2 dashboard, under Load Balancing-drop down --> Load Balancer(new tab)

#### How to edit desired, maximum, minimum

- Go to EC2 dashboard, under Auto Scaling --> Auto Scaling Groups
- select any then click "edit"
- Desired capacity: 1
- minimum capacity: 1
- maximum capacity: 2
- Scroll down to bottom, click on "Update"

### 65. ELB/ASG - Resource cleanup - [Lab]<a id="65"></a>

#### How to delete auto scaling group

- Go to EC2 dashboard, under Auto Scaling --> Auto Scaling Groups
- select any group --> Delete --> Delete load balancer

#### How to delete

- Go to EC2 dashboard, under Load Balancing --> Load Balancers
- select any --> actions

- Go to EC2 dashboard, under Load Balancing --> Target Group
- select any --> Actions --> Delete

#### How to delete launch template

- Go to EC2 dashboard, under Instances --> Launch Template
- select any --> Actions --> Delete template
