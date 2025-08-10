### What is Requirements Engineering?
Requirements Engineering is the process of identifying, analysing, documenting, and managing software requirements.
**Role:**
- Foundation of software development.
- Ensures the product meets needs and quality standards.
- Reduces the risk of failure, cost overruns, and delays.
### Types of Requirements
#### 1. Functional Requirements

- **Definition**: Describe the **functions and tasks** the software must perform.
    
- **Question answered**: _What will the software do?_
    
- **Characteristics**:
    
    - Directly related to the behaviour of the system.
        
    - Often expressed in **use cases**, **user stories**, or business process descriptions.
        
- **Examples**:
    
    1. Allow users to log in with email/password.
        
    2. Calculate order totals and apply discount codes.
        
    3. Generate monthly sales reports.
        

---

#### 2. Non-functional Requirements

- **Definition**: Describe the **quality attributes** and **constraints** the system must meet.
    
- **Question answered**: _How well will the system perform?_ or _Under what conditions?_
    
- **Common categories**:
    
    - **Performance**: Response time < 2 seconds.
        
    - **Reliability**: System uptime of 99.9%.
        
    - **Security**: Data encrypted using AES-256.
        
    - **Usability**: New users can complete main tasks within 5 minutes.
        
    - **Maintainability**: Code follows Google Java Style Guide.
        
    - **Scalability**: Support growth from 1,000 to 10,000 concurrent users.
        

---

#### 3. User Requirements

- **Definition**: Needs, expectations, and priorities of **end-users or stakeholders**.
    
- **Goal**: Ensure the product matches the desired user experience.
    
- **Examples**:
    
    - The app must be easy to use on mobile devices.
        
    - Dark mode option for user comfort.
        

---

#### 4. System Requirements

- **Definition**: Technical requirements for the software to operate effectively.
    
- **Examples**:
    
    - Server must run on Ubuntu 22.04.
        
    - Minimum 8GB RAM.
        
    - Network speed of at least 10Mbps.
        
    - Java 17 installed.
        

---

#### 5. Business Requirements

- **Definition**: Goals, rules, and constraints from the organisation or business perspective.
    
- **Examples**:
    
    - Must comply with PCI-DSS standards for credit card processing.
        
    - Total development cost must not exceed $8,000.
        
    - Must launch before Q4 to meet peak season demand.
### Requirements Elicitation (Thu thập yêu cầu)
#### 1. Definition
- **Requirements Elicitation** is the process of **gathering information** from stakeholders and other sources to understand what the software system should do.
    
- It’s not just “asking questions” — it’s about **discovering, exploring, and clarifying** the needs, constraints, and expectations.
    

---

#### 2. Purpose

- Build a **clear and shared understanding** of requirements.
    
- Identify both **explicit needs** (what users say they want) and **implicit needs** (what they don’t state but are essential).
    
- Reduce misunderstandings and incorrect assumptions.
    

---

#### 3. Common Elicitation Techniques

##### a) Interviews

- **Description**: One-on-one or small-group sessions with stakeholders.
    
- **When to use**:
    
    - When you need in-depth information.
        
    - When requirements are complex or sensitive.
        
- **Advantages**:
    
    - Allows follow-up questions.
        
    - Builds rapport with stakeholders.
        
- **Disadvantages**:
    
    - Time-consuming.
        
    - Limited coverage if many stakeholders exist.
        

---

##### b) Questionnaires / Surveys

- **Description**: Written questions sent to multiple stakeholders.
    
- **When to use**:
    
    - When you need input from a large audience.
        
    - When you want to quantify opinions or preferences.
        
- **Advantages**:
    
    - Quick distribution to many people.
        
    - Standardised format makes analysis easier.
        
- **Disadvantages**:
    
    - Limited ability to clarify answers.
        
    - Risk of low response rate.
        

---

##### c) Observation

- **Description**: Watching users perform their work in the real environment.
    
- **When to use**:
    
    - When processes are **routine but not well-documented**.
        
    - When users cannot easily describe their workflow.
        
- **Advantages**:
    
    - Reveals real-world behaviour and pain points.
        
    - Identifies workarounds users may not mention.
        
- **Disadvantages**:
    
    - Can be intrusive.
        
    - May cause users to change behaviour while being observed.
        

---

##### d) Focus Groups

- **Description**: Group discussion with selected stakeholders led by a facilitator.
    
- **When to use**:
    
    - When brainstorming ideas.
        
    - When you need consensus quickly.
        
- **Advantages**:
    
    - Encourages discussion and idea sharing.
        
    - Can expose conflicting needs early.
        
- **Disadvantages**:
    
    - Risk of dominant voices overshadowing others.
        
    - Requires skilled facilitation.
        

---

##### e) Brainstorming

- **Description**: Open idea-generation session without judgement.
    
- **When to use**:
    
    - Early in the project to explore all possible solutions.
        
- **Advantages**:
    
    - Encourages creativity.
        
    - Generates many options quickly.
        
- **Disadvantages**:
    
    - Can produce irrelevant ideas.
        
    - Needs follow-up analysis to refine ideas.
        

---

#### 4. Best Practices for Elicitation

1. **Identify all stakeholder groups** early (clients, users, technical staff, management).
    
2. **Prepare questions in advance** but remain flexible.
    
3. **Use multiple techniques** — one method rarely captures all requirements.
    
4. **Document immediately** after sessions.
    
5. **Confirm understanding** with stakeholders (validation).
### Requirements Analysis & Specification
#### 1. Definition
- **Requirements Analysis**: The process of working with information collected during **elicitation** to:
    
    - Clarify details.
        
    - Remove conflicts.
        
    - Determine priorities.
        
    - Turn vague needs into clear, testable requirements.
        
- **Requirements Specification**: Documenting requirements in a **formal, structured format** to be used as the basis for design, development, and testing.
    

---
#### 2. Objectives

- Ensure **all stakeholders share the same understanding** of requirements.
    
- Identify **all necessary functions and constraints**.
    
- Create documentation that serves as a **contract** between the client and the development team.
#### 3. Key Activities
##### a) Requirements Analysis

- **Classify requirements**: functional, non-functional, business, system.
    
- **Find relationships and dependencies** between requirements.
    
- **Remove conflicts** between stakeholders’ needs.
    
- **Prioritise**:
    
    - Must-have (essential).
        
    - Should-have (important but not critical).
        
    - Nice-to-have (optional).
        
- **Check feasibility**:
    
    - Technical feasibility.
        
    - Schedule feasibility.
        
    - Cost feasibility.
##### b) Analysis Techniques 
###### 1. Scenario
- **Definition**:  
    A short, descriptive story showing **how a user interacts with the system** in a specific situation.
- **Purpose**:
    
    - Makes requirements more **realistic** by showing them in context.
        
    - Helps discover hidden requirements.
        
- **Structure**:
    
    1. Actors involved.
        
    2. Starting situation.
        
    3. Sequence of actions.
        
    4. Expected result.
        
- **Example** (Online Shopping):  
    _A registered user logs in, searches for “wireless headphones,” adds them to the cart, and checks out using PayPal._
---
###### 2. User Story

- **Definition**:  
    A short, simple sentence that captures a specific user need from their perspective.
    
- **Format**:  
    **As a [type of user], I want [goal] so that [benefit].**
    
- **Purpose**:
    
    - Focuses on **value to the user** rather than technical details.
        
    - Often used in Agile development.
        
- **Example**:
    
    - _As a shopper, I want to filter products by price so that I can quickly find items within my budget._
###### 3. Use Case Diagram
![[Use Case Diagram.png]]
**Definition**
- A **Use Case Diagram** is a visual representation that shows:
    1. **What functions** the system provides (**use cases**).
    2. **Who** interacts with those functions (**actors**).
- It’s part of **Unified Modeling Language (UML)**, commonly used in **requirements analysis**.
- Provide a **big-picture overview** of system functionality.
- Show the **boundaries** between the system and the outside world.
- Help communicate with stakeholders (especially non-technical ones) because it’s **simple and easy to understand**.
- Serve as a starting point for creating **detailed use case descriptions**.
    
---
 **Key Components**
 **a) Actor**
- **Definition**: An entity that interacts with the system (can be a person, another system, or an organisation).
- **Types**:
    1. **Primary actor** – initiates interaction to achieve a goal (e.g., Customer).
        
    2. **Secondary actor** – supports the system in achieving the goal (e.g., Payment Gateway).       
- **Notation**: Stick figure.                                  
---
 **b) Use Case**
- **Definition**: A specific function or goal the system provides for an actor.
- **Notation**: Oval shape with the name of the function inside.
- **Example**: _Place Order_, _Login_, _Search Product_.
---
**c) System Boundary**
- **Definition**: A rectangle that encloses all the use cases to show the scope of the system.
    
- **Purpose**: Clarifies which functions are part of the system and which are external.
    
---
**d) Association**
- **Definition**: A line connecting an actor to a use case they interact with.
    
- **Meaning**: Shows communication between the actor and the function.
    

---

**e) Relationships Between Use Cases**
- **Include** (<<include>>):
    
    - One use case **always** uses the behaviour of another.
        
    - Example: _Place Order_ **includes** _Process Payment_.
        
- **Extend** (<<extend>>):
    
    - A use case may optionally add behaviour to another.
        
    - Example: _Checkout_ **extends** _Place Order_ with _Apply Discount_.
        
- **Generalisation**:
    
    - One actor or use case is a specialised version of another.
        
    - Example: Actor _Admin_ is a specialisation of Actor _User_.
---
**4. How to Create a Use Case Diagram**
		1. **Identify actors** – Who or what will interact with the system?
			
		2. **Identify main use cases** – What does each actor want from the system?
			
		3. **Draw the system boundary** – Mark the scope clearly.
			
		4. **Connect actors and use cases** – Use associations.
			
		5. **Add relationships** – <<include>>, <<extend>>, generalisation if needed.
			
---
 **5. Diagram Tips**
	 **A. Identifying Elements**
	1. **Actor**:
		
		- Think of **roles**, not specific names.
			
		- Example: “Customer” instead of “John Smith”.
			
	2. **Use Case**:
		
		- Keep names **short** and use **verb + noun** format.
			
		- Example: “Book Room”, “Process Order”.
			
	3. **System Boundary**:
		
		- Clearly define what’s **inside** (system scope) and **outside** (external).
			
	
	---
	
	 **B. Layout Tips**
	
	- Place actors **outside** the system boundary (usually left or right side).
		
	- Place use cases **inside** the system boundary.
		
	- Keep association lines straight — avoid too many crossings.
		
	- Group related use cases together.
		
	
	---
	
	 **C. Using Relationships**
	
	- **Include**:
		
		- Use when one function **always requires** another.
			
		- Example: _Checkout_ **include** _Verify Payment_.
			
	- **Extend**:
		
		- Use when a function is **optional or conditional**.
			
		- Example: _Place Order_ **extend** _Apply Discount_.
			
	- **Generalisation**:
		
		- Use when an actor or use case is a **specialised version** of another.
			
		- Example: Actor _Admin_ inherits from Actor _User_.
###### 4. Use case
**1. Definition**
- A **Use Case** is a description of **how a user (actor)** interacts with a system to achieve a specific goal.
    
- It focuses on **what the system does** from the user’s perspective, **not** how it is implemented.
    
- Usually written as a **narrative** or **structured steps**.
---
 **2. Purpose**

- Capture **functional requirements** in a way that’s easy for both technical and non-technical people to understand.
- Show all possible interactions between users and the system.
- Serve as a basis for:
    
    - Writing test cases.
        
    - Designing system functions.
        
    - Estimating project scope.
---
 **3. Key Components of a Use Case**
	a. **Use Case Name** – Short and clear, using _verb + noun_.  
		_Example: “Place Order”, “Search Product”_.
		
	b. **Actors** – Who interacts with the system in this use case.
		
	c. **Goal/Purpose** – What the actor wants to achieve.
		
	d. **Preconditions** – What must be true before the use case starts.
		
	e. **Main Flow (Basic Flow)** – The normal sequence of steps from start to goal.
		
	f. **Alternate Flows** – Variations in steps (e.g., user cancels order).
		
	g. **Exception Flows** – What happens if there is an error or failure.
		
	h. **Postconditions** – What must be true after the use case ends.
		

---

**4. Example – “Place Order”**
	**Use Case Name**: Place Order  
	**Actor**: Customer  
	**Goal**: Customer completes an online purchase.  
	**Preconditions**: Customer is logged in; items are in cart.
	
	**Main Flow**:
	
	1. Customer clicks “Checkout”.
		
	2. System displays order summary.
		
	3. Customer enters delivery address.
		
	4. Customer selects payment method.
		
	5. System processes payment.
		
	6. System confirms order and shows order number.
		
	
	**Alternate Flow**:
	
	- If customer chooses “Cash on Delivery”, skip payment processing step.
		
	
	**Exception Flow**:
	
	- If payment fails, system displays an error and returns to payment step.
		
	
	**Postconditions**:
	
	- Order is stored in the database.
		
	- Confirmation email is sent.
		

---
