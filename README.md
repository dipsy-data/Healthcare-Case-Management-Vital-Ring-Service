# Vital Ring Healthcare Case Management System

## Overview
The **Vital Ring Healthcare Case Management System** integrates data from the Vital Ring device to streamline case management, improve service efficiency, and ensure high-quality healthcare delivery. It organizes patient information, manages service requests, and collects feedback to enhance healthcare operations.


## Features

- **Patient Case Management**: Manage cases with detailed patient and service information.
- **Service Requests & Orders**: Capture service requests and process service orders efficiently.
- **Feedback Mechanism**: Incorporates satisfaction feedback for quality assurance.
- **Reports & Analytics**: Generate insights on cases, resolution times, and technician performance.
- **AWS Cloud Deployment**: The database is deployed on AWS Cloud for scalable and reliable access.


## Advantages

- **Enhanced Data Organization**: Improves case tracking and resolution.
- **Streamlined Service Efficiency**: Ensures quicker response times.
- **Integrated Feedback Mechanisms**: Supports continuous quality improvement.


## Use Cases
This system is suitable for:
- Telemedicine and remote healthcare services.
- Public health tracking and community initiatives.
- Insurance claims and patient case studies.
- Elderly care facilities for personalized healthcare plans.


## Database Design

The system's database is designed with:

- **Third Normal Form (3NF)**: Ensures data integrity and eliminates redundancy.
- **Enhanced Entity-Relationship (EER) Model**: Represents entities like patients, agents, and service requests.

Key entities include:

- **Agent**: Employees managing and resolving cases.
- **ServiceRequest**: Tracks issues reported by patients.
- **Feedback**: Records patient satisfaction scores.


## Cloud Deployment
The database is deployed on **AWS Cloud**, allowing seamless integration with applications. Deployment scripts and configurations are included in the repository.


## Business Rules

- **Case Creation**: Cases are created with detailed issue and device information.
- **Case Assignment**: Assigned based on technician expertise and location.
- **Prioritization**: Automated based on severity levels.
- **Quality Assurance**: Random sampling for case reviews.
- **Escalation Procedures**: Unresolved critical issues are escalated automatically.
- **Reporting**: Generate regular reports for management decision-making.


## Sample Queries
1. **Case Count by Customer:**:
   ```sql
   SELECT 
    Cust.CustomerID, Cust.FirstName, Cust.LastName, 
    COUNT(sr.CaseID) AS CaseCount
   FROM 
    Customer Cust
   LEFT JOIN 
    ServiceRequest sr ON Cust.CustomerID = sr.CustomerID
   GROUP BY 
    Cust.CustomerID, Cust.FirstName, Cust.LastName;

2. **Agent Performance:**:
   ```sql
   SELECT 
    Agent.AgentID, FirstName, LastName, t.NumberOfCases
   FROM 
    Agent
   JOIN 
    (SELECT AgentID, COUNT(CaseID) AS NumberOfCases 
     FROM ServiceRequest 
     GROUP BY AgentID) AS t ON Agent.AgentID = t.AgentID
   ORDER BY 
    t.NumberOfCases DESC;
   


### More Queries

Additional SQL queries for analysis and reporting can be found in the `Vital Ring Service - Project Submission.docx` file within this repository.


## Repository Contents

- **SQL Scripts**: Database creation and interaction scripts.
- **Python Colab File**: AWS database deployment details.
- **Documentation**: Detailed explanation of implementation and business rules.


## How to Use

1. **Clone the repository**:
   ```bash
   git clone https://github.com/dipsy-data/Healthcare-Case-Management-Vital-Ring-Service.git
   
2. Deploy the database using the provided scripts.
3. Interact with the database using the SQL queries included.
4. Explore the Python Colab notebook for cloud deployment.


## License

This project is licensed under the MIT License.

---

