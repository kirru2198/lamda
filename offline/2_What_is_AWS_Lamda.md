**Hello everyone and welcome to this video!**

In this video, we’ll learn **what AWS Lambda is** and **how it’s different from other services**.

---

### What is AWS Lambda?

**AWS Lambda** is a **serverless compute service**.  
This means:
- Your code runs **only when triggered by an event** (like a file uploaded to S3 or a message in a queue).
- AWS automatically manages the **servers and infrastructure** for you.

So, if a service sends a response, **Lambda can be triggered** to do a task — like sending a message or processing data.

Lambda is usually used in the **backend** of applications.

---

### What Does “Serverless” Mean?

Lambda is called **serverless** because:
- You **don’t need to set up or manage servers**.
- It runs automatically when triggered.

In contrast, **EC2** (Elastic Compute Cloud) is a **compute service that uses servers**.  
With EC2, you set up everything — like operating systems, security, and software.

---

### Lambda vs EC2

| Feature | Lambda | EC2 |
|--------|--------|-----|
| Type | **Platform as a Service (PaaS)** | **Infrastructure as a Service (IaaS)** |
| Server Management | Handled by AWS | Handled by you |
| Setup | Just write code | Install OS, software, and manage setup |
| Languages | Limited to supported ones | Any language, more flexibility |
| Runtime | You choose the environment | You create the environment |
| Flexibility | Less (focus on code) | More (choose OS, instance type, etc.) |
| Use Case | Lightweight, event-driven tasks | Full control over infrastructure |

With **Lambda**, you just choose a runtime (like Python), write your code, and AWS takes care of the rest.  
With **EC2**, you have to do everything — install software, set up environments, and manage updates.

---

### Lambda vs Elastic Beanstalk

Both **Lambda** and **Elastic Beanstalk** let you focus on your **code**, not the infrastructure.

But here’s how they differ:

| Feature | Lambda | Elastic Beanstalk |
|--------|--------|-------------------|
| Resource Selection | AWS chooses automatically | You choose (instances, DB, etc.) |
| Flexibility | Less control | More control |
| Stateless or Stateful | **Stateless** (doesn’t store data) | **Stateful** (can store and manage data) |
| Best For | Short tasks triggered by events | Running full web apps or APIs |

**Lambda** runs based on **workload** and scales automatically. You **don’t manage any servers or storage**.  
**Elastic Beanstalk** gives you more control — you can choose the infrastructure, but AWS still helps manage it.

---

### Key Takeaways

- **Lambda is great for simple, event-based tasks.**
- You don’t manage infrastructure — just write and upload your code.
- It’s **stateless** — it doesn't remember or store past data.
- Compared to **EC2**, it’s simpler but less flexible.
- Compared to **Elastic Beanstalk**, it gives less control but is quicker to set up for small functions.
