127. [What is Docker?](#127)
128. [Managing docker containers on AWS](#128)
129. [Running docker containers on ECS - Deep dive](#129)
130. [What is Serverless computing?](#130)
131. [AWS Lambda - Overview](#131)
132. [Create a virtual function with AWS Lambda - [Lab]](#132)

---

<br>

### 127. What is Docker?<a id="127"></a>

<img src="notes/docker 1.png" width="700">

<img src="notes/docker 2.png" width="700">

<img src="notes/docker 3.png" width="700">

<img src="notes/docker 4.png" width="700">

<img src="notes/docker 5.png" width="700">

### 128. Managing docker containers on AWS<a id="128"></a>

<img src="notes/service 1.png" width="700">

<img src="notes/service 2.png" width="700">

<img src="notes/service 3.png" width="700">

<img src="notes/service 4.png" width="700">

<img src="notes/service 5.png" width="700">

<img src="notes/service 6.png" width="700">

<img src="notes/service 7.png" width="700">

<img src="notes/service 8.png" width="700">

### 129. Running docker containers on ECS - Deep dive<a id="129"></a>

<img src="notes/ecs 1.png" width="700">

<img src="notes/ecs 2.png" width="700">

<img src="notes/ecs 3.png" width="700">

### 130. What is Serverless computing?<a id="130"></a>

<img src="notes/serverless 1.png" width="700">

<img src="notes/serverless 2.png" width="700">

### 131. AWS Lambda - Overview<a id="131"></a>

<img src="notes/lambda function.png" width="700">

### 132. Create a virtual function with AWS Lambda - [Lab]<a id="132"></a>

- Go to aws console, In auto search type 'lambda' then pin it to navigation bar
- click on Lambda
- click on Next:Lambda responds to events --> Scale seamlessly --> Create a function

#### Create Function

- ✅ Use a blueprint

#### Basic information

- Blueprint name: Hello world function python3.7
- function name: myLambdaFunction
- Execution role: create a new role with basic Lambda permissions

#### Lambda function code

- default
- scroll down --> Create function

#### myLambdaFunction

- Go to Lambda --> Functions --> myLambdaFunction

#### Code source

- click on "Test"
- Test event creation: Create new event
- Event name: MyLambdaTest
- scroll down --> Save
- click on "Test"

#### How to delete Lambda function

- Go to Lambda --> Functions --> ✅ myLambdaFunction
- Actions --> Delete
