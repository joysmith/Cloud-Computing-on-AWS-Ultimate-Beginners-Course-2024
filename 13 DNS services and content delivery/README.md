116. [AWS Route 53 - Overview](#116)
117. [Register a domain name - [Lab]](#117)
118. [Amazon Route 53 - Domain name issues](#118)
119. [Amazon Certificate manager - Overview](#119)
120. [Provision a SSL/TLS certificate - [Lab]](#120)
121. [Assign a SSL/TLS certificate to a load balancer - [Optional Lab]](#121)
122. [CloudFront - Overview](#122)
123. [CloudFront: Practical pre-cleanup - [Lab]](#123)
124. [Create a CloudFront distribution - [Lab]](#124)
125. [AWS Global Accelerator - Overview](#125)
126. [Evaluating the use of Global Accelerator - [Lab]](#126)

---

<br>

### 116. AWS Route 53 - Overview<a id="116"></a>

<img src="notes/route 1.png" width="700">

<img src="notes/route 2.png" width="700">

<img src="notes/route 3.png" width="700">

<img src="notes/route 4.png" width="700">

<img src="notes/route 5.png" width="700">

<img src="notes/route 6.png" width="700">

<img src="notes/route 7.png" width="700">

<img src="notes/route 8.png" width="700">

<img src="notes/route 9.png" width="700">

### 117. Register/Buy a domain name - [Lab]<a id="117"></a>

- Go to AWS console, In auto search type "Route 53", pin it to navigation bar
- click on "Route 53"
- click on "Get Started"

- Go to Route 53 --> Domain-sidebar --> Register domains
- click on "Register domain"
- search for domain: "electronictetris.com" --> select --> proceed to checkout --> Next -->
- Go to Route 53 Dashboard --> Hosted zones

### 118. Amazon Route 53 - Domain name issues<a id="118"></a>

### 119. Amazon Certificate manager - Overview<a id="119"></a>

<img src="notes/certificate 1.png" width="700">

<img src="notes/certificate 2.png" width="700">

### 120. Provision a SSL/TLS certificate - [Lab]<a id="120"></a>

- Go to AWS console, In auto search type "Certificate Manager", pin it to navigation bar
- click on "Certificate Manager"
- click on "Request a certificate"

#### Request certificate

- Certificate type: Request a public certificate --> Next

#### Domain name

- Fully qualified domain name: electronictetris.com
- Add another name to this certificate: www.electronictetris.com

#### Validation method

- ✅ DNS validation

#### Key algorithm

- ✅ RSA 2048
- Scroll down --> Request

- Go to AWS Certificate Manger --> Certificates --> certificate_id 012fd512dsf10

---

- Go to Route 53 Dashboard--> Hosted zone --> electronictetris.com --> Create Record
- (new tab) Go to AWS Certificate Manger --> Certificates --> certificate_id 012fd512dsf10

#### Quick create record

- Record name: CNAME name (copy from AWS Certificate Manger --> Certificates --> certificate_id 012fd512dsf10)
- Record value: CNAME value (copy from AWS Certificate Manger --> Certificates --> certificate_id 012fd512dsf10)
- Record type: CNAME

- click on "Add another record" for www.electronictetris.com
- Record name: CNAME name (copy from AWS Certificate Manger --> Certificates --> certificate_id 012fd512dsf10)
- Record value: CNAME value (copy from AWS Certificate Manger --> Certificates --> certificate_id 012fd512dsf10)
- Record type: CNAME
- Scroll down --> Create records

### 121. Assign a SSL/TLS certificate to a load balancer - [Optional Lab]<a id="121"></a>

- Go to aws console, in auto search type "EC2" open it
- click on instance(running) --> Launch instance

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

- Firewall (security group): select existing security group- launch-wizard-1

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

- On left sidebar click hamburger icon, select Load Balancing-dropdown --> Load balancers

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

- Add rule (for http, address:ipv4)
- type: http, source: anywhere(0.0.0.0/0)

- Add rule (for http, address:ipv6)
- type: http, source: anywhere(::/0)

- Add rule (for https, address:ipv4 )
- type: https, source: anywhere(0.0.0.0/0)

- Add rule (for https, address:ipv6)
- type: https, source: anywhere(::/0)

- Scroll down in the end click on "Create security group"

#### Security group (continue..)

- security group: DemoAppLB-SG

#### Listeners and routing

- Open in new tab by clicking on "Create target group"

##### Basic configuration

- choose a target type: instances
- Target group name: DemoAppTG
- Scroll down till end click --> "Next"

##### Register target

- select server1, click on "Include as pending below"

##### Review target

- Target: default
- Scroll down till end click --> "Create target group"

#### Listening and routing (continue)

- Default action: DemoAppTG
- Scroll down till end click --> "Create load balancer"

#### Create Application Load Balancer

- click on "View load balancer"

---

- Go to EC2 dashboard --> Load balancers --> ✅ DemoAppLB --> 🔼 look bottom click
- click on listener-tab --> Add Listener

#### Listener detail:HTTP:81

- Protocol: HTTPS
- port: 443
- default actions: forward
- Target group: DemoAppTG

#### Secure listener settings

- Default SSL/TLS certificate: From ACM, electronictetris.com
- Scroll down --> Next

---

- EC2 --> Load balancers --> DemoAppLB
- click on Listener-tab

#### Listeners

- ✅ HTTP:80
- Actions --> edit listener

#### Listener details

- 1. Forward to --> Remove
- Add action --> Redirect

##### 1. Redirect

- Protocol: HTTPS
- Port: 443
- Scroll down --> Save change

---

- EC2 --> Load balancers --> ✅ DemoAppLB
- click on Listener-tab

---

- Go to Route 53 --> Domain-sidebar --> Hosted zone --> electronictetris.com --> Create record

#### Quick create record

- ✅ Alias
- Route traffic to: Alias to application and classic load balancer
- region: mumbai
- Load balancer: dualstack.DemoAppLB-0221546156156...

- Add another record
- Record name: www
- Record type: A
- ✅ Alias
- Route traffic to: Alias to application and classic load balancer
- region: mumbai
- Load balancer: dualstack.DemoAppLB-0221546156156...
- Scroll down --> Create records

---

- go to google search and type "electronictetris.com"
- go to google search and type "wwww.electronictetris.com"

---

#### Resource clean up

- EC2 --> Load balancer --> ✅ DemoAppLB
- Actions --> Delete Load balancer

- EC2 --> Target group --> ✅ DemoAppLB
- Actions --> Delete

- EC2 --> Security group --> ✅ DemoAppLB
- Actions --> Delete security group

- Route 53 --> Hosted zones --> ✅ wwww.electronictetris.com" --> ✅ electronictetris.com"
- Delete records

- Ec2 --> Running instance --> instance --> ✅ Server 1
- Actions --> Terminate

### 122. CloudFront/CDN - Overview<a id="122"></a>

<img src="notes/cloud front 1.png" width="700">

<img src="notes/cloud front 2.png" width="700">

<img src="notes/cloud front 3.png" width="700">

<img src="notes/cloud front 4.png" width="700">

### 123. CloudFront: Practical pre-cleanup - [Lab]<a id="123"></a>

- Go to aws dashboard in auto search type "S3" pin it to navigation bar
- Amazon S3 --> buckets
- ✅ dss-demo-bucket --> empty
- ✅ dss-demo-bucket --> delete

### 124. Create a CloudFront distribution - [Lab]<a id="124"></a>

### 125. AWS Global Accelerator - Overview<a id="125"></a>

<img src="notes/global acclerator.png" width="700">

### 126. Evaluating the use of Global Accelerator - [Lab]<a id="126"></a>
