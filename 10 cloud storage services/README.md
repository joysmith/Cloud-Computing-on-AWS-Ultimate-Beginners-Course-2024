66. [S3 - Overview](#66)
67. [S3 - Working with buckets and objects - [Lab]](#67)
68. [S3 - What is a bucket policy?](#68)
69. [S3 - Create a bucket policy - [Lab]](#69)
70. [S3 - Encryption types](#70)
71. [S3 - Host a static website - [Lab]](#71)
72. [S3 - What is bucket versioning?](#72)
73. [S3 - Enable bucket versioning - [Lab]](#73)
74. [S3 - Introduction to access logging](#74)
75. [S3 - Setup access logging on a bucket - Part 1 - [Lab]](#75)
76. [S3 - What is Replication?](#76)
77. [S3 - Perform Cross-Region-Replication - [Lab]](#77)
78. [S3 - The different types of storage classes](#78)
79. [S3 - Defining object lock](#79)
80. [S3 - Lock an object - [Lab]](#80)
81. [S3 - Setup access logging on a bucket - Part 2 - [Lab]](#81)
82. [S3 - Resource cleanup](#82)
83. [Storage space with EC2?](#83)
84. [EBS - Overview](#84)
85. [EBS - Create an EBS volume - [Lab]](#85)
86. [EBS - Analyzing the snapshot architecture](#86)
87. [EBS - Constructing snapshots - [Lab]](#87)
88. [EFS - Overview](#88)
89. [EC2 Instance store - Overview](#89)

---

### 66. S3 - Overview<a id='66'></a>

<img src="notes/s3 1.png" width="700">

<img src="notes/s3 2.png" width="700">

### 67. S3 - Working with buckets and objects - [Lab]<a id='67'></a>

- Go to aws dashboard in auto search type "S3" pin it to navigation bar
- S3 --> create bucket

Note:

- a bucket is just a folder
- folder inside bucket as seen as object in amazon

#### General configuration

- Bucket name: dss-demo-bucket
- Aws Region: Mumbai
- Scroll down till bottom, click on "Create bucket"

#### Buckets

- select any bucket by clicking on it

#### How to upload file(object) in bucket : File management operations

- minimize browser horizontal then drag and drop image, index.html file
- Scroll down to the bottom click on "Upload"

##### How to view files : File management operations

- Amazon S3 --> Buckets --> dss-demo-bucket --> click on "cat.jpg" --> open

##### How to delete any object from bucket : File management operations

- Amazon S3 --> Buckets --> dss-demo-bucket --> ☑️ cat.jpg --> Delete --> permanently delete --> Delete object

##### How to download any object from bucket : File management operations

- Amazon S3 --> Buckets --> dss-demo-bucket --> ☑️ index.html --> Download

##### How to view files : File management operations

- Amazon S3 --> Buckets --> dss-demo-bucket --> ☑️ index.html --> Open

##### How to move, edit, copy ... files : File management operations

- Amazon S3 --> Buckets --> dss-demo-bucket --> click on "index.html" --> Object actions

##### How to create folder : File management operations

- Amazon S3 --> Buckets --> dss-demo-bucket --> create folder
- folder name: cats

### 68. S3 - What is a bucket policy?<a id='68'></a>

<img src="notes/1 policy.png" width="700">
  
<img src="notes/2 policy.png" width="700">

### 69. S3 - Create a bucket policy - [Lab]<a id='69'></a>

- Amazon S3 --> Buckets --> dss-demo-bucket --> Permission-tab

#### Block public access (bucket settings)

- click on "Edit" --> ❌ Block all public access --> Save changes

#### Bucket policy

- click on "Edit" --> Policy generator (open in new tab)

---

#### AWS policy generator

- select type of policy : S3 bucket policy
- Effect: allow
- Principal: \* (everyone)
- Actions: GetObject
- Amazon resource name: go to bucket copy and paste here with forward-slash with star at end '/_' (arn:aws:s3::dss-demo-bucket/_)
- click on "add statement" --> generate policy --> copy all the json code (switch to Bucket policy tab)

---

#### Bucket policy

- Policy: paste all the json code here
- Scroll down --> "Save changes"

- Amazon S3 --> Buckets --> dss-demo-bucket --> index.html --> object URl (open link in new tab)

### 70. S3 - Encryption types<a id='70'></a>

<img src="notes/encryption 1.png" width="700">

<img src="notes/encryption 2.png" width="700">

<img src="notes/encryption 3.png" width="700">

<img src="notes/encryption 4.png" width="700">

### 71. S3 - Host a static website - [Lab]<a id='71'></a>

- Amazon S3 --> Buckets --> dss-demo-bucket --> Properties-tab
- Scroll down to bottom until you see "Static website hosting"

#### Static website hosting

- click on "Edit"
- Static website hosting: Enable
- Hosting type: Host a static website
- Index document: index.html
- Scroll down --> Save change

- Amazon S3 --> Buckets --> dss-demo-bucket
- Scroll down till "Static website hosting" --> open link in new point

### 72. S3 - What is bucket versioning?<a id='72'></a>

<img src="notes/versoin 1.png" width="700">

<img src="notes/versoin 2.png" width="700">

<img src="notes/versoin 3.png" width="700">

### 73. S3 - Enable bucket versioning - [Lab]<a id='73'></a>

Option 1: When creating new bucket

- Amazon S3 --> Buckets --> Create Bucket

#### General configuration

- Bucket name: dss-demo-bucket
- Aws Region: Mumbai
- Scroll down till bottom, click on "Create bucket"

#### Bucket versioning

- Bucket versioning: ✔️ enable

---

Option 2: After creating new bucket

- Amazon S3 --> Buckets --> dss-demo-bucket --> properties-tab --> Bucket versioning --> edit
- Bucket versioning: ✔️ enable
- Scroll down --> "Save changes"

---

- Amazon S3 --> Buckets --> dss-demo-bucket --> show version(option)
- edit the same index.html file on desktop, that we upload on bucket
- shrink the browser window, drag and drop index.html file to upload --> Upload
- Amazon S3 --> Buckets --> dss-demo-bucket --> index.html --> open
- to rollback to earlier file just delete the new index.html file by selecting --> delete

### 74. S3 - Introduction to access logging<a id='74'></a>

### 75. S3 - Setup access logging on a bucket - Part 1 - [Lab]<a id='75'></a>

### 76. S3 - What is Replication?<a id='76'></a>

### 77. S3 - Perform Cross-Region-Replication - [Lab]<a id='77'></a>

### 78. S3 - The different types of storage classes<a id='78'></a>

### 79. S3 - Defining object lock<a id='79'></a>

### 80. S3 - Lock an object - [Lab]<a id='80'></a>

### 81. S3 - Setup access logging on a bucket - Part 2 - [Lab]<a id='81'></a>

### 82. S3 - Resource cleanup<a id='82'></a>

### 83. Storage space with EC2?<a id='83'></a>

### 84. EBS - Overview<a id='84'></a>

### 85. EBS - Create an EBS volume - [Lab]<a id='85'></a>

### 86. EBS - Analyzing the snapshot architecture<a id='86'></a>

### 87. EBS - Constructing snapshots - [Lab]<a id='87'></a>

### 88. EFS - Overview<a id='88'></a>

### 89. EC2 Instance store - Overview<a id='89'></a>
