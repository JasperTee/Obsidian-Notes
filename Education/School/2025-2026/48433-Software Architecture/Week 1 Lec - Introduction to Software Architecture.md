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
# 2. Architectural Structures & Views

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

#### 1. **Module Structures** (Static Structures)

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

#### 2. **Component-and-Connector (C&C) Structures** (Dynamic Structures)

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

#### 3. **Allocation Structures** (Mapping Structures)

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