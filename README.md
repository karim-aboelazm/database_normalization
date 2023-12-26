Normalization is the process of organizing data in a database efficiently. It involves structuring a database in a way that reduces redundancy and dependency of data. The primary goals of normalization are to minimize redundancy, avoid anomalies during data modification, and ensure data integrity.

Here are examples of different normalization forms:

### First Normal Form (1NF):
In 1NF, each column in a table contains atomic (indivisible) values, and each column has a unique name.

**Example:**
Consider a table `StudentCourses`:

| StudentID | Name  | Courses              |
| --------- | ----- | -------------------- |
| 1         | John  | Math, Physics        |
| 2         | Sarah | Chemistry, Biology   |
| 3         | Alex  | Math, Chemistry, Gym |

To convert this to 1NF, separate the repeating groups into individual rows:

| StudentID | Name  | Course    |
| --------- | ----- | --------- |
| 1         | John  | Math      |
| 1         | John  | Physics   |
| 2         | Sarah | Chemistry |
| 2         | Sarah | Biology   |
| 3         | Alex  | Math      |
| 3         | Alex  | Chemistry |
| 3         | Alex  | Gym       |

### Second Normal Form (2NF):
In 2NF, the table is in 1NF, and all non-key attributes are fully dependent on the primary key.

**Example:**
Consider a table `Sales`:

| OrderID | Product | Category    | Price |
| ------- | ------- | ----------- | ----- |
| 1       | Laptop  | Electronics | 1000  |
| 2       | TV      | Electronics | 800   |
| 3       | Banana  | Fruits      | 10    |

In this case, `Category` is partially dependent on the primary key. To achieve 2NF, create separate tables:

**Products:**

| ProductID | Product | CategoryID |
| --------- | ------- | ---------- |
| 1         | Laptop  | 1          |
| 2         | TV      | 1          |
| 3         | Banana  | 2          |

**Categories:**

| CategoryID | Category    |
| ---------- | ----------- |
| 1          | Electronics |
| 2          | Fruits      |

### Third Normal Form (3NF):
In 3NF, the table is in 2NF, and there is no transitive dependency (non-key attributes depending on other non-key attributes).

**Example:**
Consider a table `Employees`:

| EmployeeID | EmployeeName | Department | DepartmentLocation |
| ---------- | ------------ | ---------- | ------------------ |
| 1          | John         | IT         | Building A         |
| 2          | Sarah        | HR         | Building B         |
| 3          | Alex         | IT         | Building A         |

Here, `DepartmentLocation` depends on `Department`, not directly on the primary key `EmployeeID`. To achieve 3NF:

**Employees:**

| EmployeeID | EmployeeName | DepartmentID |
| ---------- | ------------ | ------------ |
| 1          | John         | 1            |
| 2          | Sarah        | 2            |
| 3          | Alex         | 1            |

**Departments:**

| DepartmentID | Department | Location   |
| ------------ | ---------- | ---------- |
| 1            | IT         | Building A |
| 2            | HR         | Building B |

This breaks the transitive dependency, isolating `DepartmentLocation` into the `Departments` table.
