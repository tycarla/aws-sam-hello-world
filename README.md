### **What is a Lambda Function?**

AWS Lambda is a serverless computing service that runs your code in response to events. You don’t need to manage servers—just upload your function, and AWS handles everything else.

👉 **Key Features:**

- Runs **only when triggered** (e.g., via API Gateway, S3, DynamoDB, etc.)
- **Pay-as-you-go** pricing—no charges when idle
- Supports multiple programming languages (Python, Node.js, Java, etc.)
- **Auto-scales** without extra configuration

### **Why Use a Serverless Backend for a Low-Budget Project?**

If you have little to no budget, running a backend on AWS Lambda makes sense because:

✅ **No server costs** when it's idle

✅ **No need for infrastructure management**

✅ **Scales automatically** with traffic

✅ **Easy to integrate** with other AWS services

💡 *Example Use Case:*

You're building a small API for a project, but you don’t want to pay for a full-time server. AWS Lambda runs **only when needed**, making it super cost-efficient.

### **Setting Up AWS Lambda Locally**

Now let’s set up our Lambda function locally using AWS SAM (Serverless Application Model).

**Install Required Tools**

✅ Install **AWS CLI** ([Download](https://aws.amazon.com/cli/))

✅ Install **AWS SAM CLI** ([Download](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/install-sam-cli.html))

✅ Install **Docker** (Download) – needed to emulate AWS Lambda locally

Check if SAM is installed:

```bash
sam --version
```

**Using AWS SAM to Create a Lambda Function Locally**

Now, let’s create a simple **Hello World** Lambda function and test it locally.

### **Initialize a New AWS SAM Project**

Run this command in your terminal:

```bash
sam init
```

You'll be asked a few questions:

- **Choose "Quick start template"**
- **Choose "AWS Quick Start Templates"**
- **Select runtime: Python 3.x**
- **Project name:** hello-world-lambda

Once it's done, go into the project folder:

```bash
cd hello-world-lambda
```

### **Running Lambda Locally with AWS SAM**

**Check the Function Code**

Go to the hello_world folder and open app.py. You’ll see a function like this:

```python
import json

def lambda_handler(event, context):

return {

"statusCode": 200,

"body": json.dumps({"message": "Hello, World!"})

}
```

This is our Lambda function—it just returns a simple JSON response.

### **Run the Lambda Function Locally**

Run this command:

```bash
sam local invoke "HelloWorldFunction"
```

✅ If everything is set up correctly, you should see an output like:

```json
{

"statusCode": 200,

"body": "{\"message\": \"Hello, World!\"}"

}
```

**Run the Function as an API**

To test the Lambda function through an API Gateway locally, use:

```bash
sam local start-api
```

Then, open your browser and go to:

👉 http://127.0.0.1:3000/hello

You should see:

```json
{



"message": "Hello, World!"

}
```
**project folder**
hello-world/
│── events/
│── hello_world/
│   ├── __init__.py
│   ├── app.py  ← (Main Lambda function)
│── template.yaml  ← (AWS SAM template)
│── README.md
│── tests/
