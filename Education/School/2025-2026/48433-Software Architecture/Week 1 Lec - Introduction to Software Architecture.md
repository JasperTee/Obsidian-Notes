### What is Software Architecture?
> **Software Architecture** is the **set of structures** needed to understand, design, and reason about a software system.  

  These structures describe:

#### 1. **What the system is made of? - Module Structures **
- Focus on **code organisation**
    
- Show how the system is broken into **implementation units** (modules, classes, packages)
    
- Describe **relationships** like: “uses”, “inherits”, “contains”
    
- Help answer:
    
    - What does each module do?
        
    - How are responsibilities divided?
        
    - What does this module depend on?
    
> → Architecture defines **how the system is built in code**
#### 2. **How those parts connect and interact - Component-and-Connector (C&C) Structures**
- Focus on **runtime behavior**
    
- Show how components (e.g., services, clients) **interact during execution**
    
- Define **connectors** (e.g., function calls, data flow, events) that manage communication
    
- Help answer:
    - What components run?
        
    - How do they talk to each other?
        
    - What is the data flow?
        
> → Architecture shows how the system **behaves when running**
#### 3. **Where those parts are deployed or assigned - Allocation Structures**
- Focus on **deployment and team structure**
    
- Map software parts to:
    
    - **Hardware** (e.g., servers, cloud)
        
    - **Files** (e.g., project folders)
        
    - **Teams** (e.g., which team builds what)
        
- Help answer:
    
    - Where does this run?
        
    - Who is responsible for this part?
        
    - What infrastructure is needed?
        

> → Architecture connects software to the **real-world environment**
