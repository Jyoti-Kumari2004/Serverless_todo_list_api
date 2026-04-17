<div align="center">

```
╔════════════════════════════════════════════════════════════╗
║                                                            ║
║        ☁️   S E R V E R L E S S   T O D O   A P I   ☁️    ║
║                                                            ║
║          No servers. No ops. Just ship and scale.          ║
║                                                            ║
╚════════════════════════════════════════════════════════════╝
```

### Built on AWS · Written in Python · Zero Infrastructure

<br/>

<!-- ───────── AWS SERVICE ICONS ───────── -->

<table>
<tr>
<td align="center" width="160">
<img src="https://img.icons8.com/color/64/amazon-api-gateway.png" width="52"/><br/>
<sub><b>API Gateway</b></sub><br/>
<sub>HTTP Routing</sub>
</td>
<td align="center" width="40"><sub>──────►</sub></td>
<td align="center" width="160">
<img src="https://img.icons8.com/color/64/aws-lambda.png" width="52"/><br/>
<sub><b>AWS Lambda</b></sub><br/>
<sub>Python Logic</sub>
</td>
<td align="center" width="40"><sub>──────►</sub></td>
<td align="center" width="160">
<img src="https://img.icons8.com/color/64/amazon-dynamodb.png" width="52"/><br/>
<sub><b>DynamoDB</b></sub><br/>
<sub>NoSQL Storage</sub>
</td>
</tr>
</table>

<br/>

[![Live](https://img.shields.io/badge/🟢%20API-LIVE-00c853?style=flat-square)](https://d3oyezkjyi.execute-api.us-east-1.amazonaws.com/prod)
[![Python](https://img.shields.io/badge/Python-3.x-3776AB?style=flat-square&logo=python&logoColor=white)](https://python.org)
[![AWS](https://img.shields.io/badge/Cloud-AWS-FF9900?style=flat-square&logo=amazonaws&logoColor=white)](https://aws.amazon.com)
[![DynamoDB](https://img.shields.io/badge/DB-DynamoDB-4053D6?style=flat-square&logo=amazondynamodb&logoColor=white)](https://aws.amazon.com/dynamodb)
[![License](https://img.shields.io/badge/License-MIT-gray?style=flat-square)](LICENSE)

</div>

---

## 〉 What Is This?

A **production-ready serverless REST API** for managing tasks — fully deployed on AWS.

> Write code, not config. AWS handles the servers, scaling, and uptime automatically.

**Why serverless?**
- 💸 **Pay only for what you use** — zero traffic = zero cost
- 📈 **Auto-scales** — handles 1 request or 1 million, same config
- 🔧 **Zero ops** — no EC2, no patching, no capacity planning

---

## 〉 Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                         AWS CLOUD                           │
│                                                             │
│   CLIENT          API GATEWAY        LAMBDA      DYNAMODB   │
│                                                             │
│   curl    ──►   [  /todos  ]   ──►  [Python]  ──►  [{DB}]  │
│   browser ──►   [ /todos/id]   ──►  [  fn  ]  ──►  [{DB}]  │
│   app     ──►   [  routing ]   ──►  [ logic]  ◄──  [{DB}]  │
│                                                             │
│                            ◄─── JSON response ──────────   │
└─────────────────────────────────────────────────────────────┘
```

| # | Layer | AWS Service | Responsibility |
|---|-------|-------------|----------------|
| 1 | 🌐 **Edge** | Amazon API Gateway | Receives HTTP, validates, routes |
| 2 | ⚙️ **Compute** | AWS Lambda · Python | Runs CRUD logic on each request |
| 3 | 🗄️ **Storage** | Amazon DynamoDB | Persists items as JSON documents |

---

## 〉 Live API

```
Base URL:  https://d3oyezkjyi.execute-api.us-east-1.amazonaws.com/prod
Region:    us-east-1 (N. Virginia)
```

| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/todos` | 📋 Fetch all tasks |
| `POST` | `/todos` | ➕ Create a new task |
| `GET` | `/todos/{id}` | 🔍 Get task by ID |
| `PUT` | `/todos/{id}` | ✏️ Update a task |
| `DELETE` | `/todos/{id}` | 🗑️ Delete a task |

---

## 〉 Quick Start — Try It Now

**➤ Create a task**
```bash
curl -X POST https://d3oyezkjyi.execute-api.us-east-1.amazonaws.com/prod/todos \
  -H "Content-Type: application/json" \
  -d '{"title": "Buy groceries"}'
```
```json
{ "todoId": "a1b2c3d4-e5f6-7890-abcd-ef1234567890" }
```

**➤ List all tasks**
```bash
curl https://d3oyezkjyi.execute-api.us-east-1.amazonaws.com/prod/todos
```

**➤ Mark as completed**
```bash
curl -X PUT https://d3oyezkjyi.execute-api.us-east-1.amazonaws.com/prod/todos/{id} \
  -H "Content-Type: application/json" \
  -d '{"status": "completed"}'
```

**➤ Delete a task**
```bash
curl -X DELETE https://d3oyezkjyi.execute-api.us-east-1.amazonaws.com/prod/todos/{id}
```

---

## 〉 Data Schema (DynamoDB)

```json
{
  "todoId"    :  "a1b2c3d4-..."         ,  ← Primary Key (auto UUID)
  "title"     :  "Buy groceries"        ,  ← Task description
  "status"    :  "pending | completed"  ,  ← Task state
  "createdAt" :  "2026-04-16T22:45:00Z"    ← ISO 8601 timestamp
}
```

---

## 〉 Key Concepts

```
┌─────────────────┬──────────────────────────────────────────────┐
│ Concept         │ What it means here                           │
├─────────────────┼──────────────────────────────────────────────┤
│ Serverless      │ You write functions, AWS runs the servers     │
│ Event-driven    │ Lambda sleeps until a request wakes it up     │
│ NoSQL           │ DynamoDB stores JSON — no rigid SQL schema    │
│ Pay-per-use     │ Charged per 1ms of Lambda execution time      │
│ Auto-scaling    │ AWS adds capacity automatically under load    │
└─────────────────┴──────────────────────────────────────────────┘
```

---

## 〉 Screenshots

> 📁 Add your images inside a `screenshots/` folder in this repo, then they'll render here automatically.

<br/>

### 🔹 API Gateway — Route Configuration
![API Gateway Configuration](<img width="1902" height="424" alt="Screenshot 2026-04-16 232241" src="https://github.com/user-attachments/assets/f36d97e6-3a5a-4c2c-b6c5-07029c947c1a" />
)

<br/>


### 🔹 API Gateway — Resource Structure
![Resource Structure](screenshots/api-gateway-resources.png)

<br/>

### 🔹 Deployment Stage
![Deployment Stage](screenshots/deployment-stage.png)

<br/>

### 🔹 Live Testing in Postman
![Postman Tests](screenshots/postman-tests.png)

---

## 〉 Known Limitations

| Issue | Impact | Notes |
|-------|--------|-------|
| ❄️ Cold Starts | ~200–500ms first request | Mitigated with Provisioned Concurrency |
| 🔍 Debugging | Harder than monoliths | Use CloudWatch + X-Ray |
| 🔒 Vendor Lock-in | AWS-specific services | Abstract with IaC if needed |

---

## 〉 Roadmap

- [ ] 🔐 **Auth** — JWT tokens / AWS Cognito user pools
- [ ] 📄 **Pagination** — cursor-based for large datasets
- [ ] 🚀 **CI/CD** — GitHub Actions → AWS CodePipeline
- [ ] 📊 **Monitoring** — CloudWatch dashboards + X-Ray tracing
- [ ] 🌍 **Multi-region** — Global DynamoDB tables + Route 53

---

## 〉 Author

<table>
<tr>
<td align="center">
<b>Jyoti Kumari</b><br/>
<sub>Cloud · Backend · Serverless</sub>
</td>
</tr>
</table>

---

<div align="center">

```
[ Serverless ]  ·  [ Scalable ]  ·  [ Event-Driven ]  ·  [ Cloud-Native ]
```

*Built to demonstrate modern AWS backend architecture*

</div>
