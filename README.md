# 🚀 Serverless To-Do List API (AWS)

A production-ready **serverless REST API** for managing tasks, built using AWS cloud services with a fully scalable, event-driven architecture.

---

## 📌 Overview

This project demonstrates the design and deployment of a **cloud-native backend** using serverless principles. It implements a complete **CRUD (Create, Read, Update, Delete)** API for managing to-do items without provisioning or managing servers.

Deployed on AWS, the API is publicly accessible and designed for **high scalability, low cost, and minimal operational overhead**.

---

## 🏗️ Architecture

The system follows a **three-tier serverless architecture**:

```
Client → API Gateway → AWS Lambda → DynamoDB → Response
```

* **Amazon API Gateway** – Handles HTTP requests and routing
* **AWS Lambda** – Executes backend logic (Python)
* **Amazon DynamoDB** – Stores to-do items (NoSQL database)

---

## ⚙️ Tech Stack

* **Runtime:** Node.js 18.x
* **Cloud Provider:** AWS
* **Services Used:**

  * AWS Lambda
  * Amazon API Gateway (REST)
  * Amazon DynamoDB
* **Region:** us-east-1 (N. Virginia)

---

## ✨ Features

* Full CRUD operations for tasks
* Fully serverless (no infrastructure management)
* Automatic scaling
* Pay-per-use cost model
* RESTful API design
* JSON-based communication

---

## 📡 Live API Endpoints

Base URL:

```
https://d3oyezkjyi.execute-api.us-east-1.amazonaws.com/prod
```

| Method | Endpoint    | Description           |
| ------ | ----------- | --------------------- |
| GET    | /todos      | Retrieve all tasks    |
| POST   | /todos      | Create a new task     |
| GET    | /todos/{id} | Retrieve a task by ID |
| PUT    | /todos/{id} | Update a task         |
| DELETE | /todos/{id} | Delete a task         |

---

## 🧪 Example Usage

### ➤ Create Task

```bash
curl -X POST https://d3oyezkjyi.execute-api.us-east-1.amazonaws.com/prod/todos \
-H "Content-Type: application/json" \
-d '{"title": "Buy groceries"}'
```

### ➤ Response

```json
{
  "todoId": "a1b2c3d4-e5f6-7890-abcd-ef1234567890"
}
```

---

## 🗄️ Database Schema (DynamoDB)

| Attribute | Type   | Description         |
| --------- | ------ | ------------------- |
| todoId    | String | Primary key (UUID)  |
| title     | String | Task description    |
| status    | String | pending / completed |
| createdAt | String | ISO timestamp       |

---

## 📷 Screenshots

### 🔹 API Gateway Configuration

![API Gateway]("C:\Users\hp\Pictures\Screenshots\Screenshot 2026-04-16 224521.png")

### 🔹 Resource Structure

![Resources]("C:\Users\hp\Pictures\Screenshots\Screenshot 2026-04-16 224508.png")

### 🔹 Deployment Stage

![Deployment]("C:\Users\hp\Pictures\Screenshots\Screenshot 2026-04-16 224456.png")

### 🔹 API Testing (Postman)

![Postman]("C:\Users\hp\Pictures\Screenshots\Screenshot 2026-04-16 224140.png")

---


---

## 🧠 Key Learnings

* Serverless architecture eliminates infrastructure management
* AWS Lambda enables event-driven execution
* DynamoDB provides fast, scalable NoSQL storage
* API Gateway simplifies REST API creation

---

## ⚠️ Limitations

* Cold start latency in Lambda
* Debugging distributed systems is harder
* Vendor lock-in (AWS-specific services)

---

## 🔮 Future Improvements

* Authentication (JWT / AWS Cognito)
* Pagination support
* CI/CD pipeline (GitHub Actions / AWS CodePipeline)
* Monitoring (CloudWatch + X-Ray)

---

## 📜 License

MIT License

---

## 👨‍💻 Authors

* Jyoti Kumari

---

## ⭐ Why This Project Matters

This project demonstrates real-world backend engineering using **modern cloud architecture**, making it highly relevant for roles in:

* Backend Development
* Cloud Engineering
* DevOps / Platform Engineering

---
