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