## 1. Cloud Computing Fundamentals
- **Cloud computing**: A model that provides **on-demand network access** to a **shared pool of configurable resources**(servers, storage, networks, applications, services).
    
- Resources can be provisioned and released quickly, with minimal management effort.
## 1.1 Key Characteristics of Cloud Computing

### 1. Broad Network Access

- **Meaning:**  
    Cloud resources are available over a network and accessible through standard protocols. Customers can reach them anywhere, anytime, using various devices.
    
- **Key points:**
    
    - Access from laptops, smartphones, tablets, or workstations.
        
    - Promotes interoperability with multiple applications and systems.
        
- **Example:**
    
    - A student edits a Google Docs file at university on a laptop, then continues on a smartphone at home.
        
    - Cloud APIs (e.g., REST) allow applications to integrate with services like AWS S3 or Google Maps.
        

---

### 2. Measured Service

- **Meaning:**  
    Cloud usage is metered, monitored, and billed according to consumption.
    
- **Key points:**
    
    - “Pay-as-you-go” model: customers pay only for what they use.
        
    - Enables transparency and optimization of resource usage.
        
    - Defined in the SLA (Service Level Agreement).
        
- **Example:**
    
    - AWS charges EC2 instances per second of usage.
        
    - Google Cloud Storage charges per GB stored per month.
        

---

### 3. Multi-tenancy
![[Multi-tenancy.png]]
- **Meaning:**  
    Multiple customers (tenants) share the same physical or virtual resources, but their data and operations are securely isolated.
    
- **Key points:**
    
    - Improves efficiency by pooling resources.
        
    - Requires strong identity and access management.
        
    - A single organization can create multiple tenants for internal teams.
        
- **Example:**
    
    - Microsoft 365 hosts email for thousands of companies, yet each company’s data is completely separated.
        
    - On AWS, different customers run applications on the same infrastructure without interference.
        

---

### 4. On-demand Self-service

- **Meaning:**  
    Customers can provision and manage resources automatically, without human interaction with the provider.
    
- **Key points:**
    
    - Immediate provisioning (minutes instead of days or weeks).
        
    - Reduces cost and effort for customers.
        
- **Example:**
    
    - A developer creates a new virtual machine on Azure through a web portal in minutes.
        
    - A user upgrades Dropbox storage from 2 GB to 2 TB instantly.
        

---

### 5. Rapid Elasticity and Scalability
![[Rapid Elasticity and Scalability.png]]
- **Meaning:**  
    Resources can be scaled up or down quickly, often automatically, to match demand.
    
- **Key points:**
    
    - To customers, resources seem unlimited.
        
    - Avoids over-provisioning (waste) and under-provisioning (outages).
        
- **Example:**
    
    - Netflix scales up servers during peak hours in the evening and scales down at night.
        
    - An online ticketing site adds servers during a high-demand concert release.
        

---

### 6. Resource Pooling
![[Resource Pooling.png]]
- **Meaning:**  
    The provider’s physical or virtual resources are pooled together to serve multiple customers dynamically.
    
- **Key points:**
    
    - Abstracts away the complexity: customers don’t know or control the exact location of resources.
        
    - Provider optimizes efficiency across global data centers.
        
- **Example:**
    
    - Google Photos stores user pictures in data centers around the world, but users just access them seamlessly.
        
    - AWS RDS (Relational Database Service) manages shared infrastructure but each customer has isolated databases.
## 1.2 Cloud Service Categories (7 Service Models)

### 1. Software as a Service (SaaS)
![[Software as a Service (SaaS).png]]
- **Meaning:**  
    Customers use applications hosted and maintained by the cloud provider. No need to install or manage infrastructure, only use the software via browser or app.
    
- **Key points:**
    
    - Accessible through a web browser or API.
        
    - Customer only manages user-level settings.
        
    - All backend (servers, storage, updates) handled by provider.
        
- **Examples:**
    
    - Gmail, Outlook.com (email service).
        
    - Google Docs, Microsoft 365 (office productivity).
        
    - Dropbox (cloud storage).
        

---

### 2. Platform as a Service (PaaS)
![[Platform as a Service (PaaS).png]]
- **Meaning:**  
    Customers deploy their own applications on the provider’s platform, using programming languages, libraries, and tools supported by the provider.
    
- **Key points:**
    
    - Customer focuses on app code; provider manages servers, OS, middleware.
        
    - Supports rapid development and deployment.
        
- **Examples:**
    
    - Google App Engine.
        
    - Heroku.
        
    - Microsoft Azure App Services.
        

---

### 3. Infrastructure as a Service (IaaS)
![[Infrastructure as a Service (IaaS).png]]
- **Meaning:**  
    Customers rent fundamental resources: virtual machines, networks, storage, and can install any OS or application.
    
- **Key points:**
    
    - Customers control the OS, applications, and configurations.
        
    - Provider only manages the underlying infrastructure.
        
- **Examples:**
    
    - Amazon EC2 (Elastic Compute Cloud).
        
    - Microsoft Azure Virtual Machines.
        
    - Google Compute Engine.
        

---

### 4. Network as a Service (NaaS)
![[Network as a Service (NaaS).png]]
- **Meaning:**  
    Customers rent and manage network services like connectivity, routing, VPNs.
    
- **Key points:**
    
    - No need to buy network hardware.
        
    - Customers configure virtual networks, bandwidth, firewalls.
        
- **Examples:**
    
    - AWS VPC (Virtual Private Cloud).
        
    - Akamai Content Delivery Network (CDN).
        
    - Cloudflare network services.
        

---

### 5. Communications as a Service (CaaS)

- **Meaning:**  
    Provides real-time communication features such as messaging, voice, or video conferencing.
    
- **Key points:**
    
    - Customers don’t manage underlying network protocols.
        
    - Services support multiple modes of communication.
        
- **Examples:**
    
    - Zoom (video calls).
        
    - Twilio (SMS, voice, chat APIs).
        
    - Microsoft Teams, Slack (team collaboration).
        

---

### 6. Compute as a Service (CompaaS)

- **Meaning:**  
    Customers rent raw processing power (CPUs, GPUs, TPUs) to run applications or algorithms.
    
- **Key points:**
    
    - Often used for high-performance computing (HPC) or AI/ML.
        
    - Can be specialized (e.g., GPU for deep learning).
        
- **Examples:**
    
    - Google Cloud TPUs (Tensor Processing Units).
        
    - AWS EC2 GPU instances.
        
    - IBM Cloud HPC clusters.
        

---

### 7. Data Storage as a Service (DSaaS)

- **Meaning:**  
    Customers store and manage data in the provider’s infrastructure, from simple files to large-scale databases.
    
- **Key points:**
    
    - Includes backups, disaster recovery, geo-replication.
        
    - Can support both structured (databases) and unstructured (files, media) data.
        
- **Examples:**
    
    - Amazon S3 (object storage).
        
    - Google Cloud Storage.
        
    - Firebase Realtime Database.
## 1.3 Cloud Deployment Models (4 Types)

### 1. Private Cloud

- **Meaning:**  
    Cloud infrastructure is dedicated to a **single organization (one customer)**.  
    The organization (CSC – Cloud Service Customer) fully controls access, security, and data.
    
- **Key points:**
    
    - Exclusive use → only one organization uses the cloud.
        
    - Can be hosted **on-premises** (in the company’s own data center) or managed by a third party.
        
    - Provides more **control, security, and compliance**.
        
- **Advantages:**
    
    - High security and privacy (sensitive data protected).
        
    - Better control over data location and configuration.
        
    - Easier compliance with legal/regulatory requirements.
        
- **Disadvantages:**
    
    - High cost (must buy and maintain infrastructure).
        
    - Limited scalability compared to public cloud.
        
- **Examples:**
    
    - A bank using a private cloud for handling customer financial transactions.
        
    - Government agencies hosting classified data on their private cloud.
        

---

### 2. Public Cloud
![[Public Cloud.png]]
- **Meaning:**  
    Cloud services are available to **any customer** over the public internet.  
    Infrastructure is owned and operated by the **cloud provider (CSP)**.
    
- **Key points:**
    
    - Shared by multiple tenants (multi-tenancy).
        
    - Customers pay for resources they consume (pay-as-you-go).
        
    - Provider manages everything: hardware, networking, security.
        
- **Advantages:**
    
    - Cost-effective (no need to buy hardware).
        
    - Highly scalable, virtually unlimited capacity.
        
    - Quick deployment and easy to access.
        
- **Disadvantages:**
    
    - Less control over security and compliance.
        
    - Data location may be outside customer’s jurisdiction.
        
- **Examples:**
    
    - AWS (Amazon Web Services).
        
    - Microsoft Azure.
        
    - Google Cloud Platform (GCP).
        

---

### 3. Community Cloud
![[Community Cloud.png]]
- **Meaning:**  
    Cloud infrastructure is **shared by a specific group of organizations** that have similar needs, goals, or regulations.
    
- **Key points:**
    
    - Shared infrastructure but limited to organizations in the same “community”.
        
    - Operated by one or more members of the community, or by a third party.
        
    - Cost and resources are shared among participants.
        
- **Advantages:**
    
    - More affordable than private cloud (shared costs).
        
    - Tailored for specific industries with common needs.
        
    - Ensures compliance with sector-specific standards.
        
- **Disadvantages:**
    
    - Still more expensive than public cloud.
        
    - Governance can be complex since multiple organizations are involved.
        
- **Examples:**
    
    - Universities sharing a community cloud for research.
        
    - Hospitals sharing a cloud for patient health records (complying with HIPAA).
        
    - Law firms sharing infrastructure for legal document storage.
        

---

### 4. Hybrid Cloud
![[Hybrid Cloud.png]]
- **Meaning:**  
    A combination of **private cloud** and **public cloud**, bound together to enable data and application portability.
    
- **Key points:**
    
    - Organizations keep sensitive workloads in private cloud and use public cloud for less sensitive workloads or for scaling.
        
    - Requires integration technologies (e.g., APIs, cloud management platforms).
        
    - Provides flexibility to choose the best environment for each workload.
        
- **Advantages:**
    
    - Balance between cost efficiency and security.
        
    - High scalability: use public cloud for “bursting” extra demand.
        
    - Suitable for businesses with varying regulatory and performance needs.
        
- **Disadvantages:**
    
    - More complex to manage (integration issues).
        
    - Requires strong governance and monitoring.
        
- **Examples:**
    
    - A retail company keeps customer payment info in private cloud but uses public cloud for seasonal traffic spikes.
        
    - A healthcare provider stores patient records privately while using public cloud for big data analytics.
## 1.4 Cloud Computing Cross-cutting Aspects
### 1. Auditability

- **Meaning:** The ability to **collect, log, and provide evidence** of cloud service operations for audits.
    
- **Why important:** Required for compliance (financial, healthcare, legal regulations).
    
- **Example:**
    
    - AWS CloudTrail keeps logs of every API call for auditing.
        
    - A bank uses audit logs to prove compliance with financial authorities.
        

---

### 2. Availability

- **Meaning:** The ability of a service to **stay operational** as required.
    
- **Key factors:** reliability, recoverability, maintainability.
    
- **Example:**
    
    - AWS promises 99.99% uptime for certain services.
        
    - Netflix depends on high availability to stream videos worldwide without downtime.
        

---

### 3. Governance

- **Meaning:** The system of **rules and decision-making** for managing cloud services (who controls, who is responsible).
    
- **Example:**
    
    - An organization enforces policies to control which data can be stored in public cloud.
        
    - A company sets governance to ensure developers can’t spin up unauthorized cloud resources.
        

---

### 4. Interoperability

- **Meaning:** The ability of one cloud service or system to **interact with another** and exchange data in predictable ways.
    
- **Example:**
    
    - Migrating data from AWS S3 to Google Cloud Storage.
        
    - A company uses APIs to connect Salesforce (SaaS) with an internal HR system.
        

---

### 5. Maintenance and Versioning

- **Meaning:** Updating cloud services after delivery to fix bugs, improve performance, or adapt to changes.
    
- **Example:**
    
    - Microsoft Azure rolls out automatic patches for security vulnerabilities.
        
    - A SaaS provider updates its app to support new mobile devices.
        

---

### 6. Performance

- **Meaning:** How quickly and efficiently the cloud service responds to requests.
    
- **Key metric:** response time, throughput, latency.
    
- **Example:**
    
    - A gaming platform requires low latency for smooth online gameplay.
        
    - AWS Lambda needs sub-second execution time for serverless functions.
        

---

### 7. Portability

- **Meaning:** The ability to **move applications or data** from one cloud to another, or between customer systems and cloud.
    
- **Example:**
    
    - Migrating a web app from AWS to Azure without rewriting the code.
        
    - Exporting a database from Google Cloud SQL to on-premises.
        

---

### 8. Protection of Personally Identifiable Information (PII)

- **Meaning:** Handling personal data securely (collecting, processing, storing, and deleting it properly).
    
- **Example:**
    
    - A healthcare system ensures patient records comply with HIPAA.
        
    - Using encryption and anonymization to protect customer names, emails, credit card info.
        

---

### 9. Regulatory Compliance

- **Meaning:** Cloud services must follow **laws and regulations**, which differ across regions.
    
- **Example:**
    
    - GDPR in the EU (right to data protection).
        
    - Australian Privacy Act for data storage.
        
    - Financial institutions must follow regional banking regulations.
        

---

### 10. Resiliency

- **Meaning:** The ability of a cloud system to **recover and continue operating** despite failures (hardware, software, attacks, disasters).
    
- **Example:**
    
    - Google Cloud automatically shifts workloads if a server crashes.
        
    - AWS offers multi-region replication to withstand regional outages.
        

---

### 11. Reversibility

- **Meaning:** Customers can **retrieve their data** when leaving a provider, and the provider deletes all data afterwards.
    
- **Example:**
    
    - A company exports all its documents from Microsoft 365 before contract termination.
        
    - CSP guarantees to wipe customer data after service closure.
        

---

### 12. Security

- **Meaning:** Protecting information by ensuring **confidentiality, integrity, and availability (CIA)**.
    
- **Extended aspects:** authenticity, accountability, non-repudiation, reliability.
    
- **Example:**
    
    - Confidentiality: Encrypting data at rest in AWS S3.
        
    - Integrity: Hash checks to ensure data isn’t modified.
        
    - Availability: DDoS protection to keep services online.
# 2. Cloud Computing Reference Architecture (CCRA)
**Cloud Computing Reference Architecture (CCRA)** là một khung kiến trúc (architectural framework) dùng để mô tả, phân tích và thiết kế các hệ thống điện toán đám mây. Nó không gắn với một nhà cung cấp cụ thể (vendor-neutral) mà đưa ra chuẩn chung để mọi người có thể hiểu, so sánh và xây dựng hệ thống cloud.
## 2.1 Goals of CCRA
1. **Mô tả cộng đồng các bên liên quan (stakeholders community)**
    
    - Xác định các **bên tham gia trong môi trường cloud**:
        
        - Cloud Service Customer (CSC) – khách hàng.
            
        - Cloud Service Provider (CSP) – nhà cung cấp.
            
        - Cloud Service Partner (CSN) – đối tác.
            
    - Giúp hiểu rõ **ai đóng vai trò gì** và **quan hệ giữa các bên**.
        
    
    _Ví dụ:_ Trong một công ty thương mại điện tử:
    
    - CSC là nhóm dev cần deploy app.
        
    - CSP là AWS cung cấp hạ tầng.
        
    - CSN là một công ty tư vấn hỗ trợ tối ưu cloud.
        

---

2. **Mô tả các đặc điểm cơ bản của hệ thống điện toán đám mây (fundamental characteristics)**
    
    - CCRA chỉ ra **những thuộc tính nền tảng** (như Broad Network Access, Scalability, Measured Service) cần có trong một hệ thống cloud đúng nghĩa.
        
    - Giúp đảm bảo bất kỳ hệ thống nào tuân theo CCRA sẽ có tính chuẩn hóa, dễ so sánh.
        
    
    _Ví dụ:_ Một dịch vụ SaaS muốn gọi là “cloud-based” thì phải có tính năng **on-demand self-service** và **elasticity**, không thể chỉ là “phần mềm online”.
    

---

3. **Xác định các hoạt động và thành phần chức năng (activities & functional components)**
    
    - CCRA định nghĩa **các chức năng cốt lõi** mà hệ thống cloud phải có, ví dụ: quản lý tài nguyên, bảo mật, vận hành, phát triển ứng dụng, tích hợp dịch vụ.
        
    - Các chức năng này được tổ chức thành **viewpoints (user, functional, implementation, deployment)** để dễ mô tả.
        
    
    _Ví dụ:_ Trong Functional View, hệ thống có 4 lớp: user, access, service, resource – giúp ta biết nên đặt mỗi chức năng ở đâu.
    

---

4. **Mô tả quan hệ giữa các thành phần và môi trường (relationships)**
    
    - Không chỉ liệt kê thành phần, CCRA còn mô tả **cách chúng tương tác** với nhau và với môi trường bên ngoài (network, client apps, APIs).
        
    - Điều này giúp tránh thiết kế rời rạc, mà hướng đến **hệ thống tổng thể đồng bộ**.
        
    
    _Ví dụ:_ Trong cloud, **service layer** phụ thuộc **resource layer**, còn **access layer** cung cấp API cho người dùng truy cập.
    

---

5. **Xác định nguyên tắc thiết kế & phát triển CCRA (design & evolution principles)**
    
    - Hướng dẫn **cách xây dựng kiến trúc cloud-native** theo chuẩn hiện đại:
        
        - Tự động hóa (Automation).
            
        - Stateless design.
            
        - Ưu tiên managed services.
            
        - Defense-in-depth (bảo mật đa tầng).
            
        - Always Be Architecting (liên tục cải tiến).
            
    - Giúp hệ thống cloud **phát triển linh hoạt theo nhu cầu doanh nghiệp và công nghệ mới**.
        
    
    _Ví dụ:_ Một công ty video streaming áp dụng nguyên tắc **Always Be Architecting**: từ 1080p → 4K → 8K, hạ tầng cloud phải liên tục thích nghi.
## 2.2 Cloud-Native Architecture Principles

Cloud-native means building applications **specifically for the cloud environment**, not just moving traditional apps into cloud infrastructure. It leverages elasticity, automation, and distributed systems.

There are 5 key principles:

---

### **Principle 1: Design for Automation**

- **Meaning:**  
    Traditional environments required manual provisioning: ordering hardware, installing OS, configuring middleware—slow and error-prone.  
    In cloud-native, automation is at the core.
    
- **Practices:**
    
    - Use **Infrastructure as Code (IaC):** Terraform, Ansible, CloudFormation.
        
    - Automate CI/CD pipelines: Jenkins, GitHub Actions, Google Cloud Build.
        
    - Autoscaling: automatically increase/decrease instances.
        
    - Monitoring and self-healing systems.
        
- **Example:**
    
    - Netflix autoscaling servers to meet peak viewing demand.
        
    - Using Terraform to spin up 100 AWS EC2 instances in minutes.
        

---

### **Principle 2: Be Smart with State**

- **Meaning:**  
    _State_ = information about current user/application context (e.g., login session, shopping cart).  
    Traditional apps stored state on local server memory → if the server crashed, the state was lost.  
    Cloud-native favors **stateless design**.
    
- **Practices:**
    
    - Make apps stateless so any server can handle requests.
        
    - Store state externally: Redis, cloud databases, object storage.
        
    - Decouple state management from application logic.
        
- **Example:**
    
    - E-commerce: shopping cart stored in Redis, not in server session.
        
    - When a request arrives, any server can fetch cart data from Redis.
        

---

### **Principle 3: Favor Managed Services**

- **Meaning:**  
    Cloud providers offer **managed services** (databases, ML, messaging). Instead of managing infrastructure yourself, use these services.
    
- **Benefits:**
    
    - Saves operational overhead.
        
    - Provider ensures reliability, scaling, patching.
        
    - Teams focus on business logic, not infrastructure.
        
- **Example:**
    
    - Use **AWS RDS** instead of running your own MySQL VM.
        
    - Use **Google BigQuery** for analytics instead of self-hosted Hadoop.
        
    - Use **Firebase Authentication** for user logins.
        
- **Challenge:**
    
    - **Vendor lock-in** risk (dependence on one cloud provider).
        

---

### **Principle 4: Practice Defense in Depth**

- **Meaning:**  
    Cloud-native apps are internet-facing, so security risks are higher. One firewall is not enough → need **multi-layered security**.
    
- **Practices:**
    
    - **Edge Firewall:** defend against DDoS.
        
    - **Network Segmentation:** enforce authentication inside the system.
        
    - **Application Security:** input validation, API authentication.
        
    - **Endpoint Security:** secure VMs, containers.
        
    - **Data Encryption:** secure data at-rest and in-transit.
        
    - **Monitoring & SIEM:** detect suspicious activity (Splunk, AWS GuardDuty).
        
- **Example:**
    
    - SaaS app setup:
        
        - WAF (Web Application Firewall) at the edge.
            
        - OAuth2 between microservices.
            
        - AES-256 database encryption.
            
        - Continuous monitoring with alerts.
            

---

### **Principle 5: Always Be Architecting**

- **Meaning:**  
    Cloud-native systems are **constantly evolving**. Architecture must adapt to new business needs, technologies, and provider capabilities.
    
- **Practices:**
    
    - Continuous architectural reviews.
        
    - Proactively adopt new cloud services for efficiency.
        
    - Avoid “one-time design” mindset—embrace ongoing evolution.
        
- **Example:**
    
    - Netflix adapting infrastructure from 480p → 1080p → 4K → 8K streaming.
        
    - An AI company upgrading architecture to leverage new GPUs/TPUs.
## 2.3 CCRA Viewpoints 

---

### **1. User View**
![[User View.png]]
#### **Meaning**

- Describes the **system context**: which parties are involved in cloud computing, what **roles** they play, and what **activities** they perform.
    
- Helps clarify **who uses cloud, who provides it, and who supports it**.
    

---

#### **Parties (based on ISO/IEC 22123-2)**

1. **Cloud Service Customer (CSC)**
    
    - The individual or organization that purchases and uses cloud services.
        
    - **Sub-roles:**
        
        - End User (consumes the service).
            
        - Administrator (manages resources).
            
        - Developer (deploys applications).
            
2. **Cloud Service Provider (CSP)**
    
    - The organization delivering cloud services.
        
    - **Sub-roles:**
        
        - Service Manager.
            
        - Operations Manager.
            
        - Security Manager.
            
3. **Cloud Service Partner (CSN)**
    
    - Third-party entities that support cloud usage.
        
    - **Sub-roles:**
        
        - Auditor (independent verification).
            
        - Broker (matchmaking between customer and providers).
            
        - Carrier (network infrastructure, telecom).
            

---

#### **Activities**

- **CSC Activities:** request services, manage usage, pay bills.
    ![[CSC Activities.png]]
- **CSP Activities:** provision services, monitor, enforce SLA, ensure security.
    ![[CSP Activities.png]]
- **CSN Activities:** auditing, network connectivity, service brokerage.
    ![[CSN Activities.png]]

---

#### **Example**

- An **e-commerce company** using the cloud:
    
    - **CSC:** the company (developers deploy the app, admins manage resources).
        
    - **CSP:** AWS providing infrastructure (EC2, S3, RDS).
        
    - **CSN:** Deloitte auditing compliance, Cloudflare providing CDN.
        

---

### **2. Functional View**

#### **Meaning**

- A **technology-neutral perspective** that describes the **functions** required to build a cloud system.
    
- Organizes these functions into **layers** and shows their relationships.
    

---

#### **Functional Layers (4 main layers)**
![[Functional Layers (4 main layers).png]]
1. **User Layer**
    
    - Interfaces where users interact with cloud services.
        
    - Includes web/mobile apps, dashboards, portals.
        
    - Example: Accessing Dropbox via mobile app.
        
2. **Access Layer**
    
    - Manages how users access services.
        
    - Includes APIs, self-service portals, authentication/authorization (IAM).
        
    - Example: AWS API Gateway enabling applications to call cloud services.
        
3. **Service Layer**
    
    - Provides the actual cloud services (SaaS, PaaS, IaaS).
        
    - Example:
        
        - SaaS = Google Docs.
            
        - PaaS = Azure App Service.
            
        - IaaS = AWS EC2.
            
4. **Resource Layer**
    
    - Physical and virtual resources that support services.
        
    - Servers, storage, networks, virtualization.
        
    - Example: AWS storage clusters running under the hood.
        

---

#### **Cross-Layer Functions (span all layers)**

- **Security functions** – authentication, encryption.
    
- **Integration functions** – service orchestration, APIs.
    
- **Development support** – CI/CD tools.
    
- **Business support** – billing, SLA, customer management.
    
- **Operational support** – monitoring, logging, backups.
    

---

#### **Example Flow (User Request)**

When a user uploads a photo to Google Drive:

1. **User Layer:** user interacts via mobile app.
    
2. **Access Layer:** request passes through API + OAuth2 authentication.
    
3. **Service Layer:** Google Drive storage service processes the upload.
    
4. **Resource Layer:** file stored in physical/virtual storage cluster.
    
5. **Cross-layer:** security (encryption), billing (storage quota), monitoring.