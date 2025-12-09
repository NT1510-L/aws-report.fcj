---
title: "Week 10 Worklog"
date: "2025-09-09"
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---



### Week 10 Objectives:

* Connect and get acquainted with members of First Cloud Journey.
* Understand basic AWS services, how to use the console & CLI.

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                   | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 2   |  - DynamoDB Hands-on Labs: <br>&emsp; + Getting Started with DynamoDB <br>&emsp; + Create DynamoDB Tables and Load Sample Data <br>&emsp; + Explore DynamoDB with CLI (Read, Query, Scan, Insert/Update, Delete) <br>&emsp; + Work with Transactions and Global Secondary Indexes <br>&emsp; + Explore DynamoDB Console (View, Query, Scan, Modify Data) <br>&emsp; + Implement Backups (Point-In-Time Recovery, On-Demand, Scheduled) <br>&emsp; + Relational Modeling & Migration with DMS <br>&emsp; + Configure MySQL Environment and DynamoDB Migration <br>&emsp; + Clean up resources | 11/10/2025 | 11/10/2025      | <https://000039.awsstudygroup.com/> |
| 3   | - **LBED: Generative AI with DynamoDB zero-ETL to OpenSearch integration and Amazon Bedrock:** <br>&emsp; + Getting Started - Obtain & Review Code <br>&emsp; + Service Configuration (OpenSearch Service Permissions, Enable Amazon Bedrock Models, Load DynamoDB Data) <br>&emsp; + Configure Integrations and Create zero-ETL Pipeline <br>&emsp; + Query and Conclusion <br>- **LADV: Advanced Design Patterns for Amazon DynamoDB:** <br>&emsp; + Getting Started (Systems Manager Console, Python/AWS CLI, boto3, workshop files) <br>&emsp; + Exercise 1: DynamoDB Capacity Units and Partitioning <br>&emsp; + Exercise 2: Sequential and Parallel Table Scans <br>&emsp; + Exercise 3: Global Secondary Index Write Sharding <br>&emsp; + Exercise 4: Global Secondary Index Key Overloading <br>&emsp; + Exercise 5: Sparse Global Secondary Indexes <br>&emsp; + Exercise 6: Composite Keys <br>&emsp; + Exercise 7: Adjacency Lists <br>&emsp; + Exercise 8: DynamoDB Streams and AWS Lambda <br>- **LCDC: Change Data Capture for Amazon DynamoDB:** <br>&emsp; + Getting Started (Cloud9, EC2 Instance) <br>&emsp; + Scenario Overview (Create DynamoDB Tables, Load Sample Data) <br>&emsp; + Change Data Capture using DynamoDB Streams <br>&emsp; + Change Data Capture using Kinesis Data Streams <br>&emsp; + Summary and Clean Up | 11/11/2025 | 11/11/2025       | <https://000039.awsstudygroup.com/> |
| 4   | - **LMR: Build and Deploy a Global Serverless Application with Amazon DynamoDB:** <br>&emsp; + Getting Started <br>&emsp; + Module 1: Deploy the backend resources <br>&emsp; + Module 2: Explore Global Tables <br>&emsp; + Module 3: Interact with the Globalflix Interface <br>&emsp; + Global Tables Discussion Topics <br>&emsp; + Summary and Clean up <br>- **LEDA: Build a Serverless Event Driven Architecture with DynamoDB:** <br>&emsp; + Getting Started and Overview <br>&emsp; + Optional - Pipeline Deep Dive <br>&emsp; + Lab 1: Connect the pipeline (StateLambda, MapLambda trigger, ReduceLambda) <br>&emsp; + Lab 2: Ensure fault tolerance and exactly once processing <br>&emsp; + Summary: Conclusions | 11/12/2025 | 11/12/2025       | <https://000039.awsstudygroup.com/> |
| 5   | - **LGME: Modeling Game Player Data with Amazon DynamoDB:** <br>&emsp; + Getting Started <br>&emsp; + Plan your data model (Best Practices, Entity-Relationship Diagram, Access Patterns) <br>&emsp; + Core usage: user profiles and games (Design primary key, Retrieve item collections) <br>&emsp; + Create the table and bulk-load data <br>&emsp; + Find open games (Model sparse GSI, Create sparse GSI, Query and Scan sparse GSI) | 11/13/2025 | 11/13/2025       | <https://000039.awsstudygroup.com/> |
| 6   | - **LGME Continued: Advanced Game Operations:** <br>&emsp; + Join and close games (Add users to game, Start a game) <br>&emsp; + View past games (Add inverted index, Retrieve games for user) <br>&emsp; + Summary & Cleanup <br>- **LDC: Design Challenges:** <br>&emsp; + Retail Cart Scenario with References <br>&emsp; + Bank Payments Scenario with References <br>&emsp; + NoSQL Design: Reference Materials | 10/14/2025 | 10/14/2025      | <https://000039.awsstudygroup.com/> |


### Week 10 Achievements:

* **Mastered comprehensive Amazon DynamoDB fundamentals and advanced concepts:**
  * NoSQL database principles and DynamoDB architecture
  * Table creation, data modeling, and primary key design
  * CLI and Console operations (CRUD, Query, Scan, Transactions)
  * Backup strategies (Point-In-Time Recovery, On-Demand, Scheduled)
  * Database migration from relational systems using DMS

* **Implemented advanced DynamoDB design patterns and optimization techniques:**
  * Global Secondary Indexes (GSI) including sparse, write sharding, and key overloading
  * Composite keys for complex querying patterns
  * Adjacency lists for hierarchical data relationships
  * Capacity units, partitioning, and performance optimization
  * Sequential and parallel table scans

* **Built real-time data processing and integration solutions:**
  * DynamoDB Streams for change data capture
  * Kinesis Data Streams integration for high-volume processing
  * Lambda functions for event-driven architectures
  * Zero-ETL integration with OpenSearch and Amazon Bedrock for AI applications

* **Developed serverless applications with global distribution:**
  * Global Tables for multi-region deployment
  * Serverless event-driven architectures with fault tolerance
  * Exactly-once processing and idempotency patterns
  * Global serverless application deployment (Globalflix)

* **Applied DynamoDB to real-world scenarios:**
  * Game player data modeling with matchmaking systems
  * Retail cart and e-commerce data patterns
  * Banking and financial services payment systems
  * Advanced inverted indexes for complex queries

* **Gained expertise in enterprise-level NoSQL design challenges:**
  * Data modeling best practices for NoSQL systems
  * Performance optimization and cost management
  * Integration patterns with other AWS services
  * Design challenges for retail and financial applications
