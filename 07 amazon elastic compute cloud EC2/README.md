38. [EC2 - Overview](#38)
39. [EC2 - Launching our first EC2 instance - [Lab]](#39)
40. [EC2 - Changing Instance states - [Lab]](#40)
41. [EC2 - Introduction to Security groups](#41)
42. [EC2 - Managing our Security groups - [Lab]](#42)
43. [EC2 - What are the different instance types?](#43)
44. [EC2 - Exploring various instance types - [Lab]](#44)
45. [EC2 - SSH with Windows - [Optional]](#45)
46. [EC2 - Remotely connect to our EC2 Instance - [Optional]](#46)
47. [EC2 - Introduction to Instance connect](#47)
48. [EC2 - Utilize Instance connect - [Lab]](#48)
49. [EC2 - Resource cleanup - [Lab]](#49)
50. [EC2 - Instance pricing options](#50)
51. [EC2 - Instance pricing options - Deep dive - [Lab]](#51)
52. [EC2 - Quick start AMI - [Reminder]](#52)
53. [EC2 - What is an AMI?](#53)
54. [EC2 - Building our own AMI - [Lab]](#54)

---

<br>

### 38. EC2 - Overview<a id="38"></a>

<img src="notes/ec2 1.png" width="700">

<img src="notes/ec2 2.png" width="700">

<img src="notes/ec2 3.png" width="700">

<img src="notes/ec2 4.png" width="700">

<img src="notes/ec2 5.png" width="700">

<img src="notes/ec2 6.png" width="700">

<img src="notes/ec2 7.png" width="700">

### 39. EC2 - Launching our first EC2 instance - [Lab]<a id="39"></a>

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

- Firewall (security group): Create security group
- ✔️ Allow SSH traffic from "anywhere"
- ✔️ Allow HTTP traffic from the internet

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

- select running instance, copy public-IPv4 paste to browser url

### 40. EC2 - Changing Instance states - [Lab]<a id="40"></a>

- Go to EC2 instance --> running instance --> select any instance
- instance state: stop instance
- instance state: start instance
- instance state: terminate instance

NOTE: whenever we stop and start the instance, public-IPv4 address change and assigned new address.

### 41. EC2 - Introduction to Security groups<a id="41"></a>

<img src="notes/sg 1.png" width="700">

<img src="notes/sg 2.png" width="700">

<img src="notes/sg 3.png" width="700">

<img src="notes/sg 4.png" width="700">

<img src="notes/sg 5.png" width="700">

<img src="notes/sg 6.png" width="700">

<img src="notes/sg 7.png" width="700">

### 42. EC2 - Managing our Security groups - [Lab]<a id="42"></a>

- Go to aws console --> EC2 --> running instance --> select instance --> click on Security-tab
- In left side click hamburger icon --> "Network & Security"-dropdown --> Security Groups --> select any

#### Inbound rules

- click on "Edit inbound rule" --> add rule
- type: HTTP
- Anywhere: 0.0.0.0/0
- save

#### Outbound rules

- click on "Edit outbound rule"
-

### 43. EC2 - What are the different instance types?<a id="43"></a>

<img src="notes/type 1.png" width="700">

<img src="notes/type 2.png" width="700">

<img src="notes/type 3.png" width="700">

<img src="notes/type 4.png" width="700">

<img src="notes/type 5.png" width="700">

<img src="notes/type 6.png" width="700">

### 44. EC2 - Exploring various instance types - [Lab]<a id="44"></a>

### 45. EC2 - SSH with Windows - [Optional]<a id="45"></a>

### 46. EC2 - Remotely connect to our EC2 Instance - [Optional]<a id="46"></a>

### 47. EC2 - Introduction to Instance connect<a id="47"></a>

### 48. EC2 - Utilize Instance connect - [Lab]<a id="48"></a>

### 49. EC2 - Resource cleanup - [Lab]<a id="49"></a>

### 50. EC2 - Instance pricing options<a id="50"></a>

### 51. EC2 - Instance pricing options - Deep dive - [Lab]<a id="51"></a>

### 52. EC2 - Quick start AMI - [Reminder]<a id="52"></a>

### 53. EC2 - What is an AMI?<a id="53"></a>

### 54. EC2 - Building our own AMI - [Lab]<a id="54"></a>
