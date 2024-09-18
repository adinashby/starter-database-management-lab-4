# Database Management - Lab 4

This template repository is the starter project for Database Management Lab 4. Written in Access.

### Question(s)

### Microsoft Access Lab: Advanced Queries with Criteria, Calculated Fields, Grouping Functions, and Regular Expressions (RegEx)

#### Objective:
By the end of this lab, students will understand how to use selection queries with criteria, calculated fields, and grouping functions in Microsoft Access. Additionally, students will learn how to use simple regular expressions (RegEx) within queries to search and filter data.

---

### Part 1: Selection Queries with Criteria

#### Step 1: Open Your Database
1. Open the **StudentRecords.accdb** database you used in previous labs.

#### Step 2: Create a Selection Query
1. Go to **Create** > **Query Design**.
2. Add the **Students** table and the **Courses** table to the query.
3. Select the following fields:
   - **FirstName** (from **Students**)
   - **LastName** (from **Students**)
   - **DateOfBirth** (from **Students**)
   - **CourseName** (from **Courses**)

#### Step 3: Add Criteria to Filter Results
1. In the **Criteria** row under **DateOfBirth**, enter `>= #1/1/2000#`. This will filter the query results to only show students born on or after January 1, 2000.
2. Run the query to see the results.

#### Questions:
1. What does adding criteria to a query do?
2. How does filtering by **DateOfBirth** affect the query results?

---

### Part 2: Creating a Calculated Field

#### Step 1: Add a Calculated Field to the Query
1. In the same query, create a new calculated field to determine the student's age. In the next available column, enter the following in the **Field** row:
   ```
   Age: DateDiff("yyyy", [DateOfBirth], Date()) - IIf(Format([DateOfBirth], "mmdd") > Format(Date(), "mmdd"), 1, 0)
   ```
2. Run the query. This field will calculate each student’s age based on their **DateOfBirth**.

#### Step 2: Add Criteria for the Calculated Field
1. In the **Criteria** row under **Age**, enter `>= 18`. This will filter the query to show only students who are 18 or older.
2. Run the query again.

#### Questions:
1. What is the purpose of a calculated field?
2. How does the age calculation formula work in this query?

---

### Part 3: Grouping Functions

#### Step 1: Create a Grouped Query
1. Create a new query using **Query Design**.
2. Add the **Courses** table.
3. In the **Query Grid**, select the following fields:
   - **CourseName**
   - **Credits**

4. Click on the **Totals** button (∑) in the toolbar. This will enable grouping functions.
5. In the **Total** row for **Credits**, choose **Sum** to calculate the total credits for each course.
6. Run the query to see the grouped results.

#### Step 2: Grouping with Criteria
1. Add the **Students** table to the query.
2. In the **Query Grid**, select:
   - **CourseName**
   - **Credits** (with **Sum** in the **Total** row)
   - **StudentID** (with **Count** in the **Total** row to count the number of students per course)
   
3. Run the query to see the total credits and number of students enrolled in each course.

#### Questions:
1. What does the **Totals** button (∑) do in a query?
2. How does grouping data affect the way results are displayed?

---

### Part 4: Using Regular Expressions (RegEx) in Queries

Regular expressions can be useful in Access queries for pattern matching, such as searching for specific formats in text fields.

#### Step 1: Query with RegEx to Search for Emails
1. Create a new query in **Query Design**.
2. Add the **Students** table.
3. Select the following fields:
   - **FirstName**
   - **LastName**
   - **Email**

4. In the **Criteria** row under the **Email** field, enter the following:
   ```
   Like "*@[a-zA-Z]*.com"
   ```
   This regular expression-like pattern filters email addresses that match the domain “.com”.

5. Run the query to see results with only email addresses ending in “.com”.

#### Step 2: Query with RegEx for Phone Numbers
1. In the **Criteria** row under the **PhoneNumber** field, enter:
   ```
   Like "[0-9][0-9][0-9]-[0-9][0-9][0-9]-[0-9][0-9][0-9][0-9]"
   ```
   This regular expression-like pattern filters phone numbers in the format "###-###-####" (where "#" represents a number).

2. Run the query to see results.

#### Questions:
1. What are the benefits of using regular expressions (RegEx) in queries?
2. How does the RegEx pattern help in filtering data?

---

### Part 5: Conclusion
- **Discussion**: Summarize how selection queries with criteria help refine and filter data, how calculated fields add more depth to data analysis, and how grouping functions provide summary data. Additionally, discuss how regular expressions can be used in queries to perform more advanced filtering based on patterns in text data.