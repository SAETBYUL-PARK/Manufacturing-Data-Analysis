# Manufacturing-Data-Analysis
To address data silo issues in real-world material engineering, I implemented a relational database model that automates data integration through SQL Triggers.

Project Overview: Experimental Data Management System
"A streamlined SQL-based system for tracking material science experiments, featuring automated data integration through Triggers."

![캡처1](https://github.com/user-attachments/assets/e14f1dcb-0109-4e2a-b04b-821ba592a4c5)

Entity Relationship Diagram (ERD) Description
1. Design Objective
"This database is designed to systematically manage the organic relationship between Raw Materials, Manufacturing Processes, and their subsequent Test Results. The primary focus is on minimizing data redundancy and ensuring high traceability of experimental outcomes based on variable shifts in material composition and processing conditions."

2. Entity Relationships
material_component to test_result (1:1)
Each material entry is mapped to exactly one test result record. * Logic: When a new material is registered, a Database Trigger automatically initializes a corresponding row in the test_result table.

Benefit: This ensures a strict 1:1 mapping between a specific chemical composition and its experimental outcome, preventing data duplication and ensuring 100% traceability.

② process to test_result (1:1)
A specific process run is uniquely linked to one test result.

Logic: Since the system is designed to track a single experimental "Material-Process" pair, each process_id in the test_result table acts as a unique reference for that specific trial.

Benefit: It simplifies the data pipeline by treating each manufacturing trial as a unique, non-repeatable event, which is critical for high-precision materials research.

③ test_result (Associative Entity)
This table serves as an intersection entity that captures the unique combination of a specific material and a specific process.

It centralizes the final experimental metrics, ensuring that every data point is contextually linked to its source material and processing history.

3. Data Automation: Trigger Implementation
"Automating Data Integration & Ensuring Integrity"

To streamline the data entry workflow, an AFTER INSERT Trigger was implemented on the material_component table.

Upon the insertion of new process parameters, the system automatically identifies the most recent material_id and initializes a corresponding record in the test_result table. This prevents data silos and ensures that experimental results are never orphaned from their metadata.


💡 Key Highlights
Relational Architecture: Designed a normalized schema to decouple material compositions from processing variables, ensuring 100% data traceability.

Workflow Automation: Implemented SQL Triggers to automatically link process parameters with material data, reducing manual entry errors and maintaining data integrity.

Industrial Use-case: Modeled after real-world ceramic/material engineering scenarios (e.g., Silicastone purity & Firing cycles) to demonstrate domain-specific database application.

🛠 Tech Stack
Database: MySQL

Language: SQL

Features: Triggers, Foreign Key Constraints, Auto-incrementation, Relational Mapping

📖 How to Use
Define Process Parameters:
First, insert specific firing and heating parameters into the process table. This acts as the foundation for manufacturing run.

Register Material & Link to Process:
Insert raw material specifications into material_component. At this stage, you link each material to its corresponding process_id.

Automatic Result Generation:
Once a material is registered, the Database Trigger automatically evaluates the purity and creates a dedicated entry in test_result with an initial status (pass or inspection).

Benefit: It simplifies the data pipeline by treating each manufacturing trial as a unique, non-repeatable event, which is critical for high-precision materials research.
