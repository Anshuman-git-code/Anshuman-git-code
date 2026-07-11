<div align="center">

<img src="https://readme-typing-svg.herokuapp.com?font=JetBrains+Mono&weight=500&size=24&pause=1500&color=36BCF7&center=true&vCenter=true&width=650&lines=Cloud+Engineer;I+design+systems+before+I+choose+services.;Business+Requirements+%E2%86%92+Architecture+%E2%86%92+AWS" alt="Typing SVG" />

**Anshuman Mohapatra**
Cloud Engineer · AWS · Serverless · Infrastructure as Code

[GitHub](https://github.com/Anshuman-git-code) · [Portfolio](https://anshuman-git-code.github.io/Portfolio/) · [LinkedIn](https://www.linkedin.com/in/anshuman-mohapatra-a6b1b0325/) · [Email](mailto:anshuman.mohapatra04@gmail.com)

</div>

<br>

## About

I don't start by picking an AWS service. I start by understanding the business problem the system is supposed to solve, then I work forward — actors, capabilities, access patterns, architecture — and only then do the services get chosen.

That approach came from repetition, not theory. Across four production-oriented serverless systems, the pattern that mattered most wasn't *which* AWS service I used, it was *why* — what business requirement it satisfied and what trade-off it introduced. A dashboard that shows total clicks isn't interesting. The decision to let a redirect succeed even when its analytics update fails, because a user should never see a broken link over a tracking hiccup, is.

I'm currently completing my B.Tech in Computer Science Engineering at ITER, SOA University, and was selected as Team Lead during my cloud engineering internship at F13 Technologies for how I broke down and owned architecture decisions across a team.

<br>

## How I Think

```
Business Problem
      ↓
Business Requirements
      ↓
Actors & Capabilities
      ↓
Architecture
      ↓
Engineering Decisions & Trade-offs
      ↓
AWS Services
      ↓
Infrastructure as Code
      ↓
Implementation
      ↓
Production Improvements
```

AWS shows up two-thirds of the way down that list — deliberately. It's the last decision, not the first.

<br>

## Engineering Principles

| Principle | What it means to me |
|---|---|
| **Business First** | The architecture serves a requirement — it doesn't exist for its own sake |
| **Design Before Implementation** | Access patterns and data models get worked out before a single table is created |
| **Serverless by Default** | Compute should scale with demand, not sit idle waiting for it |
| **Least Privilege** | Every Lambda gets its own role, scoped to exactly what it touches |
| **Cost Awareness** | Every architectural choice has a dollar figure — I track it, not guess it |
| **Infrastructure as Code** | If it isn't reproducible from a repo, it isn't done |
| **Maintainability** | One responsibility per function, per service — nothing does two jobs |

<br>

## Featured Projects

### EventSphere — Event-Driven Serverless Ticketing Platform
*Flagship project*

The center of this system isn't the event — it's the registration. Every downstream action (ticket generation, delivery, attendance tracking) exists because a registration succeeded, and that insight shaped the whole architecture.

Registration is decoupled from ticket generation using EventBridge: the Registration Lambda writes to DynamoDB and returns success immediately, while a separate Lambda handles QR generation, S3 storage, and delivery through SES — asynchronously, without making the user wait. Three DynamoDB tables (Events, Registrations, Tickets) are modeled around access patterns with Global Secondary Indexes rather than designed table-first. Auth runs on Cognito JWTs with role-based authorization, least-privilege IAM, and pre-signed URLs so ticket files are never public.

`Cognito` `EventBridge` `DynamoDB` `Lambda` `API Gateway` `CloudFront` `SES` `Terraform`

[Repository](https://github.com/Anshuman-git-code/Event-Ticketing-System-V3.git) · [Live Demo](https://d2xd67ws8yeqrk.cloudfront.net/)

---

### LinkForge Pro — Serverless URL Shortener & Analytics Platform

Split into three independently deployable capabilities — link creation, redirection, and administration — instead of one large function. The redirect path is intentionally prioritized over the analytics path: if a click-count update fails, the user is still redirected. Analytics should never be allowed to break the core product.

DynamoDB uses the short code as a hash key for single-digit-millisecond lookups, and the whole platform is deployed through CloudFormation for reproducibility.

`Lambda` `API Gateway` `DynamoDB` `S3` `CloudFormation`

[Repository](https://github.com/Anshuman-git-code/Linkforge_Pro.git) · [Live Demo](http://url-shortener-infra-frontend-690081480550.s3-website-us-east-1.amazonaws.com/)

---

### Cloud-Native Resume Processing & Candidate Matching Platform

A four-stage event-driven pipeline — upload, Textract extraction, skill parsing, job matching — where each stage triggers the next through S3 events rather than one service handling every step sequentially. Textract handles document intelligence so the parsing logic never has to touch raw PDF structure directly, and each stage can evolve or scale independently of the others.

`Textract` `Lambda` `S3` `DynamoDB Streams` `API Gateway`

[Repository](https://github.com/Anshuman-git-code/Resume-Parser-Skill-Matcher.git) · [Live Demo](http://resume-parser-bucket-main-anshuman.s3-website.ap-south-1.amazonaws.com/frontend/index.html)

---

### Serverless Media Processing Platform

The core decision here was keeping Lambda out of the file transfer path entirely. The frontend uploads directly to S3 using a pre-signed URL that a lightweight Lambda authorizes — Lambda grants permission, S3 does the heavy lifting. An S3 `ObjectCreated` event then triggers image processing into three resolutions, stored in a separate output bucket for cleaner IAM boundaries. All 30 resources are provisioned through Terraform.

`S3` `Lambda` `API Gateway` `Terraform` `IAM`

[Repository](https://github.com/Anshuman-git-code/serverless-image-optimizer.git) · [Live Demo](http://image-pipeline-frontend-man.s3-website.ap-south-1.amazonaws.com/)

<br>

## Current Focus

I'd rather be upfront about this than inflate it. Right now I'm deepening:

- **Python** — moving from scripting Lambda handlers to writing production-grade, tested code
- **Kubernetes** — patterns beyond deployments and services: HPA tuning, ingress design, real workload orchestration
- **Linux fundamentals** — the layer underneath the managed services I've been building on
- **Observability** — structured logging, tracing, and alerting, not just dashboards after the fact

<br>

## Technology Stack

**Cloud** — AWS (Lambda, API Gateway, EventBridge, DynamoDB, S3, Cognito, SES, CloudWatch, IAM, VPC, Route53, Textract, EC2, ECS, EKS)

**Infrastructure as Code** — Terraform, CloudFormation, AWS CDK

**Containers** — Docker, Kubernetes, Helm, ArgoCD

**CI/CD** — Jenkins, GitHub Actions

**Monitoring** — CloudWatch, Prometheus, Grafana, ELK Stack

**Programming** — Python, JavaScript, Bash, Java, C++

<br>

## GitHub Activity

<div align="center">

<img src="https://github-readme-stats.vercel.app/api?username=Anshuman-git-code&show_icons=true&theme=tokyonight&hide_border=true&count_private=true" alt="GitHub Stats" height="165"/>
<img src="https://github-readme-stats.vercel.app/api/top-langs/?username=Anshuman-git-code&layout=compact&theme=tokyonight&hide_border=true&langs_count=6" alt="Top Languages" height="165"/>

</div>

<br>

## Connect

<div align="center">

[LinkedIn](https://www.linkedin.com/in/anshuman-mohapatra-a6b1b0325/) · [Portfolio](https://anshuman-git-code.github.io/Portfolio/) · [Email](mailto:anshuman.mohapatra04@gmail.com) · [GitHub](https://github.com/Anshuman-git-code)

</div>

<br>

<div align="center">

*"Good cloud architecture isn't about moving data through more services — it's about moving data as little as possible while moving permissions intelligently."*

</div>
