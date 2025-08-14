## 1. Types of Data

### **1.1 Structured Data**
![[Structured Data.png]]
- **Definition**:  
    Data stored in a **predefined tabular format** with rows and columns, typically in **relational databases**.
    
- **Characteristics**:
    
    - Each row is a record, each column holds a specific attribute.
        
    - Schema (structure) is fixed.
        
    - Querying is done with **SQL**.
        
- **Lecture Example**:  
    Table of journal articles: Title, Journal, Volume, Issue, Date, Pages.
    
- **Advantages**:
    
    - High accuracy and consistency.
        
    - Easy to maintain, backup, and integrate.
        
    - Mature tools and strong query support.
        
- **Limitations**:
    
    - Rigid structure, hard to handle rapidly changing data formats.
        
- **Applications**:
    
    - Banking transactions, retail sales data, employee records.
        

---

### **1.2 Semi-structured Data**
![[Semi-structured data.png]]
- **Definition**:  
    Data that doesn’t fit perfectly into tables but has **tags, markers, or keys** that make it self-describing.
    
- **Common Formats**: XML, JSON, YAML.
    
- **Characteristics**:
    
    - Flexible schema, not all records must have the same attributes.
        
    - Self-describing — each field has its own label.
- **Advantages**:
    
    - Easier to evolve as needs change.
        
    - Works well for data exchange between systems.
        
- **Limitations**:
    
    - Slower queries compared to structured data.
        
    - Needs parsing and validation for consistency.
        
- **Applications**:
    
    - API responses, system configurations, cross-platform data exchange.
        

---

### **1.3 Unstructured Data**
![[Unstructured Data.png]]
- **Definition**:  
    Data without a predefined data model or organization.
    
- **Examples**:
    
    - Emails, PDF files, Word documents.
        
    - Social media posts, chat messages.
        
    - Raw server logs.
        
- **Advantages**:
    
    - Can store any content type.
        
    - Rich in detail and context.
        
- **Limitations**:
    
    - Hard to search and analyze directly.
        
    - Often requires AI, NLP, or data preprocessing.
        
- **Applications**:
    
    - Sentiment analysis, document archiving, legal discovery.
        

---

### **1.4 Spatial Data**
![[Spatial Data.png]]
- **Definition**:  
    Data that includes a geographic or spatial component.
    
- **Examples**:
    
    - GIS (Geographic Information System) data.
        
    - GPS coordinates.
        
    - Satellite images, maps.
        
- **Advantages**:
    
    - Enables location-based insights and analysis.
        
- **Limitations**:
    
    - Large storage requirements.
        
    - Needs specialized tools (ArcGIS, PostGIS).
        
- **Applications**:
    
    - Logistics optimization, city planning, environmental monitoring.
        

---

### **1.5 Time Series Data**
![[Time Series Data.png]]
- **Definition**:  
    Data collected and stored over time to capture changes and trends.
    

#### **Type 1: Regular Interval Time Series**

- **Characteristics**:
    
    - Data recorded at consistent, fixed intervals.
        
    - Easy to handle with statistical methods and time series databases.
        
- **Lecture Examples**:
    
    - Hourly weather readings.
        
    - Daily closing stock prices.
        
    - Sensor readings every second.
        
- **Advantages**:
    
    - Easy to analyze and visualize.
        
    - Supports trend detection and forecasting.
        
- **Limitations**:
    
    - Can produce redundant data if no change occurs between intervals.
        

#### **Type 2: Irregular Interval Time Series**

- **Characteristics**:
    
    - Data recorded only when an event occurs.
        
    - Time gaps between data points are inconsistent.
        
- **Lecture Examples**:
    
    - GPS tracking when position changes.
        
    - Log entries on system errors.
        
    - Sensor reports when thresholds are exceeded.
        
- **Advantages**:
    
    - Efficient storage and transmission.
        
    - Captures only relevant events.
        
- **Limitations**:
    
    - Harder to apply certain statistical models (may need resampling).
        

---

### **1.6 Graph Data**
![[Graph Data.png]]
- **Definition**:  
    Data stored as nodes (entities) and edges (relationships).
    
- **Examples**:
    
    - Social media networks (user-to-user connections).
        
    - Fraud detection (transactions and their relationships).
        
- **Advantages**:
    
    - Efficient for relationship-based queries.
        
    - Good for traversing connected data.
        
- **Limitations**:
    
    - Requires specialized databases (Neo4j, OrientDB).
        
- **Applications**:
    
    - Recommendation engines, supply chain mapping.
        

---

### **1.7 Multimedia Data**
![[Multimedia Data.png]]
- **Definition**:  
    Data in image, video, audio, or graphics format.
    
- **Examples**:
    
    - Digital photos, surveillance videos, audio recordings.
        
- **Advantages**:
    
    - Highly engaging and rich in information.
        
- **Limitations**:
    
    - Large file sizes require high storage and processing capacity.
        
- **Applications**:
    
    - Media streaming, advertising, facial recognition, voice analytics.
## 2. Data Architecture 
### 2.1 Concepts
Data Architecture is the **“overall blueprint”** for the entire lifecycle of data within an organization.  
It specifies **where the data comes from, where it is stored, how it is processed, and how it is ultimately used**.

If we think of data as raw materials, then Data Architecture is like a factory assembly line that ensures the raw materials go through the right paths, are processed correctly, and result in high-quality finished products.

---
### 2.2 Role
- Connects data from various sources into a **unified system**.
    
- Ensures **high-quality data** – accurate, complete, consistent, and ready for use.
    
- Supports decision-making based on **processed and analyzed data**.
    
- Reduces cost and risk by **optimizing data flows** and implementing **centralized governance**
### 2.3 Main Layers in Data Architecture

#### 2.3.1 Data Sources (Nguồn dữ liệu)

This is where **all the raw data originates**.  
Think of it as the “input warehouse” of your factory.

- **Transactional Databases** – Data from applications that handle day-to-day transactions (e.g., sales systems, banking systems).
    
- **Log Files** – Records of system activity, user actions, and error tracking.
    
- **Applications** – Business software like CRM, ERP that generate data.
    
- **IoT Sensors** – Devices that collect environmental readings like temperature, location, machine status.
    
- **APIs** – Data pulled from other systems or platforms via programmatic access.
    
- **Third-party Data** – Data purchased or received from external providers, such as market research or demographic data.
    

💡 _In short: This is the “raw ingredient” stage before any cleaning or processing happens._

---

#### 2.3.2 Operational Data Layer (Lớp dữ liệu vận hành)

The **working area** where data is stored and accessed for **real-time business operations**.

- Usually based on **OLTP (Online Transaction Processing)** systems.
    
- Handles frequent updates, inserts, and queries.
    
- Focuses on **speed and accuracy** to support day-to-day activities like order entry, banking transactions, or inventory updates.
    

💡 _Analogy: This is like the “production floor” where materials are actively used in daily operations._

---

#### 2.3.3 Ingestion & Staging Layer (Lớp tiếp nhận và lưu tạm)

A **temporary holding area** for raw data before it is processed.

- **Data Ingestion**: Pulling in data from multiple sources.
    
- **Staging**: Storing that data in its raw form without altering it.
    
- Allows data engineers to **validate quality** before it moves forward.
    
- Protects **original, unmodified copies** for backup and auditing.
    

💡 _Analogy: This is the “receiving dock” where goods arrive and are checked before being sent into production._

---

#### 2.3.4 Integration & Transformation Layer (Lớp tích hợp và chuyển đổi)

This is where **data cleaning, merging, and formatting** happens.

- **Integration**: Combine data from multiple sources into one consistent format.
    
- **Transformation**: Change data structure, remove duplicates, standardize units, fix missing values.
    
- Ensures data is **accurate, consistent, and analysis-ready**.
    

💡 _Analogy: This is the “quality control & assembly area” where raw parts are processed into usable components._

---

#### 2.3.5 Analytics Data Layer (Lớp phân tích dữ liệu)

A **centralized storage** for cleaned and structured data ready for reporting and analysis.

- Often implemented as **Data Warehouse** or **Data Mart**.
    
- Stores **historical data** for trend analysis and strategic planning.
    
- Supports **OLAP (Online Analytical Processing)** for deep analysis and querying.
    

💡 _Analogy: This is the “finished goods warehouse” where products are ready to be shipped to customers (in this case, the customers are analysts and decision-makers)._

---

#### 2.3.6 Business Intelligence (BI) Layer (Lớp thông tin kinh doanh)

The **user-facing layer** where decision-makers interact with the data.

- Provides **dashboards**, **reports**, and **data visualizations**.
    
- Tools like **Power BI, Tableau, Qlik** help managers and staff extract insights quickly.
    
- Supports **data-driven decision making** at all levels of the organization.
    

💡 _Analogy: This is the “storefront” where the final products are displayed and delivered to customers in the most usable form._

### 2.4 Components of Data Architecture
#### 2.4.1 Data Modelling

##### 2.4.1.1 Definition
Data Modelling is the process of **identifying, organising, and representing the structure of data** in a system so that it is clear, consistent, and understandable for both technical teams and business stakeholders.

- It defines **what data needs to be stored**, **how it relates to other data**, and **what business rules** apply.
    
- Think of it as the “blueprint” of the data system, similar to how an architectural drawing works for a building.
    

---

##### 2.4.1.2 Main Objectives

- Ensure **data consistency** across the entire system.
    
- Provide a **common language** for everyone involved in the project.
    
- Reduce errors during implementation by creating a complete, agreed-upon plan before coding.
    
- Create a foundation for query optimisation and data management.
    

---

##### 2.4.1.3 Three Levels of Data Modelling

###### a) Conceptual Data Model
![[Conceptual Data Model.png]]
- **Purpose:** Provide a big-picture view of the data in the system.
    
- **Focus:**
    
    - Identify **entities** (things we store information about) and **relationships** between them.
        
    - Does **not** define tables or database structures yet.
        
- **Characteristics:**
    
    - High-level, business-oriented.
        
    - Example: “Customer” places “Orders”.
        
    - May show relationships such as one-to-many or many-to-many, but not the exact table design.
        
- **When used:** Early in the project, to align understanding with stakeholders.
    

---
###### b) Logical Data Model
![[Logical Data Model.png]]
- **Purpose:** Turn the conceptual model into a more technical structure, but still **not tied to any specific technology**.
    
- **Focus:**
    
    - Define **attributes** for each entity.
        
    - Specify **primary keys (PK)** and **foreign keys (FK)** logically.
        
    - Show relationship cardinality (1:1, 1:N, M:N).
        
- **Characteristics:**
    
    - More detail than conceptual, but independent of the database platform.
        
    - Example: “Customer” table has `CustomerID`, `Name`, `Email`; “Order” table has `OrderID`, `CustomerID`, `OrderDate`.
        
- **When used:** After finalising the conceptual model, to prepare for database design.
    

---

###### c) Physical Data Model
![[Physical Data Model'.png]]
- **Purpose:** Implement the logical model into an **actual database structure** on a specific DBMS.
    
- **Focus:**
    
    - Create **real database tables**.
        
    - Define **exact data types** (`VARCHAR`, `INT`, `DATE`, etc.).
        
    - Add **indexes, constraints, partitions** for performance optimisation.
        
    - Set storage, backup, and user permissions.
        
- **Characteristics:**
    
    - Highly technical, depends on chosen technology (e.g., MySQL, PostgreSQL, Oracle).
        
    - Example:
        
        sql
        
        CopyEdit
        
        `CREATE TABLE Customers (   CustomerID INT PRIMARY KEY,   Name VARCHAR(100),   Email VARCHAR(100) );`
        
- **When used:** During implementation, before starting application development.
    

---

##### 2.4.1.4 Relationship Between the Three Levels

- **Conceptual:** Decides **WHAT** to store.
    
- **Logical:** Decides **HOW** to organise data logically.
    
- **Physical:** Decides **HOW** to implement it technically in the database.
    

---

##### 2.4.1.5 Benefits of Data Modelling

- Reduces misunderstandings between business and technical teams.
    
- Makes maintenance and future expansion easier.
    
- Enables accurate reporting and analytics.
    
- Improves system performance by optimising design early.
#### 2.4.2 Data Ingestion 
##### 2.4.2.1 Definition 
Data Ingestion is **the process of collecting and bringing data from multiple sources** into a centralized storage location (Data Destination) such as a Data Lake, Data Warehouse, or analytics platform for storage, processing, and analysis.

- It is the **first step** in a data pipeline.
    
- Can happen in **batch mode** or **real-time/streaming** mode.
##### 2.4.2.2 Purpose

- Bring **data from various sources** (databases, IoT devices, APIs, applications, external providers) into a centralised system.
    
- Ensure data is **captured in a consistent, accurate, and timely manner**.
    
- Support **real-time decision-making** or **batch processing** for reports and analytics.
    
---

##### 2.4.2.3 Types of Data Ingestion

1. **Batch Ingestion**
    
    - Data is collected and loaded at **scheduled intervals** (e.g., hourly, daily).
        
    - Best for large volumes of data that don’t require instant updates.
        
    - Example: Loading daily sales transactions from a store’s POS system to a central data warehouse at midnight.
        
2. **Real-Time (Streaming) Ingestion**
    
    - Data is ingested **continuously** as it is created or updated.
        
    - Useful for applications that require **instant insights**.
        
    - Example: Live stock price updates, IoT sensor readings, or social media feeds.
        
3. **Micro-Batch Ingestion**
    
    - Hybrid approach: very small batches processed frequently (e.g., every few minutes).
        
    - Balances speed with processing efficiency.
#####  2.4.2.4 General Workflow
Data ingestion typically follows one of two main patterns: **ETL** or **ELT**
###### a) ETL (Extract – Transform – Load)
**Definition of ETL (Extract – Transform – Load)**  
	ETL is a traditional data processing model, especially common for loading data into an **Enterprise Data Warehouse (EDW)**.  
	The process consists of three main steps:
	- **Extract**
		- Copy data from various source systems into a **staging area**.
		- Usually performed in **batch mode** (e.g., every hour, every day).
	- **Transform**
		- **Data cleansing** → remove errors, duplicates, and missing values.		
		- **Data enrichment** → add necessary supplementary information.
		- Convert structure and format so the data fits the **data warehouse schema**.
	- **Load**
		- Load the processed data into the tables of the **data warehouse**.
		
---

**Limitations of the ETL Model**
- Suitable only for **batch processing** → not optimized for **real-time data processing**.

- Rigid schema in EDW → difficult to change or adapt when the source data structure changes.
    
- Does not support **unstructured data** → data without a schema (unstructured) or binary data is difficult to load into EDW.
    
- Loss of data that cannot be loaded → if data can’t be loaded into EDW, it becomes unavailable for analysis.
    
- Loss of **lineage information** (data origin) → once loaded into EDW, the source history is not retained, making backtracking difficult.
    
---
**When to Use ETL?**

- When data is **stable** and schema changes are rare.
    
- When **real-time analytics** is not required.
    
- When strict **data control and standardization** is needed before storage.
######  b) ELT (Extract – Load – Transform)
**Definition of ELT**  
ELT is a variation of ETL, but the processing order changes: instead of **Extract → Transform → Load**, ELT performs **Extract → Load → Transform**.

**Steps in ELT:**

- **Extract and Load**
    
    - Data from multiple source systems is extracted and directly loaded into a **centralized repository**, often in the form of a **data lake**.
        
    - The data is stored in its **raw form** immediately upon loading, without any processing.
        
- **Transform**
    
    - When analysis is needed, the data in the data lake is **cleansed** (error removal, handling missing values), **enriched** (adding supplemental data), and **transformed** (structural and format changes).
        
    - The processed data is then sent to the most appropriate location for analysis, for example:
        
        - **Data Warehouse** (with clear tabular structure)
            
        - **NoSQL Database** (for unstructured data)
            

---

 **Advantages of ELT**

- **Preserves Raw Data** – Keeps all original data in the data lake, protecting historical records and **data lineage**(origin tracking).
    
- **Supports All Data Types** – Works with structured, semi-structured (JSON, XML), unstructured (text, images, videos), and binary data.
    
- **Flexible** – You can transform data only when needed, rather than before loading.
    
- **Faster Loading** – Since transformation is skipped during ingestion, large datasets can be loaded quickly.
    
- **Real-time Friendly** – Works well with streaming and real-time ingestion.
    

---

 **When to Use ELT**

- When you have **large volumes** of data from many sources.
    
- When you need to **retain raw historical data** for auditing, compliance, or future analysis.
    
- When your analytics environment needs to **handle diverse data types** (structured + unstructured).
    
- When you use **modern cloud-based platforms** that can store and process raw data at scale (e.g., Snowflake, Databricks, BigQuery).
###### c) ETL vs ELT 
 **1. Processing Order**
- **ETL**: Extract → **Transform** → Load
    
    - Data is cleaned and transformed **before** loading into the target system.
        
- **ELT**: Extract → **Load** → Transform
    
    - Data is loaded **first** in its raw form, then transformed **later** when needed.
        

---
 **2. Where the Transformation Happens**

- **ETL**: In a **separate ETL processing engine** before the data reaches the data warehouse.
    
- **ELT**: Inside the **target system** (data lake, cloud warehouse) after data is already stored.
    

---
 **3. Storage of Raw Data**

- **ETL**: Raw data is **not stored** — only processed data is kept in the data warehouse.
    
- **ELT**: Raw data is **stored and preserved**, which means you keep full historical records and lineage.
    

---
 **4. Data Types Supported**

- **ETL**: Mostly **structured data** (tabular, fixed schema).
    
- **ELT**: Can handle **structured, semi-structured, unstructured, and binary** data.
    

---
 **5. Speed and Flexibility**

- **ETL**: Slower to load large datasets because transformation happens first.
    
- **ELT**: Faster to load because transformation is skipped during ingestion, and more flexible since transformation can be done anytime.
    

---
 **6. Real-Time Capability**

- **ETL**: Mainly batch processing, not optimized for real-time.
    
- **ELT**: Works well with **real-time and streaming** data ingestion.
##### 2.4.2.5 Data Sources
Common types include:

- **Apache Kafka** (streaming platform)
    
- **JDBC** (database connectors)
    
- **Oracle CDC** (Change Data Capture)
    
- **HTTP Clients** (API data ingestion)
    
- **HDFS** (Hadoop Distributed File System)
    

---

##### 2.4.2.5 Data Destinations  
Common destinations include:

- **Apache Kafka** (for streaming pipelines)
    
- **JDBC** (to write into databases)
    
- **Snowflake** (cloud data warehouse)
    
- **Amazon S3** (cloud object storage)
    
- **Databricks** (big data analytics platform)
#### 2.4.3 Data Management Systems
##### 2.4.3.1 Definition
A **Data Management System** is a platform or set of tools that allows an organization to **store, manage, process, and retrieve data** efficiently.  
Its goal is to ensure that data is **accurate, complete, secure, easily accessible**, and **ready to support analysis and decision-making**.

---
##### 2.4.3.2 Main Components

###### a) Data Warehouse
1. **Definition**
A **Data Warehouse (DW)** is a **large-scale, centralized storage system** designed to **collect, store, and manage data**from multiple sources for the purpose of **analysis, reporting, and business intelligence (BI)**.  
Unlike operational databases, which are optimized for day-to-day transaction processing (OLTP), a DW is optimized for **querying large volumes of historical data** (OLAP – Online Analytical Processing).

---

2. **Purpose**

- **Integrate data** from multiple systems (ERP, CRM, sales databases, sensors, etc.) into a single, unified format.
    
- **Support decision-making** by providing accurate, consistent, and up-to-date analytical data.
    
- Allow **fast, complex queries** without affecting operational systems.
    
- Provide a **"single source of truth"** for the organization’s historical and analytical data.
    

---

 3. **Key Characteristics**

- **Structured Data Only** → Data must be cleaned, validated, and stored in a defined schema before loading.
    
- **Read-Optimized** → Designed for high-performance queries and analytics, not for frequent writes or updates.
    
- **Historical Focus** → Stores years of historical data for trend analysis and forecasting.
    
- **Centralized Repository** → All analytical data is stored in one place to ensure consistency.
    

---

 4. **Three-Tier Data Warehouse Architecture**

 **Tier 1 – Bottom Tier (Data Source Layer)**

- Data comes from **internal systems** (transaction databases, log files, etc.) and **external sources** (third-party data providers).
    
- **ETL process** (Extract → Transform → Load) cleans, standardizes, and prepares data.
    
- Data is stored in the **staging area** before being loaded into the warehouse.
    

 **Tier 2 – Middle Tier (Data Storage Layer)**

- **Central database** for storing processed, integrated data.
    
- Managed by a **Database Server** (often an OLAP server).
    
- Data is organized into **fact tables** (quantitative metrics) and **dimension tables** (descriptive attributes).
    

 **Tier 3 – Top Tier (Presentation Layer)**

- **Business Intelligence & Analytics tools** connect to the DW to perform:
    
    - Data mining
        
    - Reporting
        
    - Dashboards
        
    - Trend and forecasting analysis
        
- Examples: Tableau, Power BI, Qlik.
    

---

 5. **Advantages**

- **High Performance Queries** → Optimized indexing and schema for fast analytics.
    
- **Data Consistency** → All data is standardized into one schema.
    
- **Business Intelligence Support** → Enables complex analysis, KPIs, and strategic insights.
    
- **Historical Analysis** → Long-term trend identification and forecasting.
    

---

 6. **Limitations**

- **Schema rigidity** → Changes in business requirements or source systems may require redesigning the schema.
    
- **No unstructured data support** → Only works well with structured, schema-defined data.
    
- **High cost** → Requires significant infrastructure and maintenance.
    
- **Not Real-Time** → Usually batch-loaded, so it may not reflect the very latest transactions.
    

---

 7. **When to Use a Data Warehouse**

- When you need **organization-wide reporting**.
    
- When your data sources are mostly **structured** and relatively stable in schema.
    
- When historical analysis and trend forecasting are important.
    
- When you want a **single, consistent version of the truth** for decision-making.
---

###### b) Data Mart
 1. **Definition**
A **Data Mart** is a **subset** of a **Data Warehouse**, designed to serve the needs of a **specific group of users, department, or business function** within an organization.

If a **Data Warehouse** is the “main warehouse” containing all processed enterprise data, a **Data Mart** is like a “smaller store section” that contains only the data relevant to **one specific purpose**.

**Examples:**

- Marketing department → **Marketing Data Mart** with campaign, lead, and market analysis data.
    
- Finance department → **Finance Data Mart** with revenue, cost, and profit data.
    

---

 2. **Purpose**
- Provide **quick access** to data relevant to a specific business function.
    
- Reduce complexity compared to a full Data Warehouse (DW) → smaller and easier to use.
    
- **Improve query performance** because it only contains necessary data for that user group.
    
- Reduce data processing cost and time.
    

---

 3. **Types of Data Marts**

	 **Dependent Data Mart**
	- Built **from an existing Data Warehouse**.
	    
	- Uses a **top-down approach**: data is loaded into the DW first, then a subset is extracted to create the Data Mart.
	    
	- **Pros:**
	    
	    - Data is consistent with the DW.
	        
	    - Centralized management and easier maintenance.
	        
	- **Cons:**
	    
	    - Fully dependent on the DW — if DW data is delayed, the Data Mart is also delayed.
	        
	
	---
	
	**Independent Data Mart**
	
	- Operates **independently** of a Data Warehouse.
	    
	- Sources data directly from operational or external systems → processes it → stores it in the Data Mart.
	    
	- **Pros:**
	    
	    - Quick deployment, no need for a DW first.
	        
	    - Good for analyzing a small, focused dataset.
	        
	- **Cons:**
	    
	    - **Data inconsistency** risk if multiple independent marts exist.
	        
	    - Harder to integrate into a centralized DW later.
	        
	
	---
	
	**Hybrid Data Mart**
	
	- Combines data from both **a Data Warehouse** and **other operational sources**.
	    
	- More flexible — has the speed of an independent mart plus the consistency of a dependent mart.
	    
	- Common when:
	    
	    - Real-time operational data is needed.
	        
	    - Historical data from DW is still valuable.
	        

---

 4. **Advantages**

- **Faster** → quicker deployment and query times than a full DW.
    
- **Simpler** → only contains relevant data.
    
- **Lower cost** compared to building a full DW for one department.
    
- **Focused** → tailored to the needs of a specific group.
    

---

 5. **Disadvantages**

- Without proper synchronization, **data discrepancies** may arise between Data Marts and DW.
    
- **Limited analysis scope** — only department-specific data.
    
- Independent marts can cause **data duplication** and waste resources.
    

---

 6. **When to Use**

- When a department needs fast analytics **without waiting for DW implementation**.
    
- When analysis is **focused on a specific dataset or function**.
    
- When improving query performance is a priority due to smaller data volume.

---
###### c) Data Lake
 1. **Definition**

A **Data Lake** is a **centralized storage repository** that holds **large volumes of raw data** in its **native format** — whether **structured, semi-structured, or unstructured** — without requiring transformation before storage.

It is built for **scalability, flexibility, and cost efficiency**, making it ideal for **big data, advanced analytics, artificial intelligence (AI), and machine learning (ML)** workloads.

📌 Analogy: If a **Data Warehouse** is a neatly organized supermarket, a **Data Lake** is like a massive storage yard where you keep everything first, then organize and process it only when needed.

---

 2. **Purpose**

- Store **all types of data** from multiple sources in one place.
    
- Enable **schema-on-read** → apply structure only when the data is read for analysis.
    
- Support modern analytics, AI, and ML that require raw, diverse datasets.
    
- Reduce preparation time for data scientists and analysts.
    

---

 3. **Key Characteristics**

- **Stores raw data** exactly as received, without forcing it into a fixed schema.
    
- **Highly scalable** — can hold petabytes (PB) or even exabytes (EB) of data.
    
- **Cost-effective storage** using cloud-based object storage systems.
    
- **Supports all data types**:
    
    - **Structured** (tables, CSV files, relational DB dumps)
        
    - **Semi-structured** (JSON, XML, logs)
        
    - **Unstructured** (text, images, videos, audio)
        
    - **Binary** files
        
- **Compatible with multiple processing frameworks** (batch, streaming, real-time).
    

---

 4. **Typical Architecture**

 **a) Ingestion Layer**

- Collects data from various sources: databases, APIs, streaming platforms (e.g., Kafka), IoT devices, files, etc.
    
- Uses **ELT** or streaming pipelines to ingest data into the lake.
    

 **b) Storage Layer**

- Stores raw data in cloud object storage (AWS S3, Azure Data Lake Storage, Google Cloud Storage).
    
- Often partitioned by source, date, or metadata for easier retrieval.
    

 **c) Processing Layer**

- Processes data **on demand** using tools like Apache Spark, Databricks, Presto, Flink.
    
- Supports **batch** and **real-time** processing.
    

**d) Consumption Layer**

- Serves data to BI tools, analytics platforms, AI, and ML systems.
    
- Examples: Tableau, Power BI, Jupyter Notebook, TensorFlow, PyTorch.
    

---

 5. **Advantages**

- **Stores everything** — no need to decide upfront what to keep.
    
- **Flexible** — works with any data format.
    
- **Scalable** — can grow without performance loss.
    
- **Cost-efficient** — cloud object storage is cheaper than relational databases.
    
- **Supports modern analytics** — AI, ML, predictive analytics, and big data processing.
    

---

6. **Challenges**

- **Data swamp risk** — without proper governance, the lake can become unorganized and hard to use.
    
- **Security** — sensitive data must be encrypted and access-controlled.
    
- **Metadata management** — without proper cataloging, finding and understanding data becomes difficult.
    
- **Skilled workforce needed** — requires data engineers and scientists with advanced tools.
    

---

 7. **When to Use a Data Lake**

- When data comes in **various formats** (structured, semi-structured, unstructured).
    
- When you need to retain **raw historical data** for compliance, auditing, or future analysis.
    
- When working on **machine learning, AI, or big data analytics**.
    
- When you need **real-time streaming** and **batch processing** together.
#### 2.4.4 Type of Data Architecture
##### 2.4.4.1 Data Fabric
 **1. Definition**
**Data Fabric** is a data architecture that enables **end-to-end integration** of data from multiple sources (databases, data warehouses, data lakes, APIs, cloud systems, and external platforms) into a **unified, intelligent, and automated ecosystem**.
- It creates a **virtualized, metadata-driven layer** on top of existing data systems.
    
- Users and applications can **access data without knowing its physical location, format, or storage details**.
    

> In simple terms: **Data Fabric is a “data network fabric” that connects and integrates all data across the organization seamlessly**.

---

 **2. Components & How It Works**
From the slides, we can view Data Fabric’s evolution in **three stages**:

 **a. Traditional Data Management**
![[Traditional Data Management.png]]
- Data from multiple sources (**Operational Systems, Individual Databases, Websites, Social Media, IoT Devices, Flat Files**) is collected through **ETL** and stored in **Data Warehouses, Data Lakes, or Data Marts**.
    
- Consumers (BI tools, reporting systems, applications) access the data via **APIs** or **SQL**.
    
- **Limitation:** Data must be moved and duplicated to central storage before use → slower and more resource-intensive.
    

---

 **b. Data Virtualization Architecture**
![[Data Virtualization Architecture.png]]
- Introduces an **Abstraction Layer** containing:
    
    - **Virtual View**: Provides a combined view of data from multiple sources without physically moving it.
        
    - **Data Catalog & Metadata**: Stores information about data location, structure, meaning, and relationships.
        
- Allows direct access via APIs or SQL without heavy data replication.
    

---

 **c. Data Fabric (Modern Approach)**
 ![[Data Fabric (Modern Approach).png]]
- Builds on **Data Virtualization** but adds **AI/ML automation** and **metadata-driven orchestration**:
    
    - **Knowledge Graph**: Maps and visualizes relationships between datasets.
        
    - **Recommendation Engine**: Suggests relevant datasets for analysis.
        
    - **Business Rules**: Automates data governance and processing logic.
        
    - **Metadata & Data Catalog**: Centralized data descriptions to track lineage and improve discovery.
        
- AI/ML helps automate:
    
    - **Ingestion**: Loading data from diverse sources.
        
    - **Transformation**: Cleaning and enriching data.
        
    - **Data Delivery**: Supplying data to BI tools, dashboards, and business apps.
        

---

**3. Key Characteristics** 

- **Data Integration**: Connects all types of sources—databases, warehouses, lakes, APIs, and external systems.
    
- **Data Virtualization**: Lets applications access data without needing to know where it is physically stored.
    
- **Data Governance**: Implements security, privacy, compliance, and quality controls.
    
- **Data Orchestration**: Automates pipelines, workflows, and delivery processes.
    
- **Metadata Management**: Maintains a centralized metadata repository for complete data asset visibility (definitions, relationships, lineage).
    

---

**4. Benefits**

- **Real-time access** to distributed data without duplication.
    
- **Keeps original data at the source**, reducing redundancy.
    
- Speeds up integration and analysis.
    
- Flexible to add new sources without heavy reengineering.
    
- Supports **structured, semi-structured, unstructured, and streaming** data.
    
---

**5. Best Use Cases**

- Organizations with **multi-cloud, hybrid, or on-premise** data environments.
    
- Businesses that need **fast analytics** without waiting for ETL processes.
    
- Scenarios where **data must remain in source systems** for compliance or cost reasons.
    
- Enterprises that want **metadata-driven insights** and **AI-assisted data discovery**.
##### 2.4.4.2 Data Mesh
 **1. Definition**

**Data Mesh** is a **decentralized data architecture** that focuses on delegating data management responsibilities to each business domain (e.g., Marketing, Sales, Finance) and treats data as a product (**Data as a Product**).

- Each domain **owns, manages, and is responsible** for its own data.
    
- Domains create, store, process, and share their data through a **self-serve data infrastructure**.
    
- A **federated governance** framework ensures that data from different domains is interoperable, secure, and reliable.
    

> In other words: **Data Mesh turns data into a “product” and gives each team full responsibility for the entire lifecycle of that data**.

---

 **2. Components & How It Works**
  **a. Traditional Centralized Data Management**

- A central data team collects, processes, and manages data from all domains.
    
- Data is stored in a centralized **Data Warehouse** or **Data Lake**.
    
- **Limitation:** Prone to bottlenecks, lacks deep domain knowledge, and responds slowly to specialized data needs.
- 
- **b. Data mesh Approach**
 ![[Data Mesh.png]]
- **Domain-Oriented Ownership:** Each domain owns and manages its own data.
    
- **Data as a Product:**
    
    - Data comes with clear metadata, APIs, and documentation.
        
    - Standards for quality, security, and accessibility are applied.
        
- **Self-Serve Data Platform:**
    
    - A shared platform provides tools for domains to ingest, transform, store, and share data without depending on the central team.
        
- **Federated Computational Governance:**
    
    - A unified set of rules ensures that all domain data meets organizational standards.
        
    - Governance is automated via infrastructure.
        

---

 **3. Key Characteristics**

- **Decentralized Data Ownership:** Data responsibility lies within the domains.
    
- **Data Product Mindset:** Data is treated as a product, serving multiple consumers.
    
- **Self-Service Infrastructure:** Domains have full access and tools to work with their data.
    
- **Federated Governance:** Combines common standards with domain autonomy.
    
- **Interoperability:** Data from different domains can be easily integrated.
    

---

 **4. Benefits**

- **Scalable:** Easily expand without overloading the central data team.
    
- **Faster Delivery:** Domains can quickly create and share data.
    
- **Higher Quality:** Data is created and managed by those with deep domain knowledge.
    
- **Flexibility:** Each domain can choose the tools and methods that suit them best.
    

---

 **5. Best Use Cases**

- Organizations with multiple independent domains and large data volumes.
    
- Businesses needing agility and speed in creating data products.
    
- Complex and diverse data requiring deep domain expertise.
    
- When wanting to avoid bottlenecks caused by a centralized data team.
    

---
## 3. Big Data Era
### 3.1 **Definition**

The **Big Data Era** describes the current stage of computing and data management where:

- The **volume** of data is massive (terabytes to petabytes).
    
- The **velocity** is high (data arrives in real-time or streams).
    
- The **variety** of data is large (structured, semi-structured, unstructured, multimedia).
    
- The **veracity** of data—its quality and reliability—must be maintained despite scale.
    
- The **value** comes from using this data to gain insights, make predictions, and drive business actions.
### 3.2 **Shift in Data Management Requirements**

#### **Legacy Demands** (Old Approach)

- Small number of users.
    
- Designed to run on a **single server**.
    
- Focused on **transactions** with ACID properties, consistency, and integrity.
    
- Goal was **storage efficiency** and optimized relational database structures.
    

#### **Modern Demands** (Big Data Era)

- Massive numbers of **users and devices**.
    
- Need **scale and performance** to handle large datasets quickly.
    
- **Flexibility** for agile development and fast adaptation.
    
- Adoption of **microservices architectures**.
    
- Support for **web, mobile, and IoT** experiences.
### 3.3 ***Architectural Shifts in Big Data Era***
### **1. Generation**

- **From (Before):**
    
    - Mostly **on-prem(physically inside the organization’s own facilities — instead of being hosted in the cloud)** relational databases.
        
    - Only **structured data**.
        
    - Data collected in **batch** mode.
        
- **To (Now):**
    
    - **Cloud-based relational** and **NoSQL databases**.
        
    - Both **structured** and **unstructured** data.
        
    - Handles **real-time** and batch.
        
- **Rationale:**
    
    - Moving to the **cloud** for **flexibility** and **scalability**.
        
    - **Polyglot persistence**: use the most suitable database type for each task.
        

---

### **2. Ingestion**

- **From:**
    
    - **On-prem ETL tools**.
        
    - Structured data only.
        
    - Batch mode.
        
- **To:**
    
    - **Cloud-based ELT tools**.
        
    - Structured + unstructured data.
        
    - Real-time & batch processing.
        
- **Rationale:**
    
    - Traditional **ETL** replaced by more **flexible** and **high-performance ELT**, supporting real-time ingestion.
        

---

### **3. Storage**

- **From:**
    
    - **On-prem centralized data warehouse**.
        
- **To:**
    
    - **Cloud-based data warehouse**.
        
    - **Distributed storage** systems.
        
    - **Data lakes** for raw data in multiple formats.
        
- **Rationale:**
    
    - Greater **flexibility** in collecting and storing from multiple sources, **scalability**, and **advanced analytics**.
        

---

### **4. Analytics**

- **From:**
    
    - **Historical** and **prescriptive** analytics (recommendations based on past data).
        
    - Batch processing.
        
    - Traditional data mining.
        
- **To:**
    
    - **Prescriptive & predictive** analytics (forecasting future trends).
        
    - Real-time and batch.
        
    - **AI/ML models**.
        
- **Rationale:**
    
    - Moving from just **prescriptive** to **predictive** analytics.
        
    - Leveraging **AI/ML approaches**.
        

---

### **5. Consumption**

- **From:**
    
    - **Dashboards & reports**.
        
    - Centralized administration.
        
- **To:**
    
    - **AI/ML model-driven insights**.
        
    - **Self-service** analytics for business users.
        
- **Rationale:**
    
    - Enables **non-technical users** to run analytics themselves via self-service portals.