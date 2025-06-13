# 🧠 Research Projects Database

This SQL project models a **Research Projects Management System** using relational databases and follows an Entity-Relationship (ER) schema. The database maintains records of research projects, employees, project managers, and funding agencies.

## 🗃️ Key Features

- Tracks research projects with their **name, duration, budget, manager**, and **funding agency**.
- Supports **multiple employees per project** (many-to-many relationship).
- Associates **each project with a single manager** (who is also an employee).
- Links **each project to one funding agency**.
- Ensures **data integrity** using primary and foreign keys.

## 🛠️ Tables Included

1. **Employee**: Contains employee details (SSN, name, salary).
2. **FundingAgency**: Stores information about funding agencies (name, address).
3. **Project**: Stores project details (name, budget, duration).
4. **Project_Manager**: Associates each project with a single employee who manages it.
5. **Employee_Project**: A junction table showing which employees are working on which projects.

## 📂 SQL Table Creation

```sql
-- 1. Employee Table
CREATE TABLE Employee (
    SSN INT PRIMARY KEY,
    Emp_Name VARCHAR(50),
    Salary DECIMAL
);

-- 2. FundingAgency Table
CREATE TABLE FundingAgency (
    Agency_ID INT PRIMARY KEY,
    Name VARCHAR(100),
    Address VARCHAR(255)
);

-- 3. Project Table
CREATE TABLE Project (
    Project_ID INT PRIMARY KEY,
    Name VARCHAR(100),
    Duration INT,  -- Duration in months
    Budget DECIMAL(12, 2)
);

-- 4. Project_Manager Table
CREATE TABLE Project_Manager (
    Project_ID INT PRIMARY KEY,
    Manager_SSN INT,
    FOREIGN KEY (Project_ID) REFERENCES Project(Project_ID),
    FOREIGN KEY (Manager_SSN) REFERENCES Employee(SSN)
);

-- 5. Employee_Project Table
CREATE TABLE Employee_Project (
    SSN INT,
    Project_ID INT,
    Manager_SSN INT,
    PRIMARY KEY (SSN, Project_ID),
    FOREIGN KEY (SSN) REFERENCES Employee(SSN),
    FOREIGN KEY (Project_ID) REFERENCES Project(Project_ID),
    FOREIGN KEY (Manager_SSN) REFERENCES Employee(SSN)
);
![image](https://github.com/user-attachments/assets/10439b21-2e66-47be-9f45-03ac27f5ec00)

![image](https://github.com/user-attachments/assets/af57ad84-5e50-48a7-9194-93cb0407b0aa)


