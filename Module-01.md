# Module 01 — GitLab কী, এবং কেন

## GitLab আসলে কী?

GitLab হলো একটা all-in-one DevOps platform। Jenkins শুধু CI/CD tool — Git hosting আলাদা (GitHub/GitLab/Bitbucket) লাগে, webhook দিয়ে connect করতে হয়। কিন্তু GitLab এর মধ্যে এক জায়গায় সব আছে:

- Git repository hosting (GitHub এর মতো)
- Issue tracking / project management (Jira এর মতো)
- CI/CD pipeline (Jenkins এর মতো, কিন্তু built-in)
- Container Registry (Docker images রাখার জায়গা)
- Kubernetes integration
- Security scanning (SAST, dependency scanning)

তাই GitLab মানে ধরে নাও: **GitHub + Jenkins + Docker Hub + Jira** — সব এক platform এ মিশে গেছে।

---

# GitLab vs GitHub vs Jenkins — পার্থক্যটা ক্লিয়ার করি

| জিনিস | GitHub | Jenkins | GitLab |
|--------|---------|----------|---------|
| Git hosting | ✅ Native | ❌ (লাগেই না, শুধু connect করে) | ✅ Native |
| CI/CD | GitHub Actions (আলাদা feature) | ✅ এটাই মূল কাজ | ✅ Built-in (GitLab CI/CD) |
| Config file | `.github/workflows/*.yml` | `Jenkinsfile` | `.gitlab-ci.yml` |
| Runner/Agent | GitHub-hosted runners | Jenkins agents (তুমি নিজে setup করো) | GitLab Runners (নিজে setup করো বা shared) |
| Setup complexity | কম | তুলনামূলক বেশি (তুমি experience করেছ) | মাঝামাঝি |

তোমার জন্য বড় সুবিধা: **Jenkinsfile** এ যেভাবে stages/steps লিখতে শিখেছ, GitLab এর **`.gitlab-ci.yml`** এও প্রায় same logic — শুধু syntax YAML-based এবং structure একটু আলাদা।

---

# SaaS vs Self-hosted — কোনটা দিয়ে শিখবে

দুইভাবে GitLab ব্যবহার করা যায়:

### GitLab.com (SaaS)

সরাসরি **gitlab.com** এ account খুলে ব্যবহার করা, install করা লাগে না। 

### Self-hosted GitLab (GitLab CE - Community Edition)

নিজের machine/server এ Docker দিয়ে install করে চালানো। এটা exactly Jenkins এর মতো experience দেবে — নিজে server manage করা, production-realistic।
