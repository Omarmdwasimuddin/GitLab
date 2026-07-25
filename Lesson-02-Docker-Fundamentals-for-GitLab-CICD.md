# Lesson 02 — Docker Fundamentals for GitLab CI/CD

> Module: Foundation  
> Estimated Time: 3 Hours

# Learning Objectives

After this lesson you will:

- Understand why Docker is required for GitLab CI/CD.
- Explain Container vs Virtual Machine.
- Understand Images, Containers, Volumes, Networks.
- Understand Docker Compose.
- Be ready to install GitLab in Lesson 03.

---

# 1. Why Docker?

GitLab Self-Managed runs on Linux. If your host is Windows or macOS, Docker provides a Linux environment without creating a full virtual machine.

For CI/CD, Docker also gives every pipeline a clean, reproducible environment.

---

# 2. Virtual Machine vs Container

| Virtual Machine | Container |
|---|---|
| Includes full guest OS | Shares host kernel |
| Heavier | Lightweight |
| Slower startup | Starts in seconds |
| Larger storage | Smaller images |

Think of a VM as a full house and a container as a furnished apartment inside the same building.

---

# 3. Docker Architecture

```text
Developer
    │
Docker CLI
    │
Docker Engine
    │
 ├── Images
 ├── Containers
 ├── Networks
 └── Volumes
```

---

# 4. Image vs Container

**Image**
- Read-only template.
- Example: `node:22`, `postgres:17`.

**Container**
- A running instance of an image.

```text
Image
  │
docker run
  ▼
Container
```

---

# 5. Volumes

Containers are temporary.

Without a volume:

```text
Container Deleted
      │
      ▼
Data Lost
```

With a volume:

```text
Container
   │
Volume
   │
Persistent Data
```

GitLab stores repositories, configuration, and logs in persistent volumes.

---

# 6. Networks

Docker containers communicate over Docker networks.

Example:

```text
GitLab Container ───── GitLab Runner
          │
     PostgreSQL
```

---

# 7. Docker Compose

Docker Compose lets you define multiple containers in a single `compose.yaml` file.

Benefits:
- Version-controlled infrastructure
- One command to start services
- Easy recreation

---

# 8. Why Docker Executor?

A GitLab Runner using the Docker executor starts a fresh container for each job.

```text
Pipeline
   │
Runner
   │
Docker Executor
   │
node:22 container
   │
npm install
npm test
npm run build
```

This keeps jobs isolated and reproducible.

---

# Official Documentation

Primary references:

- https://docs.docker.com/get-started/
- https://docs.docker.com/engine/
- https://docs.gitlab.com/runner/executors/docker/

---

# Hands-on Lab

1. Install Docker Desktop (if not already installed).
2. Run:
```bash
docker --version
docker compose version
```
3. Open Docker Desktop and verify the engine is running.

No GitLab installation yet.

---

# Common Mistakes

- Confusing images with containers.
- Storing important data inside containers instead of volumes.
- Assuming Docker Compose is a replacement for Docker.

---

# Homework

- Explain Image vs Container.
- Explain Volume vs Container storage.
- Draw the Docker architecture from memory.

---

# Interview Questions

1. What is Docker?
2. Why use Docker in CI/CD?
3. Image vs Container?
4. What is a Docker Volume?
5. What is Docker Compose?
6. Why is Docker Executor popular in GitLab?

---

# Summary

Today you learned the Docker concepts required for GitLab CI/CD. In the next lesson we will install GitLab Community Edition locally using Docker Compose.
