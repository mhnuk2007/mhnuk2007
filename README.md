<div align="center">

<!-- ANIMATED HEADER -->
<img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=6,12,20&height=180&section=header&text=Mohan%20Lal&fontSize=70&fontAlignY=35&animation=fadeIn&fontColor=fff&desc=Java%20%26%20Spring%20Boot%20Engineer%20%7C%20Open%20Source%20Contributor&descSize=20&descAlignY=55" />

<!-- TYPING ANIMATION -->
<img src="https://readme-typing-svg.herokuapp.com/?font=Fira+Code&weight=600&size=28&pause=1000&color=6366F1&center=true&vCenter=true&width=800&lines=Self-Taught+Java+Full+Stack+Engineer;Java+%2B+Spring+Boot+%7C+Angular+%2B+React;Open+Source+Contributor+%7C+Eclipse+JNoSQL;Cloud-Native+Systems+%7C+AWS+%2B+Docker+%2B+Kubernetes;Building+AI-Powered+Microservices" alt="Typing Animation" />

<br><br>

<!-- SOCIAL BADGES -->
[![Portfolio](https://img.shields.io/badge/🌐_Live_Portfolio-6366F1?style=for-the-badge&logoColor=white)](https://mhnuk2007.github.io/)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/mhnuk2007/)
[![LeetCode](https://img.shields.io/badge/LeetCode-Profile-FFA116?style=for-the-badge&logo=leetcode&logoColor=white)](https://leetcode.com/u/mhnuk2007/)
[![Email](https://img.shields.io/badge/Email_Me-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:contact+mhnuk2007@example.com)
[![AWS Community](https://img.shields.io/badge/AWS_Emerging_Talent-FF9900?style=for-the-badge&logo=amazon-aws&logoColor=white)](https://linkedin.com/in/mhnuk2007/)

</div>

<br>

<!-- PROFILE VIEWS COUNTER -->
<div align="center">
  <img src="https://komarev.com/ghpvc/?username=mhnuk2007&label=Profile%20Views&color=6366f1&style=flat-square" alt="Profile Views" />
</div>

---

## 🌟 Open Source Contributions

### Eclipse JNoSQL

Contributing to the Jakarta NoSQL ecosystem through bug investigation, root-cause analysis, regression testing, and production fixes.

#### 🐛 Fixed `Page.totalElements()` Access Outside Transactions

**JNoSQL Extensions — PR #209 · Merged**

Identified and fixed an issue where `Page.totalElements()` could fail after an automatically created repository transaction had completed.

**What I contributed:**

* Traced the transaction lifecycle around repository method execution.
* Identified that `Page` content was eagerly loaded, while totals remained lazy.
* Updated `EnsureTransactionInterceptor` to evaluate `totalElements()` while the automatically created transaction was still active.
* Added `PageOutsideTransactionTest` as a regression test.
* Fix merged into the `1.1.x` branch.

**Result:** `Page.totalElements()` can safely be accessed after the repository call returns.

🔗 [Issue #707](https://github.com/eclipse-jnosql/jnosql/issues/707) · [Merged PR #209](https://github.com/eclipse-jnosql/jnosql-extensions/pull/209)

---

#### 🧪 Ported Regression Coverage to the Main Branch

**JNoSQL Extensions — PR #210 · Merged**

After a major Jakarta Persistence refactoring, I ported the regression scenario from the `1.1.x` fix to the `main` branch.

**What I contributed:**

* Adapted the regression test to the new `1.2.0-SNAPSHOT` implementation.
* Verified `Page.totalElements()` remains accessible without an active transaction.
* Reused the repository-level scenario against the refactored implementation.
* Added permanent regression coverage for the behavior on `main`.

🔗 [Merged PR #210](https://github.com/eclipse-jnosql/jnosql-extensions/pull/210)

> Maintainers confirmed that the regression scenario remained valid after the Jakarta Persistence refactoring.

---

#### 🔧 Fixed `ConstructorBuilder` ServiceLoader Lookup on `1.1.x`

**JNoSQL — Issue #631 / PR #765 · Merged**

Investigated a `NoSQLException` reported in a reactive Quarkus application where `ConstructorBuilderSupplier` could not be discovered during initialization.

The issue was traced to `ServiceLoader` lookup through the thread context class loader (TCCL). In environments where the initializing thread's TCCL could not see the provider, `ConstructorBuilder` failed during static initialization.

**What I contributed:**

* Investigated the failure using standalone and Quarkus/Vert.x-based reproducer projects.
* Isolated the problem to `ServiceLoader` provider discovery and class-loader visibility during `ConstructorBuilder` initialization.
* Implemented a **TCCL-first with defining-class-loader fallback** strategy.
* Preserved normal TCCL-based provider discovery where available.
* Added regression coverage using an isolated TCCL that cannot access the provider.
* Validated the fix against dedicated regression tests, the complete module test suite, and downstream reproducer scenarios.

**Result:** `ConstructorBuilderSupplier` can still be discovered when the current thread's context class loader cannot see the provider.

🔗 [Issue #631](https://github.com/eclipse-jnosql/jnosql/issues/631) · [Merged PR #765](https://github.com/eclipse-jnosql/jnosql/pull/765)

---

#### 🚀 Applied the `ConstructorBuilder` Fix to the Main Branch

**JNoSQL — PR #768 · Open**

Applied the same `ConstructorBuilder` ServiceLoader fix to the `main` branch, which targets the Jakarta EE 12 line.

**What I contributed:**

* Added the TCCL-first provider lookup strategy to the current `main` implementation.
* Falls back to `ConstructorBuilder.class.getClassLoader()` when the TCCL is `null` or cannot discover a provider.
* Added a dedicated regression test that initializes `ConstructorBuilder` with an isolated TCCL.
* Verified that the fallback path successfully discovers the provider.
* Ran the complete `jnosql-mapping-api-core` test suite.

**Validation:**

```text
Dedicated regression test:
Tests run: 1, Failures: 0, Errors: 0, Skipped: 0

Complete module test suite:
Tests run: 67, Failures: 0, Errors: 0, Skipped: 0

Checkstyle: 0 violations
Apache RAT: 0 unapproved files
Java 21 CI: Passed
Java 25 CI: Passed
Eclipse Contributor Agreement check: Passed
```

🔗 [PR #768](https://github.com/eclipse-jnosql/jnosql/pull/768)

---

#### ⚡ Added `CompletionStage` Repository Return Support

**JNoSQL — PR #764 · Open**

Worked on support for asynchronous repository methods returning `CompletionStage` types.

**What I contributed:**

* Added handling for `CompletionStage<T>`.
* Added support for `CompletionStage<List<T>>`.
* Added support for `CompletionStage<Optional<T>>`.
* Added regression coverage for asynchronous repository return types.
* Kept this capability change separate from the class-loader fix so each change can be reviewed independently.

🔗 [PR #764](https://github.com/eclipse-jnosql/jnosql/pull/764)

---

#### 🔍 Investigated Common Class-Loader and `ServiceLoader` Handling

**JNoSQL — Issue #766 · Investigation and Local Implementation**

Investigated opportunities to centralize repeated class-loader and `ServiceLoader` handling across the project.

The work explores extracting common lookup behavior into a reusable utility while keeping targeted bug fixes independently reviewable.

🔗 [Issue #766](https://github.com/eclipse-jnosql/jnosql/issues/766)

---

### 🌱 Spring Lens

#### ✨ Implemented `BeanDefinitionSummary` Domain Model

**Spring Lens — Issue #269 / PR #270 · Merged**

Implemented a new immutable domain model for aggregating Spring bean-definition metrics.

**What I contributed:**

* Added the immutable `BeanDefinitionSummary` Java record.
* Implemented defensive copying using `Map.copyOf()`.
* Added null-safe handling for distribution maps.
* Added validation for non-negative bean definition totals.
* Introduced the `LoadingMode` enum with `EAGER` and `LAZY` values after identifying a missing dependency in the original issue specification.
* Added comprehensive unit tests for validation, immutability, null handling, and `empty()`.
* Added JavaDoc for the model and factory method.

**Testing:**

```text
mvn -pl spring-lens-core test
BeanDefinitionSummaryTest: 5 tests passed
```

🔗 [Issue #269](https://github.com/sdlc-pro/spring-lens/issues/269) · [Merged PR #270](https://github.com/sdlc-pro/spring-lens/pull/270)

---

<div align="center">

### 📌 Open Source Impact

| 🐛 Production Bug Fix |    🧪 Regression Coverage    |        🔧 Class-Loader Fix       | ⚡ Async Repository Support |  🏗️ Domain Modeling  |
| :-------------------: | :--------------------------: | :------------------------------: | :------------------------: | :-------------------: |
|   JNoSQL Extensions   |       JNoSQL Extensions      |              JNoSQL              |           JNoSQL           |      Spring Lens      |
| Transaction lifecycle | Jakarta Persistence refactor |     `ServiceLoader` fallback     |  `CompletionStage` returns | Immutable Java record |
|  **PR #209 · Merged** |     **PR #210 · Merged**     | **PR #765 · Merged / #768 Open** |     **PR #764 · Open**     |  **PR #270 · Merged** |

</div>

---

## 🌱 What Open Source Has Taught Me

Open source has changed the way I approach software engineering.

It has pushed me beyond simply writing code that works. I have learned to investigate unfamiliar codebases, reproduce difficult failures, trace framework behavior, understand class loaders and transaction lifecycles, write regression tests, respond to review feedback, and maintain changes across multiple release branches.

The most valuable lesson has been simple:

> **Confidence does not always come before difficult work. Sometimes confidence is built by doing the difficult work you initially think you are not ready for.**

Every issue investigated, reproducer built, failed hypothesis, regression test, review, and merged pull request has made me a better engineer.

I started contributing to learn from established open-source projects. Along the way, I discovered that I could investigate real problems, understand complex systems, and contribute meaningful fixes.

**Open source did not just improve my GitHub profile — it improved my confidence as an engineer.**

---

## Recent Learning Updates (2026)

### C#/.NET Learning Journey
- Built hands-on console apps covering C# fundamentals, OOP, exception handling, collections, string operations, and parsing/type conversion.
- Expanded backend perspective by learning C# alongside Java and Python.
- Repository: [C#/.NET Practice](https://github.com/mhnuk2007/learning-dotnet)

### Python DSA Journey
- Practiced Big-O analysis, recursion, number problems, and algorithm optimization strategies.
- Compared iterative, recursive, memoization, and dynamic programming approaches to reduce TLE.
- Repository: [Python DSA Practice](https://github.com/mhnuk2007/python-dsa)

### Python Learning Milestone
- Completed a full Python path including OOP, data structures, file handling, exceptions, regex, and event-driven/polling programming.
- Repository: [Python Learning Repository](https://github.com/mhnuk2007/learning-python)

### Current DSA Focus (Java)
- Practicing daily on LeetCode with a pattern-based plan: two pointers, sliding window, recursion, binary search, and hashing.
- Tracking complexity for every solution and pushing clean Java implementations to GitHub.
- LeetCode: [Profile](https://leetcode.com/u/mhnuk2007/)
- GitHub: [Java DSA Repository](https://github.com/mhnuk2007/leetcodepractice)

---

## 👨‍💻 About Me

```typescript
const mohanLal = {
    role: "Java & Spring Boot Engineer | Open Source Contributor",
    location: "Karachi, Pakistan 🇵🇰",
    background: "Self-Taught Developer (No CS Degree Required)",

    expertise: {
        backend: ["Java", "Spring Boot", "Spring Security", "Spring AI", "Microservices"],
        frontend: ["Angular", "React", "Next.js", "TypeScript"],
        cloud: ["AWS", "Azure", "Docker", "Kubernetes", "Terraform"],
        data: ["PostgreSQL", "MySQL", "pgvector", "Vector Embeddings"]
    },

    currentFocus: [
        "Practicing Java DSA daily (patterns + complexity analysis)",
        "Building C#/.NET console projects to strengthen fundamentals",
        "Solving optimization-focused Python DSA problems",
        "Applying algorithmic thinking to backend API design"
    ],

    achievements: ["AWS Emerging Talent Community Member 🏆"],

    philosophy: "Code is poetry; architecture is storytelling",

    funFact: "Built everything without formal CS education—just curiosity, persistence, and 10,000+ hours of hands-on learning"
};
```

<br>

---

## 🚀 What I Bring to the Table

<table>
<tr>
<td width="50%" valign="top">

### 💼 Backend Engineering
**Building scalable, secure systems**

- ✅ **RESTful API Design** - Clean, documented, production-ready
- ✅ **Microservices Architecture** - Event-driven, resilient services
- ✅ **Spring Ecosystem Mastery** - Boot, Security, Data, AI
- ✅ **Database Optimization** - SQL tuning, indexing, query optimization
- ✅ **AI Integration** - Embeddings, vector search, RAG patterns
- ✅ **Authentication & Security** - OAuth2, JWT, Spring Security

**Technologies:**
![Java](https://img.shields.io/badge/Java-ED8B00?style=flat-square&logo=openjdk&logoColor=white)
![Spring](https://img.shields.io/badge/Spring-6DB33F?style=flat-square&logo=spring&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring_Boot-6DB33F?style=flat-square&logo=spring-boot&logoColor=white)
![Spring Security](https://img.shields.io/badge/Spring_Security-6DB33F?style=flat-square&logo=spring-security&logoColor=white)
![Microservices](https://img.shields.io/badge/Microservices-FF6B6B?style=flat-square)

</td>
<td width="50%" valign="top">

### 🎨 Frontend Development
**Crafting modern, responsive experiences**

- ✅ **Component Architecture** - Modular, reusable, testable
- ✅ **State Management** - RxJS, Redux, NgRx patterns
- ✅ **Responsive Design** - Mobile-first, accessible UIs
- ✅ **TypeScript First** - Type-safe development
- ✅ **Performance Optimization** - Lazy loading, code splitting
- ✅ **Modern Frameworks** - Angular 18+, React 18+, Next.js 14+

**Technologies:**
![Angular](https://img.shields.io/badge/Angular-DD0031?style=flat-square&logo=angular&logoColor=white)
![React](https://img.shields.io/badge/React-20232A?style=flat-square&logo=react&logoColor=61DAFB)
![Next.js](https://img.shields.io/badge/Next.js-000?style=flat-square&logo=next.js&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black)

</td>
</tr>
<tr>
<td width="50%" valign="top">

### ☁️ Cloud & Infrastructure
**Deploying at scale with confidence**

- ✅ **Multi-Cloud Expertise** - AWS & Azure certified paths
- ✅ **Container Orchestration** - Kubernetes production deployments
- ✅ **Infrastructure as Code** - Terraform for repeatable deployments
- ✅ **CI/CD Pipelines** - Automated testing and deployment
- ✅ **Monitoring & Logging** - Observability-first approach
- ✅ **Cost Optimization** - Efficient resource utilization

**Technologies:**
![AWS](https://img.shields.io/badge/AWS-232F3E?style=flat-square&logo=amazon-aws&logoColor=FF9900)
![Azure](https://img.shields.io/badge/Azure-0072C6?style=flat-square&logo=microsoftazure&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=flat-square&logo=kubernetes&logoColor=white)
![Terraform](https://img.shields.io/badge/Terraform-7B42BC?style=flat-square&logo=terraform&logoColor=white)

</td>
<td width="50%" valign="top">

### 🗄️ Data & AI
**Making data intelligent and searchable**

- ✅ **Relational Databases** - PostgreSQL, MySQL expertise
- ✅ **Vector Databases** - pgvector for semantic search
- ✅ **AI/ML Integration** - Spring AI framework implementation
- ✅ **Embedding Models** - Text-to-vector transformations
- ✅ **Semantic Search** - Cosine similarity, RAG patterns
- ✅ **Data Modeling** - Normalization, optimization strategies

**Technologies:**
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-316192?style=flat-square&logo=postgresql&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white)
![Vector DB](https://img.shields.io/badge/pgvector-316192?style=flat-square&logo=postgresql&logoColor=white)
![Spring AI](https://img.shields.io/badge/Spring_AI-6DB33F?style=flat-square&logo=spring&logoColor=white)
![Embeddings](https://img.shields.io/badge/Vector_Embeddings-8B5CF6?style=flat-square)

</td>
</tr>
</table>

<br>

---

## 📊 GitHub Analytics

<div align="center">

![GitHub Stats](https://github-readme-stats.vercel.app/api?username=mhnuk2007&show_icons=true&theme=react&bg_color=0D1117&title_color=6366F1)

![Streak Stats](https://github-readme-streak-stats.herokuapp.com/?user=mhnuk2007&theme=react&bg_color=0D1117&title_color=6366F1)

</div>

### Why Work With Me?

✅ **Problem-Solver Mindset** - I debug, research, and build until it works
✅ **Full-Stack Versatility** - Comfortable at every layer of the stack
✅ **Self-Directed Learner** - If I don't know it, I'll master it
✅ **Production-Focused** - Code that scales, deploys, and performs
✅ **Clear Communicator** - Technical concepts explained simply

<br>

<div align="center">

### 📬 Get In Touch

**Let's connect and create something amazing!**

[![Portfolio](https://img.shields.io/badge/Portfolio-Visit_My_Work-6366F1?style=for-the-badge&logo=google-chrome&logoColor=white)](https://mhnuk2007.github.io/)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Let's_Connect-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/mhnuk2007/)
[![Email](https://img.shields.io/badge/Email-Drop_a_Message-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:your-email@example.com)

</div>

<br>

---

<div align="center">

### ⚡ The Journey

**No formal CS degree. No bootcamp. Just pure curiosity and relentless practice.**

I've spent 10,000+ hours building real projects, debugging production issues, and learning from every failure. Every line of code in my repositories represents a problem solved, a concept mastered, and a step forward in my journey.

**The best part?** I'm just getting started. 🚀

<br>

<sub>💙 Crafted with code and coffee • Last updated: August 2026</sub>

</div>

<!-- FOOTER WAVE -->
<img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=6,12,20&height=120&section=footer" />