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
![[Layered Architecture.png]]
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
![[Microservices Architecture.png]]
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

#### Cons

- **Operational complexity:** requires advanced infrastructure (Kubernetes, monitoring, logging, tracing).
    
- **Network overhead:** inter-service communication over a network is slower than in-process calls.
    
- **Data consistency issues:** hard to maintain strong consistency if each service has its own database.
    
- **Testing challenges:** harder to perform end-to-end testing across many services.
    

---

#### Real-world Examples

- **Netflix:**
    
    - Runs hundreds of microservices (streaming, recommendations, billing, authentication).
        
    - Each can have thousands of instances to serve millions of users.
        
- **Amazon:**
    
    - Uses microservices for _Order Service_, _Payment Service_, _Inventory Service_, _Shipping Service_.
        

---

#### Use Cases

- Large systems needing **independent scaling** of features.
    
- Organizations with many teams working in parallel.
    
- Cloud-native applications requiring continuous deployment and updates.

## 3. Patterns of Communication

The tutorial lists four common ways containers/services talk to each other: **via a repository, via an API, via persistent connections, and via queues/brokers**.
### 3.1. Communication via a Repository (Shared Database)

#### Definition

- This pattern means **multiple containers or services read from and/or write to the same repository**, usually a cloud-based database.
    
- The repository acts as the **intermediary** for sharing data.
    
- Instead of calling each other’s APIs, containers interact through **basic CRUD (Create, Read, Update, Delete)**operations on the shared database.
    

---

#### How It Works

1. A **producer service** writes data to the database.
    
2. A **consumer service** reads data from the database when needed.
    
3. Often, **multiple services** both read and write to the same database.
    

**Example from tutorial:**

- In the _We Feel System_, several services (tweet gatherer, tweet annotator, summary builder) all read/write to **Amazon DynamoDB** to store summaries of emotional data over time.
    

---

#### Pros

- **Simple to implement:** just connect all services to the same database.
    
- **No need for APIs** between services.
    
- **Quick for small systems:** useful when there are only a few containers.
    

---

#### Cons

- **Limited to CRUD interactions:** no rich messaging semantics.
    
- **Polling is wasteful:** if consumers constantly check the DB for updates, resources are wasted.
    
- **Consistency problems:**
    
    - Multiple writers can overwrite each other’s changes.
        
    - Example: two services updating the same inventory count at the same time.
        
- **Scalability issues:** the database may become a **bottleneck** as load grows.
    

---

#### Example Scenario

In an **e-commerce application**:

- **Order Service** and **Payment Service** both update the same **Orders DB**.
    
- Order Service inserts a new order.
    
- Payment Service updates the order status to “Paid.”
    
- Risk: if Payment updates before Order has fully written → inconsistent data.
    

---

#### When to Use

- Small applications with few services.
    
- When data sharing is **simple CRUD**.
    
- When only one service writes while others just read (avoids conflicts).
    

#### When to Avoid

- Large systems with many services writing simultaneously.
    
- When **real-time updates** or **event-driven communication** are required.
    
- When you want to avoid bottlenecks at a single database.
### 3.2. Communication via APIs

#### Definition

- This is the **consumer ↔ provider** model:
    
    - **Consumer:** initiates all communication.
        
    - **Provider:** offers data/services, but doesn’t know or care who is consuming.
        
- All interactions are **started by the consumer** — it _pulls_ when it needs information and _pushes_ when it wants to send something.
    

---

#### Key Characteristics

- **Consumer depends on provider:** the consumer must know where the provider is, and what APIs it exposes.
    
- **Provider does not depend on consumer:** it just waits and responds when called.
    
- Communication follows a defined **API contract** (endpoints, methods, request/response formats).
    

---

#### REST API – the most common standard

- **URL = nouns (resources):**  
    Example: `/users/123/orders`.
    
- **HTTP methods = verbs (operations):**
    
    - `GET` → retrieve data
        
    - `POST` → create new
        
    - `PUT/PATCH` → update
        
    - `DELETE` → delete
        
- **Stateless:** each request is independent; the server does not keep session state; authentication usually comes in headers.
    
- **Responses:** JSON payload + HTTP status codes (200 OK, 404 Not Found, 500 Server Error).
    
- **Relationships:** expressed through chaining:
    
    - `GET /shows/lion-king/tickets/` → fetch all tickets
        
    - `DELETE /shows/lion-king/tickets/13` → delete ticket 13
        

---

#### Pros

- **Clear and standardized** → easy to learn and use.
    
- **Easy to test** with tools like Postman or curl.
    
- **Cacheable:** especially GET requests.
    
- **Widely compatible** with many systems and languages.
    

---

#### Cons

- **Consumer-initiated only:** the server cannot push information to clients proactively.
    
    - Example: in a chat app, when one user sends a message, the server cannot notify other clients via REST unless they request it.
        
- **Not real-time:** designed for request/response, not continuous updates.
    
- **Versioning challenges:** when the API changes, all consumers must adapt.
    

---

#### Example Scenario

A **ticket booking app**:

- **Consumer:** front-end web app (Angular).
    
- **Provider:** back-end API (Spring MVC).
    
- Flow:
    
    1. User clicks “Buy ticket.”
        
    2. Web app sends `POST /tickets`.
        
    3. Back-end API processes, stores in DB, and returns JSON:
        
        `{ "id": 123, "status": "paid" }`
        

---

#### When to Use

- Basic CRUD operations (orders, user profiles, product info).
    
- Synchronous **request/response** patterns.
    
- Integrating services with well-defined contracts.
    

#### When Not to Use

- Systems requiring **real-time notifications** (chat, games, dashboards).
    
- Many-to-many communication (one event must fan out to multiple consumers).
    

---
### 3.3. Communication via Persistent Connections (WebSockets)

#### Definition

- A **persistent connection** is when a **client** opens a long-lived connection to a **server**.
    
- While the connection remains open, **both sides can send messages at any time**.
    
- Either side can close the connection.
    
- The most common example: **WebSockets**, supported by all modern browsers.
    

---

#### Key Characteristics

- **Bidirectional:** unlike REST (where the client requests and server responds), here the **server can also push messages** to the client.
    
- **Real-time:** data is delivered immediately as events happen.
    
- **Long-lived connection:** only one handshake is required; the connection stays open, reducing overhead compared to repeated HTTP requests.
    

---

#### Pros

1. **Real-time updates:** ideal for low-latency apps like chat, gaming, and live dashboards.
    
2. **Server push:** server can notify clients without waiting for them to poll.
    
3. **Less overhead:** fewer connection setups compared to traditional request/response.
    

---

#### Cons

1. **Ambiguous interface:**
    
    - WebSocket does **not enforce message formats**.
        
    - Developers must define their own schema/protocol (e.g., JSON structure, custom commands).
        
    - Lacks the strong standardization of REST APIs.
        
2. **Difficult to scale:**
    
    - WebSocket servers are **stateful** (must remember client sessions).
        
    - Handling millions of simultaneous connections is challenging.
        
    - Requires load balancing and often extra infrastructure (brokers).
        
3. **Not microservice-friendly:**
    
    - WebSockets create direct client ↔ server channels.
        
    - They don’t provide **loose coupling** between many services like message queues or event buses do.
        

---

#### Example Scenario

A **chat application**:

- **User A** sends a message → client A sends it via WebSocket to the server.
    
- **Server** immediately pushes the message to client B.
    
- Both clients maintain open connections, so the message is delivered instantly.
    

**With REST:** client B would only see the new message after polling the server repeatedly (“Do I have new messages?”).

---

#### When to Use

- Applications requiring **real-time two-way communication**: chat apps, multiplayer games, live notifications, stock trading dashboards.
    
- When the number of concurrent connections is moderate and manageable.
    

#### When Not to Use

- Large-scale **microservice systems** that need strong decoupling.
    
- Workflows that require **reliability guarantees** (acknowledgments, retries, message ordering) → better suited for message queues/brokers.
    
- Systems with **millions of concurrent connections** where scaling WebSocket servers is very complex.
    

---
### 3.4. Communication via Queues and Brokers
#### Main Idea

- Instead of **A calling B directly**, we put a **queue** or a **broker** in the middle.
    
- **Producer (sender)** → pushes a message into the queue.
    
- **Consumer (receiver)** → pulls the message from the queue when it’s ready.
    
- This way:
    
    - A doesn’t need to know who B is or if B is online.
        
    - B can process later without losing data.
        

---

#### Real-life Analogy

1. **Post Office (Message Queue):**
    
    - You (producer) write a letter and drop it into a mailbox (queue).
        
    - The post office (broker) delivers it.
        
    - The receiver (consumer) picks it up when they can.  
        → You don’t need direct contact with the receiver.
        
2. **E-commerce Application:**
    
    - When you **place an order** → Order Service produces an event _“OrderCreated”_.
        
    - The event is stored in the queue.
        
    - Then:
        
        - Payment Service takes it → processes payment.
            
        - Email Service takes it → sends confirmation email.
            
        - Analytics Service takes it → records statistics.  
            → One event, many services react independently.
            

---

#### Pros (Why it’s useful)

- **Loose coupling:** Producer and Consumer don’t depend on each other.
    
- **Handles overload:** If consumers are slow, the queue buffers messages (no loss).
    
- **Fan-out:** One event can go to multiple consumers.
    
- **Scalable:** Add more consumers to process faster.
    

---

#### Cons (Why it’s hard)

- **More complex than APIs:** requires infrastructure like Kafka, RabbitMQ, AWS SQS.
    
- **Harder to trace/debug:** messages go through a middleman.
    
- **Possible bottleneck:** if the broker isn’t scaled properly.
    

---

#### Quick Comparison

- **REST API:** like making a phone call → you ask directly and wait for the answer.
    
- **WebSocket:** like keeping a call line open → both sides can talk anytime.
    
- **Message Queue:** like using the post office → you send a letter, the receiver reads it later, and many receivers can get copies.
    

---

👉 **When to use Queues/Brokers**

- When **multiple services need the same event**.
    
- When you want **reliability** (messages survive even if consumers are temporarily down).
    
- When you need **asynchronous workflows** (don’t need an immediate response).