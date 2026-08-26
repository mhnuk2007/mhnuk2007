<div align="center">

<!-- ANIMATED HEADER -->
<img src="https://capsule-render.vercel.app/api?type=waving&amp;color=gradient&amp;customColorList=6,12,20&amp;height=180&amp;section=header&amp;text=Mohan%20Lal&amp;fontSize=70&amp;fontAlignY=35&amp;animation=fadeIn&amp;fontColor=FFFFFF" alt="Mohan Lal - Java and Spring Boot Engineer" />

<!-- TYPING ANIMATION -->
<img src="https://readme-typing-svg.herokuapp.com/?font=Fira+Code&weight=600&size=28&pause=1000&color=6366F1&center=true&vCenter=true&width=800&lines=Java+%26+Spring+Boot+Engineer;Java+Full+Stack+Developer;Open+Source+Contributor+%7C+Eclipse+JNoSQL;Jakarta+EE+%7C+Jakarta+NoSQL;Microservices+%7C+Docker+%7C+Kubernetes;Cloud-Native+Development+%7C+AWS;Building+AI-Powered+Applications" alt="Mohan Lal - Java and Spring Boot Engineer" />

<br><br>

<!-- SOCIAL BADGES -->
[![Portfolio](https://img.shields.io/badge/🌐_Live_Portfolio-6366F1?style=for-the-badge&logoColor=white)](https://mhnuk2007.github.io/)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/mhnuk2007/)
[![LeetCode](https://img.shields.io/badge/LeetCode-Profile-FFA116?style=for-the-badge&logo=leetcode&logoColor=white)](https://leetcode.com/u/mhnuk2007/)
[![GitHub](https://img.shields.io/badge/GitHub-mhnuk2007-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/mhnuk2007)

</div>

<br>

<div align="center">
  <img src="https://komarev.com/ghpvc/?username=mhnuk2007&label=Profile%20Views&color=6366f1&style=flat-square" alt="GitHub profile views for mhnuk2007" />
</div>

---

# 👋 Hi, I'm Mohan Lal

I'm a **Java and Spring Boot Engineer and Open Source Contributor** focused on backend engineering, microservices, cloud-native systems, and modern full-stack development.

My primary backend stack is **Java and Spring Boot**, with hands-on experience in REST APIs, microservices, databases, security, testing, Docker, Kubernetes, AWS, Terraform, and AI-powered applications.

I contribute to open-source projects in the Java ecosystem, including **Eclipse JNoSQL, Jakarta EE, Jakarta Agentic AI, and Spring-related projects**, where I investigate real issues, build reproducible test cases, implement fixes, and contribute regression tests.

### 🔎 Core Focus

- **Java & Spring Boot**
- **Spring Framework & Spring Security**
- **Microservices & REST APIs**
- **Jakarta EE & Jakarta NoSQL**
- **Eclipse JNoSQL**
- **Jakarta Agentic AI**
- **PostgreSQL & MySQL**
- **Docker & Kubernetes**
- **AWS & Terraform**
- **Angular, React & Next.js**
- **Spring AI & AI-powered applications**
- **Data structures & algorithms**

> **GitHub:** [`mhnuk2007`](https://github.com/mhnuk2007)
> **Primary focus:** Java • Spring Boot • Microservices • Cloud • Open Source

---

## 🌟 Open Source Contributions

### Eclipse JNoSQL

Contributing to the Jakarta NoSQL ecosystem through bug investigation, root-cause analysis, regression testing, and production fixes.

#### 🐛 Fixed `Page.totalElements()` Access Outside Transactions

**JNoSQL Extensions — PR #209 · Merged**

Identified and fixed an issue where `Page.totalElements()` could fail after an automatically created repository transaction had completed.

**What I contributed:**

- Traced the transaction lifecycle around repository method execution.
- Identified that `Page` content was eagerly loaded while totals remained lazy.
- Updated `EnsureTransactionInterceptor` to evaluate `totalElements()` while the automatically created transaction was still active.
- Added `PageOutsideTransactionTest` as a regression test.
- Contributed the fix to the `1.1.x` branch.

**Result:** `Page.totalElements()` can safely be accessed after the repository call returns.

🔗 [Issue #707](https://github.com/eclipse-jnosql/jnosql/issues/707) · [Merged PR #209](https://github.com/eclipse-jnosql/jnosql-extensions/pull/209)

---

#### 🧪 Ported Regression Coverage to the Main Branch

**JNoSQL Extensions — PR #210 · Merged**

After a major Jakarta Persistence refactoring, I ported the regression scenario from the `1.1.x` fix to the `main` branch.

**What I contributed:**

- Adapted the regression test to the new implementation.
- Verified that `Page.totalElements()` remains accessible without an active transaction.
- Reused the repository-level scenario against the refactored implementation.
- Added permanent regression coverage to `main`.

🔗 [Merged PR #210](https://github.com/eclipse-jnosql/jnosql-extensions/pull/210)

---

#### 🔧 Fixed `ConstructorBuilder` ServiceLoader Lookup

**JNoSQL — Issue #631 / PR #765 · Merged**

Investigated a `NoSQLException` reported in a reactive Quarkus application where `ConstructorBuilderSupplier` could not be discovered during initialization.

The issue was traced to **Java `ServiceLoader` provider discovery and thread context class loader (TCCL) visibility**.

**What I contributed:**

- Investigated the failure using standalone and Quarkus/Vert.x reproducer projects.
- Isolated the problem to `ServiceLoader` provider discovery and class-loader visibility.
- Implemented a **TCCL-first with defining-class-loader fallback** strategy.
- Preserved normal TCCL-based provider discovery where available.
- Added regression coverage using an isolated TCCL.
- Validated the fix with dedicated regression tests and downstream reproducer scenarios.

**Result:** `ConstructorBuilderSupplier` can still be discovered when the current thread's context class loader cannot see the provider.

🔗 [Issue #631](https://github.com/eclipse-jnosql/jnosql/issues/631) · [Merged PR #765](https://github.com/eclipse-jnosql/jnosql/pull/765)

---

#### 🚀 Applied the `ConstructorBuilder` Fix to the Main Branch

**JNoSQL — PR #768 · Open**

Applied the same `ConstructorBuilder` ServiceLoader fix to the `main` branch targeting the Jakarta EE 12 line.

**What I contributed:**

- Added the TCCL-first provider lookup strategy.
- Added fallback to `ConstructorBuilder.class.getClassLoader()`.
- Added a dedicated regression test using an isolated TCCL.
- Verified provider discovery through the fallback path.
- Ran the complete `jnosql-mapping-api-core` test suite.

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

- Added support for `CompletionStage<T>`.
- Added support for `CompletionStage<List<T>>`.
- Added support for `CompletionStage<Optional<T>>`.
- Added regression coverage for asynchronous repository return types.
- Kept the asynchronous capability change separate from the class-loader fix.

🔗 [PR #764](https://github.com/eclipse-jnosql/jnosql/pull/764)

---

#### 🔍 Investigated Common Class-Loader and `ServiceLoader` Handling

**JNoSQL — Issue #766**

Investigated opportunities to centralize repeated class-loader and `ServiceLoader` handling across the project.

The work explores extracting common lookup behavior into a reusable utility while keeping targeted bug fixes independently reviewable.

🔗 [Issue #766](https://github.com/eclipse-jnosql/jnosql/issues/766)

---

## 🤖 Jakarta Agentic AI

Contributing to the **Jakarta Agentic AI** project through practical improvements to example applications and domain models.

### 💰 Added JSR 354 `MonetaryAmount` to `BankTransaction`

**Jakarta Agentic AI — Issue #11 / PR #59 · Merged**

Updated the fraud-detection example's `BankTransaction` model to represent monetary values using **JSR 354 `MonetaryAmount`**, making the example closer to a realistic financial domain model.

**What I contributed:**

- Replaced the simplistic monetary representation with JSR 354 `MonetaryAmount`.
- Added the required `javax.money:money-api:1.1` dependency.
- Added basic getters and setters for the transaction fields.
- Updated the fraud-detection example to use the monetary value type.
- Verified the implementation with the project's Maven build and tests.
- Kept the change focused on the requested domain-model improvement.

**Validation:**

```text
git diff --check

mvn -pl examples/fraud-detection -am clean test

Build completed successfully.
```

**Result:** `BankTransaction` now models monetary values using the standard Java Money API rather than a simplistic numeric representation.

🔗 [Issue #11](https://github.com/jakartaee/agentic-ai/issues/11) · [Merged PR #59](https://github.com/jakartaee/agentic-ai/pull/59)

---

## 🌱 Spring Lens

### ✨ Implemented `BeanDefinitionSummary`

**Spring Lens — Issue #269 / PR #270 · Merged**

Implemented a new immutable domain model for aggregating Spring bean-definition metrics.

**What I contributed:**

- Added the immutable `BeanDefinitionSummary` Java record.
- Implemented defensive copying using `Map.copyOf()`.
- Added null-safe handling for distribution maps.
- Added validation for non-negative bean-definition totals.
- Introduced `LoadingMode` with `EAGER` and `LAZY` values.
- Added comprehensive unit tests.
- Added JavaDoc for the model and factory method.

**Testing:**

```text
mvn -pl spring-lens-core test

BeanDefinitionSummaryTest:
5 tests passed
```

🔗 [Issue #269](https://github.com/sdlc-pro/spring-lens/issues/269) · [Merged PR #270](https://github.com/sdlc-pro/spring-lens/pull/270)

---

<div align="center">

### 📌 Open Source Impact

| 🐛 Production Bug Fix | 🧪 Regression Coverage | 🔧 Class-Loader Fix | ⚡ Async Repository Support | 💰 Java Money API | 🏗️ Domain Modeling |
| :---: | :---: | :---: | :---: | :---: | :---: |
| JNoSQL Extensions | JNoSQL Extensions | JNoSQL | JNoSQL | Jakarta Agentic AI | Spring Lens |
| Transaction lifecycle | Jakarta Persistence | `ServiceLoader` fallback | `CompletionStage` | JSR 354 `MonetaryAmount` | Immutable Java record |
| **PR #209 · Merged** | **PR #210 · Merged** | **PR #765 · Merged / #768 Open** | **PR #764 · Open** | **PR #59 · Merged** | **PR #270 · Merged** |

</div>

---

## 💡 What Open Source Has Taught Me

Open source has changed the way I approach software engineering.

It has pushed me beyond simply writing code that works. I have learned to investigate unfamiliar codebases, reproduce difficult failures, trace framework behavior, understand class loaders and transaction lifecycles, work with Java platform APIs, write regression tests, respond to review feedback, and maintain changes across multiple release branches.

The most valuable lesson has been simple:

> **Confidence does not always come before difficult work. Sometimes confidence is built by doing the difficult work you initially think you are not ready for.**

Every issue investigated, reproducer built, failed hypothesis, regression test, review, and merged pull request has made me a better engineer.

I started contributing to learn from established open-source projects. Along the way, I discovered that I could investigate real problems, understand complex systems, and contribute meaningful fixes.

**Open source has not only improved my GitHub profile — it has improved my confidence as an engineer.**

---

## 📚 Current Learning & Development

### ☕ Java & Spring Boot

My primary development focus is **Java and Spring Boot**, with continued work in:

- Spring Boot
- Spring Security
- REST APIs
- Microservices
- Persistence
- Testing
- Cloud-native applications
- AI integration

### 🧩 Jakarta EE & JNoSQL

Continuing to learn and contribute to the Jakarta ecosystem through hands-on work with:

- Jakarta EE
- Jakarta Persistence
- Jakarta NoSQL
- Eclipse JNoSQL
- `ServiceLoader`
- asynchronous repository APIs
- transaction management
- Java class-loader behavior

### 🤖 Jakarta Agentic AI

Exploring practical AI application development within the Jakarta ecosystem while contributing improvements to real project examples.

Current interests include:

- Agentic AI applications
- Jakarta EE
- Java-based AI systems
- realistic domain modeling
- enterprise application architecture

### 🧠 Data Structures & Algorithms

Practicing algorithmic problem solving with Java and tracking:

- Time complexity
- Space complexity
- Pattern recognition
- Dynamic programming
- Sliding window
- Two pointers
- Binary search
- Hashing
- Trees and graphs

LeetCode: [@mhnuk2007](https://leetcode.com/u/mhnuk2007/)
Java DSA: [leetcodepractice](https://github.com/mhnuk2007/leetcodepractice)

### 🐍 Python DSA

- Big-O analysis
- Recursion
- Algorithm optimization
- Memoization
- Dynamic programming

Repository: [Python DSA Practice](https://github.com/mhnuk2007/python-dsa)

### 💠 C# / .NET

Exploring C# and .NET fundamentals through hands-on console applications covering:

- C# fundamentals
- OOP
- Collections
- Exception handling
- Parsing and type conversion

Repository: [C#/.NET Practice](https://github.com/mhnuk2007/learning-dotnet)

---

## 👨‍💻 Technical Skills

### Backend Engineering

**Java • Spring Boot • Spring Framework • Spring Security • Spring AI • Microservices • REST APIs**

- RESTful API design
- Microservices architecture
- Authentication and authorization
- OAuth2 and JWT
- Database integration
- Testing and regression coverage
- AI-powered backend applications

### Jakarta & Enterprise Java

**Jakarta EE • Jakarta Persistence • Jakarta NoSQL • Eclipse JNoSQL • ServiceLoader**

- Enterprise Java APIs
- Persistence
- Repository abstractions
- Transaction management
- Service provider discovery
- Class-loader behavior
- Asynchronous repository APIs

### Frontend Development

**Angular • React • Next.js • TypeScript • JavaScript**

- Component architecture
- State management
- Responsive interfaces
- Type-safe development
- Performance optimization

### Cloud & Infrastructure

**AWS • Docker • Kubernetes • Terraform • CI/CD**

- Containerization
- Kubernetes orchestration
- Infrastructure as Code
- Cloud deployments
- Automated testing and deployment

### Data & AI

**PostgreSQL • MySQL • pgvector • Spring AI**

- Relational database design
- Query optimization
- Vector search
- Embeddings
- Semantic search
- Retrieval-Augmented Generation patterns

---

## 🛠️ Technology Stack

**Backend**

![Java](https://img.shields.io/badge/Java-ED8B00?style=flat-square&logo=openjdk&logoColor=white)
![Spring](https://img.shields.io/badge/Spring-6DB33F?style=flat-square&logo=spring&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring_Boot-6DB33F?style=flat-square&logo=spring-boot&logoColor=white)
![Spring Security](https://img.shields.io/badge/Spring_Security-6DB33F?style=flat-square&logo=spring-security&logoColor=white)
![Microservices](https://img.shields.io/badge/Microservices-FF6B6B?style=flat-square)

**Jakarta & Enterprise Java**

![Jakarta EE](https://img.shields.io/badge/Jakarta_EE-007396?style=flat-square&logo=eclipse&logoColor=white)
![Jakarta NoSQL](https://img.shields.io/badge/Jakarta_NoSQL-007396?style=flat-square&logo=eclipse&logoColor=white)
![Eclipse JNoSQL](https://img.shields.io/badge/Eclipse_JNoSQL-2C2255?style=flat-square&logo=eclipse&logoColor=white)

**Frontend**

![Angular](https://img.shields.io/badge/Angular-DD0031?style=flat-square&logo=angular&logoColor=white)
![React](https://img.shields.io/badge/React-20232A?style=flat-square&logo=react&logoColor=61DAFB)
![Next.js](https://img.shields.io/badge/Next.js-000?style=flat-square&logo=next.js&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black)

**Cloud & DevOps**

![AWS](https://img.shields.io/badge/AWS-232F3E?style=flat-square&logo=amazon-aws&logoColor=FF9900)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=flat-square&logo=kubernetes&logoColor=white)
![Terraform](https://img.shields.io/badge/Terraform-7B42BC?style=flat-square&logo=terraform&logoColor=white)

**Data & AI**

![PostgreSQL](https://img.shields.io/badge/PostgreSQL-316192?style=flat-square&logo=postgresql&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white)
![pgvector](https://img.shields.io/badge/pgvector-316192?style=flat-square&logo=postgresql&logoColor=white)
![Spring AI](https://img.shields.io/badge/Spring_AI-6DB33F?style=flat-square&logo=spring&logoColor=white)

---

## 📊 GitHub Analytics

<div align="center">

![GitHub Stats](https://github-readme-stats.vercel.app/api?username=mhnuk2007&show_icons=true&theme=react&bg_color=0D1117&title_color=6366F1)

![Streak Stats](https://github-readme-streak-stats.herokuapp.com/?user=mhnuk2007&theme=react&bg_color=0D1117&title_color=6366F1)

</div>

---

## 🤝 Why Work With Me?

- ✅ **Problem Solver** — I investigate, reproduce, debug, and fix difficult problems.
- ✅ **Java & Spring Boot Focused** — My primary backend ecosystem.
- ✅ **Open Source Contributor** — Experience working with real production codebases.
- ✅ **Jakarta Ecosystem Contributor** — Hands-on contribution to Jakarta EE, Jakarta NoSQL, and Jakarta Agentic AI projects.
- ✅ **Full-Stack Versatility** — Comfortable across backend, frontend, databases, and infrastructure.
- ✅ **Self-Directed Learner** — I continuously learn by building and contributing.
- ✅ **Production Mindset** — Focused on testing, maintainability, reliability, and scalability.
- ✅ **Continuous Improvement** — Every issue and code review is an opportunity to become a better engineer.

---

<div align="center">

## 📬 Connect With Me

**Mohan Lal · `mhnuk2007`**

[![Portfolio](https://img.shields.io/badge/Portfolio-Visit_My_Work-6366F1?style=for-the-badge&logo=google-chrome&logoColor=white)](https://mhnuk2007.github.io/)
[![GitHub](https://img.shields.io/badge/GitHub-mhnuk2007-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/mhnuk2007)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Let's_Connect-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/mhnuk2007/)
[![LeetCode](https://img.shields.io/badge/LeetCode-Profile-FFA116?style=for-the-badge&logo=leetcode&logoColor=white)](https://leetcode.com/u/mhnuk2007/)

</div>

<br>

---

<div align="center">

### ⚡ The Journey

**Self-taught. Curious. Persistent. Always learning.**

My development journey is built around hands-on practice, real projects, open-source contributions, debugging difficult problems, and continuous learning.

I don't believe a developer's growth is defined by a degree or a job title. It is defined by the problems they are willing to understand, the systems they are willing to build, and the effort they put into becoming better every day.

**Still learning. Still building. Still contributing. 🚀**

<br>

<sub>💙 Crafted with code and coffee • Last updated: August 2026</sub>

</div>

<!-- FOOTER WAVE -->
<img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=6,12,20&height=120&section=footer" />