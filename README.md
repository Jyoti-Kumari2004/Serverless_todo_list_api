
☁️ Serverless ToDo API
Ship tasks. Not servers.

### Built on AWS · Written in Python · Zero Infrastructure

<br/>

<div style="display: flex; justify-content: center; align-items: center; gap: 24px; margin: 32px 0; flex-wrap: wrap;">
  <div style="text-align: center;">
    <div style="font-size: 48px; margin-bottom: 8px;">🌐</div>
    <div style="font-weight: 600; font-size: 14px;">API Gateway</div>
    <div style="font-size: 12px; color: #666; margin-top: 4px;">HTTP Routes</div>
  </div>
  <div style="font-size: 24px; color: #999;">→</div>
  <div style="text-align: center;">
    <div style="font-size: 48px; margin-bottom: 8px;">⚙️</div>
    <div style="font-weight: 600; font-size: 14px;">AWS Lambda</div>
    <div style="font-size: 12px; color: #666; margin-top: 4px;">Python Logic</div>
  </div>
  <div style="font-size: 24px; color: #999;">→</div>
  <div style="text-align: center;">
    <div style="font-size: 48px; margin-bottom: 8px;">🗄️</div>
    <div style="font-weight: 600; font-size: 14px;">DynamoDB</div>
    <div style="font-size: 12px; color: #666; margin-top: 4px;">NoSQL Data</div>
  </div>
</div>


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
<img width="1902" height="424" alt="Screenshot 2026-04-16 232241" src="https://github.com/user-attachments/assets/f5c3c9ba-730b-44fc-bd63-75567fd22caa" />

<br/>


### 🔹 API Gateway — Resource Structure
<img width="1911" height="837" alt="Screenshot 2026-04-16 224508" src="https://github.com/user-attachments/assets/26c3f140-712e-48bc-b622-5097d21063ba" />

<br/>

### 🔹 Deployment Stage
<img width="1888" height="859" alt="Screenshot 2026-04-16 224456" src="https://github.com/user-attachments/assets/59af8c3c-6f4b-4b5b-8c30-d57b321dff5c" />
<img width="1764" height="786" alt="Screenshot 2026-04-16 223402" src="https://github.com/user-attachments/assets/8b14981e-124f-40e4-8c37-5360a59e3129" />


<br/>

### 🔹 Live Testing in Postman
<img width="1342" height="947" alt="Screenshot 2026-04-17 152611" src="https://github.com/user-attachments/assets/31670b2c-69f2-44c4-bab6-ca4949ce4dbc" />
<img width="1792" height="910" alt="Screenshot 2026-04-16 225004" src="https://github.com/user-attachments/assets/2f5790b8-0ee3-4607-bb28-14843c2861a2" />


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
