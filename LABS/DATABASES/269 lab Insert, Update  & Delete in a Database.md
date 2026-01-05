# Lab 269: Database Data Manipulation (Insert, Update, & Delete)

## Introduction
In this lab, I explored the core components of **Data Manipulation Language (DML)**. My goal was to move beyond simply viewing data and learn how to actively manage the lifecycle of a record—from its initial creation to modification and, eventually, its removal.

---

## 1. How I Handled Data Entry (INSERT)
To populate the database, I used the `INSERT INTO` statement. I practiced two different methods:
* **Specific Column Entry:** I specified the columns to ensure that data was mapped correctly, even if I didn't have a value for every field.
* **Bulk Insertion:** I experimented with adding multiple rows in a single query to improve efficiency.

**My Key Takeaway:** I learned that I must always respect the `PRIMARY KEY` constraints; attempting to insert a duplicate ID resulted in an error, which taught me how the database maintains integrity.

---

## 2. Modifying Existing Records (UPDATE)
When I needed to change data, I used the `UPDATE` command. This was the most "dangerous" part of the lab because it required precision.

* **The Power of WHERE:** I quickly realized that without a `WHERE` clause, I would accidentally update every single row in the table. 
* **Verification:** I developed a habit of running a `SELECT` query first to "preview" the rows I was about to change.

> **Note to Self:** Always double-check the condition (e.g., `WHERE user_id = 101`) before hitting execute.

---

## 3. Removing Data (DELETE)
The final stage of my lab involved cleaning up the database using the `DELETE` statement.

* **Specific Deletion:** I practiced removing individual records based on unique identifiers.
* **The Trap:** I learned the difference between `DELETE` (which removes rows) and `DROP` (which removes the entire table structure). 

---

## Summary of Commands Used
| Command | My Purpose | Risk Level |
| :--- | :--- | :--- |
| `INSERT` | Add new information to the system. | Low |
| `UPDATE` | Fix mistakes or update statuses. | **High** (Can overwrite everything) |
| `DELETE` | Remove obsolete or incorrect data. | **High** (Irreversible without backups) |

---

## Conclusion
Through this lab, I gained a practical understanding of how to maintain a dynamic database. I am now comfortable performing the basic "CUD" (Create, Update, Delete) operations that sit at the heart of most backend applications.
