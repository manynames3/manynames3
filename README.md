# Aiden Rhaa

**AWS Solutions Architect Associate · AWS Developer Associate · HashiCorp Terraform Associate**

![AWS SAA](https://img.shields.io/badge/AWS-Solutions_Architect_Associate-FF9900?style=flat-square&logo=amazonaws&logoColor=white)
![AWS DVA](https://img.shields.io/badge/AWS-Developer_Associate-FF9900?style=flat-square&logo=amazonaws&logoColor=white)
![Terraform](https://img.shields.io/badge/HashiCorp-Terraform_Associate-7B42BC?style=flat-square&logo=terraform&logoColor=white)

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Aiden_Rhaa-0A66C2?style=flat-square&logo=linkedin)](https://www.linkedin.com/in/aidenrhaa)
[![Email](https://img.shields.io/badge/Email-aidenrhaacloud%40gmail.com-gray?style=flat-square)](mailto:aidenrhaacloud@gmail.com)

---

I design and build serverless systems on AWS — event-driven architectures, AI-powered pipelines, and infrastructure managed entirely through code. My projects aren't toy apps: they're production-deployed tools solving real problems in domains I know well, built with the same discipline I'd apply on any engineering team. Every architectural decision here has a reason behind it.

---

### Engineering judgment · decisions and rationale

| Project | Decision | Why | Outcome |
|---|---|---|---|
| `pulpit` | DynamoDB on-demand over RDS | Sermon search is burst-heavy, not steady-state. RDS idles at $15–25/mo regardless of traffic. On-demand scales to zero between Sunday spikes and charges only per request. | ~$2/mo total · right-sized for the load |
| `super-transcriber` | EventBridge async over Lambda polling | Transcribe jobs run 30–90s. Polling every 5s burns invocations and adds latency jitter. EventBridge fires exactly once on completion — zero wasted compute in between. | Event-driven · no idle invocation cost |
| `photoscribe-ai` | S3 Vectors over managed vector DB | Pinecone and Weaviate start at $70–100/mo with capacity you pay for whether you use it or not. S3 Vectors stores embeddings at S3 pricing — right for personal-scale semantic search. | $0.023/GB vs $70+/mo floor |
| `selah` | Cloudflare R2 over S3 for media | Audio files load on every page visit. S3 egress at $0.09/GB accumulates fast for a media-heavy app. R2 is S3-compatible with zero egress fees. | $0 egress · identical integration surface |

---

### How I approach every build

**01 — Understand the access pattern before choosing the data layer**
SQLite for single-writer CLIs. DynamoDB on-demand for bursty serverless APIs. Supabase Postgres when you need relational joins and built-in auth. The access pattern dictates the tool — not the other way around.

**02 — Async by default where latency tolerance allows**
Synchronous chains hold Lambda invocations open and couple services tightly. EventBridge, SQS, and S3 event triggers decouple producers from consumers and eliminate idle compute cost.

**03 — IaC from the first resource, no exceptions**
Every project provisions via Terraform. No console click-ops, no configuration drift, no forgotten resources generating charges. Tear down and redeploy with a single command.

**04 — Only provision what the current problem actually requires**
Over-engineered infrastructure is a liability — more to maintain, more to debug, more to explain. The question isn't "what could we add?" It's "what's the minimum surface area that solves this well?"

---

### Stack

**Cloud & Infra**
`AWS Lambda` `AWS Bedrock` `DynamoDB` `S3` `EventBridge` `API Gateway` `Cognito` `Terraform`

**Frontend & Edge**
`React` `TypeScript` `Cloudflare Pages` `Cloudflare R2`

**Backend & Data**
`Python` `Node.js` `Supabase` `SQLite` `Playwright`

**AI / ML**
`AWS Bedrock` `Titan Embeddings` `Amazon Transcribe` `RAG pipelines`

---
