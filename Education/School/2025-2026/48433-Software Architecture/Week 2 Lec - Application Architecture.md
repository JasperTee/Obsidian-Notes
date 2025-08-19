## 1. The Context of an Architecture

### 1.1 Why Context Matters

- An architecture **cannot exist in isolation** – it must **fit the context** in which it is developed.
    
- Architecture is not only about implementing functionality, but also about aligning with:
    
    - **Stakeholder goals** (users, customers, regulators, developers, etc.).
        
    - **Constraints** such as time, budget, resources, technologies, and policies.
        
    - **Risks and opportunities** in the market and organizational environment.
        

**Example**:  
A fintech company designing a payment platform:

- If they focus only on performance but ignore regulatory constraints (e.g., PCI-DSS for payment security), the system may become illegal.
    
- If they fail to catch a market opportunity, competitors might release a similar product earlier and gain dominance.
    

---

### 1.2 Elements of Context

#### (a) Functional Requirements

- Define **what the system must do**.
    
- Example: an e-commerce system should allow:
    
    - User registration/login.
        
    - Shopping cart management.
        
    - Online payment.
        

> Note: functionality is essential, but **does not determine the architecture** by itself. The same functionality can be implemented with very different architectures.

---

#### (b) Stakeholder Goals

Stakeholders may have different, sometimes conflicting goals:

- **Functional goals**: correct system behavior.
    
- **System quality goals**: non-functional requirements (performance, security, usability, modifiability).
    
- **Technology goals**: platforms, frameworks, cloud adoption.
    
- **Organizational capability goals**: leveraging team expertise, training, or existing skills.
    

**Key stakeholders**:

- Users, customers, regulators, developers, system administrators, suppliers, support staff, and architects.
    

**Example**:

- Users want the app to be “fast and easy to use.”
    
- Developers want “popular frameworks that are easy to maintain.”
    
- Regulators demand “compliance with privacy and security laws.”
    

---

#### (c) Constraints and Enablers

- **Common constraints**:
    
    - Time (deadlines).
        
    - Money (limited budget).
        
    - Resources (staffing, expertise).
        
    - Technology (legacy systems, mandatory standards).
        
    - Policies and regulations.
        
- **Enablers**: factors that make development easier or faster.
    
    - Advanced technology (cloud, AI).
        
    - Strong organizational capabilities (e.g., a team with many experienced Java developers).
        
    - Shared industry standards.
        

**Example**:  
A startup developing an IoT app:

- Constraint: low budget → can’t afford a large team.
    
- Enabler: cloud platforms like AWS IoT reduce infrastructure costs and speed up development.
    

---

#### (d) Opportunities and Risks

- **Risks**:
    
    - Technological failure.
        
    - Late release → losing market share.
        
    - Misjudging customer needs.
        
    - Compliance or tax issues.
        
- **Opportunities**:
    
    - New technologies (5G, AI, blockchain).
        
    - Growing market demand.
        
    - Leveraging existing organizational strengths.
        

**Risk analysis technique**:

- Review past **failure stories** in the organization.
    
- Ask: _“Could this happen again in our current project?”_
    

---

### 1.3 Usage Narratives

- An **informal story** that describes how the system will be used.
    
- Consists of: **character (persona)** + **goal** + **actions**.
    
- Helps capture **tacit requirements** that are hard to express in technical specifications.
    
- Often a precursor to formal **use cases**.
    

**Lecture Example**:

- Julie (a wildlife officer) wants to analyze five years of tracking data for a species of bandicoot in Sydney and compare it with bushfire patterns. She retrieves, sorts, and exports the data for statistical analysis.
    

**Real-world Example**:

- Persona: “Tom, 20 years old, student, wants to buy a bus ticket on the mobile app.”
    
- Narrative: Tom opens the app, selects a bus route, pays via digital wallet, and receives a QR code ticket.
    
- This narrative clarifies system needs before formalizing them into use cases.
## 2. Quality Attributes in Architecture
- **Functionality**: what the system does (its intended work).  
    → However, **functionality alone does not define the architecture**.
    
- Architectures are shaped primarily by **quality attributes** (non-functional requirements).
    
- Stakeholders rarely state non-functional requirements clearly → architects must uncover and balance them.
    
- Common **quality attributes**: availability, deployability, energy efficiency, modifiability, performance, security, testability, usability.
    

**Key point**: You can design many different architectures for the same functionality, but the quality attributes will determine which design is best.

---

### 2.1 Availability

- **Definition**: the system is available when needed, and can recover from failures.
    
- Includes reliability, robustness, recovery.
    
- Closely related to **performance** (slow system can seem unavailable) and **security** (DoS attack makes it unavailable).
    
- **Measurement**: “Five nines” = 99.999% uptime.
    

**Tactics & Patterns**:

- Redundancy: hot spare (active), warm spare (passive), cold spare.
    
- Triple Modular Redundancy (TMR).
    
- Retry tactic, Circuit breaker (Netflix OSS Hystrix).
    

**Example**:  
Banking systems keep redundant servers in different data centers. If one fails, another takes over immediately.

---

### 2.2 Deployability

- **Definition**: system can be deployed/rolled back **predictably and efficiently**.
    
- Important for **continuous delivery and DevOps**.
    
- **Pipeline**: Development → Integration → Staging → Production.
    
- **Metrics**:
    
    - Cycle time (speed of release).
        
    - Traceability (track what caused a bug).
        
    - Repeatability (consistent results in deployments).
        

**Patterns**:

- Microservices architecture.
    
- Blue/Green deployment.
    
- Rolling upgrades.
    
- Canary release, A/B testing.
    

**Example**:  
Facebook deploys new features to 1% of users (canary testing). If no errors occur, they expand to all users.

---

### 2.3 Energy Efficiency

- **Why important?**
    
    - Mobile devices, IoT, and cloud infrastructure → energy cost matters.
        
- Architects must balance energy efficiency with performance and availability.
    

**Patterns**:

- Sensor fusion (use low-power sensors first; only trigger high-power sensors when needed).
    
- Kill abnormal tasks (terminate power-hungry apps).
    
- Power monitor (turn off unused devices or interfaces).
    

**Example**:  
Smartphones disable GPS and switch to Wi-Fi/cell-tower location when possible to save battery.

---

### 2.4 Modifiability

- **Definition**: system can be changed easily and at low cost.
    
- Flavors: scalability, variability, portability, location independence.
    

**Tactics**:

- Reduce **coupling** (dependencies between modules).
    
- Increase **cohesion** (modules have clear responsibilities).
    
- Flexible **binding times** (e.g., configuration at runtime rather than hard-coded).
    

**Patterns**:

- Client-server.
    
- Plug-in / Microkernel (extensions).
    
- Layers.
    
- Publish-subscribe (event-driven).
    

**Example**:  
Web browsers use **plug-in architecture** (extensions). This allows adding/removing functionality without modifying the browser core.

---

### 2.5 Performance

- **Definition**: ability to meet timing requirements.
    
- Measured in: latency, throughput, response time, memory efficiency.
    

**Tactics**:

- Reduce resource demand.
    
- Manage available resources better.
    

**Patterns**:

- Service Mesh (sidecar proxy, e.g., Istio).
    
- Load balancer (distributes requests).
    
- Throttling (limit number of requests).
    
- MapReduce (parallel processing for big data).
    

**Example**:  
Google Search uses **load balancing + MapReduce** to handle billions of queries per day.

---

### 2.6 Security

- **Definition**: protect data and systems from unauthorized access.
    
- **CIA triad**:
    
    - Confidentiality (data not leaked).
        
    - Integrity (data not altered incorrectly).
        
    - Availability (system remains usable).
        

**Patterns**:

- Intercepting Validator (check requests/messages).
    
- Intrusion Prevention System (detect and block attacks).
    

**Example**:  
Paypal applies intrusion detection and prevention systems to block fraudulent transactions in real time.

---

### 2.7 Testability

- **Definition**: system makes faults easy to reveal, replicate, and isolate.
    
- Reduces overall testing cost.
    

**Patterns**:

- Dependency Injection (separates behavior from dependencies).
    
- Strategy Pattern (swap algorithms at runtime, use test versions).
    
- Intercepting Filter (insert test logic without changing system code).
    

**Example**:  
Spring Framework uses **dependency injection**, which makes unit testing much easier.

---

### 2.8 Usability

- **Definition**: how easy it is for users to accomplish tasks and feel satisfied.
    
- Includes: learning curve, efficiency, error recovery, adaptability, satisfaction.
    

**Tactics**:

- Support user initiative (undo, cancel, pause, resume).
    
- Support system initiative (predictive typing, progress bars, UI customization).
    

**Patterns**:

- Model-View-Controller (MVC).
    
- Observer (UI updates when data changes).
    
- Memento (undo/redo functionality).
    

**Example**:

- Microsoft Word uses the **Memento pattern** to allow undo/redo.
    
- Search engines use **predictive typing** to enhance usability.
## Solution architecture vs. Enterprise architecture
### 1. Solution Architecture

It’s like when you **build a private house**.  
You need to know:

- What the owner wants (a big living room, 3 bedrooms, a garage).
    
- What materials to use (bricks, cement, steel).
    
- How to arrange it (first floor, second floor).
    

The **Solution Architect** is like the architect of that house:

- Draws the blueprint.
    
- Chooses the materials.
    
- Supervises the construction team to ensure the house is built according to the plan.
    

→ Solution Architecture focuses only on a **specific and short-term project**.

**Example in IT**:  
A company wants to build a **mobile banking application**. The solution architect will design this app:

- The user interface.
    
- The connection with the core banking system.
    
- The choice of technologies (Java, PostgreSQL, Kubernetes).
    
- Supervise the development process.
    

---

### 2. Enterprise Architecture

It’s like when you **plan an entire city**.  
You need to consider:

- The city’s development vision for the next 10–20 years.
    
- Roads, electricity, water, parks, hospitals, schools.
    
- Every house must fit into the city’s overall master plan.
    

The **Enterprise Architect** is like the city planner:

- Ensures no one builds a house blocking a road.
    
- Ensures every building aligns with the long-term strategy.
    
- Considers whether new technologies fit with the overall direction.
    

→ Enterprise Architecture focuses on the **entire organization**, in a **long-term and continuous** way.

**Example in IT**:  
That same bank doesn’t just have a mobile banking app, but also:

- A CRM system (customer management).
    
- A data warehouse system.
    
- Security and risk management systems.
    

The enterprise architect will make sure **all these systems connect smoothly**, align with the strategy of international expansion, comply with legal regulations, and remain easy to upgrade in the future.