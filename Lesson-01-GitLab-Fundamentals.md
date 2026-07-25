# Lesson 01 — GitLab Fundamentals

> **Module:** Foundation  
> **Estimated Time:** 2–3 Hours

---

# Learning Objectives

After this lesson you will be able to:

- Explain what GitLab is.
- Explain the difference between Git, GitHub, and GitLab.
- Understand CI and CD.
- Describe GitLab architecture.
- Identify the major GitLab components.

---

# Prerequisites

- Basic Git commands (`clone`, `commit`, `push`)
- Docker installed (we'll use it later)

---

# 1. What is GitLab?

GitLab is an **end-to-end DevSecOps platform**.

It provides:

- Git Repository
- Code Review (Merge Requests)
- Issue Tracking
- Wiki
- Package Registry
- Container Registry
- CI/CD Pipelines
- Runner
- Security Scanning

Think of GitLab as a complete software delivery platform rather than just a Git hosting service.

---

# 2. Git vs GitHub vs GitLab

| Tool | Purpose |
|------|---------|
| Git | Version Control System |
| GitHub | Cloud platform for Git repositories |
| GitLab | DevSecOps platform built around Git |

**Remember**

- Git = Tool
- GitHub = Platform
- GitLab = Platform + CI/CD + DevOps features

---

# 3. What is CI?

Continuous Integration means developers frequently merge code into a shared repository.

Typical flow:

```text
Developer
   │
Commit
   │
Push
   │
GitLab
   │
Pipeline
   │
Build
   │
Test
```

Benefits:

- Detect bugs early
- Reduce integration problems
- Keep main branch healthy

---

# 4. What is CD?

CD has two meanings:

## Continuous Delivery

Software is always ready for deployment.

## Continuous Deployment

Every successful pipeline deploys automatically.

---

# 5. Why GitLab CI/CD?

Without CI/CD

```text
Developer
↓

Push

↓

Manual Build

↓

Manual Test

↓

Manual Deploy
```

With GitLab CI/CD

```text
Developer
↓

Push

↓

Pipeline

↓

Build

↓

Test

↓

Deploy
```

Automation improves consistency and speed.

---

# 6. GitLab High-Level Architecture

```text
Developer
     │
 git push
     │
     ▼
 GitLab Server
     │
 Creates Pipeline
     │
     ▼
 GitLab Runner
     │
 Executes Jobs
     │
 Docker Container
```

Important:

- GitLab schedules jobs.
- Runner executes jobs.

---

# 7. Major Components

- GitLab Server
- Repository
- Pipeline
- Runner
- Registry
- Users
- Groups
- Projects

---

# Real-World Example

A developer pushes a Next.js change.

Pipeline automatically:

1. Install dependencies
2. Run ESLint
3. Run TypeScript checks
4. Generate Prisma Client
5. Build application

If any step fails, merge should not proceed until fixed.

---

# Official Documentation

Use these as the primary learning resources:

- https://docs.gitlab.com/
- https://docs.gitlab.com/ci/
- https://docs.gitlab.com/topics/autodevops/

---

# Hands-on Lab

No installation today.

Draw the architecture from memory and answer:

1. What is Git?
2. What is GitLab?
3. What is a Runner?
4. Difference between CI and CD?

---

# Common Mistakes

- Thinking Git and GitLab are the same.
- Thinking GitLab executes jobs itself.
- Assuming CI means deployment.

---

# Best Practices

- Learn concepts before commands.
- Read official documentation first.
- Understand the architecture before writing `.gitlab-ci.yml`.

---

# Homework

1. Explain Git, GitHub and GitLab in your own words.
2. Draw the GitLab architecture.
3. Explain CI vs CD without notes.

---

# Interview Questions

1. What is GitLab?
2. Difference between Git and GitLab?
3. What is Continuous Integration?
4. What is Continuous Delivery?
5. What is GitLab Runner?
6. Does GitLab execute jobs?

---

# Summary

Today you learned:

- GitLab overview
- Git vs GitHub vs GitLab
- CI/CD
- Architecture
- Components

## Next Lesson

**Lesson 02 — Docker Fundamentals for GitLab CI/CD**
