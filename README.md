<div align="center">

<img src="https://readme-typing-svg.herokuapp.com?font=JetBrains+Mono&weight=500&size=22&pause=1500&color=FF9900&center=true&vCenter=true&width=700&lines=Cloud+Engineer;Every+system+starts+with+the+business+problem.;Business+Requirements+%E2%86%92+Architecture+%E2%86%92+AWS" alt="Typing SVG" />

# Anshuman Mohapatra

**Cloud Engineer · AWS · Serverless · Infrastructure as Code**

[![Portfolio](https://img.shields.io/badge/Portfolio-anshuman.cloud-FF9900?style=flat-square&logo=google-chrome&logoColor=white)](https://anshuman-git-code.github.io/Portfolio/)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/anshuman-mohapatra-a6b1b0325/)
[![Email](https://img.shields.io/badge/Email-anshuman.mohapatra04@gmail.com-EA4335?style=flat-square&logo=gmail&logoColor=white)](mailto:anshuman.mohapatra04@gmail.com)

</div>

---

### 📊 Engineering Activity & Metrics

<div align="center">

  <img src="https://github-profile-summary-cards.vercel.app/api/cards/profile-details?username=Anshuman-git-code&theme=tokyonight" alt="GitHub Profile Details" height="175" />
  <img src="https://github-readme-stats.vercel.app/api?username=Anshuman-git-code&show_icons=true&theme=tokyonight&hide_border=true&count_private=true&title_color=FF9900&icon_color=FF9900&text_color=94A3B8" alt="GitHub Stats" height="175" />
  <img src="https://github-readme-streak-stats.herokuapp.com/?user=Anshuman-git-code&theme=tokyonight&hide_border=true&ring=FF9900&fire=FF9900&currStreakLabel=FF9900&background=1A1B27" alt="GitHub Streak" height="175" />

  <br/><br/>

  <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=Anshuman-git-code&layout=compact&theme=tokyonight&hide_border=true&title_color=FF9900&text_color=94A3B8&langs_count=8&hide=html" alt="Top Languages Expanded" height="175" />
  <img src="https://github-profile-summary-cards.vercel.app/api/cards/repos-per-language?username=Anshuman-git-code&theme=tokyonight" alt="Repos Per Language" height="175" />
  <img src="https://github-profile-summary-cards.vercel.app/api/cards/most-commit-language?username=Anshuman-git-code&theme=tokyonight" alt="Most Commit Language" height="175" />

</div>

---

## About

Every system starts with the business problem. From there the work moves forward — actors, capabilities, access patterns, architecture — and only then do the services get chosen.

That approach came from repetition, not theory. Across four production-oriented serverless systems, the pattern that mattered most was the *why* behind each decision — what business requirement it satisfied and what trade-off it introduced.

A dashboard showing total clicks is straightforward to build. The decision to let a redirect succeed even when its analytics update fails — because a user should always get where they're going regardless of a tracking hiccup — is where the real engineering thinking lives.

Currently completing B.Tech in Computer Science Engineering at ITER, SOA University. Selected as Team Lead during my cloud engineering internship at F13 Technologies for how I broke down and owned architecture decisions across a team.

---

## How I Think

```text
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
AWS Services Selection
      ↓
Infrastructure as Code (Terraform)
      ↓
Implementation
      ↓
Production Improvements
```


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
Terraform · CloudFormation

**Containers**
Docker · Kubernetes · Helm · ArgoCD

**CI/CD**
GitHub Actions · Jenkins · GitLab CI 

**Monitoring**
CloudWatch · Prometheus · Grafana · ELK Stack

**Programming**
Python · JavaScript · TypeScript · Bash 

---

<div align="center">

*"Good cloud architecture is about moving data as little as possible while moving permissions intelligently."*

</div>

---

## 📈 Extended Telemetry & Analytics

<details>
<summary><b>🔍 Expand to view deep-dive GitHub activity, milestones, code telemetry & historical records</b></summary>
<br/>

<div align="center">

  <!-- ========================================== -->
  <!-- 1. LIVE PROFILE VISITOR & REPO TELEMETRY   -->
  <!-- ========================================== -->
  <h4>👀 Live Profile Telemetry & Traffic</h4>
  <p><i>Real-time profile views, network followers, and global ecosystem interaction</i></p>
  <img src="https://komarev.com/ghpvc/?username=Anshuman-git-code&style=flat-square&color=FF9900&label=PROFILE+VIEWS" alt="Profile Views" />
  <img src="https://img.shields.io/github/followers/Anshuman-git-code?label=FOLLOWERS&style=flat-square&color=FF9900&logo=github&logoColor=white" alt="GitHub Followers" />
  <img src="https://img.shields.io/github/stars/Anshuman-git-code?label=TOTAL+STARS+EARNED&style=flat-square&color=FF9900&logo=github&logoColor=white" alt="GitHub Total Stars" />

  <br/><br/>
  <hr style="border: 0.5px solid #24283b; width: 85%;" />
  <br/>

  <!-- ========================================== -->
  <!-- 2. CORE GITHUB STATS & STREAK COUNTERS    -->
  <!-- ========================================== -->
  <h4>⚡ Core Contribution & Streak Telemetry</h4>
  <p><i>Aggregated commits, pull requests, issue resolutions, and longest active streak records</i></p>
  <img src="https://github-readme-stats.vercel.app/api?username=Anshuman-git-code&show_icons=true&include_all_commits=true&count_private=true&theme=tokyonight&hide_border=true&title_color=FF9900&icon_color=FF9900&text_color=94A3B8" alt="GitHub Stats Summary" height="175" />
  <img src="https://github-readme-streak-stats.herokuapp.com/?user=Anshuman-git-code&theme=tokyonight&hide_border=true&ring=FF9900&fire=FF9900&currStreakLabel=FF9900&background=1A1B27" alt="GitHub Streak Stats" height="175" />

  <br/><br/>
  <hr style="border: 0.5px solid #24283b; width: 85%;" />
  <br/>

  <!-- ========================================== -->
  <!-- 3. EXPANDED REPO & PR/REVIEW RESOLUTION    -->
  <!-- ========================================== -->
  <h4>📊 Repository & Review Resolution Telemetry</h4>
  <p><i>Code reviews, merged pull requests, and multi-repository interaction metrics</i></p>
  <img src="https://github-readme-stats.vercel.app/api?username=Anshuman-git-code&show_icons=true&include_all_commits=true&count_private=true&theme=tokyonight&hide_border=true&title_color=FF9900&icon_color=FF9900&text_color=94A3B8&show=reviews,discussions_started,discussions_answered,prs_merged,prs_merged_percentage" alt="Expanded Repository Details" height="185" />

  <br/><br/>
  <hr style="border: 0.5px solid #24283b; width: 85%;" />
  <br/>

  <!-- ========================================== -->
  <!-- 4. GITHUB TROPHIES & MILESTONES            -->
  <!-- ========================================== -->
  <h4>🏆 Milestone Achievements & Trophies</h4>
  <p><i>Badges earned for commit consistency, repository ownership, stars, and PR milestones</i></p>
  <img src="https://github-profile-trophy.vercel.app/?username=Anshuman-git-code&theme=tokyonight&no-frame=true&no-bg=true&margin-w=4&margin-h=4&row=1&column=7" alt="GitHub Trophies" />

  <br/><br/>
  <hr style="border: 0.5px solid #24283b; width: 85%;" />
  <br/>

  <!-- ========================================== -->
  <!-- 5. CODEBASE COMPOSITION & LANGUAGES        -->
  <!-- ========================================== -->
  <h4>💻 Codebase Composition & Language Weight</h4>
  <p><i>Distribution of primary languages, framework files, and scripts across public repos</i></p>
  <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=Anshuman-git-code&layout=compact&theme=tokyonight&hide_border=true&title_color=FF9900&text_color=94A3B8&langs_count=8&hide=html" alt="Top Languages Expanded" height="180" />
  <img src="https://github-profile-summary-cards.vercel.app/api/cards/repos-per-language?username=Anshuman-git-code&theme=tokyonight" alt="Repos Per Language" height="180" />
  <img src="https://github-profile-summary-cards.vercel.app/api/cards/most-commit-language?username=Anshuman-git-code&theme=tokyonight" alt="Most Commit Language" height="180" />

  <br/><br/>
  <hr style="border: 0.5px solid #24283b; width: 85%;" />
  <br/>

  <!-- ========================================== -->
  <!-- 6. CODE TIME & PRODUCTIVITY HABITS         -->
  <!-- ========================================== -->
  <h4>⏱️ Productivity Habits & Coding Time Distribution</h4>
  <p><i>Analysis of active commit hours, days of the week, and development cadence</i></p>
  <img src="https://github-profile-summary-cards.vercel.app/api/cards/productive-time?username=Anshuman-git-code&theme=tokyonight&utcOffset=5.5" alt="Productive Time Breakdown" height="185" />
  <img src="https://github-profile-summary-cards.vercel.app/api/cards/profile-details?username=Anshuman-git-code&theme=tokyonight" alt="GitHub Profile Details" height="185" />
  <img src="https://github-readme-stats.vercel.app/api/wakatime?username=Anshuman-git-code&theme=tokyonight&hide_border=true&title_color=FF9900&icon_color=FF9900&text_color=94A3B8&layout=compact" alt="WakaTime Stats" height="185" />

  <br/><br/>
  <hr style="border: 0.5px solid #24283b; width: 85%;" />
  <br/>

  <!-- ========================================== -->
  <!-- 7. DYNAMIC VELOCITY CURVE & HEATMAPS       -->
  <!-- ========================================== -->
  <h4>📉 30-Day Dynamic Commit Velocity Graph</h4>
  <p><i>Continuous contribution density with TokyoNight area rendering</i></p>
  <img src="https://github-readme-activity-graph.vercel.app/graph?username=Anshuman-git-code&theme=tokyo_night&hide_border=true&color=FF9900&line=FF9900&point=FFFFFF&area=true&hide_title=false" alt="Activity Graph" width="95%" />

  <br/><br/>

  <h4>🗓️ Annual Commit Cadence Heatmap</h4>
  <p><i>Interactive daily timeline with full GitHub calendar visualization</i></p>
  <img src="https://ghchart.rshah.org/FF9900/Anshuman-git-code" alt="Commit Calendar" width="95%" />

  <br/><br/>
  <hr style="border: 0.5px solid #24283b; width: 85%;" />
  <br/>

  <!-- ========================================== -->
  <!-- 8. 3D ISOMETRIC / VOLUMETRIC LANDSCAPE     -->
  <!-- ========================================== -->
  <h4>🧊 3D Contribution Landscape</h4>
  <p><i>Volumetric view of commit density across historical intervals</i></p>
  <img src="https://github-contributions-api.deno.dev/Anshuman-git-code.svg?scheme=tokyonight&no-bg=true" alt="3D Contribution Graph" width="95%" />

  <br/><br/>
  <hr style="border: 0.5px solid #24283b; width: 85%;" />
  <br/>

  <!-- ========================================== -->
  <!-- 9. REAL-TIME ACTIVITY LOG & EVENT STREAM   -->
  <!-- ========================================== -->
  <h4>⚡ Recent GitHub Events & Log Stream</h4>
  <p><i>Real-time activity log showing pushes, branches created, and releases</i></p>
  <img src="https://activity-graph.vercel.app/api?username=Anshuman-git-code&theme=tokyonight&hide_border=true&title_color=FF9900&custom_title=Latest%20Developer%20Stream" alt="Developer Activity Log" width="90%" />

  <br/><br/>
  <hr style="border: 0.5px solid #24283b; width: 85%;" />
  <br/>

  <!-- ========================================== -->
  <!-- 10. REPOSITORY SPOTLIGHT & HIGH-IMPACT PINS-->
  <!-- ========================================== -->
  <h4>⭐ Pinned Project Architectures & Live Metrics</h4>
  <p><i>Real-time star tracking, branch states, and fork counts across key cloud systems</i></p>
  <a href="https://github.com/Anshuman-git-code/Event-Ticketing-System-V3">
    <img src="https://github-readme-stats.vercel.app/api/pin/?username=Anshuman-git-code&repo=Event-Ticketing-System-V3&theme=tokyonight&hide_border=true&title_color=FF9900&icon_color=FF9900&text_color=94A3B8" alt="EventSphere Pin" />
  </a>
  <a href="https://github.com/Anshuman-git-code/Linkforge_Pro">
    <img src="https://github-readme-stats.vercel.app/api/pin/?username=Anshuman-git-code&repo=Linkforge_Pro&theme=tokyonight&hide_border=true&title_color=FF9900&icon_color=FF9900&text_color=94A3B8" alt="LinkForge Pin" />
  </a>
  <br/>
  <a href="https://github.com/Anshuman-git-code/Resume-Parser-Skill-Matcher">
    <img src="https://github-readme-stats.vercel.app/api/pin/?username=Anshuman-git-code&repo=Resume-Parser-Skill-Matcher&theme=tokyonight&hide_border=true&title_color=FF9900&icon_color=FF9900&text_color=94A3B8" alt="Resume Parser Pin" />
  </a>
  <a href="https://github.com/Anshuman-git-code/serverless-image-optimizer">
    <img src="https://github-readme-stats.vercel.app/api/pin/?username=Anshuman-git-code&repo=serverless-image-optimizer&theme=tokyonight&hide_border=true&title_color=FF9900&icon_color=FF9900&text_color=94A3B8" alt="Image Optimizer Pin" />
  </a>

  <br/><br/>
  <hr style="border: 0.5px solid #24283b; width: 85%;" />
  <br/>

  <!-- ========================================== -->
  <!-- 11. INFRASTRUCTURE & TOOLING BADGE MATRIX  -->
  <!-- ========================================== -->
  <h4>🏷️ Infrastructure & Tooling Footprint</h4>
  <p><i>Ecosystem technologies deployed across repositories</i></p>
  <img src="https://img.shields.io/badge/AWS_Cloud-Lambda_·_EventBridge_·_DynamoDB-FF9900?style=for-the-badge&logo=amazonaws&logoColor=white" alt="AWS Footprint" />
  <img src="https://img.shields.io/badge/IaC-Terraform_·_CloudFormation-7B42BC?style=for-the-badge&logo=terraform&logoColor=white" alt="IaC Footprint" />
  <img src="https://img.shields.io/badge/Orchestration-Docker_·_Kubernetes-2496ED?style=for-the-badge&logo=docker&logoColor=white" alt="Containers" />

</div>

</details>

<br/>
