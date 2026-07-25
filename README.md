## GitLab CI/CD Learning Roadmap

> Goal: Become a **Job-ready GitLab CI/CD Developer** by learning concepts, architecture, and hands-on implementation.

## Module 1 — Foundation (Lessons 1–5)

**Goal:** Understand GitLab, CI/CD, and architecture.

### Lesson 1
- GitLab কী?
- Git vs GitHub vs GitLab
- CI/CD কী?
- GitLab Architecture
- GitLab Components

### Lesson 2
- Docker Basics
- Container vs VM
- Docker Network
- Docker Volume
- Docker Compose

### Lesson 3
- Local GitLab CE Installation
- GitLab Container
- Volumes
- Ports
- Initial Login

### Lesson 4
- GitLab UI Tour
- Groups
- Projects
- Users
- Access Tokens

### Lesson 5
- GitLab Runner
- Runner কী?
- Runner Architecture
- Shell Executor
- Docker Executor

---

## Module 2 — Basic CI/CD (Lessons 6–10)

**Goal:** Write your first pipeline.

### Lesson 6
- `.gitlab-ci.yml`
- Job
- Stage
- Script

### Lesson 7
- Variables
- Environment Variables
- Secrets

### Lesson 8
- Rules
- only
- except
- when

### Lesson 9
- Cache
- Artifacts

### Lesson 10
- Pipeline Debugging

---

## Module 3 — Intermediate Pipeline (Lessons 11–15)

### Lesson 11
- needs
- dependencies

### Lesson 12
- Parallel Jobs

### Lesson 13
- Child Pipeline

### Lesson 14
- Parent Pipeline

### Lesson 15
- Include
- Template

---

## Module 4 — Docker CI (Lessons 16–18)

### Lesson 16
- Docker Executor

### Lesson 17
- Docker Image Build

### Lesson 18
- Container Registry

---

## Module 5 — Next.js Production Pipeline (Lessons 19–22)

We will use your own **Next.js project**.

```text
Install
  ↓
Lint
  ↓
Type Check
  ↓
Prisma Generate
  ↓
Build
  ↓
Test
  ↓
Artifact
  ↓
Docker Image Build
```

---

## Module 6 — Advanced GitLab (Lessons 23–26)

- Environments
- Review Apps
- Deployments
- Merge Request Pipelines

---

## Module 7 — Production (Lessons 27–29)

- Protected Branch
- Protected Variables
- Secrets
- Tags
- Manual Approval
- Rollback
- Release Pipeline

---

## Module 8 — Final Project (Lesson 30)

Enterprise-level CI/CD project.

```text
Developer
   ↓
Push
   ↓
GitLab
   ↓
Runner
   ↓
Install
   ↓
Test
   ↓
Build
   ↓
Docker Build
   ↓
Container Registry
   ↓
Deploy
```

---

# Standard Lesson Structure

Every lesson will include:

1. Concept
2. Architecture Diagram (ASCII)
3. Official GitLab Documentation
4. Hands-on Lab
5. Homework
6. Interview Questions
7. Common Mistakes
8. Production Tips

---

# Skills You Will Gain

- Self-managed GitLab installation
- GitLab Runner configuration
- Docker Executor
- Professional `.gitlab-ci.yml`
- Next.js CI/CD pipelines
- Cache, Artifacts, Rules, Variables
- Docker image build & registry
- Production deployment concepts
- Interview preparation
- Real-world GitLab CI/CD workflow

---

# Learning Rules

- Understand **what** a feature is.
- Learn **why** it exists.
- Practice **how** it works.
- Always verify behavior using the **official GitLab documentation** before relying on third-party sources.

