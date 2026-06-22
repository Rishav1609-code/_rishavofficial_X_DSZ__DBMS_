# UNIT - 2: DBMS 1 MARK QUESTIONS & LONG QUESTIONS

## 1. What is a query language?
* A query language is a formal language used to request data from a database. The most common query language is SQL (Structured Query Language).

## 2. What is Query Processing?
* Query processing is the overall process of parsing, validating, optimizing and executing a query to retrieve the required data from the database.

## 3. What is Query Optimization?
* Query optimization is the process of selecting the most efficient execution plan for a query from among various equivalent execution plans to minimize the cost (time, I/O, etc.).

## 4. What is Query Equivalence?
* Two queries are said to be equivalent if they produce the same result for any legal instance of the database.

## 5. Define Armstrong's Axioms.
The Armstrong's Axioms are the inference rules used to derive all functional dependencies.
(i) **Reflexivity:** If $Y \subseteq X$, then $X \rightarrow Y$
(ii) **Augmentation:** If $X \rightarrow Y$, then $XZ \rightarrow YZ$
(iii) **Transitivity:** If $X \rightarrow Y$ and $Y \rightarrow Z$, then $X \rightarrow Z$

## 6. Define Functional Dependency (FD).
* A functional dependency $X \rightarrow Y$ holds in a relation R if for any two tuples $t_1$ and $t_2$ in R, if $t_1[X] = t_2[X]$ then $t_1[Y] = t_2[Y]$. It is written as $X \rightarrow Y$.

## 7. Define Candidate Key.
* A candidate key is a minimal superkey. That is, it uniquely identifies a tuple in a relation and no proper subset of it can do so.

## 8. What is Normalization?
* Normalization is the process of organizing data in a database to reduce redundancy and avoid insertion, update and deletion anomalies by decomposing relations into smaller relations.

## 9. What is MySQL?
* MySQL is an open-source Relational Database Management System (RDBMS) that uses SQL for database management.

## 10. What is an Index?
* An index is a database object that improves the speed of data retrieval operations on a table at the cost of extra storage and maintenance overhead.

## 11. Which operator performs pattern matching in SQL?
* The LIKE operator is used in SQL to perform pattern matching.

## 12. Which character function can be used to return a specified portion of a character string in SQL?
* The SUBSTRING() (or SUBSTR()) function is used to return a specified portion of a character string.

---

# LONG QUESTIONS

## 1. Write a short note on Degree of Relationship.
* **Degree of Relationship:**
  The degree of a relationship in ER model is defined as the number of entity types participating in that relationship.
* **Types of degree of relationship:**
  1. Unary (Degree 1)
  2. Binary (Degree 2)
  3. Ternary (Degree 3)
  4. N-ary (Degree n)

**Key Points:**
* Degree indicates how many entity sets are involved in a relationship.
* The most common is Binary relationship.
* Higher degree relationships (Ternary, N-ary) are used when interaction among more than two entities is required.

**(1) Unary Relationship (Degree 1):**
* Involves only one entity set.
* Represents a relationship among instances of the same entity set.
Example: An employee manages another employee.
```bash
ER Diagram:
           EMPLOYEE
          +--------+
          |        |
  Manager |        | Subordinate
          v        v
        +------------+
        |  Manages   |
        +------------+
```

**(2) Binary Relationship (Degree 2):**
* Involves two entity sets.
* Most common type of relationship.
Example: A student studies in a college.
```bash
ER Diagram:
+---------+              +-------------+              +---------+
| STUDENT |----(1,N)-----<  Studies In >----(1,1)-----| COLLEGE |
+---------+              +-------------+              +---------+
```

**(3) Ternary Relationship (Degree 3):**
* Involves three entity sets.
* Represents a relationship among three entities simultaneously.
Example: A supplier supplies a part to a project.
```bash
ER Diagram:
           +----------+
           | SUPPLIER |
           +----------+
                |
                |
          +------------+
          |  Supplies  |
          +------------+
           /          \
          /            \
    +------+          +---------+
    | PART |          | PROJECT |
    +------+          +---------+
```

**(4) N-ary Relationship (Degree n):**
* Involves more than three entity sets.
* Rare but necessary in some real-life scenarios.
Example: A lecturer teaches a course to a student in a semester.
```bash
ER Diagram:
+----------+              +---------+
| LECTURER |              | COURSE  |
+----------+              +---------+
          \                /
           \              /
          +----------------+
          |    Teaches     |
          +----------------+
           /              \
          /                \
+----------+              +----------+
| STUDENT  |              | SEMESTER |
+----------+              +----------+
```

**Summary Table:**
| Degree | No. of Entity Sets | Example | Use |
| :--- | :--- | :--- | :--- |
| Unary | 1 | Employee manages Employee | Self-relationship within same entity. |
| Binary | 2 | Student studies in College | Most common relationships. |
| Ternary | 3 | Supplier supplies Part to Project | Interaction among three entities. |
| N-ary | n (>3) | Lecturer teaches Course to Student in Semester | Complex relationships involving many entities. |

---

## 2. Explain various update anomalies that can arise in a relational database with examples.
**Update Anomalies:**
* Update anomalies arise in poorly designed relations when a relation contains redundant data (i.e., repeating groups or partial / transitive dependencies).
* There are three types of update anomalies:
  1. Insertion Anomaly
  2. Deletion Anomaly
  3. Update (Modification) Anomaly

**Example Relation (Unnormalized):**
Consider a relation EMP_PROJ(EmpID, EmpName, DeptName, ProjID, ProjName, ProjLocation)

| EmpID | EmpName | DeptName | ProjID | ProjName | ProjLocation |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 101 | Ravi | IT | P1 | Library System | Kolkata |
| 101 | Ravi | IT | P2 | Website | Kolkata |
| 102 | Sita | HR | P1 | Library System | Kolkata |
| 103 | Amit | IT | P3 | Mobile App | Bangalore |

Here, Department and Project information are repeated for multiple tuples. This redundancy causes update anomalies.

**(1) Insertion Anomaly:**
* We cannot insert information about a department or project unless we have some employee or other related data to insert.
* Problem: New project or department details cannot be stored until related employee data exists. Leads to loss of information.

**(2) Deletion Anomaly:**
* Deleting a tuple may cause unintended loss of information.
* Problem: Deleting a tuple removes other useful information. Causes loss of data.

**(3) Update (Modification) Anomaly:**
* Same fact is stored in multiple tuples.
* Problem: Multiple updates are required. Easy to forget some tuples. Leads to inconsistent data.

---

## 3. Explain all Relational Algebra operations with examples.
Relational Algebra is a procedural query language. It consists of a set of operations that operate on one or two relations and return a relation as result.

**The basic Relational Algebra operations are:**
| S.No. | Operation | Symbol | Meaning |
| :--- | :--- | :--- | :--- |
| 1 | Selection | $\sigma$ | Selects tuples (rows) that satisfy a condition. |
| 2 | Projection | $\pi$ | Selects specified attributes (columns) from a relation. |
| 3 | Union | $\cup$ | Combines tuples from two relations (must be union compatible). |
| 4 | Set Difference | $-$ | Tuples in first relation but not in second (union compatible). |
| 5 | Cartesian Product | $\times$ | Combines each tuple of first relation with each tuple of second. |
| 6 | Rename | $\rho$ | Renames relation or its attributes. |
| 7 | Intersection | $\cap$ | Tuples common to both relations (union compatible). |
| 8 | Join | $\bowtie$ | Combines tuples from two relations based on a condition. |

**(1) Selection ($\sigma$)**
* Selects tuples that satisfy the given condition.
Syntax: $\sigma_{condition}(R)$

**(2) Projection ($\pi$)**
* Selects required columns (attributes) from a relation.
Syntax: $\pi_{attribute list}(R)$

**(3) Union ($\cup$)**
* Combines tuples from two relations.
Syntax: $R \cup S$

**(4) Set Difference ($-$)**
* Tuples that are in R but not in S.
Syntax: $R - S$

**(5) Cartesian Product ($\times$)**
* Combines each tuple of R with every tuple of S.
Syntax: $R \times S$

**(6) Rename ($\rho$)**
* Renames relation or its attributes.
Syntax: $\rho_{NewRelName}(OldRelName)$

**(7) Intersection ($\cap$)**
* Tuples that are common in both relations.
Syntax: $R \cap S$

**(8) Join ($\bowtie$)**
* Combines tuples from two relations based on a condition.
Syntax: $R \bowtie_{condition} S$

---

## 4. Discuss Tuple Relational Calculus with suitable examples.
Tuple Relational Calculus (TRC) is a non-procedural query language. It uses variables, logical connectives and quantifiers to express queries over tuples.
**(1) Syntax:**
$\{ t \mid P(t) \}$
Where $t$ is a tuple variable and $P(t)$ is a logical predicate formula.

**(2) Components of TRC:**
* Tuple Variables: Represents tuples.
* Predicate: A condition involving tuples.
* Logical Connectives: $\wedge$ (and), $\vee$ (or), $\neg$ (not), $\rightarrow$ (implies), $\leftrightarrow$ (iff).
* Quantifiers: $\exists$ (there exists), $\forall$ (for all).

**(3) Examples:**
(i) Find all students in the CSE department.
Query: $\{ t \mid Student(t) \wedge t.Dept = 'CSE' \}$

(ii) Find students older than 20.
Query: $\{ t \mid Student(t) \wedge t.Age > 20 \}$

(iii) Find all departments that have at least one student.
Query: $\{ d \mid Dept(d) \wedge \exists t (Student(t) \wedge t.Dept = d.DeptID) \}$

---

## 5. Discuss insertion, deletion and update anomalies.
These anomalies cause problems in inserting, deleting and updating data when a table is not properly normalized.

**(1) Insertion Anomaly:**
Occurs when we cannot insert a fact without having information about other related entities.
**(2) Deletion Anomaly:**
Occurs when deleting a tuple causes the loss of other useful information.
**(3) Update Anomaly:**
Occurs when the same fact is stored in multiple rows, and updating it in one place but not others leads to inconsistency.

**How to Remove Anomalies?**
By decomposing the relation into smaller relations through **Normalization**.

---

## 6. Distinguish between Lossless and Lossy decomposition.
Decomposition is the process of breaking a relation schema R into smaller relation schemas $R_1, R_2, ..., R_n$.

**(1) Lossless Decomposition:**
* A decomposition is lossless if no information is lost.
* The natural join of the decomposed relations must recreate the original relation exactly.

**(2) Lossy Decomposition:**
* A decomposition is lossy if joining the decomposed relations does not produce the original relation (extra spurious tuples are generated).

**Key Differences:**
| Lossless Decomposition | Lossy Decomposition |
| :--- | :--- |
| No information is lost. | Some information is lost (or spurious tuples generated). |
| Natural join returns the original relation. | Natural join does not return the original relation. |
| Ensures data integrity. | May lead to data redundancy and inconsistencies. |
| Preferred in database design. | Generally avoided in database design. |

---

## 7. Discuss different types of join operations in SQL with examples.
A JOIN clause is used to combine rows from two or more tables based on a related column between them.

**(1) INNER JOIN ($\theta$-JOIN):**
Returns only the matching rows from both tables.
```bash
  E             D
+---+         +---+
|   |///////|   |
|   |///////|   |
+---+         +---+
```

**(2) LEFT OUTER JOIN (LEFT JOIN):**
Returns all rows from the left table (E) and matching rows from the right table (D).
```bash
  E             D
///////       +---+
///////|      |   |
///////       +---+
```

**(3) RIGHT OUTER JOIN (RIGHT JOIN):**
Returns all rows from the right table (D) and matching rows from the left table (E).
```bash
  E             D
+---+       ///////
|   |      |///////
+---+       ///////
```

**(4) FULL OUTER JOIN (FULL JOIN):**
Returns all rows when there is a match in either left (E) or right (D) table.
```bash
  E             D
///////       ///////
///////|     |///////
///////       ///////
```

**(5) CROSS JOIN (Cartesian Product):**
Returns the Cartesian product of both tables.
```bash
  E             D
+---+         +---+
|   |    X    |   |
+---+         +---+
```

**(6) SELF JOIN:**
A table joined with itself. Used when we need to compare rows within the same table.

---

## 8. What is Query equivalence? How does it help in query optimization?
Two queries are said to be equivalent if they produce the same result for all possible database instances.

**(1) Query Equivalence:**
Two relational algebra expressions $E_1$ and $E_2$ are equivalent if for every legal instance of the database, they return the same relation.

**(2) How Query Equivalence Helps in Query Optimization?**
Query optimization is the process of finding an equivalent query plan that has the minimum execution cost (time, I/O, CPU).
```bash
+--------------------+       +----------------------------+
| SQL / Relational   |       | Equivalent Transformations |
| Algebra Query      |------>| Q1 <-> Q2 <-> Q3 <-> ...   |
| (Initial Form)     |       | (All Equivalent Queries)   |
+--------------------+       +----------------------------+
                                          |
                                          v
                                 +------------------+
                                 | Cost Estimation  |
                                 +------------------+
                                          |
                                          v
                                 +------------------+
                                 | Choose Query     |
                                 | with Minimum Cost|
                                 +------------------+
```
Equivalence helps by expanding the search space for better plans, enabling rule-based and cost-based optimization, and reducing query execution time and resources.

---

## 9. Explain the process of Lossless Decomposition and Lossy decomposition in database design. Why is it required?
In database design, a relation schema R is decomposed into smaller relation schemas to reduce redundancy and improve efficiency. The decomposition should be such that the original relation can be reconstructed by joining the decomposed relations.

**Why is Lossless Decomposition Required?**
* Ensures that no data is lost when relations are decomposed.
* Allows accurate reconstruction of the original relation.
* Maintains data integrity and consistency.
* Essential for normalizing relations without affecting correctness of data.

---

## 10. Discuss the basic form of SQL query. Explain about aggregate operators in SQL with examples.
**(A) BASIC FORM OF SQL QUERY:**
```bash
SELECT [DISTINCT] <select_list>       --> Columns to be displayed.
FROM <table_list>                     --> Table(s) from where data is retrieved.
[WHERE <condition>]                   --> Filters rows before grouping.
[GROUP BY <column_list>]              --> Groups rows having same values.
[HAVING <group_condition>]            --> Filters groups after aggregation.
[ORDER BY <column_list> [ASC|DESC]];  --> Sorts the final result.
```

**(B) AGGREGATE OPERATORS IN SQL:**
Aggregate operators perform calculations on a set of values and return a single value. They are often used with GROUP BY clause.
| Operator | Description |
| :--- | :--- |
| COUNT() | Returns the number of rows that match a condition. |
| COUNT(DISTINCT col) | Counts distinct (unique) values in a column. |
| SUM(col) | Returns the total sum of numeric values. |
| AVG(col) | Returns the average of numeric values. |
| MIN(col) | Returns the minimum value in a column. |
| MAX(col) | Returns the maximum value in a column. |

---

## 11. Why we need query optimization?
Query optimization is the process of selecting the most efficient execution plan for a given query.
It is needed to:
* **Improve Performance:** Reduces response time by minimizing I/O, CPU time and memory usage.
* **Efficient Resource Utilization:** Chooses the best order of operations.
* **Handle Large Data:** Ensures fast retrieval in large databases.
* **Reduce Cost:** Selects the plan with minimum estimated cost.

## 12. Why are entity integrity and referential integrity important in a database?
Integrity constraints maintain accuracy, consistency and reliability of data in a database.
**(A) ENTITY INTEGRITY**
* Ensures that each tuple (row) in a relation can be uniquely identified.
* Rule: Primary key values cannot be NULL.
**(B) REFERENTIAL INTEGRITY**
* Ensures that a value in a foreign key must either match a primary key value in the referenced relation or be NULL.
* Rule: A foreign key value must reference an existing primary key value.

## 13. What do you mean by unary and binary operations in Relational algebra? Give example.
**(A) UNARY OPERATIONS (One input relation)**
1) Selection ($\sigma$) - Selects rows satisfying a condition.
2) Projection ($\pi$) - Selects specified columns.
3) Renaming ($\rho$) - Renames relations or attributes.

**(B) BINARY OPERATIONS (Two input relations)**
1) Union ($\cup$) - Tuples in R or S or both.
2) Intersection ($\cap$) - Tuples common in both R and S.
3) Difference ($-$) - Tuples in R but not in S.
4) Cartesian Product ($\times$) - All possible concatenations of tuples from R and S.

## 14. Write a short note on Armstrong's axioms.
Armstrong's axioms are three fundamental rules used to infer functional dependencies. They are sound and complete.
1. **Reflexivity (Triviality) Rule:** If $Y \subseteq X$, then $X \rightarrow Y$
2. **Augmentation Rule:** If $X \rightarrow Y$, then $XZ \rightarrow YZ$
3. **Transitivity Rule:** If $X \rightarrow Y$ and $Y \rightarrow Z$, then $X \rightarrow Z$

## 15. Explain the following terms:
1. **Normalization:** The systematic process of organizing data in a database to minimize redundancy and avoid anomalies by dividing large tables into smaller, well-structured tables using functional dependencies.
```bash
  UNNORMALIZED TABLE
         | Normalization
         v
   NORMALIZED TABLES
  /      |      \
Table 1 Table 2 Table n
```
2. **Full Functional Dependency:** A functional dependency $X \rightarrow Y$ is full if Y depends on the entire super key X and not on any proper subset of X.
3. **Transitive Dependency:** If $X \rightarrow Y$ and $Y \rightarrow Z$, where Y is not a candidate key, then Z is transitively dependent on X via Y.
4. **Partial Dependency:** If a non-prime attribute depends on a part (proper subset) of a composite candidate key, it is called partial dependency.
5. **Non Transitive Dependency:** A dependency $X \rightarrow Y$ is non-transitive if Y does not depend on any other non-prime attribute.
6. **BCNF (Boyce-Codd Normal Form):** A relation R is in BCNF if for every non-trivial FD $X \rightarrow Y$, X is a super key.
