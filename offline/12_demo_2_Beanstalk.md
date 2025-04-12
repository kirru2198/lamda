# 🚀 Hands-On: Deploy PHP App on AWS Elastic Beanstalk

In this hands-on session, we will walk through the steps to:

- Create an Elastic Beanstalk environment
- Deploy a PHP application
- Understand how Elastic Beanstalk sets up your infrastructure
- Upload new versions of your app
- Use deployment strategies like **traffic splitting**

---

## 📌 Prerequisites

- AWS account
- Basic understanding of PHP
- A zipped PHP file with an `index.php` homepage

---

## 🔧 Step 1: Open the Elastic Beanstalk Console

1. Log in to the [AWS Management Console](https://console.aws.amazon.com/).
2. In the search bar, type **Elastic Beanstalk** and select the service.

---

## 📂 Step 2: Create an Application & Environment

1. Click **Create Application**.
2. Enter a name, e.g., `my-beanstalk`.
3. Choose the **Platform**:
   - Language: PHP
   - Platform Branch: Amazon Linux
4. Under **Application code**:
   - You can either use the **Sample Application** or **Upload your code**.
   - For this hands-on, select **Sample Application** to start with.
5. Click **Create Application**.

> ✅ **Tip:** Using the sample app first allows you to test your environment before uploading your own code. You can then version your app easily.

---

## ⚙️ Step 3: Elastic Beanstalk Sets Up the Environment

After a few minutes, AWS Elastic Beanstalk will:

- Create an **S3 bucket** and upload the sample app
- Set up a **Target Group**
- Create **Security Groups**
- Set up **Health Checks**
- Create an **Auto Scaling Group** and **Policies**
- Set up **CloudWatch Alarms**
- Launch an **EC2 instance**
- Create a **Load Balancer and Listener**
- Deploy the app and make it accessible via a public URL

You can view all these actions under the **Recent Events** section in the Elastic Beanstalk console.

---

## 🌐 Step 4: Access the Sample Application

Click the provided **URL** in your environment dashboard. You should see the default PHP sample application running.

---

## 🆕 Step 5: Upload a New Version of Your PHP App

### Requirements:
- Your PHP app should be zipped
- The main file should be named `index.php`

### Steps:

1. Create a `.zip` file containing your `index.php`.
2. In the Elastic Beanstalk dashboard:
   - Go to **Application versions**
   - Click **Upload and Deploy**
   - Choose your `.zip` file
   - Give it a **Version Label** (e.g., `v1`)
   - Click **Deploy**

### Example:

```php
<?php
echo "Hello, World!";
?>
```

> ✅ The new version will replace the sample application after the deployment completes and health checks pass.

---

## 🛠 Step 6: Make Changes & Deploy Again

1. Update your `index.php`. Example:

```php
<?php
echo "Hi, World from Beanstalk!";
?>
```

2. Zip the file again as `index.zip`.
3. Go back to Elastic Beanstalk → **Upload and Deploy**
4. Choose deployment method:

### Deployment Policies:
- **All at Once**: Deploy to all instances simultaneously
- **Rolling**: Deploy in batches
- **Rolling with Additional Batch**: Adds a batch before removing old ones
- **Immutable**: Deploys to new instances, then switches
- **Traffic Splitting**: Gradually sends traffic to new version

### Example: Traffic Splitting
- Set **Traffic Split**: 50%
- Set **Evaluation Time**: 3 minutes
- Click **Deploy**

---

## ✅ Step 7: Confirm the Deployment

After deployment:

1. Wait for health checks to pass.
2. Refresh the application URL.
3. You should now see the updated message: **"Hi, World from Beanstalk!"**

---

## 📈 Summary

With AWS Elastic Beanstalk, you get a fully managed environment that automatically handles:

- **Auto-scaling**
- **Load balancing**
- **Monitoring (CloudWatch)**
- **Deployment strategies**
- **App versioning**

This makes it easy to focus on **code**, not infrastructure.

---

## 👋 See You in the Next One!

That’s it for this hands-on guide! You've learned how to:

- Create an Elastic Beanstalk app
- Deploy a PHP site
- Use deployment strategies like traffic splitting
- Manage versions of your app

> 📝 Keep experimenting with deployment methods to understand which fits your use case best.
