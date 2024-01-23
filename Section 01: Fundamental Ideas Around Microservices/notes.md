
# Microservices Cheat Sheet

## Understanding Microservices

### What is a Microservice?

#### The Monolithic Server Approach:
In a traditional monolithic server architecture, a client request undergoes several steps before generating a response:
- Initially, the request enters the application.
- It encounters middleware processes and is directed to the appropriate router.
- The request then interacts with the pertinent feature, accesses the database, and the response is generated back to the user.

A monolithic system typically encapsulates:
- **Routing**
- **Middleware Processes**
- **Business Logic**
- **Database Access**
- All these components work collectively to implement the complete set of application features.

#### Microservice Architecture:
In contrast, a microservice is designed to handle a singular or a small set of functionalities within an application. Each microservice is self-contained and operates a specific feature, contributing to the overall application.

![Microservice Architecture](https://i.gyazo.com/9b1c406ba243b61a78b4626783deede7.png)

Key Advantage:
- **Resilience:** The microservice architecture enhances application resilience. Specific features remain operational even if an individual service encounters issues.

### Data Management in Microservices

Microservices approach data management uniquely, optimizing service-to-service interactions.

#### Key Aspects:

1. **Independent Data Storage:**
   - Each microservice possesses its own database (when necessary).
2. **Secure Data Access:**
   - Services do not directly access databases of other services.

#### Database-Per-Service Model:
- Each service functions independently.
- Database schemas may evolve without impacting other services.
- Services can utilize different database types (SQL, NoSQL) based on their specific requirements.

![Database-Per-Service Model](https://i.gyazo.com/3c71a440122ebfab7ec1da5d382a634a.png)

**Drawback of Shared Databases:**
- Shared databases limit scalability as they need to be scaled for all services collectively.

### Communication Strategies in Microservices

Microservices can communicate synchronously or asynchronously, each with its own implications.

#### Synchronous Communication:
- **Direct Service Interactions:**
  - Services communicate through direct requests.
- **Pros:**
  - Easier to conceptualize.
  - Some services may not require a direct database.
- **Cons:**
  - Dependency between services.
  - If one service request fails, it can affect the entire process.
  - Limited by the slowest request.
  - Can lead to complex inter-service dependencies.

#### Asynchronous Communication:
- **Event-Driven Interactions:**
  - Services communicate via events, often using an event bus.
- **Pros:**
  - Services remain independent, reducing direct dependencies.
  - Faster request handling due to immediate data availability.
- **Cons:**
  - Data duplication leads to higher storage costs.
  - More complex to implement and understand, suitable for large-scale systems with numerous services.
