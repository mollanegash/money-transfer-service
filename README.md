# 💸 Money Transfer Service

A Spring Boot–based backend service for handling financial transactions between accounts.  
This project demonstrates asynchronous processing, external API orchestration, and resilient backend design patterns used in distributed systems.

---

## 🚀 Core Features

- Transfer funds between accounts via REST API
- Coordinate multiple external services (transfer + confirmation)
- Asynchronous processing using `CompletableFuture`
- Timeout handling for long-running operations
- Centralized error handling with proper HTTP status mapping

---

## 🧠 System Design Highlights

- **Asynchronous Orchestration**  
  Uses `CompletableFuture` to execute external API calls without blocking the main thread

- **External Service Integration**  
  Coordinates multiple downstream services (`/transfer`, `/confirm`) to complete a transaction

- **Resilience & Fault Handling**  
  - Timeout protection for long-running operations  
  - Exception propagation using Spring `ResponseStatusException`  
  - Fail-fast behavior when dependent services fail  

- **Layered Architecture**  
  Controller → Service separation for clean design and maintainability

---

## ⚙️ Tech Stack

- Java 17  
- Spring Boot  
- REST APIs  
- CompletableFuture (async processing)  

---

## ⚠️ Real-World Design Considerations

This project demonstrates core concepts. In a production-grade financial system, additional patterns would be applied:

- **Idempotency**  
  Prevent duplicate transactions in retry scenarios

- **Retry Mechanisms**  
  Handle transient failures using exponential backoff

- **Distributed Transactions**  
  Implement Saga pattern or compensation workflows

- **Event-Driven Architecture**  
  Use Kafka / message queues for decoupled processing

- **Persistence Layer**  
  Store transactions with ACID guarantees (e.g., PostgreSQL)

---

## ▶️ API Example

**POST /transfer**

```json
{
  "fromAccount": "A123",
  "toAccount": "B456",
  "amount": 100.0
}
