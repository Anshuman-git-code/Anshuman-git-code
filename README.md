<div align="center">

<img src="https://readme-typing-svg.herokuapp.com?font=JetBrains+Mono&weight=500&size=22&pause=1500&color=FF9900&center=true&vCenter=true&width=700&lines=Cloud+Engineer;Every+system+starts+with+the+business+problem.;Business+Requirements+%E2%86%92+Architecture+%E2%86%92+AWS" alt="Typing SVG" />

# Anshuman Mohapatra

**Cloud Engineer · AWS · Serverless · Infrastructure as Code**

[![Portfolio](https://img.shields.io/badge/Portfolio-anshuman.cloud-FF9900?style=flat-square&logo=google-chrome&logoColor=white)](https://anshuman-git-code.github.io/Portfolio/)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/anshuman-mohapatra-a6b1b0325/)
[![Email](https://img.shields.io/badge/Email-anshuman.mohapatra04@gmail.com-EA4335?style=flat-square&logo=gmail&logoColor=white)](mailto:anshuman.mohapatra04@gmail.com)

</div>

---

## About

Every system starts with the business problem. From there the work moves forward — actors, capabilities, access patterns, architecture — and only then do the services get chosen.

That approach came from repetition, not theory. Across four production-oriented serverless systems, the pattern that mattered most was the *why* behind each decision — what business requirement it satisfied and what trade-off it introduced.

A dashboard showing total clicks is straightforward to build. The decision to let a redirect succeed even when its analytics update fails — because a user should always get where they're going regardless of a tracking hiccup — is where the real engineering thinking lives.

Currently completing B.Tech in Computer Science Engineering at ITER, SOA University. Selected as Team Lead during my cloud engineering internship at F13 Technologies for how I broke down and owned architecture decisions across a team.

---

## How I Think

Business Problem ↓ Business Requirements ↓ Actors & Capabilities ↓ Architecture ↓ Engineering Decisions & Trade-offs ↓ AWS Services ↓ Infrastructure as Code ↓ Implementation ↓ Production Improvements


AWS shows up two-thirds of the way down that list — deliberately. It's the last decision, not the first.

---

## Engineering Principles

| Principle | What it means in practice |
|---|---|
| **Business First** | Architecture serves a requirement — it exists to solve something real |
| **Design Before Implementation** | Access patterns and data models get worked out before a single table is created |
| **Serverless by Default** | Compute should scale with demand, not sit idle waiting for it |
| **Least Privilege** | Every Lambda gets its own role, scoped to exactly what it touches |
| **Cost Awareness** | Every architectural choice has a dollar figure — I track it, not guess it |
| **Infrastructure as Code** | Every resource is defined, versioned, and reproducible from a single apply |
| **Maintainability** | Each component owns exactly one responsibility |

---

## Featured Projects

### 🎟 EventSphere — Event-Driven Serverless Ticketing Platform
> *Flagship project*

The center of this system is the **registration**, not the event. Every downstream action — ticket generation, delivery, attendance tracking — exists because a registration succeeded, and that insight shaped the entire architecture.

Registration is decoupled from ticket generation using EventBridge: the Registration Lambda writes to DynamoDB and returns success immediately, while a separate Lambda handles QR generation, S3 storage, and SES delivery asynchronously. Three DynamoDB tables are modeled around access patterns with Global Secondary Indexes. Auth runs on Cognito JWTs with role-based authorization, least-privilege IAM, and ticket files stay private in S3 — accessible only through short-lived pre-signed URLs.

`Cognito` `EventBridge` `DynamoDB` `Lambda` `API Gateway` `CloudFront` `S3` `SES` `Terraform`

[![Repo](https://img.shields.io/badge/Repository-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/Anshuman-git-code/Event-Ticketing-System-V3.git)
[![Demo](https://img.shields.io/badge/Live_Demo-FF9900?style=flat-square&logo=amazonaws&logoColor=white)](https://d2xd67ws8yeqrk.cloudfront.net/)

---

### 🔗 LinkForge Pro — Serverless URL Shortener & Analytics Platform

Split into three independently deployable capabilities — link creation, redirection, and administration — instead of one large function. The redirect path is **intentionally prioritized** over the analytics path: a click-count update can fail gracefully while the user is still redirected. The core user experience always takes priority over instrumentation.

DynamoDB uses the short code as a hash key for single-digit-millisecond lookups. Frontend hosted on S3 static website. Full infrastructure deployed through CloudFormation.

`Lambda` `API Gateway` `DynamoDB` `S3` `CloudFormation` `IAM` `CloudWatch`

[![Repo](https://img.shields.io/badge/Repository-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/Anshuman-git-code/Linkforge_Pro.git)
[![Demo](https://img.shields.io/badge/Live_Demo-FF9900?style=flat-square&logo=amazonaws&logoColor=white)](http://url-shortener-infra-frontend-690081480550.s3-website-us-east-1.amazonaws.com/)

---

### 📄 Cloud-Native Resume Processing & Candidate Matching Platform

A four-stage event-driven pipeline — upload, Textract extraction, skill parsing, job matching — where each stage triggers the next through S3 events and DynamoDB Streams rather than one service handling everything sequentially. Textract handles document intelligence so the parsing logic works on structured extracted text, keeping each stage focused on a single responsibility. Each stage can evolve or scale independently.

`Textract` `Lambda` `S3` `DynamoDB Streams` `API Gateway` `IAM` `Terraform`

[![Repo](https://img.shields.io/badge/Repository-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/Anshuman-git-code/Resume-Parser-Skill-Matcher.git)
[![Demo](https://img.shields.io/badge/Live_Demo-FF9900?style=flat-square&logo=amazonaws&logoColor=white)](http://resume-parser-bucket-main-anshuman.s3-website.ap-south-1.amazonaws.com/frontend/index.html)

---

### 🖼 Serverless Media Processing Platform

The core decision: **keep Lambda out of the file transfer path entirely**. The frontend uploads directly to S3 using a pre-signed URL that a lightweight Lambda authorizes — Lambda grants permission, S3 handles the transfer. An S3 `ObjectCreated` event triggers image processing into three resolutions, stored in a separate output bucket for cleaner IAM boundaries. All 30 resources provisioned through Terraform.

`S3` `Lambda` `API Gateway` `Terraform` `IAM` `Pillow`

[![Repo](https://img.shields.io/badge/Repository-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/Anshuman-git-code/serverless-image-optimizer.git)
[![Demo](https://img.shields.io/badge/Live_Demo-FF9900?style=flat-square&logo=amazonaws&logoColor=white)](http://image-pipeline-frontend-man.s3-website.ap-south-1.amazonaws.com/)

---

## Technology Stack

**Cloud**
AWS — Lambda · API Gateway · EventBridge · DynamoDB · S3 · Cognito · SES · CloudWatch · IAM · VPC · Route 53 · Textract · EC2 · ECS · EKS

**Infrastructure as Code**
Terraform · CloudFormation · AWS CDK

**Containers**
Docker · Kubernetes · Helm · ArgoCD

**CI/CD**
GitHub Actions · Jenkins

**Monitoring**
CloudWatch · Prometheus · Grafana · ELK Stack

**Programming**
Python · JavaScript · Bash · Java · C++

---

## Current Focus

Being upfront rather than inflating it. Right now I'm deepening:

- **Python** — moving from scripting Lambda handlers to writing production-grade, tested code
- **Kubernetes** — patterns beyond deployments and services: HPA tuning, ingress design, real workload orchestration
- **Linux fundamentals** — the layer underneath the managed services I've been building on
- **Observability** — structured logging, tracing, and alerting, not just dashboards after the fact

---

## GitHub Activity

<div align="center">

![GitHub Stats](https://github-readme-stats.vercel.app/api?username=Anshuman-git-code&show_icons=true&theme=tokyonight&hide_border=true&count_private=true&title_color=FF9900&icon_color=FF9900)

![GitHub Streak](https://github-readme-streak-stats.herokuapp.com/?user=Anshuman-git-code&theme=tokyonight&hide_border=true&ring=FF9900&fire=FF9900&currStreakLabel=FF9900)

</div>

---

<div align="center">

*"Good cloud architecture is about moving data as little as possible while moving permissions intelligently."*

</div>
