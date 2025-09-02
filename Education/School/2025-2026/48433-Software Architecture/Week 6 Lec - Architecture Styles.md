## 1. Bad Architecture
### 1.1. Monolithic Architecture (Anti-pattern)

#### Definition

- A **monolithic architecture** is when an entire software system is built as **one large, unified block** (a single deployable unit).
    
- All features and responsibilities are tightly coupled inside the same component or application.
    
- It is not considered a good architectural style – it is an **anti-pattern** because it violates fundamental design principles.
    

---

#### Characteristics

- **God Component:** one huge component contains many unrelated responsibilities.
    
- **Single codebase, single deployment:** everything is packaged together and deployed at once.
    
- **Tight coupling:** all modules depend on each other directly.
    
- **Lack of clear separation:** no clear boundaries between different features (e.g., authentication, profile management, recommendations).
    

---

#### Example

Imagine building a social media app:

- In a **monolithic design**, one application would handle:
    
    - Authentication (login/logout).
        
    - User profile management.
        
    - Messaging.
        
    - News feed.
        
    - Notifications.
        
    - Friend recommendations.
        

Everything is inside one big codebase, one big database, and one big deployment.

---

#### Problems (Why it’s bad)

1. **Maintenance difficulty:**
    
    - Changing one feature (e.g., notifications) may accidentally break another (e.g., messaging).
        
2. **Scaling issues:**
    
    - If only the messaging feature needs scaling, you still have to scale the entire system.
        
3. **Slow development:**
    
    - Many developers working on the same codebase → merge conflicts, dependencies, bottlenecks.
        
4. **Deployment risks:**
    
    - Even small updates require redeploying the entire system. If it fails, the whole app goes down.
        
5. **Technology lock-in:**
    
    - You cannot easily use different programming languages or databases for different features – everything must use the same stack.
        

---

#### Anti-pattern Recognition

- When you see a **Map Page** doing everything (map display, compass, pins, sidebar, search), instead of being split into smaller components.
    
- When a **single repository or service** handles multiple responsibilities like authentication, user management, and recommendations.
    

---

#### Better Alternative

- Apply **Single Responsibility Principle**: break down the system into smaller, focused components.
    
- Move towards **Layered Architecture** (front-end, API, back-end) or **Microservices** (independent services).
## 2. Common Architecture Styles
### 2.1. Layered Architecture

#### Definition

- **Layered Architecture** is a design model where the system is divided into **layers**, and each layer has a specific responsibility.
    
- Layers are arranged in a **logical order** and often separated **physically** (deployed on different servers).
    
- A higher layer communicates with the layer below it only through an **interface or API**, without knowing the internal details.
    

---

#### Key Characteristics

- **Clear separation:** each layer has its own responsibility (UI, business logic, data).
    
- **Top-down dependency:** higher layers depend on lower ones.
    
- **API as a bridge:** front-end usually communicates with back-end via an API.
    

---

#### Example

An **e-commerce application** can be split into:

1. **Presentation Layer (Front-end/UI):**
    
    - Manages the user interface: displaying products, handling shopping cart.
        
    - Technologies: React, Angular, Vue.
        
2. **Application Layer (Back-end/Business Logic):**
    
    - Handles business rules: calculating prices, processing orders.
        
    - Technologies: Java Spring, .NET, Node.js.
        
3. **Data Layer (Database):**
    
    - Stores data: user accounts, products, orders.
        
    - Technologies: MySQL, PostgreSQL, MongoDB.
        

**Flow Example:** When the user clicks “Buy”:

- UI sends a request → Backend processes the payment → Database saves the order.
    

---

#### Pros

- **Efficient resource usage:** heavy rendering happens at UI, logic at backend, storage at DB.
    
- **Modularity:** easy to expand or replace a layer.
    
- **Testability:** easier to write unit tests for separate layers.
    
- **Security boundaries:** each layer can be isolated for better security.
    
- **Division of labor:** work naturally divided between UI developers, backend developers, and database admins.
    

---

#### Cons

- **Too many layers → complexity:** more layers can make the system complicated and create “silos” (skill gaps).
    
- **API bottleneck:** API between layers may become a single point of failure or slowdown.
    
- **Coupling:** layers evolve together (if API changes, both front-end and back-end must adapt).
    
- **Complexity concentration:** splitting into layers doesn’t eliminate complexity—it may pile up in one layer (often the backend).
    

---

#### Use Cases

- **Traditional web applications** (front-end + API + backend + database).
    
- **Enterprise systems** (ERP, CRM) where division of responsibilities is important.
    
- Systems needing **security control**, since firewalls can be placed between layers.
### 2.2. Service-Oriented Architecture (SOA)

#### Definition

- **Service-Oriented Architecture (SOA)** is an architectural style in which a system is built from multiple **independent services**.
    
- Each service is like a **black box**: it hides its internal logic and only exposes a **standardized interface** for others to use.
    
- The idea: instead of rewriting everything, we can **assemble services** to build more complex systems.
    

---

#### Characteristics of a Service

A service in SOA usually has these qualities:

1. **Encapsulation:**
    
    - The internal details (code, data, logic) are hidden.
        
    - Other services interact only through the interface (API/contract).
        
2. **Autonomy:**
    
    - Each service is free to implement its internal logic however it wants.
        
    - It doesn’t rely on other services to perform its core job.
        
3. **Discoverability:**
    
    - The service provides metadata describing what it does and how to use it.
        
    - Example: WSDL files in SOAP web services.
        
4. **Standardization:**
    
    - Interfaces follow agreed-upon standards (SOAP, XML, JSON, HTTP).
        
    - Ensures different systems can interoperate.
        
5. **Loose Coupling:**
    
    - Services can be added, removed, or replaced without breaking the whole system.
        
6. **Reusability:**
    
    - A single service can be reused across multiple applications.
        
    - Example: a Payment Service can be reused in e-commerce apps, subscription apps, or other platforms.
        

---

#### Example

In an **e-commerce system**, SOA could consist of:

- **User Service:** manages user accounts and profiles.
    
- **Product Service:** handles product catalogs.
    
- **Payment Service:** processes payments (can be reused in other apps).
    
- **Shipping Service:** calculates shipping fees and tracks deliveries.
    

→ Together, these services form a complete e-commerce platform.

---

#### Pros

- **High modularity:** easier to maintain and extend.
    
- **Reusability:** one service can serve many applications.
    
- **Integration-friendly:** can connect with many external systems via standards.
    
- **Flexibility:** easy to swap or update services without major rewrites.
    

---

#### Cons

- **High complexity:** requires infrastructure for service management (registries, monitoring, governance).
    
- **Communication overhead:** since services often communicate over a network.
    
- **Harder integration testing:** need to test not only each service but also the interactions.
    
- **Security challenges:** many exposed endpoints increase the attack surface.
    

---

#### Use Cases

- Large enterprises that need to integrate multiple systems (ERP, CRM, HRM).
    
- Applications that need to **evolve incrementally** by adding new services.
    
- When common services (e.g., authentication, payments) need to be reused across projects.
### 2.3. Event-Driven Architecture (EDA)

#### Definition

- **Event-Driven Architecture (EDA)** is a model where **data and behavior** are communicated through **events**.
    
- An **event** is any significant change in the system, such as _“OrderCreated”_, _“UserLoggedIn”_, _“TripCompleted”_.
    
- Components do not call each other directly. Instead, they interact by **publishing** and **subscribing** to events.
    

---

#### Key Characteristics

- **Event Processors:**
    
    - Each processor cares about specific event types.
        
    - It **receives an event**, processes it, then **emits a new event**.
        
    - It does **not care who consumes** the output event.
        
- **Event Flow:**
    
    - Input Event → Processor → Output Event.
        
    - Example:
        
        - _“TripCompleted”_ (input) → calculate charge → emit _“ChargeCalculated”_ (output).
            

---

#### Topologies

1. **Broker Topology:**
    
    - Each processor is independent, only needs to know which event type it handles.
        
    - An **event broker** is responsible for distributing events to the right processors.
        
    - Provides flexibility and scalability.
        
2. **Mediator Topology:**
    
    - A central **event mediator** coordinates complex event chains.
        
    - Mediator knows what steps must be executed in sequence.
        
    - Useful for **orchestration** when workflows require multiple steps.
        

---

#### Pros

- **Highly Scalable:** multiple processors can handle the same event type.
    
- **Extensible:** easy to add new processors without disrupting the system.
    
- **Isolation:** each processor is independent → easier to develop, test, and deploy.
    
- **Flexible Deployment:** processors can be upgraded or replaced independently.
    

---

#### Cons

- **Communication Overhead:** event passing adds network and processing cost.
    
- **Traceability & Testability Issues:** hard to track full event flows, hard to test end-to-end.
    
- **Potential Pitfalls:**
    
    - Events can be **dropped** (lost).
        
    - Event schemas may evolve → downstream processors break.
        
    - Slow or failing processors → bottlenecks, queue overflow.
        
    - Humans in the loop may introduce delays.
        

---

#### Example

A ride-hailing app (like Uber):

1. Event: **TripCompleted**.
    
2. Event processors respond:
    
    - **CalculateCharge** → emits _“ChargeCalculated”_.
        
    - **PayDriver** → emits _“DriverPaid”_.
        
    - **ChargeRider** → emits _“PaymentSuccess”_.
        
    - **ReactivateDriver** → emits _“DriverAvailable”_.
        

→ Each processor is independent, making the system extensible and maintainable.

---

#### Use Cases

- **Large, scalable systems:** e-commerce, fintech, logistics.
    
- **Real-time applications:** data streaming, IoT, sensor networks.
    
- **Asynchronous workflows:** order processing, sending emails/SMS, payments.
### 2.4. Microservices Architecture

#### Definition

- **Microservices Architecture** is a model where a system is built from many **small, independent services (microservices)**.
    
- Each microservice is a **self-contained web service** that can be developed, deployed, scaled, and maintained independently.
    
- Unlike **SOA**, microservices emphasize **small scope, single responsibility**, and **containerized deployment**.
    

---

#### Key Characteristics

1. **Self-contained service:**
    
    - Each microservice has its own logic and often its own database (or schema).
        
    - Example: _User Service_, _Order Service_, _Payment Service_.
        
2. **Independent deployment:**
    
    - Each service can be deployed or updated without affecting the rest of the system.
        
3. **Polyglot freedom:**
    
    - Services can use different programming languages and technologies (Java, Python, Go, Node.js).
        
4. **Distributed nature:**
    
    - Microservices communicate through **APIs (REST, gRPC)** or **message brokers**.
        

---

#### Principle: “Cattle, not Pets”

- **Traditional (Pets):** servers are special and must be taken care of.
    
- **Microservices (Cattle):** services are disposable, replaceable, and scalable.
    
    - If one fails → replace it.
        
    - If more capacity is needed → spin up more instances.
        
- No attachment to specific machines or services.
    

---

#### Supporting Technologies

- **Containerization:**
    
    - Each microservice runs in its own **Docker container**.
        
    - Lighter than virtual machines, no need for a full OS per service.
        
- **Declarative deployment:**
    
    - Deployment described in code (Dockerfile, Kubernetes manifests).
        
    - No manual setup required.
        
- **Automated scheduling:**
    
    - Systems like Kubernetes decide where and when to deploy services.
        
- **Service discovery:**
    
    - Services automatically find and connect to each other (e.g., via Consul, Eureka).
        

---

#### Pros

- **Scalability:** scale individual services (e.g., Payment Service) without scaling the whole system.
    
- **Fault tolerance:** failure of one service doesn’t crash the entire system.
    
- **Continuous Delivery (CI/CD):** easier to update and release frequently.
    
- **Team autonomy:** each team can own and develop one microservice independently.
    
- **Technology diversity:** different services can use different languages or frameworks.
    

---

### Cons

- **Operational complexity:** requires advanced infrastructure (Kubernetes, monitoring, logging, tracing).
    
- **Network overhead:** inter-service communication over a network is slower than in-process calls.
    
- **Data consistency issues:** hard to maintain strong consistency if each service has its own database.
    
- **Testing challenges:** harder to perform end-to-end testing across many services.
    

---

### Real-world Examples

- **Netflix:**
    
    - Runs hundreds of microservices (streaming, recommendations, billing, authentication).
        
    - Each can have thousands of instances to serve millions of users.
        
- **Amazon:**
    
    - Uses microservices for _Order Service_, _Payment Service_, _Inventory Service_, _Shipping Service_.
        

---

### Use Cases

- Large systems needing **independent scaling** of features.
    
- Organizations with many teams working in parallel.
    
- Cloud-native applications requiring continuous deployment and updates.