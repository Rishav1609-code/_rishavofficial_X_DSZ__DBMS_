# UNIT - 1: DATABASE SYSTEM ARCHITECTURE

## 1. Define data abstraction.
Data abstraction is the process of hiding unnecessary details from users and showing only the essential information.

**Levels of data abstraction:**
*   **View Level** (External Level)
*   **Logical Level** (Conceptual Level)
*   **Physical Level** (Internal Level)

## 2. What is an ER diagram?
An Entity Relationship (ER) diagram is a graphical representation of entities, attributes and relationships in a database.
```bash
  +---------+                       +----------+
  | STUDENT |                       |  COURSE  |
  +---------+                       +----------+
  | Roll No |-------< Studies >-----| Course ID|
  | Name    |                       | Title    |
  +---------+                       +----------+
```

## 3. What is entity integrity?
Entity integrity states that the primary key of a relation cannot be NULL because it uniquely identifies each record.
Example: Student (Roll_No, Name)
Roll_No (Primary Key) must never be NULL.

## 4. What is referential integrity?
Referential integrity ensures that a foreign key value must either match an existing primary key value in another table or be NULL.

**Student Table**
| Roll_No | Name |
| :--- | :--- |
| 101 | Ravi |
| 102 | Priya |

**Result Table**
| Roll_No | Marks |
| :--- | :--- |
| 101 | 90 |
| 102 | 85 |

Roll_No in Result is a foreign key and must exist in Student table.

## 5. What is a foreign key?
A foreign key is an attribute in one table that refers to the primary key of another table.
```bash
    STUDENT Table                 RESULT Table
  +---------+-------+         +---------+-------+
  | Roll_No | Name  |         | Roll_No | Marks |
  |   (PK)  |       |         |   (FK)  |       |
  +---------+-------+         +---------+-------+
  |   101   | Ravi  | <-------|   101   |  90   |
  |   102   | Priya |         |   102   |  85   |
  +---------+-------+         +---------+-------+
```
Roll_No in RESULT is a foreign key.

## 6. What is a super key?
A super key is a set of one or more attributes that uniquely identifies a tuple (record) in a table.
Example: Student (Roll_No, Name, Email)
Possible super keys:
*   Roll_No
*   Email
*   Roll_No + Name

## 7. What is a schema?
A schema is the logical structure or blueprint of a database that defines tables, attributes and relationships.
Example: STUDENT (Roll_No, Name, Dept)
This structure is called a schema.

## 8. Define cardinality.
Cardinality specifies the number of entities participating in a relationship.
Types:
*   **One-to-One (1:1)**
*   **One-to-Many (1:M)**
*   **Many-to-One (M:1)**
*   **Many-to-Many (M:N)**

## 9. What is data independence?
Data independence is the ability to change the database schema without affecting application programs.
Types:
*   Physical data independence
*   Logical data independence

## 10. Differentiate between logical and physical data independence.
| Logical Data Independence | Physical Data Independence |
| :--- | :--- |
| 1. Changes logical schema | 1. Changes physical schema |
| 2. More difficult to achieve | 2. Easier to achieve |
| 3. Does not affect application programs | 3. Does not affect logical structure |
| 4. Example: Adding a column | 4. Example: Changing storage device |

## 11. Define instance in DBMS.
An instance is the collection of information stored in the database at a particular moment of time.

| Roll_No | Name |
| :--- | :--- |
| 101 | Ravi |
| 102 | Priya |

The current data stored is called an instance.

## 12. What is a data model?
A data model is a collection of concepts used to describe the structure of a database.
Types of data models:
*   ER Model
*   Relational Model
*   Network Model
*   Object-Oriented Model

## 13. Define entity.
An entity is a real-world object or thing that can be identified uniquely and about which data is stored.
Examples: Student, Employee, Book, Course

## 14. What are data manipulation operations?
Data manipulation operations are operations used to retrieve and modify data in a database.
Main operations:
*   **INSERT** - Add new records
*   **DELETE** - Remove records
*   **UPDATE** - Modify records
*   **SELECT** - Retrieve records

---

## 1. List the advantages of DBMS.
The main advantages of DBMS are:
1. It minimizes data redundancy and inconsistency.
2. It ensures data integrity.
3. It provides data security.
4. It supports data sharing and concurrency control.
5. It provides data independence.
6. It enforces standards and reduces data isolation.
7. It supports backup and recovery.
8. It increases productivity and efficiency.
9. It provides multiple user views.
10. It supports complex relationships.
11. It enforces integrity constraints.
12. It provides better data administration.

```bash
                  DBMS Architecture
        +--------+   +--------+   +--------+
        | User 1 |   | User 2 |   | User n |
        +--------+   +--------+   +--------+
            ^            ^            ^
            |            |            |
            v            v            v
     +----------------------------------------+
     |      Application Programs / Queries    |
     +----------------------------------------+
                        ^
                        |
                        v
     +----------------------------------------+
     |             DBMS Software              |
     +----------------------------------------+
                        ^
                        |
                        v
                 +--------------+
                 |   Database   |
                 |(Stored Data) |
                 +--------------+
```

## 2. Explain the advantages of DBMS over file processing system.
DBMS provides many advantages over the traditional file processing system.

| Basis | File Processing System | DBMS |
| :--- | :--- | :--- |
| 1. Data Redundancy | High redundancy and inconsistency of data. | Redundancy is minimized and consistency is maintained. |
| 2. Data Sharing | Limited data sharing. | Data can be shared among multiple users. |
| 3. Data Independence | No data independence. Changes in data structure affect programs. | Provides logical and physical data independence. |
| 4. Data Security | Security is weak and depends on the application programs. | Centralized security and access control. |
| 5. Integrity Constraints | Integrity constraints are difficult to implement. | Integrity constraints are defined and enforced by DBMS. |
| 6. Concurrency Control | Concurrency control is difficult. | Built-in concurrency control mechanisms. |
| 7. Backup and Recovery | Backup and recovery are difficult and time consuming. | Provides easy and efficient backup and recovery. |
| 8. Data Isolation | High data isolation. | Low data isolation. |
| 9. Data Access | Data access is difficult and requires program development. | Easy data access using queries (e.g., SQL). |
| 10. Maintenance | High maintenance cost. | Lower maintenance cost. |
| 11. Flexibility | Less flexible. | More flexible. |

## 3. Explain Entity, Attribute, and Relationship.
In ER (Entity-Relationship) model, the basic components are Entity, Attribute and Relationship.
*   **(i) Entity**: An entity is a real-world object or concept that can be distinguished from other objects.
    Example: Student, Book, Department, Employee, etc.
*   **(ii) Attribute**: An attribute is a property or characteristic of an entity. It describes the entity.
    Example: For entity STUDENT -> Roll_No, Name, Age, Gender, Address.
*   **(iii) Relationship**: A relationship is an association or connection between two or more entities.
    Example: ENROLLS (between STUDENT and COURSE), WORKS_FOR (between EMPLOYEE and DEPARTMENT).

```bash
                   Example of ER Diagram
         (Roll_No)   (Name)   (Age)               (Course_ID)  (Course_Name)
             \         |        /                       \           /
              \        |       /                         \         /
               +---------------+      1       N       +---------------+
(Gender)-------|    STUDENT    |----< ENROLLS >-------|     COURSE    |
               +---------------+                      +---------------+
                   /
                  /
             (Address)
```

---

## 4. Explain Data Abstraction and its Levels.
**Ans:** Data Abstraction is the process of hiding the internal details of data storage and showing only the essential information to the users. It helps in reducing complexity and provides data independence.

**Levels of Data Abstraction:**
1.  **Physical Level (Internal Level):**
    *   It is the lowest level of abstraction.
    *   Describes how data is actually stored in the database.
    *   Deals with storage devices, file organization, indexes, etc.
    *   Used by DBMS storage manager.
2.  **Logical Level (Conceptual Level):**
    *   It is the middle level of abstraction.
    *   Describes what data is stored and the relationships among data.
    *   Hides the details of physical storage.
    *   Used by database designers.
3.  **View Level (External Level):**
    *   It is the highest level of abstraction.
    *   Shows only the required data to the user.
    *   Different users can have different views of the same data.
    *   Used by end users.

```bash
      +-------------------------+
      |       VIEW LEVEL        | ---> Shows only the required
      |      (User's View)      |      data to the user.
      +-------------------------+
                  ^
                  |
                  v
      +-------------------------+
      |      LOGICAL LEVEL      | ---> Describes what data is
      | (Structure of Database) |      stored and relationships.
      +-------------------------+
                  ^
                  |
                  v
      +-------------------------+
      |      PHYSICAL LEVEL     | ---> Describes how data is stored
      |  (Actual Data Storage)  |      in the database.
      +-------------------------+
```

**Conclusion:** Data Abstraction allows users to see only the necessary data without worrying about the complexity of how data is stored. It provides data independence and security in a database system.

## 5. Explain the Role of a Database Administrator (DBA).
**Ans:** A Database Administrator (DBA) is a person who is responsible for managing, controlling and maintaining the database system.

**Role of DBA:**
1. Designs the database structure and schema.
2. Controls user access and manages security.
3. Performs backup and recovery of data.
4. Monitors database performance and optimizes queries.
5. Ensures data integrity, consistency and accuracy.
6. Manages storage space and resources.
7. Installs, configures and upgrades DBMS software.

```bash
    |   Security  |      |   Backup &  |      | Performance |
    |  Management |      |   Recovery  |      |  Monitoring |
           |                    |                    |
    +-------------------------------------------------------+
    |                        D B A                          |
    +-------------------------------------------------------+
           |                    |                    |
    |    User     |      |   Database  |      |     Data    |
    |  Management |      | Maintenance |      |  Integrity  |
```

**Conclusion:** The DBA plays a vital role in ensuring that the database is secure, available, consistent and performing efficiently to meet the organization's needs.

## 6. Discuss the Duties and Responsibilities of a DBA.
**Ans:** The DBA performs various duties and responsibilities to ensure the smooth functioning of the database system.

**Duties and Responsibilities:**
1.  **Database Installation:** Installs and configures the DBMS software.
2.  **Database Design:** Creates database schema, tables, views, relationships, etc.
3.  **Security Management:** Creates users, assigns privileges and controls access.
4.  **Backup Management:** Takes regular backups and stores them safely.
5.  **Recovery Management:** Restores the database in case of failure or disaster.
6.  **Performance Tuning:** Monitors performance and optimizes queries, indexes and storage.
7.  **Data Integrity:** Ensures accuracy, consistency and validity of data.
8.  **Storage Management:** Allocates and manages storage space efficiently.
9.  **Monitoring & Troubleshooting:** Monitors system health and solves problems.
10. **Documentation:** Maintains records, reports and documentation of the database system.

```bash
                               +---------+
                               |   DBA   |
                               +---------+
                                    |
  +---------------------------------+----------------------------------+
  |         |         |         |         |         |         |        |
  v         v         v         v         v         v         v        v
+------+ +--------+ +------+ +--------+ +-----------+ +-----------+ +----------+ +-------------+
|Design| |Security| |Backup| |Recovery| |Performance| |Maintenance| |Monitoring| |Documentation|
+------+ +--------+ +------+ +--------+ +-----------+ +-----------+ +----------+ +-------------+
```

**Conclusion:** The DBA is responsible for the overall management of the database system including design, security, backup, recovery, performance and maintenance.

---

## 7. What are the challenges faced by a DBA?
A Database Administrator (DBA) is responsible for managing the database system. The major challenges faced by a DBA are:
1.  **Data Security:** Protecting data from unauthorized access, breaches and cyber threats.
2.  **Data Integrity:** Ensuring accuracy, consistency and validity of data.
3.  **System Performance:** Tuning the database for better performance and handling heavy workloads.
4.  **Backup and Recovery:** Ensuring regular backup and quick recovery in case of failure or disaster.
5.  **Concurrency Control:** Managing multiple users accessing data simultaneously without conflicts.
6.  **Storage Management:** Managing large volumes of data efficiently and optimizing storage space.
7.  **High Availability:** Ensuring the database is available 24x7 with minimal downtime.
8.  **Evolving Technology:** Keeping up with new technologies, tools and DBMS updates.
9.  **User Management:** Managing users, roles and permissions effectively.
10. **Cost Management:** Balancing hardware, software and maintenance costs.
11. **Compliance and Standards:** Following legal regulations and organizational policies.

## 8. What do you mean by data abstraction? Explain three levels of data abstraction.
Data Abstraction means hiding the unnecessary details of data and showing only the relevant information to the users. It helps in reducing complexity and improves security. DBMS provides data abstraction at three levels.

*   **(i) External / View Level:**
    *   It is the highest level of abstraction.
    *   It shows only the part of database required by a particular user.
    *   Different users can have different views.
    *   It hides the rest of the database.
*   **(ii) Conceptual Level:**
    *   It is the community view of the entire database.
    *   It describes what data is stored in the database and the relationships among the data.
    *   It hides the physical storage details.
*   **(iii) Internal / Physical Level:**
    *   It is the lowest level of abstraction.
    *   It describes how the data is actually stored in the database.
    *   It includes details of storage structure, indexes, file organization, etc.
    *   This level is hidden from the users.

```bash
        +-------------------------+
        |  External / View Level  |
        |       (User Level)      |
        +-------------------------+
                    |
                    v
        +-------------------------+
        |    Conceptual Level     |
        |     (Logical Level)     |
        +-------------------------+
                    |
                    v
        +-------------------------+
        | Internal / Physical Level|
        |     (Storage Level)     |
        +-------------------------+
```

## 9. Explain authorization and authentication. (Difference)
*   **(i) Authentication:** It is the process of verifying the identity of a user. It ensures that the user is who he/she claims to be.
    Example: Login using username and password, biometric verification, OTP.
*   **(ii) Authorization:** It is the process of determining what an authenticated user is allowed to do or access. It ensures that the user has permission to access certain data or perform specific operations.
    Example: Giving read, write, update or delete permissions on a table.

```bash
         Authentication vs Authorization

     +----------------+       +----------------+
     | Authentication |       |  Authorization |
     | (Who are you?) |       |(What can you do?)|
     +----------------+       +----------------+
             |                        |
             v                        v
     +----------------+       +----------------+
     | Verify Identity|       |Check Permissions|
     |(e.g., Password,|       |(e.g., Read,    |
     | Biometric, OTP)|       | Write, Update, |
     |                |       | Delete)        |
     +----------------+       +----------------+
```

**Difference between Authentication and Authorization**
| Basis | Authentication | Authorization |
| :--- | :--- | :--- |
| 1. Meaning | Verifies the identity of a user. | Determines what the user is allowed to do. |
| 2. Purpose | To ensure the user is genuine. | To ensure the user has permission to access resources. |
| 3. Question Asked | "Who are you?" | "What are you allowed to do?" |
| 4. Occurs | First (before authorization). | After authentication. |
| 5. Example | Login with password, fingerprint, OTP. | Allowing read/write access to database objects. |
| 6. Result | Establishes identity. | Grants or denies access to resources. |
| 7. Failure | Access denied (user is not recognized). | Access denied (user has no permission). |

---

## 10. Explain the Three-Schema Architecture of DBMS.
The Three-Schema Architecture is a framework used in DBMS to separate user applications from the physical database. It provides data abstraction and data independence.

1.  **External Level (View Level):**
    *   It is the highest level of abstraction.
    *   It shows only the data required by a particular user.
    *   Different users can have different views of the database.
    *   It hides the remaining database details.
    *Example:* Student sees marks only, while administrator sees all records.
2.  **Conceptual Level (Logical Level):**
    *   It describes the entire database structure.
    *   It contains entities, attributes, relationships and constraints.
    *   It is independent of physical storage details.
    *Example:* Student (Roll_No, Name, Dept)
3.  **Internal Level (Physical Level):**
    *   It is the lowest level of abstraction.
    *   It describes how data is actually stored on disk.
    *   Includes file organization, indexing, storage blocks, access paths etc.

```bash
                 Three-Schema Architecture

                 +---------------------+     }
                 |    External Level   |     } Multiple
                 |     (User Views)    |     } User Views
                 +---------------------+     }
  External/                 ^
  Conceptual                |
  Mapping                   v
                 +---------------------+     } Community
                 |   Conceptual Level  |     } View of
                 |   (Logical Schema)  |     } Database
                 +---------------------+     }
  Conceptual/               ^
  Internal                  |
  Mapping                   v
                 +---------------------+     } How data
                 |    Internal Level   |     } is stored
                 |  (Physical Schema)  |     }
                 +---------------------+     }
                            ^
                            |
                            v
                 +---------------------+     } Actual
                 |   Physical Storage  |     } Stored
                 |      (Database)     |     } Data
                 +---------------------+     }
```

**Mapping in Three-Schema Architecture:**
1.  **External <-> Conceptual Mapping:** It connects user views with the conceptual schema.
2.  **Conceptual <-> Internal Mapping:** It connects the logical schema with physical storage structure.

**Advantages:**
*   Provides data abstraction.
*   Ensures data independence.
*   Enhances security.
*   Simplifies database maintenance.
*   Multiple users can access different views of the same database.

**Conclusion:** The Three-Schema Architecture consists of External Level, Conceptual Level and Internal Level. It separates user views from physical storage and helps achieve logical and physical data independence, making database management easier and more efficient.

---

## 11. Explain Strong and Weak Entities.

*   **Strong Entity:**
    An entity which has its own primary key and can exist independently is called strong entity.
    *Characteristics:*
    1.  Has a primary key.
    2.  Can exist independently.
    3.  Not dependent on any other entity.
    4.  Represented by a single rectangle.
    5.  Each entity instance is uniquely identified.
    *Example:* Student

```bash
    Example : Student                Example : Dependent of an Employee

       STUDENT                        +-------------+           +-------------+
  +----------------+                  |   EMPLOYEE  |           |  DEPENDENT  |
  +----------------+                  +-------------+           +-------------+
  | Student_ID (PK)|                  | Emp_ID (PK) |----<Has>--| Dep_Name    |
  | Name           |                  | Name        |           | (Partial Key|
  | Department     |                  +-------------+           | Age         |
  +----------------+                                            | Relationship|
                                                                +-------------+
```

*   **Weak Entity:**
    An entity which does not have a primary key of its own and depends on another entity for its identification is called weak entity.
    *Characteristics:*
    1.  Does not have a complete primary key.
    2.  Depends on a strong entity.
    3.  Represented by a double rectangle.
    4.  Identified by combining its partial key with the primary key of the owner entity.
    5.  Cannot exist independently.
    *Example:* Dependent of an Employee

**Difference between Strong and Weak Entity:**
| Basis | Strong Entity | Weak Entity |
| :--- | :--- | :--- |
| 1. Key | Has primary key | No complete primary key |
| 2. Existence | Can exist independently | Cannot exist independently |
| 3. Dependency | Not dependent on any other entity | Depends on a strong entity |
| 4. Representation | Single rectangle | Double rectangle |
| 5. Identification | Identified by its own key | Identified by partial key + owner key |
| 6. Example | Student, Doctor, Department | Dependent, Order_Item, Employee_Child |

**Conclusion:** Strong entities have their own identity and can exist on their own. Weak entities depend on strong entities for their existence and identification.

## 12. Draw the ER diagram of a Hospital Management System and explain.
A Hospital Management System is used to store information about patients, doctors, departments, appointments and treatments.

**Main Entities:**
1.  Patient
2.  Doctor
3.  Department
4.  Appointment
5.  Treatment

**Explanation of Entities:**
1.  **Patient:** Stores details of patients. Attributes: Patient_ID, Patient_Name, Age, Address.
2.  **Doctor:** Stores information about doctors. Attributes: Doctor_ID, Doctor_Name, Specialization.
3.  **Department:** Stores details of hospital departments. Attributes: Dept_ID, Dept_Name.
4.  **Appointment:** Stores appointment details of patients with doctors. Attributes: App_ID, Date, Time.
5.  **Treatment:** Stores treatment information given to patients. Attributes: Treat_ID, Disease, Medicine, Amount.

```bash
                +----------------+
                |   DEPARTMENT   |
                +----------------+
                | Dept_ID (PK)   |
                | Dept_Name      |
                +----------------+
                        | 1
                        |
                   < Works In >
                        |
                        | N
                +----------------+
                |     DOCTOR     |
                +----------------+
                | Doctor_ID (PK) |
                | Doctor_Name    |
                | Specialization |
                +----------------+
                        | 1
                        |
                    < Attends >
                        |
                        | N
+----------------+      |      +----------------+
|    PATIENT     |      |      |  APPOINTMENT   |
+----------------+      |      +----------------+
| Patient_ID (PK)|   1  |    N | App_ID (PK)    |
| Patient_Name   |---< Books >-| Date           |
| Age            |             | Time           |
| Address        |             +----------------+
+----------------+                     | 1
                                       |
                                  < Receives >
                                       |
                                       | N
                               +----------------+
                               |   TREATMENT    |
                               +----------------+
                               | Treat_ID (PK)  |
                               | Disease        |
                               | Medicine       |
                               | Amount         |
                               +----------------+
```

**Relationships:**
1.  Department works in Doctor. (1 Department - Many Doctors)
2.  Doctor attends Appointment. (1 Doctor - Many Appointments)
3.  Patient books Appointment. (1 Patient - Many Appointments)
4.  Appointment receives Treatment. (1 Appointment - Many Treatments)

---

## 13. Design an ER diagram for a University / Student Management System.

**(i) Entities and Attributes:**
1.  **STUDENT:** Student_ID (PK), Name, Gender, DOB, Address, Phone
2.  **DEPARTMENT:** Dept_ID (PK), Dept_Name, HOD
3.  **COURSE:** Course_ID (PK), Course_Name, Credits
4.  **FACULTY:** Faculty_ID (PK), Faculty_Name, Designation, Phone
5.  **EXAM:** Exam_ID (PK), Exam_Name, Date, Semester
6.  **RESULT:** Result_ID (PK), Marks, Grade

**Relationships:**
1.  Department - Has - Student (1 : M)
2.  Department - Offers - Course (1 : M)
3.  Faculty - Teaches - Course (1 : M)
4.  Student - Enrolls In - Course (M : N)
5.  Student - Appears For - Exam (M : N)
6.  Exam - Generates - Result (1 : M)

```bash
+------------+       M                 1 +-----------+
| DEPARTMENT |----< Has >----------------|  STUDENT  |
+------------+                           +-----------+
|Dept_ID (PK)|                           |Student_ID |
|Dept_Name   |   +----------+          M |Name       |
|HOD         |   |          |      +-----|Gender     |
+------------+   |          |      |     |DOB        |
      | 1        |          |      |     |Address    |
      |          |          |      |     |Phone      |
   < Offers >    |          |      |     +-----------+
      |          |          |      |           | M
      | M        v          v      v           |
+------------+   M      < Enrolls >      < Appears >
|   COURSE   |              In               For
+------------+              | M                | M
|Course_ID(PK|              |            +-----------+
|Course_Name |<-------------+            |   EXAM    |
|Credits     |                           +-----------+
+------------+                           |Exam_ID(PK)|
      | 1                                |Exam_Name  |
      |                                  |Date       |
   < Teaches >                           |Semester   |
      |                                  +-----------+
      | M                                      | 1
+------------+                                 |
|  FACULTY   |                           < Generates >
+------------+                                 |
|Faculty_ID  |                                 | M
|Faculty_Name|                           +-----------+
|Designation |                           |  RESULT   |
|Phone       |                           +-----------+
+------------+                           |Result_ID  |
                                         |Marks      |
                                         |Grade      |
                                         +-----------+
```

**(iii) Relational Tables:**
1.  **DEPARTMENT:** Dept_ID (PK), Dept_Name, HOD
2.  **STUDENT:** Student_ID (PK), Name, Gender, DOB, Address, Phone, Dept_ID (FK)
3.  **COURSE:** Course_ID (PK), Course_Name, Credits, Dept_ID (FK), Faculty_ID (FK)
4.  **FACULTY:** Faculty_ID (PK), Faculty_Name, Designation, Phone
5.  **EXAM:** Exam_ID (PK), Exam_Name, Date, Semester
6.  **ENROLLMENT (for M:N relationship):** Student_ID (FK), Course_ID (FK)
7.  **RESULT:** Result_ID (PK), Marks, Grade, Student_ID (FK), Exam_ID (FK)
8.  **PAYMENT (Optional):** Payment_ID (PK), Payment_Date, Amount, Mode, Student_ID (FK)
*Note: Payment table is optional if fee payment management is required.*

---

## 14. Supreme products manufacture products like pressure cookers, cook wares, water purifiers, food processors etc. The company markets its product to wholesalers all over the country and dealers sell them to customer. The company has five regional offices. Sales persons contact dealers and explain about products, incentives offered, panting programs for wholesalers and demonstration for customer etc. Dealers place orders with the sales persons attached with the regional office of their location. After receiving goods they make payments, which may be in installments. Company would like to develop a system to monitor sale of different products, performance of salespersons and following: order from wholesalers.
Do the following:
i) Identify entities, attributes and relationship.
ii) Draw an E-R diagram.
iii) Convert this to relational tables.

**(i) Identify entities, attributes and relationship.**
*A. Entities and Attributes:*
1.  **PRODUCT:** Product_ID (PK), Product_Name, Category, Price
2.  **REGIONAL_OFFICE:** Office_ID (PK), Office_Name, Location
3.  **SALESPERSON:** Salesperson_ID (PK), Name, Phone, Target, Office_ID (FK)
4.  **DEALER (WHOLESALER):** Dealer_ID (PK), Dealer_Name, Address, Phone, City
5.  **CUSTOMER:** Customer_ID (PK), Customer_Name, Address, Phone
6.  **ORDER:** Order_ID (PK), Order_Date, Quantity, Dealer_ID (FK), Salesperson_ID (FK)
7.  **PAYMENT:** Payment_ID (PK), Payment_Date, Amount, Mode, Order_ID (FK)

*B. Relationships:*
1.  Regional Office — Employs — Salesperson
    One Regional Office employs many Salespersons. (1 : M)
2.  Salesperson — Receives / Handles — Order
    One Salesperson receives many orders. (1 : M)
3.  Dealer — Places — Order
    One Dealer places many orders. (1 : M)
4.  Order — Contains — Product
    Many Orders contain many Products. (M : N)
5.  Order — Has — Payment
    One Order has many Payments. (1 : M)
6.  Dealer — Sells To — Customer
    One Dealer sells to many Customers. (1 : M)

```bash
+-----------+  1           M +-------------+  1         M +---------+
| REGIONAL  |----< Employs >-| SALESPERSON |---< Handles >|  ORDER  |
|  OFFICE   |                +-------------+              +---------+
+-----------+                                                  | 1
                                                               |
+-----------+  1           M +-------------+                   |
|  DEALER   |----< Places >--|             |               < Has >
+-----------+                |             |                   |
      | 1                    |             |                   | M
      |                      |             |     N         +---------+
   < Sells >                 |             |---< Contains >| PRODUCT |
      To                     |             |               +---------+
      |                      |             |
      | M                    +-------------+
+-----------+
| CUSTOMER  |
+-----------+
```

**(iii) Relational Tables:**
1.  **PRODUCT:** Product_ID (PK), Product_Name, Category, Price
2.  **REGIONAL_OFFICE:** Office_ID (PK), Office_Name, Location
3.  **SALESPERSON:** Salesperson_ID (PK), Name, Phone, Target, Office_ID (FK)
4.  **DEALER:** Dealer_ID (PK), Dealer_Name, Address, Phone, City
5.  **CUSTOMER:** Customer_ID (PK), Customer_Name, Address, Phone, Dealer_ID (FK)
6.  **ORDER:** Order_ID (PK), Order_Date, Quantity, Dealer_ID (FK), Salesperson_ID (FK)
7.  **PRODUCT_ORDER (for M:N relationship):** Order_ID (FK), Product_ID (FK), Quantity
8.  **PAYMENT:** Payment_ID (PK), Payment_Date, Amount, Mode, Order_ID (FK)

---

## 15. Some of the entries relevant to a technical university are given below: For each of them, indicate the type of relationship existing among them (for example, one-to-one, one-to-many or many-to-many). Draw a relationship diagram for each of them.

**(i) STUDENT and ENGG-BRANCH (students register for engg branches)**
*Relationship Type :* Many-to-One (M : 1)
*   Many students can register in one engineering branch.
*   One student belongs to only one branch.
```bash
        M                             1
  +---------+                     +-------------+
  | STUDENT |----< Registers >----| ENGG-BRANCH |
  +---------+         For         +-------------+
```

**(ii) BOOK and BOOK-COPY (books have copies)**
*Relationship Type :* One-to-Many (1 : M)
*   One book can have many copies.
*   One copy belongs to only one book.
```bash
        1                             M
  +---------+                     +-------------+
  |   BOOK  |-------< Has >-------|  BOOK-COPY  |
  +---------+                     +-------------+
```

**(iii) ENGG-BRANCH and SECTION (branches have sections)**
*Relationship Type :* One-to-Many (1 : M)
*   One branch can have many sections.
*   One section belongs to only one branch.
```bash
        1                             M
  +-------------+                 +-------------+
  | ENGG-BRANCH |---< Has >-------|   SECTION   |
  +-------------+                 +-------------+
```

**(iv) SECTION and CLASS-ROOM (sections are scheduled in classrooms)**
*Relationship Type :* Many-to-One (M : 1)
*   Many sections can be scheduled in one classroom (at different times).
*   One section is scheduled in only one classroom at a time.
*Note : At a particular time slot one classroom is allotted to only one section.*
```bash
        M                             1
  +---------+                     +-------------+
  | SECTION |---< Scheduled In >--| CLASS-ROOM  |
  +---------+                     +-------------+
```

**(v) FACULTY and ENGG-BRANCH (faculty teaches in a particular branch)**
*Relationship Type :* Many-to-One (M : 1)
*   Many faculty members can teach in the same branch.
*   One faculty member is associated with one branch.
```bash
        M                             1
  +---------+                     +-------------+
  | FACULTY |----< Teaches In >---| ENGG-BRANCH |
  +---------+                     +-------------+
```

**Summary Table**
| Sl. No. | Entities | Relationship Type |
| :--- | :--- | :--- |
| (i) | STUDENT - ENGG-BRANCH | Many-to-One (M : 1) |
| (ii) | BOOK - BOOK-COPY | One-to-Many (1 : M) |
| (iii) | ENGG-BRANCH - SECTION | One-to-Many (1 : M) |
| (iv) | SECTION - CLASS-ROOM | Many-to-One (M : 1) |
| (v) | FACULTY - ENGG-BRANCH | Many-to-One (M : 1) |

---

## 16. What is Data dictionary? What is metadata?
Data dictionary is a centralized repository that stores information about all the data (objects) in a database.
The data stored in the data dictionary is called **metadata**.

**(i) Data Dictionary:**
*   It is a system catalog maintained by the DBMS.
*   It contains definitions and descriptions of all database objects.
*   It stores technical information about data.
*   It is used by the DBMS to manage and control the database.

**(ii) Metadata:**
*   Metadata means "data about data".
*   It is the information that defines the structure, properties and relationships of data.
*   It describes the data, not the actual data.
*   Metadata is stored in the data dictionary.

```bash
    +------------------------+
    |  Users / Applications  |
    +------------------------+
                ^
                |
                v
    +------------------------+
    |          DBMS          |
    +------------------------+
                ^
                |
                v
       +------------------+
       |                  |
       |  Data Dictionary |
       |    (Metadata)    |
       |                  |
       +------------------+
```

**Information Stored in Data Dictionary**
| Information Type | Description |
| :--- | :--- |
| Table Information | Names of tables, attributes, data types, sizes. |
| View Information | Names of views, their definitions. |
| Index Information | Indexes on tables and views. |
| User Information | Users, roles and privileges. |
| Storage Information | File names, locations, sizes. |
| Constraint Information | Primary key, foreign key, unique, check constraints. |
| Authorization Information | Access rights and permissions. |

## 17. What is the difference between DELETE, TRUNCATE and DROP commands?
| | DELETE | TRUNCATE | DROP |
| :--- | :--- | :--- | :--- |
| **Meaning** | Deletes specific rows from a table. | Removes all rows from a table. | Deletes the entire table structure from the database. |
| **Type** | DML Command | DDL Command | DDL Command |
| **WHERE Clause** | Can use WHERE clause. | Cannot use WHERE clause. | Not applicable. |
| **Rows Affected** | Deletes selected rows. | Deletes all rows. | Deletes table structure and all rows. |
| **Rollback** | Can be rolled back. | Cannot be rolled back (in most DBMS). | Cannot be rolled back. |
| **Auto Increment (Identity)** | Identity value is not reset. | Identity value is reset. | Table is removed, so identity is also removed. |
| **Triggers** | Fires DELETE triggers. | Does not fire DELETE triggers. | Fires DROP triggers. |
| **Space** | Space is not deallocated. | Space is deallocated. | All space is deallocated. |
| **Performance** | Slower (row-by-row deletion). | Faster (deletes all rows at once). | Fastest (removes table). |
| **Command Type** | Data Manipulation Language | Data Definition Language | Data Definition Language (and Data Control Language) |
| **Example** | `DELETE FROM Student WHERE RollNo = 101;` | `TRUNCATE TABLE Student;` | `DROP TABLE Student;` |

## 18. Differentiate between DDL and DML.
**DDL (Data Definition Language)** is used to define or alter the structure of database objects.
**DML (Data Manipulation Language)** is used to retrieve and manipulate the data in database.

| Basis | DDL | DML |
| :--- | :--- | :--- |
| 1. Full Form | Data Definition Language | Data Manipulation Language |
| 2. Purpose | Used to define, modify or remove database structures. | Used to access and manipulate data stored in database. |
| 3. Type of Command | Definition Commands | Manipulation Commands |
| 4. Examples | CREATE, ALTER, DROP, TRUNCATE, RENAME | SELECT, INSERT, UPDATE, DELETE |
| 5. Works On | Database objects (tables, views, indexes, schemas, etc.) | Data (rows) in tables. |
| 6. Affects Data | Does not affect data directly. | Affects data. |
| 7. Transaction | Most DDL commands cause an implicit commit. | Can be rolled back (transaction control commands can be used). |
| 8. Rollback | Generally cannot be rolled back. | Can be rolled back. |
| 9. Speed | Executed once or rarely. | Executed frequently. |
| 10. Examples with Syntax | `CREATE TABLE Student (...);`<br>`ALTER TABLE Student ADD Age INT;`<br>`DROP TABLE Student;`<br>`TRUNCATE TABLE Student;` | `SELECT * FROM Student;`<br>`INSERT INTO Student VALUES (...);`<br>`UPDATE Student SET Age = 20 WHERE RollNo = 101;`<br>`DELETE FROM Student WHERE RollNo = 101;` |

---

