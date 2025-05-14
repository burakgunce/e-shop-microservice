# 🛒 E-Shop Microservices

A comprehensive e-commerce platform built with microservices architecture using **.NET 8.0**, implementing modern architectural patterns and cutting-edge technologies.

---

## 🧭 Architecture Overview

### 🧱 Microservices

Each service is independently deployable and follows the principles of **domain-driven design** and **event-driven architecture**.

| Service | Description | Port(s) | Database | Communication |
|--------|-------------|---------|----------|----------------|
| **Catalog Service** | Manages product catalog | `5000/5050` | PostgreSQL + Marten | REST |
| **Basket Service** | Manages shopping cart | `5001/5051` | Redis + PostgreSQL + Marten | gRPC |
| **Discount Service** | Provides discounts | `5002/5052` | SQLite | gRPC |
| **Ordering Service** | Handles order placement | `5003/5053` | SQL Server | RabbitMQ |
| **API Gateway** | Central gateway for routing | `5004/5054` | - | YARP (Reverse Proxy) |

---

## 🧩 Architectural Patterns

### 🟪 Vertical Slice Architecture

- Feature-oriented design
- Each slice includes:
  - API Endpoints  
  - Business Logic  
  - Data Access  
  - Validation  
  - Authorization  
- Reduced coupling between features

### 🔁 SAGA Pattern

- Distributed transaction management  
- Choreography-based coordination  
- Compensating actions for rollbacks  
- Ensures consistency across services  

### 🧬 Microservices Architecture

- Independent deployment and scaling  
- Decentralized data management  
- Unified access via API Gateway (YARP)  
- Service discovery and health checks  

### 🧠 Domain-Driven Design (DDD)

- Bounded contexts per service  
- Aggregates, entities, value objects  
- Domain events for behavior modeling  

### 📡 Event-Driven Architecture

- Asynchronous communication using **RabbitMQ**  
- Event sourcing for historical state  
- Eventual consistency between services  

### ⚔️ CQRS (Command Query Responsibility Segregation)

- Separate models for reads and writes  
- Read/write optimization  
- Event sourcing powered by Marten  

### 🎯 Design Patterns

- **Repository Pattern** – Abstracts data access logic  
- **Decorator Pattern** – Adds caching to repositories  
- **Mediator Pattern** – MediatR-based in-process messaging  

---

## 🧰 Technology Stack & Libraries

### 🔗 Core Libraries

- **.NET 8.0** – Modern, high-performance backend framework  
- **ASP.NET Core** – Web API and gRPC services  
- **MediatR** (v12.x) – Request/response and pipeline behaviors  
- **MassTransit** (v8.x) – Messaging abstraction with RabbitMQ  
- **Carter** – Minimal API routing and OpenAPI integration  
- **Marten** – PostgreSQL document store with event sourcing  
- **Entity Framework Core** – Data access for Ordering service  

### 🔐 Security & Validation

- **FluentValidation** – Model validation  
- **Mapster** – Lightweight object-object mapper  
- **JWT** – Token-based authentication  
- **Rate Limiting** – API protection with YARP  

### 📈 Monitoring & Diagnostics

- **HealthChecks** – For SQL Server, Redis, RabbitMQ, etc.  
- **HealthChecks UI** – Visual health dashboards  
- **Serilog** (optional) – Structured logging (can be added)

### 🧪 Testing

- **xUnit** – Unit and integration testing  
- **Bogus** – Fake data generation for testing  

### ☁️ DevOps & Containerization

- **Docker** – Containerized services  
- **Docker Compose** – Multi-container orchestration  

---

## 🗃️ Databases

| Service | Database |
|---------|----------|
| Catalog | PostgreSQL (via Marten) |
| Basket  | Redis + PostgreSQL (via Marten) |
| Discount | SQLite |
| Ordering | SQL Server |

---

## 📨 Messaging

- **RabbitMQ** – Message broker for asynchronous events  
- **MassTransit** – Abstraction for publisher/subscriber models  
- Used for:
  - Domain events  
  - SAGA orchestration  
  - Integration across microservices  

---

## 📌 Summary

**E-Shop Microservices** demonstrates a complete, modular, and production-ready **microservices-based** e-commerce platform. It integrates:

- Scalable architecture
- Clean separation of responsibilities
- Modern communication patterns (gRPC, RabbitMQ)
- Powerful data handling via PostgreSQL, SQL Server, Redis, and SQLite

This solution is ideal for enterprise-level applications seeking high cohesion, low coupling, and service autonomy.

---

To run locally using Docker:

```bash
docker-compose -f docker-compose.yml up --build
