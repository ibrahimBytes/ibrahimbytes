# Ibrahim Shaik

### Computer Science Graduate | Software Engineering | Java & Backend Development

I am a Computer Science graduate interested in **software engineering, backend systems, Java/JVM internals, databases, and problem solving**.

I learn by going beyond simply using a technology. I try to understand:

- What problem are we solving?
- What are the actual requirements and constraints?
- What is happening underneath the abstraction?
- Why does a particular design work?
- What are the trade-offs?
- How can I test whether the solution is actually correct?

I am currently focused on strengthening my fundamentals through **Java, DSA, SQL, backend development, system design, and OpenJDK source-code investigation**.

---

## Engineering Philosophy

> **Understand the problem first. Then understand the system. Then build the simplest solution that satisfies the requirements.**

I don't want to learn technologies only as a list of tools.

I want to understand the relationship between:


Problem
   ↓
Requirements
   ↓
Constraints
   ↓
Fundamental principles
   ↓
Design
   ↓
Implementation
   ↓
Testing
   ↓
Measurement
   ↓
Iteration
````

My goal is to become better at turning this process into actual working software.

I also try to be explicit about what I **know, what I have implemented, what I am investigating, and what I am still learning**.

---

## What I'm Focused On

### Java & Backend Engineering

Currently developing stronger foundations in:

* Core Java
* Object-Oriented Programming
* Java Collections
* Generics
* Exception handling
* JDBC
* Spring Boot
* REST APIs
* Authentication and authorisation
* SQL and relational databases
* PostgreSQL
* Redis
* Kafka
* Backend architecture
* Testing and debugging

### Computer Science Fundamentals

I am continuously working on:

* Data Structures & Algorithms
* Database Management Systems
* Operating Systems
* Computer Networks
* Object-Oriented Design
* Concurrency fundamentals
* System design
* Performance and reliability

### JVM / OpenJDK

I am learning how Java works beyond the application layer by exploring the OpenJDK codebase.

My current work involves:

* Navigating the JDK source code
* Understanding existing Java APIs and implementations
* Investigating real issues
* Reading existing tests
* Working with JTReg
* Understanding regression-test design
* Investigating behaviour before proposing changes
* Learning the OpenJDK contribution workflow

I am currently in the **investigation and learning stage** rather than claiming an accepted or merged OpenJDK contribution.

---

# Featured Project

## Trimly — URL Shortening & Link Analytics Platform

**Trimly** is a production-oriented URL shortening and link analytics project that I built to understand backend engineering beyond individual CRUD endpoints.

The basic problem is simple:

> Given a long URL, create a short identifier that can redirect a user to the original destination.

I used the project to explore the engineering problems that appear when a simple feature becomes a complete system.

### Core Features

* URL shortening
* Custom aliases
* URL ownership
* URL expiration
* Authentication
* JWT-based authorisation
* Two-factor authentication
* Google authentication
* Rate limiting
* Redis caching
* Click analytics
* Asynchronous analytics processing
* REST APIs
* Database indexing
* Ownership isolation

### Technology

* **Java**
* **Spring Boot**
* **Spring Security**
* **PostgreSQL**
* **Redis**
* **Apache Kafka / Spring Kafka**
* **JWT**
* **BCrypt**
* **Bucket4j**
* **Flyway**
* **Maven**
* **Docker**
* **React**
* **TypeScript**
* **Vite**
* **Tailwind CSS**

### Architecture

The redirect path is designed around fast URL resolution:

```text
Browser
   ↓
Cloudflare Worker
   ↓
Spring Boot
   ↓
Redis
   ↓
PostgreSQL fallback
   ↓
302 Redirect
```

The analytics path is separated from the redirect responsibility:

```text
User Click
    ↓
Redirect Service
    ↓
Click Event
    ↓
Kafka
    ↓
Kafka Consumer
    ↓
PostgreSQL
    ↓
Analytics API
    ↓
React Dashboard
```

### Engineering Decisions

#### Redis

The fundamental problem is repeated database lookups for frequently accessed short URLs.

Redis is used as a cache for URL mappings so that frequently accessed redirects can avoid unnecessary PostgreSQL queries.

The trade-off is that caching introduces **consistency and invalidation concerns**, so PostgreSQL remains the persistent source of truth.

#### Kafka

Redirecting a user and processing analytics have different requirements.

The redirect path is latency-sensitive, while analytics can be processed separately.

Kafka provides an event-streaming boundary between these responsibilities:

```text
Redirect Path
     |
     +----> Click Event
                 |
                 v
               Kafka
                 |
                 v
          Analytics Consumer
                 |
                 v
             PostgreSQL
```

This introduces additional distributed-system complexity, but it separates the user-facing redirect path from analytics processing.

#### Database Design

I use PostgreSQL for persistent application data and design the schema around:

* Ownership
* URL mappings
* Click events
* Relationships
* Constraints
* Indexes
* Query patterns

I also use indexes based on the access patterns rather than adding indexes without understanding their purpose.

### Performance Investigation

I have measured the deployed redirect path rather than assuming that the system is fast.

The measurements I obtained included approximately:

* Backend TTFB: **~0.345 s**
* Redirect minimum: **~0.836 s**
* Redirect mean: **~1.086 s**
* Redirect p50: **~1.143 s**
* Redirect p95: **~1.324 s**
* Redirect p99: **~1.371 s**

These measurements are observations from my current deployment, not claims of universal production performance.

### What Trimly Taught Me

The most valuable part of the project has not been the technology list.

It has been learning to reason about:

* Critical paths
* Caching
* Data ownership
* Database access
* Asynchronous processing
* Failure modes
* Security boundaries
* Performance measurement
* Deployment problems
* Trade-offs between simplicity and scalability

---

# OpenJDK Investigation

I am also exploring the OpenJDK codebase as a way to learn Java at a deeper level.

Rather than beginning with a toy project, I want to understand how a large, mature software project is actually developed.

My current exploration includes:

```text
OpenJDK source
      ↓
Understand existing implementation
      ↓
Understand expected behaviour
      ↓
Read relevant tests
      ↓
Investigate the issue
      ↓
Form a hypothesis
      ↓
Test the hypothesis
      ↓
Understand the regression implications
      ↓
Prepare for a potential contribution
```

I am particularly interested in learning through:

* JDK Java code
* Core Java APIs
* Regression tests
* JTReg
* Existing bug fixes
* Code review conventions
* Eventually, HotSpot and JVM internals

I do **not** currently claim that I have an accepted or merged OpenJDK contribution.

The goal is to earn that contribution by first understanding the codebase and the engineering process properly.

---

# Software Engineering Experience

## Software Engineer Intern — Sattva Infotech

During my software engineering internship, I gained practical exposure to:

* Java
* Spring Boot
* MySQL
* SQL
* REST APIs
* Backend development
* Relational data models
* CRUD operations
* Role-based application flows
* Debugging
* JavaScript
* Frontend development
* Filtering and UI functionality
* Forms and validation
* Local Storage

My experience was not limited to writing code.

I also learned how individual components connect:

```text
Frontend
   ↓
HTTP Request
   ↓
REST API
   ↓
Controller
   ↓
Business Logic
   ↓
Database
   ↓
HTTP Response
   ↓
Frontend
```

This experience helped me understand why software engineering requires more than knowledge of an individual programming language.

---

# Current Learning Direction

My current priority is **depth rather than collecting technologies**.

### Java

```text
Core Java
   ↓
OOP
   ↓
Collections
   ↓
Generics
   ↓
Exceptions
   ↓
JDBC
   ↓
Spring Boot
   ↓
Backend Engineering
```

### Problem Solving

I am actively working on:

* Arrays
* Strings
* Hashing
* Two pointers
* Sliding window
* Prefix sums
* Binary search
* Sorting
* Stack / Queue / Deque
* Linked lists
* Trees
* BST
* Heaps
* Graphs
* BFS / DFS
* Topological sorting
* Union-Find
* Greedy algorithms
* Dynamic programming
* Backtracking

My goal is not merely to recognise a solution.

I am working towards being able to:

```text
Understand
   ↓
Attempt independently
   ↓
Find the bottleneck
   ↓
Develop an approach
   ↓
Prove / reason about it
   ↓
Implement
   ↓
Test
   ↓
Analyse complexity
   ↓
Generalise
```

---

# How I Learn

I prefer first-principles learning.

When I encounter a problem, I try to work through:

1. What is actually happening?
2. What problem are we trying to solve?
3. Who or what is affected?
4. What are the requirements?
5. What are the constraints?
6. What assumptions are we making?
7. What is the simplest possible solution?
8. Where is the bottleneck?
9. What are the trade-offs?
10. How can we test the result?

The objective is not to memorise more information.

It is to develop the ability to **reason independently**.

---

# Technology

### Languages

* Java
* SQL
* JavaScript
* TypeScript

### Backend

* Spring Boot
* Spring Security
* REST APIs
* JDBC
* Hibernate
* JWT
* BCrypt

### Databases & Data

* PostgreSQL
* MySQL
* Redis
* Apache Kafka

### Frontend

* React
* TypeScript
* Vite
* Tailwind CSS
* HTML
* CSS
* JavaScript

### Engineering Tools

* Git
* GitHub
* Maven
* Docker
* Docker Compose
* Flyway

### Currently Exploring

* OpenJDK
* JVM internals
* JTReg
* Java source-code implementation
* Backend performance
* Distributed-system fundamentals
* System design

---

# Engineering Principles

### 1. Start with the problem

Technology should serve a requirement.

### 2. Understand before optimising

Do not optimise a system before understanding its actual bottleneck.

### 3. Prefer simple designs

Complexity should have a reason.

### 4. Measure instead of assuming

Performance, reliability, and correctness should be validated against evidence.

### 5. Understand trade-offs

Every design decision solves some problems while introducing others.

### 6. Be honest about limitations

I would rather say:

> "I haven't implemented that yet."

than claim experience I don't have.

### 7. Learn from failures

A bug, failed experiment, deployment problem, or incorrect assumption is useful if I understand why it happened and what changed afterwards.

---

# What I'm Working Towards

I am building towards becoming a stronger software engineer by developing depth across:

```text
Computer Science
      ↓
Programming
      ↓
Data Structures & Algorithms
      ↓
Backend Engineering
      ↓
Databases
      ↓
Operating Systems
      ↓
Networking
      ↓
Distributed Systems
      ↓
Performance & Reliability
      ↓
System Design
```

Long term, I want to use engineering and technology as tools for solving **meaningful problems**.

For now, my priority is simple:

> **Become capable of independently understanding, building, debugging, and improving real software systems.**

---

# GitHub

I use this GitHub profile as a record of my learning and engineering work.

I want the repositories here to show not only the final code, but also the reasoning behind the work:

* What problem was being solved
* Why a particular design was chosen
* What alternatives were considered
* What failed
* How it was debugged
* What was measured
* What remains incomplete
* What I learned

---

# Connect

* [LinkedIn](https://www.linkedin.com/in/ibrahim-shaik-1baa8a341/)
* [Bluesky](https://bsky.app/profile/s-ibrahim-dev-bsky.social)
* [Instagram](https://instagram.com/ibrahim.kernal)
* [Email](mailto:s.ibrahim.devx@gmail.com)

---

> **Build. Measure. Understand. Improve.**

*Learning to build better systems, one problem at a time.*

```

### One important change I deliberately made

I **removed the "I build production-grade infrastructure / performance-critical tools" positioning**.

Not because your ambition is too high — but because a GitHub profile should distinguish:

**What you have actually done**
from
**What you are learning**
from
**What you eventually want to do.**

Your current profile becomes much more credible if someone from IBM, Google, a startup, or an open-source project reads it and can trace every major claim back to an actual repository, implementation, test, investigation, or experience.

The strongest positioning for you **right now** is not:

> “I am already a systems engineer.”

It is:

> **“I am a CS graduate developing depth in Java/backend engineering, learning through real systems, source-code investigation, debugging, measurement, and increasingly rigorous problem solving.”**

That is both ambitious and defensible. 
``` 
