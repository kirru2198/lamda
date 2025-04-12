# 🧪 Hands-On: AWS Lambda Function with S3 Trigger and SQS Destination

Welcome! In this hands-on session, we'll create a **Lambda function** that gets triggered when a **JSON file is uploaded** to an **S3 bucket**. The Lambda will **read and log the contents** of the file, and then send the log to an **SQS queue**.

---

## 📝 Objective

By the end of this hands-on, you will:
- Create an S3 bucket
- Create a Lambda function using Python
- Add an S3 trigger to invoke the Lambda
- Read and log JSON file content in CloudWatch
- Set up an SQS queue as a destination
- Send a message to the queue upon successful execution

---

## 🔧 Step 1: Create an S3 Bucket

1. Go to the **S3 console**.
2. Click on **Create Bucket**.
3. Enter a name: `aws-hands-on-lambda`.
4. Leave default settings and click **Create Bucket**.
5. Open the bucket after it's created.

---

## 🐍 Step 2: Create a Lambda Function

1. Go to the **Lambda console**.
2. Click **Create Function** → **Author from scratch**.
3. Name it: `my-lambda-function`.
4. Runtime: **Python 3.x**.
5. Permissions: Choose **existing role** with **admin access**.
6. Click **Create Function**.

---

## ⚙️ Step 3: Add S3 Trigger

1. In your Lambda function, go to the **Triggers** tab.
2. Click **Add Trigger** → Select **S3**.
3. Choose your bucket: `aws-hands-on-lambda`.
4. Event type: **All object create events**.
5. Acknowledge and click **Add**.

---

## 🧾 Step 4: Add Python Code to Lambda

1. Go to the **Code** tab.
2. Replace the existing code with the following:

```python
import json
import boto3

def lambda_handler(event, context):
    s3 = boto3.client('s3')
    bucket = event['Records'][0]['s3']['bucket']['name']
    key = event['Records'][0]['s3']['object']['key']
    
    response = s3.get_object(Bucket=bucket, Key=key)
    content = response['Body'].read().decode('utf-8')
    
    try:
        data = json.loads(content)
        print("The data in the file is:")
        print(json.dumps(data, indent=2))
    except Exception as e:
        print("Error reading JSON:", str(e))
    
    return {
        'statusCode': 200,
        'body': json.dumps('Process completed')
    }
```

3. Click **Deploy**.

---

## 📤 Step 5: Upload JSON File to S3

1. Go to the S3 bucket.
2. Click **Upload** → **Add Files** → Choose your `sample-data.json` file.
3. Click **Upload**.

### 🧾 Example JSON:

```json
{
  "year": 2015,
  "title": "The Big New Movie",
  "info": {
    "plot": "Nothing happens at all.",
    "rating": 1.0
  }
}
```

---

## 📊 Step 6: View Logs in CloudWatch

1. Go back to Lambda → **Monitor** tab.
2. Click **View logs in CloudWatch**.
3. Open the **Log Stream** to see the Lambda output.

You’ll see:
- File name
- Confirmation of upload
- Parsed JSON data printed in the logs

---

## 📦 Step 7: Add Destination – SQS Queue

1. Go to the **SQS Console**.
2. Click **Create queue** → Select **Standard Queue**.
3. Name it: `my-queue`.
4. Leave defaults (no encryption).
5. Click **Create Queue**.

---

## 🔗 Step 8: Connect SQS to Lambda

1. Go back to the Lambda function.
2. Scroll to **Destinations** section.
3. Under **On Success**, choose:
   - Destination type: **SQS Queue**
   - Choose `my-queue`
4. Click **Save**.

---

## 📂 Step 9: Test with Another JSON File

1. Prepare another JSON file (e.g., `lambda-1.json`):

```json
{
  "fruit": "apple",
  "size": "large",
  "color": "red"
}
```

2. Upload it to your S3 bucket.
3. Wait for the Lambda to process it.

---

## 📬 Step 10: Verify in CloudWatch and SQS

- Go to **CloudWatch Logs** → Check the new log stream.
- You'll see:
  - File uploaded: `lambda-1.json`
  - Content printed in the logs

- Go to **SQS Console** → `my-queue`
- You’ll see **1 new message** sent by Lambda.

---

## ✅ Summary

In this session, we:
- Created a Lambda function triggered by an S3 upload
- Logged the contents of uploaded JSON files
- Connected SQS as a success destination
- Verified execution and data flow using CloudWatch and SQS

---

### 🎯 Key AWS Services Used:
- **Lambda** (compute)
- **S3** (storage and trigger)
- **CloudWatch** (monitoring/logs)
- **SQS** (messaging destination)
