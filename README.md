# Manufacturing-Data-Analysis
Transforming manufacturing raw data into actionable insights for process efficiency.

Project Overview: Experimental Data Management System
"A streamlined SQL-based system for tracking material science experiments, featuring automated data integration through Triggers."

![캡처1](https://github.com/user-attachments/assets/e14f1dcb-0109-4e2a-b04b-821ba592a4c5)

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
