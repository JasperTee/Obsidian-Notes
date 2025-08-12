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