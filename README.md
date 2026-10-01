# 🤖 Multi-Agent AI Platform

> A full-stack **Multi-Agent AI Platform** built with the MERN stack, LangChain, LangGraph, RAG, Qdrant, Redis, and AWS S3 — featuring specialized AI agents, document intelligence, code generation, artifact previews, AI memory, real-time streaming, and microservices-based backend architecture.

---

## 📸 Platform Preview

![Screenshot 1](./project_images/Screenshot%202026-09-30%202.png)

![Screenshot 2](./project_images/Screenshot%202026-09-30%20234tyrghfh.png)

![Screenshot 3](./project_images/Screenshot%202026-09-30%20233903.png)

![Screenshot 4](./project_images/Screenshot%202026-09-30%20234155.png)

![Screenshot 5](./project_images/Screenshot%202026-09-30%20234429.png)

![Screenshot 6](./project_images/Screenshot%202026-09-30%20234502.png)

![Screenshot 7](./project_images/Screenshot%202026-09-30%20234538.png)

![Screenshot 8](./project_images/Screenshot%202026-09-30%20234737.png)

![Screenshot 9](./project_images/Screenshot%202026-09-30%20234853.png)

![Screenshot 10](./project_images/Screenshot%202026-09-30%20234853jhjhgg.png)

![Screenshot 11](./project_images/Screenshot%202026-09-30%20235108.png)

![Screenshot 12](./project_images/Screenshot%202026-09-30%20235257.png)

![Screenshot 13](./project_images/Screenshot%202026-09-30%20235345.png)

![Screenshot 14](./project_images/Screenshot%202026-09-30%20235345hjggj.png)

![Screenshot 15](./project_images/Screenshot%202026-09-30%20235503.png)

![Screenshot 16](./project_images/Screenshot%202026-09-30%20235503hjg.png)

![Screenshot 17](./project_images/Screenshot%202026-09-mhbbh.png)

> **Note:** Screenshots are included to demonstrate the platform UI and implemented functionality. API keys, credentials, and other sensitive configuration values are intentionally excluded from the repository.

> **Note:** Screenshots are included to demonstrate the platform UI and implemented functionality. API keys, credentials, and other sensitive configuration values are intentionally excluded from the repository.

---

# 🚀 Overview

The **Multi-Agent AI Platform** is a full-stack AI application designed around a **microservices architecture** and an **agentic AI workflow**.

Instead of relying on a single general-purpose chatbot, the platform uses specialized agents that can handle different types of tasks such as:

* 💬 Conversational AI
* 🔎 Real-time web search
* 💻 Code generation
* 👁️ Vision-based tasks
* 📄 PDF generation
* 📊 PowerPoint generation
* 📚 Document-based RAG
* 🧠 AI memory
* 🗂️ File and artifact management

The system combines **LangGraph-based agent orchestration** with **LangChain**, vector search, Redis memory, and cloud object storage to create a modular AI platform.

---

# ✨ Key Features

## 🧠 Multi-Agent AI

The platform uses specialized AI agents rather than handling every request through a single workflow.

### Agents implemented

| Agent            | Responsibility                                 |
| ---------------- | ---------------------------------------------- |
| 💬 Chat Agent    | General conversational tasks                   |
| 🔎 Search Agent  | Real-time web search and information retrieval |
| 💻 Coding Agent  | Code generation and artifact creation          |
| 👁️ Vision Agent | Image-based AI tasks                           |
| 📄 PDF Agent     | AI-generated PDF documents                     |
| 📊 PPT Agent     | AI-generated presentations                     |

Agents are orchestrated using **LangGraph**, allowing workflows to maintain state and route tasks between specialized components.

---

# 🔗 LangGraph Agentic Workflow

The AI workflow is designed around stateful agent execution.

```text
                    User Query
                        │
                        ▼
                ┌───────────────┐
                │  Agent Router │
                └───────┬───────┘
                        │
          ┌─────────────┼─────────────┐
          ▼             ▼             ▼
     Chat Agent    Search Agent   Coding Agent
          │             │             │
          │             ▼             ▼
          │        Web Search      Code Tools
          │
          ├──────────────┐
          ▼              ▼
     RAG Retrieval    AI Memory
          │              │
          └───────┬──────┘
                  ▼
             Final Response
                  │
                  ▼
          Streaming to Client
```

LangGraph manages the state and execution flow between the different AI components.

---

# 📚 Retrieval-Augmented Generation (RAG)

The platform supports document-based question answering using a RAG pipeline.

```text
        User Document
              │
              ▼
      Document Processing
              │
              ▼
           Chunking
              │
              ▼
          Embeddings
              │
              ▼
       ┌───────────────┐
       │    Qdrant     │
       │ Vector Store  │
       └───────┬───────┘
               │
               ▼
          User Query
               │
               ▼
          Similarity Search
               │
               ▼
        Relevant Context
               │
               ▼
             LLM
               │
               ▼
      Context-Aware Answer
```

### RAG capabilities

* Document ingestion
* Text processing
* Chunking
* Embedding generation
* Vector similarity search
* Context retrieval
* LLM-based response generation

**Qdrant** is used as the vector database for semantic retrieval.

---

# 🧠 AI Memory with Redis

Redis is used for maintaining conversational/session state and reducing unnecessary repeated processing.

```text
User
 │
 ▼
Chat Request
 │
 ▼
Backend
 │
 ├──────► Redis
 │          │
 │          └── Conversation / Session State
 │
 ▼
LangGraph Workflow
 │
 ▼
LLM
 │
 ▼
Streaming Response
```

This allows the platform to maintain context across interactions.

---

# 💻 Coding Agent & Artifact System

One of the core features of the platform is an AI-powered coding workflow.

The Coding Agent can:

* Generate code
* Modify files
* Work with multiple files
* Map generated files to an artifact structure
* Display generated code in the UI
* Preview generated applications using an iframe

```text
User Request
      │
      ▼
 Coding Agent
      │
      ▼
Generated Files
      │
      ▼
File Mapping
      │
      ▼
Artifact Panel
      │
      ▼
Live Preview
```

This turns the AI interaction from a simple text response into an **interactive development workspace**.

---

# 📄 AI Document Generation

The platform supports AI-generated documents through specialized agents.

### PDF Generation

```text
User Prompt
     ↓
PDF Agent
     ↓
AI Generated Content
     ↓
PDF Generation
     ↓
AWS S3
     ↓
Secure File Access
```

### PowerPoint Generation

The PPT Agent extends the same workflow to generate presentation files from AI-generated content.

---

# ☁️ AWS S3 File Storage

AWS S3 is used for storing user-generated and uploaded files such as:

* PDFs
* Images
* Documents
* Generated artifacts
* AI-generated files

The platform uses **pre-signed URLs** for controlled access to stored objects.

```text
Client
  │
  ▼
Backend
  │
  ▼
Generate Pre-Signed URL
  │
  ▼
AWS S3
  │
  ▼
Secure File Upload / Download
```

This avoids exposing storage credentials directly to the frontend.

---

# 🔐 Authentication & Authorization

Authentication is implemented using **Google OAuth through Firebase**.

The authentication flow is:

```text
User
 │
 ▼
Google OAuth
 │
 ▼
Firebase Authentication
 │
 ▼
Backend Authentication Layer
 │
 ▼
Session Management
 │
 ▼
Redis
```

The platform separates authentication concerns into a dedicated **Auth Service**.

---

# 💳 Billing & Credits

The platform includes a billing service using **Razorpay**.

The billing system supports:

* Payment order creation
* Credit-based usage
* Credit deduction
* Subscription/payment workflows

Billing functionality is isolated into its own microservice to keep payment-related logic separate from the core AI services.

---

# 🏗️ Microservices Architecture

The backend is divided into independent services.

```text
                         ┌─────────────────┐
                         │ React Frontend  │
                         └────────┬────────┘
                                  │
                                  ▼
                         ┌─────────────────┐
                         │  API Gateway    │
                         └────────┬────────┘
                                  │
            ┌─────────────────────┼─────────────────────┐
            │                     │                     │
            ▼                     ▼                     ▼
     ┌────────────┐        ┌────────────┐       ┌────────────┐
     │Auth Service│        │Chat Service│       │Agent Service│
     └──────┬─────┘        └──────┬─────┘       └──────┬─────┘
            │                     │                     │
            │                     │              ┌──────┴─────────┐
            │                     │              │                │
            │                     │              ▼                ▼
            │                     │         LangGraph         AI Agents
            │                     │
            │                     ▼
            │                  Redis
            │
            ▼
       Firebase Auth

                         ┌────────────────┐
                         │ Billing Service│
                         └───────┬────────┘
                                 │
                                 ▼
                              Razorpay
```

### Core services

* **API Gateway**
* **Authentication Service**
* **Chat Service**
* **Agent Service**
* **Billing Service**

This separation makes the backend easier to maintain and extend.

---

# 🧰 Tech Stack

## Frontend

* React.js
* Redux Toolkit
* Tailwind CSS
* Responsive UI
* Streaming AI responses
* Artifact interface
* iframe-based previews

## Backend

* Node.js
* Express.js
* REST APIs
* Microservices Architecture
* API Gateway

## AI / GenAI

* LangChain
* LangGraph
* RAG
* LLMs
* Embeddings
* AI Agents
* Tool Calling
* Streaming Responses
* AI Memory

## Databases & Storage

* MongoDB
* Redis
* Qdrant
* AWS S3

## Authentication & Payments

* Firebase Authentication
* Google OAuth
* Razorpay

## DevOps / Development

* Docker
* Git
* GitHub
* Environment-based configuration

---

# 📁 Project Structure

```text
multi-agent-ai-platform/
│
├── frontend/
│   ├── components/
│   ├── pages/
│   ├── redux/
│   ├── services/
│   └── ...
│
├── backend/
│   │
│   ├── gateway/
│   │
│   ├── auth-service/
│   │
│   ├── chat-service/
│   │
│   ├── agent-service/
│   │   ├── agents/
│   │   ├── workflows/
│   │   ├── tools/
│   │   └── ...
│   │
│   └── billing-service/
│
├── docker/
│
├── screenshots/
│
├── .env.example
├── .gitignore
└── README.md
```

> Directory names may vary depending on the final implementation.

---

# ⚙️ Local Setup

## 1. Clone the repository

```bash
git clone <your-repository-url>
cd multi-agent-ai-platform
```

## 2. Install dependencies

Install dependencies separately for the frontend and backend services.

```bash
npm install
```

Repeat for individual services if required.

---

## 3. Configure environment variables

Create `.env` files based on the provided `.env.example`.

Example:

```env
MONGODB_URI=
REDIS_URL=

QDRANT_URL=
QDRANT_API_KEY=

AWS_ACCESS_KEY_ID=
AWS_SECRET_ACCESS_KEY=
AWS_REGION=
AWS_S3_BUCKET=

FIREBASE_PROJECT_ID=
FIREBASE_CLIENT_EMAIL=
FIREBASE_PRIVATE_KEY=

RAZORPAY_KEY_ID=
RAZORPAY_KEY_SECRET=

LLM_API_KEY=
```

### ⚠️ Security

**Never commit real API keys, passwords, private keys, or cloud credentials.**

Only `.env.example` files containing placeholder values should be committed.

---

# 🐳 Docker

The backend services can be containerized using Docker.

Example:

```bash
docker build -t multi-agent-platform .
```

Run the required services according to their respective Docker configuration.

---

# 🖥️ Application Screens

The repository contains screenshots demonstrating the implemented platform.

Recommended screenshots:

```text
screenshots/
│
├── login.png
├── chat.png
├── search-agent.png
├── rag.png
├── artifacts.png
├── code-preview.png
├── pdf-agent.png
├── ppt-agent.png
└── billing.png
```

---

# 🔄 End-to-End Example

A typical document-based AI interaction works approximately like this:

```text
                Upload Document
                      │
                      ▼
                 AWS S3 Upload
                      │
                      ▼
              Document Processing
                      │
                      ▼
                  Chunking
                      │
                      ▼
                 Embeddings
                      │
                      ▼
                   Qdrant
                      │
                      ▼
                 User Query
                      │
                      ▼
              LangGraph Workflow
                      │
                      ▼
              Retrieval / Tools
                      │
                      ▼
                    LLM
                      │
                      ▼
             Streaming Response
                      │
                      ▼
                   React UI
```

---

# 🎯 Engineering Highlights

This project demonstrates practical implementation of:

* Microservices architecture
* Agentic AI workflows
* Stateful AI orchestration
* Retrieval-Augmented Generation
* Vector similarity search
* Conversational memory
* Tool-based AI execution
* Streaming LLM responses
* Secure cloud file storage
* OAuth authentication
* Payment and credit systems
* AI-generated artifacts
* Containerized backend services
* Modular REST API design

---

# 🔒 Security Considerations

This repository intentionally **does not contain production credentials**.

Sensitive configuration should be supplied through environment variables.

Examples include:

* LLM API keys
* Firebase private keys
* AWS credentials
* Qdrant API keys
* Razorpay secrets
* Database credentials

If a credential is accidentally exposed, it should be **revoked/rotated immediately** rather than simply deleted from the source file.

---

# 🚧 Deployment Status

The project is currently maintained as a **local development / portfolio project**.

Cloud deployment infrastructure such as:

* AWS ECS
* Amazon ECR
* Application Load Balancer
* CloudFront
* GitHub Actions CI/CD

is **not required for the current repository**.

The focus of this implementation is the application architecture, AI workflows, backend services, RAG pipeline, agent system, and frontend experience.

---

# 🔮 Future Improvements

Potential extensions include:

* [ ] Production AWS deployment
* [ ] Automated CI/CD pipeline
* [ ] Advanced agent routing
* [ ] Agent observability and tracing
* [ ] Evaluation framework for RAG responses
* [ ] LLM cost monitoring
* [ ] Rate limiting
* [ ] Automated testing
* [ ] Improved document parsing
* [ ] Persistent user-level knowledge bases
* [ ] Agent performance analytics

---

# 📌 Disclaimer

This project is intended for **learning, experimentation, and portfolio demonstration**.

Third-party services such as LLM providers, Firebase, AWS, Qdrant, and Razorpay require their own valid credentials and may incur usage-based costs according to their respective pricing policies.

---

# 👨‍💻 Author

**Asif Raza**

B.Tech Computer Engineering

GitHub: `github.com/asif-raza01`

---

⭐ If you find the architecture or implementation useful, consider starring the repository.
