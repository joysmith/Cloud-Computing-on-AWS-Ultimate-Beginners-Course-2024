90. [Database Introduction](#90)
91. [Relational Database Service (RDS) - Overview](#91)
92. [RDS - Launching our first database - [Lab]](#92)
93. [RDS - Managing snapshots - [Lab]](#93)
94. [RDS - Deployment configurations](#94)
95. [DynamoDB - Overview](#95)
96. [DynamoDB - Create a table - [Lab]](#96)
97. [DynamoDB Accelerator (DAX) - Overview](#97)
98. [ElastiCache - Overview](#98)

---

### 90. Database Introduction<a id="90"></a>

<img src="notes/db 1.png" width="700">

<img src="notes/db 2.png" width="700">

<img src="notes/db 3.png" width="700">

<img src="notes/db 4.png" width="700">

<img src="notes/db 5.png" width="700">

### 91. Relational Database Service (RDS) - Overview<a id="91"></a>

<img src="notes/rds 1.png" width="700">

<img src="notes/rds 2.png" width="700">

### 92. RDS - Launching our first database - [Lab]<a id="92"></a>

- Go to AWS console, in auto search type "RDS", pin it to navigation bar
- click on RDS
- Amazon RDS dashboard, set region to mumbai

#### Resource

- click on DB instances

#### Databases

- click "Create Database"

#### Choose a database creation method

- ✅ standard create

#### Engine options

- Engine type: PostgreSQl

#### Templates

- ✅ Free tier

#### Settings

- DB instance identifier: database-1

#### Credentials Settings

- Master username: joy
- Master password: secret

#### Instance configuration

- default

#### Storage

- default

#### Storage autoscaling

- default

#### Connectivity

- default
- public access: ✔️YEs (to generate endpoint)

#### Additional configuration

- Initial database name: demo_2
- Scroll down --> "Create database"

- Go to RDS --> Databases --> database-1

#### How to crate database snapshot

- Go to RDS --> Databases --> database-1
- Actions --> Take snapshot
- snapshot name: DB-MainSnapshot
- Go to RDS --> Snapshots

### 93. RDS - Managing snapshots - [Lab]<a id="93"></a>

#### How to restore snapshot

By restoring a snapshot we are creating a new database

- Go to RDS --> Snapshots --> db-mainsnapshot
- Actions --> Restore snapshot
- ...same process as above

#### How to copy a snapshot (good for database recovery)

- Go to RDS --> Snapshots --> db-mainsnapshot
- Actions --> copy snapshot
- ...same process as above

#### How to share snapshot

- Go to RDS --> Snapshots --> db-mainsnapshot
- Actions --> share snapshot
- Add other people aws account id

#### How to delete snapshot

- Go to RDS --> Snapshots --> ✅ db-mainsnapshot
- Actions --> Delete snapshot

#### How to delete database

- Go to RDS --> Databases --> ✅ database-1
- Actions --> Delete
- ❌ Create final snapshot
- ❌ Retain automated backups

### 94. RDS - Deployment configurations<a id="94"></a>

<img src="notes/deployment 1.png" width="700">

<img src="notes/deployment  2.png" width="700">

<img src="notes/deployment  3.png" width="700">

<img src="notes/deployment  4.png" width="700">

<img src="notes/deployment  5.png" width="700">

### 95. DynamoDB - Overview<a id="95"></a>

<img src="notes/dynamo 1.png" width="700">

<img src="notes/dynamo 2.png" width="700">

<img src="notes/dynamo 3.png" width="700">

<img src="notes/dynamo 4.png" width="700">

### 96. DynamoDB - Create a table - [Lab]<a id="96"></a>

- incomplete

### 97. DynamoDB Accelerator (DAX) - Overview<a id="97"></a>

- incomplete

### 98. ElastiCache - Overview<a id="98"></a>

<img src="notes/elastic cache.png" width="700">
