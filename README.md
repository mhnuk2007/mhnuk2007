<div align="center">

<!-- ANIMATED HEADER -->

<img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=6,12,20&height=180&section=header&text=Mohan%20Lal&fontSize=70&fontAlignY=35&animation=fadeIn&fontColor=FFFFFF" alt="Mohan Lal - Java and Spring Boot Engineer" />

<!-- TYPING ANIMATION -->

<img src="https://readme-typing-svg.herokuapp.com/?font=Fira+Code&weight=600&size=26&pause=1000&color=6366F1&center=true&vCenter=true&width=850&lines=Java+%26+Spring+Boot+Engineer;Creator+%7C+FinSim+Financial+Network+Simulator;Creator+%7C+College+Teachers+Seniority+Portal;Open+Source+Contributor+%7C+Eclipse+JNoSQL+%26+Jakarta+Data;Distributed+Systems+%7C+Spring+Modulith+%7C+PostgreSQL;Cloud-Native+%7C+Docker+%7C+Kubernetes+%7C+AWS;Building+High-Assurance+Backend+Systems" alt="Mohan Lal - Java and Spring Boot Engineer" />

<br><br>

<!-- SOCIAL BADGES -->

[![Portfolio](https://img.shields.io/badge/%F0%9F%8C%90_Live_Portfolio-6366F1?style=for-the-badge&logoColor=white)](https://mhnuk2007.tech/)
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

I'm a **Java and Spring Boot Backend Engineer and Open Source Contributor** focused on distributed systems, financial networks, high-assurance architecture, enterprise Java, and cloud-native backend engineering.

My core backend stack is **Java 21 and Spring Boot**, with practical experience in distributed payment orchestration, idempotent workflows, finite state machines, Spring Modulith, relational databases (PostgreSQL), Docker, Kubernetes, AWS, and enterprise standards.

I actively build and contribute to open-source software in the Java and distributed systems ecosystem, including **FinSim** (creator & maintainer), **Eclipse JNoSQL**, **Jakarta EE / Jakarta Data**, **Jakarta Agentic AI**, and **Spring-related projects** — debugging complex concurrency/TCCL issues, writing regression and TCK test suites, and designing clean architecture boundaries.

### 🎯 Core Focus

- **Java 21 & Spring Boot 4**
- **Distributed Financial Networks & Payment Orchestration**
- **Finite State Machines & Idempotent Architectures**
- **Spring Modulith & Modular Monoliths**
- **Jakarta EE, Jakarta Data & Jakarta NoSQL**
- **Eclipse JNoSQL Ecosystem**
- **PostgreSQL 17, Flyway & Testcontainers**
- **Docker, Docker Compose & Kubernetes**
- **AWS & Infrastructure as Code (Terraform)**
- **Property-Based Testing & Architecture Verification (ArchUnit)**
- **Modern Full-Stack Development (Next.js 16, TypeScript, React 19)**

> **GitHub:** [`mhnuk2007`](https://github.com/mhnuk2007)  
> **Primary focus:** Java 21 • Spring Boot • Financial Systems • Distributed Systems • Jakarta EE • Cloud-Native

---

# 🚀 Featured Flagship Projects

## 💳 [FinSim — Financial Network Simulator](https://github.com/mhnuk2007/finsim)

> **An open-source distributed financial network simulator:** connect independent participant services (banks, merchants, gateways), run realistic payment flows, enforce strict idempotency, and inject distributed systems failures on purpose.

[![GitHub Repo](https://img.shields.io/badge/GitHub-mhnuk2007%2Ffinsim-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/mhnuk2007/finsim)
![Java 21](https://img.shields.io/badge/Java-21-ED8B00?style=flat-square&logo=openjdk&logoColor=white)
![Spring Boot 4](https://img.shields.io/badge/Spring_Boot-4.1-6DB33F?style=flat-square&logo=spring-boot&logoColor=white)
![Spring Modulith](https://img.shields.io/badge/Spring_Modulith-6DB33F?style=flat-square)
![PostgreSQL 17](https://img.shields.io/badge/PostgreSQL-17-316192?style=flat-square&logo=postgresql&logoColor=white)
![Swagger UI](https://img.shields.io/badge/Swagger_UI-OpenAPI_3.1-85EA2D?style=flat-square&logo=swagger&logoColor=black)
![Next.js 16](https://img.shields.io/badge/Next.js-16_(Web)-000000?style=flat-square&logo=next.js&logoColor=white)
![Testcontainers](https://img.shields.io/badge/Testcontainers-171717?style=flat-square&logo=docker&logoColor=white)
![ArchUnit](https://img.shields.io/badge/ArchUnit-Rules_Enforced-brightgreen?style=flat-square)
![License](https://img.shields.io/badge/License-Apache_2.0-blue.svg?style=flat-square)

### 🏆 Key Highlights & Architectural Scope:

- **Language-Agnostic Participant Contract (`finsim/v1`)**: External institutions (Java, Python, Node.js, Go) communicate over a versioned HTTP/JSON specification defined in OpenAPI 3.1 with interactive Swagger UI (`/swagger-ui.html`).
- **`UNKNOWN` State & ADR 0001 Forward Reconciliation**: Unlike naive sandboxes that convert network timeouts into "failed", FinSim models `UNKNOWN` as a first-class state. Retries are guarded (`409 RECONCILIATION_REQUIRED`), and an automated forward-first decision engine reconciles or reverses debit legs safely with guaranteed zero duplicate credits.
- **Strict Idempotency Enforcement**: Every mutating request requires an `Idempotency-Key` (8–128 chars); identical bodies return cached executions, conflicting bodies return `409 IDEMPOTENCY_CONFLICT`.
- **Fault Injection & Deterministic Replay Engine**: Injects synthetic latency (`DELAY`), transport cutoffs (`TIMEOUT`), and duplicated packets (`DUPLICATE_DELIVERY`). Uses domain-separated SHA-256 IDs, seeded PRNGs, and canonical trace normalization for byte-level deterministic scenario replays.
- **Deterministic Virtual Clock ("Two Clocks Rule")**: Bifurcates temporal mechanics: physical wall-clock for security checks (TLS/JWS nonce TTL) and discrete-event virtual clock for business deadlines, cut-offs, and authorization hold expirations with instantaneous time-travel.
- **Double-Entry Ledger & Conservation Invariants**: Append-only relational journal postings as the single source of truth; database-level immutability rules; mathematical multi-currency zero-sum invariant: $\sum \text{Debits} \equiv \sum \text{Credits}$.
- **Next.js 16 Web Workspace & Simulation Cockpit**: Decoupled web experience featuring an educational human-first landing page ("The flight simulator for digital money") and an observability cockpit with network topologies and trace waterfalls.
- **Strict Architecture Boundaries**: Built with Spring Modulith and ArchUnit to enforce strict cross-module isolation, deterministic clocks, and immutable audit logs (`transfer_stages`).

🔗 **Repository:** [github.com/mhnuk2007/finsim](https://github.com/mhnuk2007/finsim)

---

## 🏛️ [College Teachers Seniority & Retirement Portal](https://seniorityportal.mhnuk2007.tech/)

> **Civic technology platform for the College Education Department, Government of Sindh**  
> An authoritative, read-only analytical compendium managing seniority rosters, statutory retirement timelines, and institutional capacity for the entire collegiate cadre.

[![Live Portal](https://img.shields.io/badge/%F0%9F%8C%90_Live_Portal-seniorityportal.mhnuk2007.tech-0284C7?style=flat-square&logo=google-chrome&logoColor=white)](https://seniorityportal.mhnuk2007.tech/)
[![Vercel Mirror](https://img.shields.io/badge/Vercel_Mirror-seniorityportal.vercel.app-000000?style=flat-square&logo=vercel&logoColor=white)](https://seniorityportal.vercel.app/)
![Next.js 16](https://img.shields.io/badge/Next.js_16-000000?style=flat-square&logo=next.js&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)
![React](https://img.shields.io/badge/React_19-20232A?style=flat-square&logo=react&logoColor=61DAFB)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=flat-square&logo=tailwind-css&logoColor=white)
![Turbopack](https://img.shields.io/badge/Turbopack-000000?style=flat-square&logo=vercel&logoColor=white)
![Vitest](https://img.shields.io/badge/Vitest-6E9F18?style=flat-square&logo=vitest&logoColor=white)
![Private Repository](https://img.shields.io/badge/Source-Private_Official_Repository-yellow?style=flat-square&logo=github&logoColor=white)

### 🏆 Key Highlights & System Scope:

- **24 Cadre Categories & 8,978 Validated Records**: Unified platform encompassing all 4 teaching tiers (Professor, Associate Professor, Assistant Professor, Lecturer — Male & Female) plus Collegiate Librarians and Directors Physical Education (DPE).
- **Zero-Mutation Architectural Pipeline**: Strict read-only ingestion from official departmental master records into validated, category-scoped immutable datasets without data fabrication or guessing.
- **Retirement Analysis & Multi-Year Calendar**: Real-time deterministic retirement projection (`DOB + 60 years - 1 day`), multi-year interactive calendar (2024–2045+), upcoming cohort timelines, and senior/junior relationship mapping.
- **Institutional Directory & SNE Sanctioned Posts**: Tracks **390+ public degree colleges** and **6 regional directorates**, providing detailed sanctioned posts vs. working strength audits, staffing capacity percentages, and structural vacancy tracking.
- **Statutory Decision Support Calculators**: Implements the Sindh Civil Service Pension Calculator (qualifying service rounding, commutation factor matrices) and BPS Pay Fixation Calculator (Rule 10(3) refixation).
- **Engineering & Code Quality**: Fully type-checked with TypeScript (`tsc --noEmit`), React Compiler hygiene, 298 passing unit/integration tests with Vitest, and WCAG AA accessible light/dark theme architecture.

🔗 **Production Deployments:** [seniorityportal.mhnuk2007.tech](https://seniorityportal.mhnuk2007.tech/) • [seniorityportal.vercel.app](https://seniorityportal.vercel.app/)

---

# 📦 Open Source Contributions

## ☕ Jakarta Data

Contributing to **Jakarta Data** through TCK development, asynchronous behavior testing, transaction semantics, and compatibility-oriented test coverage.

### 🧪 Added TCK Coverage for Exceptional Async Completion

**Jakarta Data — PR #1556 • Merged**

Added TCK coverage verifying that an asynchronous repository operation completes exceptionally when an insert violates an existing entity constraint.

**What I contributed:**

- Tested exceptional `CompletionStage` completion.
- Verified `EntityExistsException` as the underlying cause.
- Added regression coverage for asynchronous repository behavior.
- Validated the test against Open Liberty.
- Incorporated review feedback and finalized the portable TCK scenario.

**Validation:**

```text
mvn clean verify — successful
Open Liberty execution — successful
```

🔗 [Issue #19](https://github.com/jakartaee/data/issues/19) • [Merged PR #1556](https://github.com/jakartaee/data/pull/1556)

---

### 🔍 Added TCK Coverage for `QueryOptions` on `JakartaQuery`

**Jakarta Data — PR #1561 • Merged**

Added TCK coverage for:

```java
@QueryOptions(flush = QueryFlushMode.FLUSH)
```

on a repository method using `@JakartaQuery`.

The test verifies that a pending entity modification becomes visible to the repository operation within an active transaction without an explicit flush.

**What I contributed:**

- Added a `@JakartaQuery` repository scenario.
- Added `QueryOptions` / `QueryFlushMode.FLUSH` coverage.
- Designed the test around portable Jakarta Data transaction semantics.
- Revised the test based on TCK review feedback.
- Verified the scenario against a development Open Liberty environment.

🔗 [Merged PR #1561](https://github.com/jakartaee/data/pull/1561)

---

### 🧪 Added `QueryOptions` TCK Coverage for Find, Query, Delete & NativeQuery

**Jakarta Data — PR #1567 • Open**

Added the remaining `@QueryOptions` scenarios from Jakarta Data issue #965:

- `@Find`
- `@Query`
- `@Delete`
- `@NativeQuery`

Each test verifies that a pending entity modification becomes visible to the repository operation when using:

```java
@QueryOptions(flush = QueryFlushMode.FLUSH)
```

**What I contributed:**

- Added `@Find` + `QueryOptions` coverage.
- Added `@Query` + `QueryOptions` coverage.
- Added `@Delete` + `QueryOptions` coverage.
- Added `@NativeQuery` + `QueryOptions` coverage.
- Designed the scenarios around active transaction semantics.
- Kept the tests portable and independent of a particular `EntityManager`.
- Validated compilation and formatting.
- All PR checks are currently passing.

**Status:** Open — awaiting review.

🔗 [Issue #965](https://github.com/jakartaee/data/issues/965) • [PR #1567](https://github.com/jakartaee/data/pull/1567)

---

## ☕ Eclipse JNoSQL

Contributing to the Jakarta NoSQL ecosystem through bug investigation, root-cause analysis, reproducible testing, regression coverage, production fixes, reusable utilities, and maintainability improvements.

### 🐛 Fixed `Page.totalElements()` Access Outside Transactions

**JNoSQL Extensions — PR #209 • Merged**

Identified and fixed an issue where `Page.totalElements()` could fail after an automatically created repository transaction had completed.

**What I contributed:**

- Traced the transaction lifecycle around repository method execution.
- Identified that `Page` content was eagerly loaded while totals remained lazy.
- Updated `EnsureTransactionInterceptor` to evaluate `totalElements()` while the automatically created transaction was still active.
- Added `PageOutsideTransactionTest` as a regression test.
- Contributed the fix to the `1.1.x` branch.

**Result:** `Page.totalElements()` can safely be accessed after the repository call returns.

🔗 [Issue #707](https://github.com/eclipse-jnosql/jnosql/issues/707) • [Merged PR #209](https://github.com/eclipse-jnosql/jnosql-extensions/pull/209)

---

### 🧪 Ported Regression Coverage to the Main Branch

**JNoSQL Extensions — PR #210 • Merged**

After a major Jakarta Persistence refactoring, I ported the regression scenario from the `1.1.x` fix to the `main` branch.

**What I contributed:**

- Adapted the regression test to the new implementation.
- Verified that `Page.totalElements()` remains accessible without an active transaction.
- Reused the repository-level scenario against the refactored implementation.
- Added permanent regression coverage to `main`.

🔗 [Merged PR #210](https://github.com/eclipse-jnosql/jnosql-extensions/pull/210)

---

### ⚙️ Fixed `ConstructorBuilder` ServiceLoader Lookup

**JNoSQL — Issue #631 / PR #765 • Merged**

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

🔗 [Issue #631](https://github.com/eclipse-jnosql/jnosql/issues/631) • [Merged PR #765](https://github.com/eclipse-jnosql/jnosql/pull/765)

---

### 🚀 Applied the `ConstructorBuilder` Fix to the Main Branch

**JNoSQL — PR #768 • Merged**

Applied the same `ConstructorBuilder` `ServiceLoader` fix to the `main` branch targeting the Jakarta EE 12 line.

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

🔗 [Merged PR #768](https://github.com/eclipse-jnosql/jnosql/pull/768)

---

### ⚡ Added `CompletionStage` Repository Return Support

**JNoSQL — PR #764 • Merged**

Worked on support for asynchronous repository methods returning `CompletionStage` types.

**What I contributed:**

- `CompletionStage<T>`
- `CompletionStage<List<T>>`
- `CompletionStage<Optional<T>>`
- `CompletionStage<Page<T>>`
- Regression coverage for asynchronous repository return types.
- Kept the asynchronous capability change separate from the class-loader fix.

🔗 [Merged PR #764](https://github.com/eclipse-jnosql/jnosql/pull/764)

---

### 🔍 Investigated Common Class-Loader and `ServiceLoader` Handling

**JNoSQL — Issue #766 • PR #769**

After investigating repeated class-loader and `ServiceLoader` handling patterns, I worked on extracting common provider-loading behavior into reusable infrastructure.

**What I contributed:**

- Investigated repeated `ServiceLoader` lookup patterns.
- Designed reusable provider-discovery behavior.
- Added tests covering provider loading.
- Migrated affected consumers.
- Preserved class-loader fallback behavior.
- Kept the reusable utility separate from the targeted `ConstructorBuilder` bug fix.

🔗 [Issue #766](https://github.com/eclipse-jnosql/jnosql/issues/766) • [PR #769](https://github.com/eclipse-jnosql/jnosql/pull/769)

---

### 📝 Updated JNoSQL License Headers

**JNoSQL — PR #770 • Merged**

Contributed a project-wide license-header update to align source files with the project's current licensing requirements.

**What I contributed:**

- Updated affected source-file license headers.
- Applied the required Eclipse Public License 2.0 / Apache License 2.0 notices.
- Preserved the project's existing licensing structure.
- Validated the changes with compliance checks.

🔗 [Merged PR #770](https://github.com/eclipse-jnosql/jnosql/pull/770)

---

# 🤖 Jakarta Agentic AI

Contributing to the **Jakarta Agentic AI** project through practical improvements to example applications and domain models.

### 💰 Added JSR 354 `MonetaryAmount` to `BankTransaction`

**Jakarta Agentic AI — Issue #11 / PR #59 • Merged**

Updated the fraud-detection example's `BankTransaction` model to represent monetary values using **JSR 354 `MonetaryAmount`**, making the example closer to a realistic financial domain model.

**What I contributed:**

- Replaced the simplistic monetary representation with JSR 354 `MonetaryAmount`.
- Added the required Money API dependency.
- Updated the transaction domain model.
- Added getters and setters.
- Verified the implementation with Maven tests.

🔗 [Issue #11](https://github.com/jakartaee/agentic-ai/issues/11) • [Merged PR #59](https://github.com/jakartaee/agentic-ai/pull/59)

---

# 🔍 Spring Lens

### 📊 Implemented `BeanDefinitionSummary`

**Spring Lens — Issue #269 / PR #270 • Merged**

Implemented an immutable domain model for aggregating Spring bean-definition metrics.

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
BeanDefinitionSummaryTest:
5 tests passed
```

🔗 [Issue #269](https://github.com/sdlc-pro/spring-lens/issues/269) • [Merged PR #270](https://github.com/sdlc-pro/spring-lens/pull/270)

---

# 🏆 Open Source Impact

| Contribution | Project | Focus | Status |
|---|---|---|---|
| **FinSim** (Simulator) | **FinSim** | Financial network simulator, payment state machines, fault injection | **Creator & Lead** |
| Transaction lifecycle fix | JNoSQL Extensions | `Page.totalElements()` outside transactions | [PR #209](https://github.com/eclipse-jnosql/jnosql-extensions/pull/209) • **Merged** |
| Regression coverage | JNoSQL Extensions | Jakarta Persistence refactoring port | [PR #210](https://github.com/eclipse-jnosql/jnosql-extensions/pull/210) • **Merged** |
| Class-loader fix | JNoSQL | `ServiceLoader` / TCCL discovery in Quarkus | [PR #765](https://github.com/eclipse-jnosql/jnosql/pull/765) • **Merged** |
| Main branch fix | JNoSQL | `ServiceLoader` / TCCL Jakarta EE 12 port | [PR #768](https://github.com/eclipse-jnosql/jnosql/pull/768) • **Merged** |
| Async repository support | JNoSQL | `CompletionStage` repository return types | [PR #764](https://github.com/eclipse-jnosql/jnosql/pull/764) • **Merged** |
| Service discovery utility | JNoSQL | Reusable provider discovery infrastructure | [PR #769](https://github.com/eclipse-jnosql/jnosql/pull/769) • Open |
| Jakarta Data TCK | Jakarta Data | Async exceptional completion | [PR #1556](https://github.com/jakartaee/data/pull/1556) • **Merged** |
| Jakarta Data TCK | Jakarta Data | `QueryOptions` / `JakartaQuery` flush semantics | [PR #1561](https://github.com/jakartaee/data/pull/1561) • **Merged** |
| Jakarta Data TCK | Jakarta Data | `Find` / `Query` / `Delete` / `NativeQuery` | [PR #1567](https://github.com/jakartaee/data/pull/1567) • Open |
| Domain modeling | Jakarta Agentic AI | JSR 354 `MonetaryAmount` in `BankTransaction` | [PR #59](https://github.com/jakartaee/agentic-ai/pull/59) • **Merged** |
| Domain modeling | Spring Lens | Immutable `BeanDefinitionSummary` record | [PR #270](https://github.com/sdlc-pro/spring-lens/pull/270) • **Merged** |
| License maintenance | JNoSQL | Project-wide EPL/Apache notices | [PR #770](https://github.com/eclipse-jnosql/jnosql/pull/770) • **Merged** |

---

# 💡 What Open Source Has Taught Me

Open source has fundamentally changed the way I approach software engineering.

It has pushed me beyond simply writing code that works. I have learned to investigate unfamiliar codebases, reproduce difficult distributed failures, trace framework lifecycles, understand class loaders and thread context switches, navigate Java platform internals, write portable regression and TCK test suites, collaborate across timezones with maintainers, and build robust public software.

The most valuable lesson has been simple:

> **Confidence does not always precede difficult work. True confidence is forged by taking on the difficult architectural problems you initially felt unready for.**

Every issue investigated, reproducer built, failed hypothesis, regression test, review, reusable utility, and merged pull request has made me a better engineer.

---

# 🛠️ Technical Skills

### Backend & Distributed Systems Engineering

**Java 21 • Spring Boot 3 • Spring Modulith • Spring Security • Distributed Networks • Microservices • REST APIs**

- Distributed payment orchestration & finite state machines (with `UNKNOWN` recovery)
- Idempotency guarantees & forward-first reconciliation
- Modular monolith architecture with Spring Modulith & ArchUnit
- RESTful API design & OpenAPI 3.1 contract specification
- Concurrency, thread context class loaders (TCCL), and `ServiceLoader` internals
- Microservices communication, failure handling & circuit breaking
- AI-powered backend applications with Spring AI

### Jakarta & Enterprise Java

**Jakarta EE • Jakarta Data • Jakarta Persistence • Jakarta NoSQL • Eclipse JNoSQL • JSR 354 Money**

- Enterprise Java APIs & TCK development
- High-integrity transaction management & flush mode semantics
- Service provider discovery & modular class loading
- Asynchronous repository abstractions (`CompletionStage`)
- Portable persistence semantics across runtimes (Open Liberty, Quarkus)

### Frontend & Web Engineering

**Next.js 16 • React 19 • TypeScript • Angular • Tailwind CSS**

- Server-side rendering (SSR), Static Site Generation (SSG) & Turbopack
- Type-safe domain models & strict component architecture
- High-density analytical dashboards & civic technology portals
- WCAG AA accessibility, responsive design & dark mode theming

### Cloud, Database & DevOps

**PostgreSQL 17 • Flyway • Testcontainers • Docker • Kubernetes • AWS • Terraform**

- Relational database schema design, migrations & optimistic locking
- Strict PostgreSQL parity testing via Testcontainers (no H2 fallbacks)
- Containerization & multi-stage Docker builds
- Infrastructure as Code (Terraform) on AWS
- Automated CI/CD pipelines (GitHub Actions, Spotless formatting, DCO enforcement)

---

# 💻 Technology Stack

### Backend & Distributed Systems

![Java](https://img.shields.io/badge/Java-21-ED8B00?style=flat-square&logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring_Boot-3-6DB33F?style=flat-square&logo=spring-boot&logoColor=white)
![Spring Modulith](https://img.shields.io/badge/Spring_Modulith-6DB33F?style=flat-square)
![Spring Security](https://img.shields.io/badge/Spring_Security-6DB33F?style=flat-square&logo=spring-security&logoColor=white)
![Microservices](https://img.shields.io/badge/Microservices-FF6B6B?style=flat-square)

### Jakarta & Enterprise Java

![Jakarta EE](https://img.shields.io/badge/Jakarta_EE-007396?style=flat-square&logo=eclipse&logoColor=white)
![Jakarta Data](https://img.shields.io/badge/Jakarta_Data-007396?style=flat-square&logo=eclipse&logoColor=white)
![Jakarta NoSQL](https://img.shields.io/badge/Jakarta_NoSQL-007396?style=flat-square&logo=eclipse&logoColor=white)
![Eclipse JNoSQL](https://img.shields.io/badge/Eclipse_JNoSQL-2C2255?style=flat-square&logo=eclipse&logoColor=white)

### Frontend

![Next.js](https://img.shields.io/badge/Next.js-16-000000?style=flat-square&logo=next.js&logoColor=white)
![React](https://img.shields.io/badge/React-19-20232A?style=flat-square&logo=react&logoColor=61DAFB)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=flat-square&logo=tailwind-css&logoColor=white)
![Angular](https://img.shields.io/badge/Angular-DD0031?style=flat-square&logo=angular&logoColor=white)

### Cloud, Database & DevOps

![PostgreSQL](https://img.shields.io/badge/PostgreSQL-17-316192?style=flat-square&logo=postgresql&logoColor=white)
![Flyway](https://img.shields.io/badge/Flyway-CC0202?style=flat-square&logo=flyway&logoColor=white)
![Testcontainers](https://img.shields.io/badge/Testcontainers-171717?style=flat-square&logo=docker&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=flat-square&logo=kubernetes&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-232F3E?style=flat-square&logo=amazon-aws&logoColor=FF9900)
![Terraform](https://img.shields.io/badge/Terraform-7B42BC?style=flat-square&logo=terraform&logoColor=white)

---

# 📈 GitHub Analytics

<div align="center">

<img src="https://github-readme-stats.vercel.app/api?username=mhnuk2007&show_icons=true&theme=react&bg_color=0D1117&title_color=6366F1&hide_border=true" alt="GitHub Stats" />

<img src="https://streak-stats.demolab.com/?user=mhnuk2007&theme=react&background=0D1117&ring=6366F1&fire=6366F1&currStreakLabel=6366F1&hide_border=true" alt="GitHub Streak Stats" />

</div>

---

# 🤝 Why Work With Me

- 🧩 **Root-Cause Problem Solver** — I investigate, reproduce, isolate, and resolve deep architectural bugs.
- ☕ **Java & Spring Boot Specialist** — Deep expertise in Java 21, Spring Boot 3, and high-assurance architecture.
- 💳 **Financial & Systems Engineering** — Proven track record building idempotent, state-machine-driven financial simulators.
- 🌐 **Open Source Provenance** — Active committer and contributor across official Jakarta EE, Eclipse JNoSQL, and Spring libraries.
- 🧪 **Testing & Verification Discipline** — Experienced in TCK development, regression test suites, property testing, and ArchUnit rules.
- ⚡ **Continuous Learner** — Persistent, self-directed, and constantly pushing into complex domains.

---

<div align="center">

# 📬 Connect With Me

**Mohan Lal • `mhnuk2007`**

[![Portfolio](https://img.shields.io/badge/Portfolio-Visit_My_Work-6366F1?style=for-the-badge&logo=google-chrome&logoColor=white)](https://mhnuk2007.tech/)
[![GitHub](https://img.shields.io/badge/GitHub-mhnuk2007-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/mhnuk2007)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Let's_Connect-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/mhnuk2007/)
[![LeetCode](https://img.shields.io/badge/LeetCode-Profile-FFA116?style=for-the-badge&logo=leetcode&logoColor=white)](https://leetcode.com/u/mhnuk2007/)

<br>

### 🌱 The Journey

**Self-taught. Curious. Persistent. Always learning.**

*Confidence is built by doing the difficult work you initially think you are not ready for.*

**Still learning. Still building. Still contributing. 🚀**

<br>

<sub>☕ Crafted with code & dedication • Last updated: November 2026</sub>

</div>

<!-- FOOTER WAVE -->

<img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=6,12,20&height=120&section=footer" />
