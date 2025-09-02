## 1. Software Architecture
### 1.1 Definition

- **Software Architecture** is not just a drawing with boxes and arrows.
    
- It is a **set of structures** used to describe a software system.
    
- Each structure includes:
    
    - **Elements (components)** → e.g., modules, services, classes, databases.
        
    - **Relations (connectors)** → e.g., dependencies, API calls, message passing.
        
    - **Properties (attributes)** → e.g., performance, security, programming language.
        

👉 In simple terms, Software Architecture answers:

- **What the system is made of** (its main building blocks).
    
- **How those parts connect and interact**.
    
- **Where those parts are deployed or assigned** in the environment.
    

---

### 1.2 Key Points

1. **Important Decisions**
    
    - Architecture focuses on **high-level decisions** that have a long-term impact.
        
    - Example: choosing between **microservices vs. monolith**, or **SQL vs. NoSQL** storage.
        
    - These are costly to change later, so they are made early.
        
2. **Abstraction**
    
    - Architecture is an **abstraction**, not detailed code.
        
    - It presents **just enough information** to reason about the system.
        
    - Example: saying _“Authentication Service exists”_ instead of showing all its Java code.
        
3. **Quality Attributes (Non-functional requirements)**
    
    - Architecture directly affects qualities like **performance, security, scalability, maintainability**.
        
    - Example: choosing a distributed database improves scalability but may reduce consistency.
        

---

### 1.3 Example

Imagine building an **e-commerce application**:

- **Elements**: Web frontend, Mobile app, Payment Service, Inventory Service, Database.
    
- **Relations**: The frontend calls Payment API, Payment Service connects to a payment gateway.
    
- **Properties**: Payment must comply with PCI-DSS (security), response time < 2 seconds.
    

👉 All of these decisions together define the **Software Architecture** of the system.
## 2. Architectural Structures & Views

### 2.1 Why We Need Structures & Views

- A **software system** is too complex to describe in a single diagram.
    
- Different stakeholders (developers, testers, managers, clients) **care about different aspects**.
    
    - A developer wants to see **modules and their dependencies**.
        
    - A system admin cares about **deployment on servers or cloud**.
        
    - A tester cares about **data flow and interactions**.
        
- Therefore, we need **multiple structures (models)** and **views** to show different perspectives of the same system.
    

👉 Think of it like **Google Maps**:

- Street view, satellite view, and traffic view show different aspects of the same city.
    
- Similarly, architecture has multiple **views** of the same system.
    

---

### 2.2 What is an Architectural Structure?

- **Definition**: A **set of elements** (components), the **relations** among them, and the **properties** of both.
    
- Each structure shows the system from a **different angle**.
    
- One system = many structures.
    

Example:

- Module structure → shows modules and dependencies.
    
- Deployment structure → shows servers, containers, and where modules run.
    
- Component-and-connector structure → shows runtime interactions (calls, messages).
### 2.3 Common Types of Structures

In software architecture, there are **many ways to describe a system**, but most fall into **three main categories**:

---

#### 2.3.1 **Module Structures** (Static Structures)
![[Module Structures.png]]
- **What it shows**:
    
    - How the software is **divided into modules** in the code.
        
    - The **static organization** (what exists in the code before runtime).
        
- **Elements**: modules, packages, classes, subsystems.
    
- **Relationships**: _is part of_, _depends on_, _uses_.
    
- **Purpose**: supports understanding, development, and maintenance.
    

**Example (E-commerce app)**:

- `User` module → login, registration.
    
- `Order` module → order processing.
    
- `Payment` module → payment logic.
    

👉 Think of it as the **blueprint of code organization**.

---

#### 2.3.2 **Component-and-Connector (C&C) Structures** (Dynamic Structures)
![[Component-and-Connector (C&C) Structures.png]]
- **What it shows**:
    
    - How the system **runs at runtime**.
        
    - **Interactions, data flow, and communication** between components.
        
- **Elements**: components (services, UI, DB, APIs) + connectors (REST calls, message queues, events).
    
- **Purpose**: helps analyze performance, reliability, and system behavior.
    

**Example (Banking app)**:

- User → Web UI (browser).
    
- UI → API Gateway → Auth Service → Database.
    
- Services talk over HTTP or MQ (message queue).
    

👉 Think of it as the **map of runtime conversations**.

---

#### 2.3.3 **Allocation Structures** (Mapping Structures)
![[Allocation Structures.png]]
- **What it shows**:
    
    - How software is **mapped onto the environment** (hardware, file system, teams).
        
- **Types**:
    
    - **Deployment View** → where software runs (servers, containers, cloud).
        
    - **Implementation View** → mapping modules to files, repos, libraries.
        
    - **Work Assignment View** → which team is responsible for which part.
        
- **Purpose**: supports project planning, deployment, and responsibility management.
    

**Example**:

- Microservices → deployed in Kubernetes cluster.
    
- Database → runs in AWS RDS.
    
- `Payment` module → owned by backend team.
    
- `UI` module → owned by frontend team.
    

👉 Think of it as the **bridge between software and its environment**.
## 3. Why is Software Architecture Important?

Software Architecture is **not just about drawing diagrams** — it plays a **critical role** in the success of a software system.

---

### 3.1 **Defines Structure and Organization**

- Architecture provides the **blueprint** for how the system is broken down (modules, components, data flows, deployment).
    
- Without it, the system may become chaotic, hard to maintain, and inconsistent.
    

**Example**: An online store with no clear separation between UI, business logic, and database → adding new features becomes slow and risky.

---

### 3.2 **Guides Development and Communication**

- Architecture acts as a **shared language** between stakeholders (developers, architects, managers, clients).
    
- Ensures **everyone understands the system** at a high level, even non-coders.
    
- Helps align technical decisions with **business goals**.
    

**Example**: When deciding between **monolithic** or **microservices**, the architecture communicates trade-offs clearly to business managers.

---

### 3.3 **Supports Quality Attributes (Non-functional Requirements)**

- Many **“-ilities”** (performance, scalability, security, reliability, maintainability, usability) are influenced by architecture.
    
- These cannot simply be “added later”; they must be designed into the system from the beginning.
    

**Example**:

- **Performance** → choosing caching layers.
    
- **Scalability** → microservices or cloud-native design.
    
- **Security** → limiting access points, authentication design.
    

---

### 3.4 **Manages Complexity**

- Modern software systems are very complex.
    
- Architecture **abstracts details** and provides **layers, modules, and views** to handle complexity step by step.
    

**Example**: In a healthcare system, architecture separates patient records, billing, and analytics into clear modules so teams don’t get overwhelmed.

---

### 3.5 **Enables Reuse and Evolution**

- A good architecture supports **reuse** of modules and services.
    
- Makes it easier to **adapt to future changes** in technology or requirements.
    

**Example**: If the payment module is well-architected, it can be reused in multiple apps (e-commerce, booking, subscription).

---

### 3.6 **Reduces Risk and Cost**

- Poor architecture leads to **technical debt**, which increases maintenance costs.
    
- Good architecture reduces risks of:
    
    - Project delays.
        
    - System failures.
        
    - Expensive rework.
        

**Example**: A banking system with poor architecture may fail to scale under high load → millions lost during peak usage.

---

### 3.7 **Supports Decision Making**

- Architecture documents trade-offs and alternatives.
    
- Provides a framework to evaluate new requirements or technologies.
    

**Example**: Deciding whether to store data in **SQL** vs **NoSQL** depends on architectural considerations (consistency vs scalability).
## 4. SOLID Principles of Object-Oriented Class Design

**SOLID** is a set of five design principles in Object-Oriented Programming (OOP). They aim to make software easier to maintain, extend, test, and reuse. These principles are considered best practices in software architecture and class design.

---

### 4.1 Single Responsibility Principle (SRP)

A class should have only **one responsibility** or reason to change.

- If a class handles multiple concerns, a change in one area can unintentionally affect another.
    
- Example:
    
    - Bad: An `InvoiceManager` class that calculates invoices, prints them, and sends emails.
        
    - Good: Separate classes such as `InvoiceCalculator`, `InvoicePrinter`, and `InvoiceEmailer`.
        

**Benefit:** Improves maintainability, readability, and testability.

---

### 4.2 Open/Closed Principle (OCP)

Classes should be **open for extension but closed for modification**.

- When requirements change, functionality should be added by creating new classes or methods (e.g., via inheritance or composition), not by modifying existing code.
    
- Example:
    
    - Bad: A `Shape` class with a method `calculateArea()` that must be edited each time a new shape (circle, square, triangle) is added.
        
    - Good: Define a `Shape` interface with `area()`; each shape implements its own logic.
        

**Benefit:** Prevents breaking existing code when adding new features.

---

### 4.3 Liskov Substitution Principle (LSP)

Subclasses should be substitutable for their base classes without breaking program behavior.

- A derived class must preserve the behavior expected of its parent class.
    
- Example:
    
    - Problem: If `Square` extends `Rectangle`, substituting a square may break logic because rectangles allow independent width and height, while squares require them to be equal.
        
    - Solution: Avoid incorrect inheritance; treat `Square` and `Rectangle` as separate implementations of `Shape`.
        

**Benefit:** Ensures correctness when using polymorphism and inheritance.

---

### 4.4 Interface Segregation Principle (ISP)

Clients should not be forced to depend on methods they do not use.

- It is better to have multiple smaller, specific interfaces rather than one large, general-purpose interface.
    
- Example:
    
    - Bad: A `Machine` interface with `print(), scan(), fax()`. A simple printer must implement methods it does not need.
        
    - Good: Split into `Printer`, `Scanner`, and `Fax` interfaces. A class implements only what it requires.
        

**Benefit:** Reduces unnecessary dependencies and increases flexibility.

---

### 4.5 Dependency Inversion Principle (DIP)

High-level modules should not depend on low-level modules. Both should depend on abstractions.

- Depend on interfaces or abstract classes rather than concrete implementations.
    
- Example:
    
    - Bad: `ReportService` directly creates `FileLogger logger = new FileLogger()`.
        
    - Good: `ReportService` depends on a `Logger` interface, and the specific implementation (`FileLogger`, `DatabaseLogger`) is injected externally.
        

**Benefit:** Reduces coupling, improves testability, and makes code easier to change or extend.
## 5. C4 Model 

### Core Idea

- When building a software system, different people (developers, testers, managers, customers) need a **shared understanding**.
    
- But each group needs **a different level of detail**.
    
- The **C4 model** solves this by providing **4 levels of diagrams**.
    
- Think of it like **Google Maps zoom**: see the whole Earth → city → streets → individual houses.
    

---

### The Four Levels

#### 1. **System Context**

- **From far above, you see the whole city.**
    
- The “system” is the city, surrounded by **users** and **other systems**.
    
- Answers: _Who uses this system? What external systems does it interact with?_
    

**Example: Internet Banking System**

- Users: customers, bank staff.
    
- External systems: VISA/MasterCard payment gateway, credit-check service.
    

---

#### 2. **Container**

- **Zoom in: now you see districts of the city.**
    
- A **container** is an application or executable part of the system (web app, mobile app, database, microservice).
    
- Answers: _What major building blocks make up the system? What technology do they use? How do they connect?_
    

**Example: Internet Banking System**

- Web Application (Java Spring MVC).
    
- Mobile App (iOS, Android).
    
- API Application (microservices).
    
- Database (PostgreSQL).
    

---

#### 3. **Component**

- **Zoom further: inside one district, you now see neighborhoods.**
    
- A **component** is a logical grouping of related functionality inside a container.
    
- Answers: _What are the main modules of one application? How do they interact?_
    

**Example: API Application**

- Authentication Service (login handling).
    
- Transaction Service (money transfers).
    
- Notification Service (email, SMS).
    

---

#### 4. **Code (Class Diagram)**

- **Zoom all the way in: now you see individual houses.**
    
- Shows classes, methods, and detailed implementation.
    
- Answers: _How is this component implemented in code?_
    

**Example: Transaction Service**

- `TransactionService` class (core business logic).
    
- `Transaction` class (represents a transaction).
    
- `TransactionRepository` class (handles database operations).
    

---

### Summary of Levels

- **System Context** → Big picture: people + external systems.
    
- **Container** → Inside system: applications/services/databases.
    
- **Component** → Inside an app: functional modules.
    
- **Code** → Inside a module: classes and methods.
    

---

### Benefits of C4

- **Managers/customers** understand the system at high level (Context + Container).
    
- **Developers** understand the technical structure (Component + Code).
    
- Whole team shares the same “map,” avoiding misunderstandings.