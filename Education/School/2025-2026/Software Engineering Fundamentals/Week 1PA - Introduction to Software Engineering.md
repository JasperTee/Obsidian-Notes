### What is Software Engineering?
- A **systematic approach** to developing software.
- That means you follow a structured plan and defined steps — not just coding randomly.
- Goal: create **reliable** and **high-quality** software systems.
### Scope Of Software Engineering
The **scope of software engineering** means the range of activities, areas, and responsibilities that software engineering covers from start to finish of a software product’s life.  
It is broader than just writing code — it includes everything needed to make the software **successful, reliable, and maintainable**.
#### **1. Software Design**
- **Meaning**: The blueprint of the software, showing how the system will be **structured** and **organized**.
- **Goal**: Ensure the system is easy to scale, easy to maintain, and meets requirements.
- **Key aspects**:
    - **Functionality**: What the software does (e.g., booking flights, processing payments).
        
    - **Modularity**: Breaking into independent modules (e.g., payment module, search module).
        
    - **Scalability**: Able to handle more users or data in the future.
        
    - **Maintainability**: Easy to fix bugs or add features.
        
- **Example**: Designing an online ticket booking system with modules for search, payment, and email confirmation.
---
#### **2. Software Development**
- **Meaning**: Turning the design into a working software system.
- **Main activities**:
    - Writing code according to standards.

    - Applying **best practices** so the code is clean and maintainable.
        
    - Using proper tools and technologies (IDE, frameworks, version control).
        
- **Example**: Coding the flight search page using Java + Spring Boot for backend, React for frontend.
---
#### **3. Software Testing**
- **Meaning**: Ensuring the software **works correctly** and **meets requirements**.
- **Activities**:
    
    - **Verification**: Checking if the system was built according to the design.
        
    - **Validation**: Checking if it meets user needs.
        
- **Example**: Testing if booking a ticket sends an email confirmation and if payment processes quickly.
---

#### **4. Software Maintenance**
- **Meaning**: Supporting and improving the software after it is deployed.
- **Activities**:
    
    - Fixing bugs.
        
    - Adding new features.
        
    - Improving performance and security.
        
- **Example**: After launching the ticket booking system, adding a seat selection feature and upgrading to handle 10,000 bookings at the same time.
---
#### **5. Project Management**
- **Meaning**: Coordinating the entire software development process.
- **Main activities**:
    
    - Planning schedule and budget.
        
    - Allocating people and resources.
        
    - Managing risks and ensuring quality.
        
- **Example**: Managing the ticket booking system project to finish within 6 months, stay under budget, and meet client requirements.
### Challenges Of Software Development
#### **1. Dealing with Changing Requirements**
- **The challenge**:
    
    - In most projects, requirements **change over time** due to new ideas, user feedback, or business shifts.
        
    - Adapting to these changes while keeping the **scope**, **timeline**, and **budget** under control is difficult.
        
- **How to address it**:
    
    - **Iterative and incremental development** – deliver the product in small parts so it’s easier to adjust.
        
    - **Frequent communication** with stakeholders – make sure everyone is aligned.
        
    - **Agile methodologies** – provide flexibility and encourage quick responses to changes.
        
- **Benefit**:
    
    - Greater adaptability, continuous feedback, and improved collaboration help manage changes effectively.
---
#### **2. Maintaining Quality and Reliability**
- **The challenge**:
    
    - Users expect the software to be **high quality** and **reliable**.
        
    - It’s difficult to ensure no defects, stable performance, and smooth operation in all conditions.
        
- **How to address it**:
    
    - **Systematic testing** – test every part thoroughly.
        
    - **Code reviews** – detect and fix issues early.
        
    - **Continuous integration** – merge and test code regularly to avoid big issues later.
        
    - **Monitoring** – track system performance and errors after deployment.
        
- **Benefit**:
    
    - Early detection of issues, more robust software, and a better user experience.
---
#### **3. Managing Project Constraints**
- **The challenge**:
    
    - Every project faces limits in **time**, **budget**, **resources**, and **technology**.
        
    - Balancing these constraints while meeting goals is difficult.
        
- **How to address it**:
    
    - **Effective project planning** – realistic schedules and milestones.
        
    - **Resource allocation** – assign the right people and tools to the right tasks.
        
    - **Risk management** – identify and handle risks early.
        
    - **Prioritisation** – focus on the most important features first.
        
- **Benefit**:
    
    - Achieves a balance between limitations and desired outcomes, leading to a successful project.
### What is Software Development Life Cycle - SDLC?
![[What is Software Development Life Cycle - SDLC?.webp]]
- **Definition**:
    - A **guide** that gives structure to the software development process.
        
    - A **process model** made of phases that help create software systematically.
- **Purpose**:
    - Ensures the product meets both **user requirements** and **quality standards**.
---
#### Phases of SDLC
##### 1. Elicitation Phase
- **Goal**: Understand stakeholders’ needs and project scope.
- **Activities**:
    - Gather information.
    - Identify user needs.
    - Define project boundaries.
- **Deliverables**:
    - Requirements documents.
    - Use cases.
    - User stories.
---
##### 2. Analysis and Specification Phase
- **Goal**: Make requirements clear and unambiguous.
- **Activities**:
    - Analyse and refine gathered requirements.
    - Document in detail.
- **Deliverables**:
    - Functional requirements.
    - Non-functional requirements.
    - System specifications.
    - Software design documents.
---
##### 3. Design Phase
- **Goal**: Turn requirements into a technical plan.
- **Focus areas**:
    - System architecture.
    - Component design.
    - Database design.
- **Deliverables**:
    - Architecture diagrams.
    - Component specifications.
    - Database schemas.
---
##### 4. Construction Phase
- **Goal**: Build the working software system.
- **Activities**:
    - Coding.
    - Unit testing.
    - Writing code documentation.
- **Deliverables**:
    - Executable code.
    - Unit test cases.
    - Code documentation.
---
##### 5. Verification and Validation Phase
- **Goal**: Ensure the system meets requirements and works as expected.
- **Testing activities**:
    - Integration testing.
    - System testing.
    - User acceptance testing (UAT).
- **Deliverables**:
    - Test plans.
    - Test cases.
    - Defect reports.
---
##### 6. Deployment Phase
- **Goal**: Release the system into the production environment.
- **Activities**:
    - Installation.
    - Configuration.
    - User training.
- **Deliverables**:
    - Deployed software.
    - User manuals.
    - Support documentation.
#### SDLC Methodologies
- Many different methodologies exist for software system development. 
- Each has its own strengths and weaknesses.
- There’s no  “good” or “bad” methodology — the best choice depends on project needs and organizational context.
##### Waterfall Model
![[Waterfall Model.png]]
- **Waterfall Model** is a **sequential** software development model where phases are carried out from top to bottom like a waterfall.  
- Each phase must be completed before moving to the next, and it is very difficult to go back and modify a previous phase once it is finished.
---
###### 1. Key Characteristics
- **Linear process**: steps are executed in a fixed order.
- **Complete one phase** before starting the next.
- **Hard to change** once a phase is completed.
---
###### 2. Phases 
1. **Project Initiation** – Start and approve the project.
2. **Project Planning** – Create and freeze the project plan.
3. **Analysis** – Define and freeze the requirement specifications.
4. **Design** – Create and freeze the design specifications.
5. **Implementation** – Develop and implement the code according to the design.
6. **Deployment** – Install and deliver the product to the end users.
---
###### 3. Advantages
- **Clear structure**, easy to follow and manage progress.
- Suitable when **requirements are clear and stable** from the start.
- Produces detailed documentation for each phase.
---
###### 4. Disadvantages
- **Not flexible** when requirements change.
- If errors are found in earlier phases, fixing them is **time-consuming and costly**.
- Users only see the final product, making early feedback difficult.
#####  Iterative models
![[Iterative models.png]]
**Iterative Models** in SDLC, such as the **Spiral Model**, focus on repeating the development process in cycles (iterations) to improve the product step-by-step.

---
###### 1. Key Characteristics
- Development happens in **multiple iterations** instead of a single pass.
- Each iteration includes development, testing, and feedback for improvement.
- Emphasis on:
    
    - **Early prototyping** – building an early version to test ideas.
        
    - **Incremental deliveries** – releasing working parts of the system step-by-step.
        
    - **Risk management** – identifying and addressing potential risks early.
        

---
###### 2. Main Steps in the Spiral Model

1. **Determine objectives** – Define the goals for the current iteration.
    
2. **Identify and resolve risks** – Analyse and address risks (technical, cost, unclear requirements).
    
3. **Development and Test** – Build and test the software for this iteration.
    
4. **Plan the next iteration** – Adjust plans based on feedback and lessons learned.
    

---

###### 3. Advantages

- Reduces risk through regular evaluation and resolution.
    
- Produces early working versions for customer review.
    
- Adapts easily to changing requirements.
---

###### 4. Disadvantages
- Can take more time and cost more if not managed well.
- Requires a team with experience in **risk management** and **iteration planning**.
##### Agile Methodologies
![[Agile Methodologies.png]]
- **Definition**: An **iterative** and **incremental** software development approach.
- **Structure**: Work is divided into short cycles called **Sprints** (usually 1–4 weeks).
- **Sprint activities**: Plan → Design → Develop → Test → Deploy → Review.
###### 1. Key characteristics:
- **Customer/stakeholder collaboration** – frequent involvement and feedback.
- **Adaptability** – can quickly adjust direction when requirements change.
###### 2.Advantages:
-  Early usable product.
- Flexibility to handle changes.
- Clear visibility of progress for customers.
###### 3.Limitations:
- Requires regular customer participation.
- Demands strong self-management and teamwork skills.
###### Agile Scrum (Framework within Agile)**
- **Approach**:
    - Uses an **empirical approach** – accepts that problems can’t be fully defined upfront.
    - Focuses on delivering value quickly.
    - Always ready to adapt to new or changing requirements.
- **Strengths**:
    - **Deliver quickly** – rapid delivery of usable product increments.
    - **Respond to emerging requirements** – highly flexible to new needs.
- **Difference from Agile in general**:
    - Agile is a **philosophy/methodology**.
    - Scrum is a **concrete framework** with defined roles, rules, and events (e.g., Sprint, Daily Scrum, Sprint Review, Sprint Retrospective).
### What Are Software Requirements?
Software requirements describe:
- **What** a software system should do.
- **How** it should behave.
- **Features** it should have.
**Purpose**:
- Ensure a **shared understanding** between stakeholders and developers.
- Act as a **communication tool** to align business needs with technical work.
---
#### Main Types of Requirements
**a) Functional Requirements**
- Define **what the system should do** — the actual features and capabilities.
- Examples:
    - User authentication.
    - Data input and output.
    - Performing calculations.
    - Data processing.

**b) Non-Functional Requirements**
- Define **how well** the system should perform, focusing on quality attributes and constraints.
- Areas:
    - Reliability
    - Performance
    - Security
    - Usability
    - Maintainability
- Examples:
    - Response time < 2 seconds.
    - 99.9% system availability.
    - Data encryption for privacy.
    - Intuitive UI design.
    - Ability to scale to more users.
---
#### **Other Requirement Types**
1. **User Requirements** – Needs, preferences, and expectations of the end-user or stakeholders.    
2. **System Requirements** – Hardware, software, network, and other technical needs for the software to run effectively.
3. **Business Requirements** – Goals, objectives, and constraints from a business perspective (e.g., cost limits, market demands, regulatory compliance).
---
### Stakeholders in Software Development
- **Clients** – Fund or request the software.
- **End-Users** – Directly use the software.
- **Project Managers** – Plan, organise, and oversee the project.
- **Software Engineers** – Design, develop, and implement the system.
- **Quality Assurance Professionals** – Ensure the system is reliable and meets standards.
- **Domain Experts** – Provide industry-specific knowledge to ensure the system fits its intended use.
#### Perspectives and Expectations
Involving stakeholders early and throughout the process ensures their perspectives and expectations are considered, reducing misunderstandings and mismatches later.

---
### Importance of Software Engineering Standards and Best Practices
 **a) Coding Conventions**
- A set of **rules and guidelines** for writing code in a consistent style.
- Benefits:
    - **Enhance Code Quality** – fewer errors, more structured code.
    - **Improve Readability** – easier for other developers to understand.
    - **Ensure Maintainability** – easier to update and fix later.

**Common Coding Conventions**:
- **Naming Conventions** – Consistent and descriptive names for variables, functions, classes.
- **Indentation & Formatting** – Standard code alignment for clarity.
- **Commenting Practices** – Explain complex logic.
- **Code Structure & Organisation** – Logical arrangement of modules and files
- Example: **Google Java Style Guide**.
    
**b) Documentation**
- Records and communicates information about the software (requirements, design, functionality, usage).
- Benefits:
    - **Facilitates Understanding** – for developers and stakeholders.
    - **Supports Maintenance** – easier to fix or upgrade.
    - **Enables Future Enhancements** – serves as a reference.

**Types of Documentation**:
1. **Requirements Documents** – Define the system’s intended functionality.
2. **Design Documents** – Describe architecture, structure, and internal components.
3. **User Manuals** – Instructions for end-users.
4. **API Documentation** – Technical reference for developers using system interfaces.
---
**c) Peer Review**
- Collaborative evaluation of software artefacts by team members.
- Benefits:
    - Identify defects early.
    - Improve code and design quality.
    - Share knowledge among the team.

**Types**:
- **Code Reviews** – Evaluate source code for errors and improvements.
- **Design Reviews** – Assess architecture and design decisions.
- **Document Reviews** – Check documentation for accuracy and clarity.