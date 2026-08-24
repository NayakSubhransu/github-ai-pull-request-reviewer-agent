# Github AI PR Reviewer Agent

A hands-on project where I am learning how to build an automated GitHub Pull Request reviewer using AI and an event-driven backend. 

> **Status: Currently Learning & Building From Scartch**  
> I am building this project step-by-step to understand how microservices communicate, how background queues handle tasks, and how LLMs can analyze code diffs.

---

## Why I'm Building This ? The Problem being Solved .

Reviewing code manually can be slow, especially for catching small bugs, syntax issues, or style violations. My goal with this project is to learn:
* How GitHub webhooks send real-time events to a backend server.
* How to use Redis and background workers to process heavy tasks without blocking requests.
* How to prompt LLMs effectively to review code diffs and post comments back to GitHub.
* How to deploy multiple backend services using Docker and Kubernetes.

---

## 💡 How It Works (Step-by-Step)

1. **PR Created:** A developer opens or updates a Pull Request on GitHub.
2. **Webhook Received:** The backend verifies the event and accepts the payload.
3. **Task Queued:** The task is pushed to a Redis queue so workers can pick it up asynchronously.
4. **AI Review:** The reviewer service pulls the code changes (diff), analyzes them using an LLM, and formats feedback.
5. **Feedback Posted:** The system posts review comments directly on the GitHub PR.

---

## Tech Stack I'm Using

* **Language & Backend:** Python, FastAPI
* **AI & Workflow:** LangGraph, OpenAI API
* **Queue & Cache:** Redis, Celery
* **Database:** PostgreSQL (with Alembic for migrations)
* **DevOps & Containers:** Docker, Kubernetes, Terraform

## 🎯 What I'm Learning & Implementing 
* [ ] Designing decoupled event-driven microservices using **FastAPI** and **Celery**. 
* [ ] Architecting multi-step agentic graph workflows with **LangGraph** for large diff chunking. 
* [ ] Managing database schema migrations using **Alembic** and **PostgreSQL**. 
* [ ] Implementing continuous feedback loops where reviewer memory adapts to repository-specific rules. 
* [ ] Provisioning cloud infrastructure with **Terraform** and scaling workloads using Kubernetes **HPA**. 
* [ ] Setting up **Prometheus & Grafana** pipelines to monitor worker queue depth and inference latencies. 

---

## 📂 Project Structure Overview

```text
├── services/
│   ├── gateway/       # Main API entry point
│   ├── webhook/       # Listens for GitHub PR events
│   ├── orchestrator/  # Manages the review flow
│   ├── reviewer/      # AI engine analyzing code diffs
│   └── learner/       # Learns repository coding rules over time
├── db/                # Database models and Alembic migrations
├── infra/             # Docker, K8s, and Terraform configs
└── scripts/           # Testing and evaluation scripts

