# SQL Database Management & Query Projects

## 📊 Project Overview
This repository showcases my SQL database management and querying skills through comprehensive hands-on projects using MySQL Workbench. The work demonstrates my ability to design database schemas, write complex queries, perform data analysis, and extract meaningful business insights from relational databases.

## 🎯 Skills Demonstrated

### SQL Expertise
- **Database Design**: Understanding primary keys, foreign keys, and relational database structures
- **Data Querying**: SELECT statements with filtering, sorting, and aggregation
- **JOIN Operations**: INNER JOIN, LEFT JOIN, RIGHT JOIN, CROSS JOIN, and SELF JOIN
- **Data Aggregation**: GROUP BY, COUNT, SUM, AVG functions
- **Complex Filtering**: WHERE clauses, BETWEEN, LIKE, IN operators
- **Subqueries**: Nested queries for advanced data retrieval
- **Data Analysis**: Extracting business insights from multi-table databases

### Database Concepts Mastery
- **Relational vs Non-Relational Databases**: Understanding use cases and differences
- **Database Relationships**: One-to-one, one-to-many, many-to-many
- **Data Normalization**: Structuring data to minimize redundancy
- **Query Optimization**: Writing efficient SQL for performance

## 📁 Database Knowledge Base

### Key Database Concepts

#### Primary vs Secondary Keys
- **Primary Key**: A field in a table that uniquely identifies each record (no duplicates allowed)
- **Secondary Key**: Can be repeated in the table, used for indexing and searching
- **Foreign Key**: Links tables together - every foreign key in one table is the primary key of another related table

#### Database Relationships

| Relationship Type | Description | Real-World Example |
|-------------------|-------------|-------------------|
| **One-to-One** | Each record in Table A relates to exactly one record in Table B | Password and Person |
| **One-to-Many** | One record in Table A relates to multiple records in Table B | One bank client having multiple accounts |
| **Many-to-Many** | Multiple records in Table A relate to multiple records in Table B | Many clients purchasing many products |

#### Relational vs Non-Relational Databases

**Relational Databases**:
- Store structured data in table format
- Grow vertically (adding more columns/rows)
- Support multi-row transactions
- Use SQL for data management
- Enforce strict schema and relationships

**Non-Relational Databases**:
- Document-based (JSON, XML)
- Grow horizontally (distributed systems)
- More dynamic and flexible schema
- Don't use SQL (NoSQL)
- Better for high-velocity, large-volume data

**Use Case Example**: IoT device data collection (air quality sensors in cities)
- Benefits from non-relational databases due to:
  - Large data volumes from thousands of devices
  - High-velocity constant updates
  - Dynamic data structures
  - Scalability requirements

## 📁 Featured Projects

### Project 1: Northwind Traders Business Analysis
**Database**: Northwind (Microsoft sample database)  
**Tools**: MySQL Workbench  
**Scenario**: Junior data analyst performing real-world business queries

#### Basic Query Operations

**1. Customer Data Retrieval**
```sql
SELECT * FROM Customers;
```
*Purpose*: Export full customer list for reporting

**2. Targeted Marketing Campaigns**
```sql
SELECT CustomerName, city FROM customers;
```
*Purpose*: Extract customer names and cities for marketing analysis

**3. Delivery Network Expansion**
```sql
SELECT DISTINCT city FROM customers;
```
*Purpose*: Identify unique cities for logistics planning

**4. High-Value Products Analysis**
```sql
SELECT * FROM products WHERE Price > 50;
```
*Purpose*: Analyze premium product inventory

**5. International Customer Targeting**
```sql
SELECT * FROM customers WHERE Country="USA" OR Country="UK";
```
*Purpose*: Target specific geographic markets

#### Advanced Filtering & Sorting

**6. Recent Orders Report**
```sql
SELECT * FROM orders ORDER BY OrderDate DESC;
```
*Purpose*: Analyze latest order trends

**7. Mid-Range Product Listing**
```sql
SELECT * FROM products WHERE products.Price BETWEEN 20 AND 50;
```
*Purpose*: Create targeted product catalog

**8. Local US Marketing Campaign**
```sql
SELECT * FROM customers 
WHERE country = "USA" AND (city="Portland" OR city="Kirkland") 
ORDER BY CustomerName ASC;
```
*Purpose*: Focus on specific US cities for local campaigns

**9. UK & London Promotional Emails**
```sql
SELECT * FROM customers WHERE Country="UK" OR city="London";
```
*Purpose*: Target UK customers for promotional campaigns

**10. Category-Based Inventory**
```sql
SELECT * FROM products 
WHERE CategoryID=1 OR CategoryID=2 
ORDER BY ProductName ASC;
```
*Purpose*: Inventory management for specific categories

#### Complex JOIN Operations

**11. Product-Supplier Relationship**
```sql
SELECT p.ProductName AS Product, s.SupplierName AS Supplier 
FROM suppliers s 
INNER JOIN products p ON s.SupplierID = p.SupplierID;
```
*Purpose*: Identify supply chain relationships

**12. Product Category Classification**
```sql
SELECT p.ProductName AS Product, c.CategoryName AS Category 
FROM categories c 
INNER JOIN products p ON c.CategoryID = p.CategoryID;
```
*Purpose*: Organize products by category

**13. Category-Specific Products (Subquery)**
```sql
SELECT ProductName AS "Meat/Poultry Product" 
FROM products 
WHERE CategoryID = (
    SELECT CategoryID 
    FROM categories 
    WHERE CategoryName = "Meat/Poultry"
);
```
*Purpose*: Retrieve products from specific category

**14. Complete Order Overview (Multi-JOIN)**
```sql
SELECT o.OrderID, o.OrderDate, c.CustomerName, 
       CONCAT(e.FirstName, ' ', e.LastName) AS EmployeeName 
FROM orders o 
INNER JOIN employees e ON o.EmployeeID = e.EmployeeID 
INNER JOIN customers c ON c.CustomerID = o.CustomerID;
```
*Purpose*: Comprehensive order details with customer and employee info

**15. Supply Chain Overview**
```sql
SELECT p.ProductName, c.CategoryName, s.SupplierName 
FROM products p 
INNER JOIN categories c ON p.CategoryID = c.CategoryID 
INNER JOIN suppliers s ON s.SupplierID = p.SupplierID;
```
*Purpose*: Complete product supply chain visibility

#### Advanced Analytics

**16. Yearly Order Analysis (1996)**
```sql
SELECT * FROM products p 
JOIN order_details d ON p.ProductID = d.ProductID 
JOIN orders o ON o.OrderID = d.OrderID 
WHERE YEAR(o.OrderDate) = '1996';
```
*Purpose*: Historical order auditing

**17. Product Count by Category**
```sql
SELECT c.CategoryName AS Category, COUNT(p.ProductID) AS 'Number of Products' 
FROM categories c 
INNER JOIN products p ON c.CategoryID = p.CategoryID 
GROUP BY c.CategoryID;
```
*Purpose*: Inventory distribution analysis

**18. Sales Volume Breakdown**
```sql
SELECT p.ProductName AS Product, p.Price, SUM(o.Quantity) AS 'Quantity Ordered' 
FROM products p 
INNER JOIN order_details o ON p.ProductID = o.ProductID 
GROUP BY Product, p.Price;
```
*Purpose*: Sales performance analysis by product

---

### Project 2: World Database Global Analysis
**Database**: World (geographic and demographic data)  
**Tools**: MySQL Workbench  
**Scenario**: International research organization analyst

#### Demographic & Geographic Analysis

**1. US Cities Count**
```sql
SELECT COUNT(*) AS 'Number of Cities' FROM city;
```
*Purpose*: Baseline demographic analysis

**2. Highest Life Expectancy**
```sql
SELECT country.Name AS 'Country', LifeExpectancy 
FROM country 
ORDER BY LifeExpectancy DESC 
LIMIT 1;
```
*Purpose*: Global health initiative prioritization

**3. Cities with "New" Promotion**
```sql
SELECT Name AS 'Cities with New' FROM city WHERE Name LIKE '%New%';
```
*Purpose*: Travel agency New Year promotion

**4. Top 10 Most Populous Cities**
```sql
SELECT Name, Population FROM city ORDER BY Population DESC LIMIT 10;
```
*Purpose*: Brief overview for reports

**5. Large Population Centers**
```sql
SELECT Name, Population FROM city 
WHERE Population > 2000000 
ORDER BY Population DESC;
```
*Purpose*: Real estate investment opportunities

**6. Cities Beginning with "Be"**
```sql
SELECT Name AS 'Cities with Be' FROM city WHERE Name LIKE 'Be%';
```
*Purpose*: Travel blogger content creation

**7. Mid-Sized Cities Analysis**
```sql
SELECT Name AS City, Population FROM city 
WHERE Population >= 500000 AND Population <= 1000000 
ORDER BY Population DESC;
```
*Purpose*: Urban planning infrastructure projects

**8. Alphabetical City List**
```sql
SELECT Name FROM city ORDER BY Name ASC;
```
*Purpose*: Educational geography lesson

**9. Most Populated Country**
```sql
SELECT country.Name AS 'Country', Population 
FROM country 
ORDER BY Population DESC 
LIMIT 1;
```
*Purpose*: Investment and strategic planning

**10. City Name Frequency Analysis**
```sql
SELECT Name AS CityName, COUNT(Name) AS Frequency 
FROM city 
GROUP BY Name 
ORDER BY Name ASC;
```
*Purpose*: Geography education support

**11. Lowest Population City**
```sql
SELECT Name AS CityName, Population 
FROM city 
ORDER BY Population ASC 
LIMIT 1;
```
*Purpose*: Census bureau demographic analysis

**12. Largest Population City**
```sql
SELECT Name AS CityName, Population 
FROM city 
ORDER BY Population DESC 
LIMIT 1;
```
*Purpose*: Economic research demographic trends

#### International Relationships & Analysis

**13. Capital of Spain**
```sql
SELECT c.Name AS CapitalCity, o.Name AS Country 
FROM city c 
INNER JOIN country o ON c.ID = o.Capital 
WHERE o.Name = 'Spain';
```
*Purpose*: Travel agency itinerary accuracy

**14. European Cities**
```sql
SELECT c.Name AS City, o.Continent AS Continent 
FROM city c 
INNER JOIN country o ON c.CountryCode = o.Code 
WHERE o.Continent = 'Europe';
```
*Purpose*: Cultural exchange program planning

**15. Average Population by Country**
```sql
SELECT AVG(c.Population), co.Name AS country 
FROM city c 
INNER JOIN country co ON c.CountryCode = co.Code 
GROUP BY c.CountryCode;
```
*Purpose*: Comparative demographic analysis

**16. Capital Cities Population Comparison**
```sql
SELECT c.Name AS CapitalCity, o.Name AS Country, c.Population 
FROM city c 
INNER JOIN country o ON c.ID = o.Capital;
```
*Purpose*: Statistical urban demographics analysis

**17. Low Population Density Countries**
```sql
SELECT Name, Population FROM country WHERE Population = 0;
```
*Purpose*: Agricultural development research

**19. Ranked City Data (Rows 31-40)**
```sql
SELECT Name, Population FROM country 
ORDER BY Population DESC 
LIMIT 30 OFFSET 10;
```
*Purpose*: Detailed market research beyond top rankings

---

## 🛠️ SQL Skills Summary

### Query Operations

| Skill | Commands | Application |
|-------|----------|-------------|
| **Data Retrieval** | SELECT, FROM, WHERE | Basic data extraction |
| **Filtering** | WHERE, AND, OR, IN, BETWEEN, LIKE | Conditional data selection |
| **Sorting** | ORDER BY ASC/DESC | Organizing results |
| **Limiting Results** | LIMIT, OFFSET | Pagination and sampling |
| **Aggregation** | COUNT, SUM, AVG, MIN, MAX | Statistical analysis |
| **Grouping** | GROUP BY, HAVING | Categorical analysis |
| **Joins** | INNER, LEFT, RIGHT, CROSS, SELF | Multi-table queries |
| **Subqueries** | Nested SELECT | Complex filtering |
| **String Functions** | CONCAT, LIKE | Text manipulation |
| **Date Functions** | YEAR, DATE | Temporal analysis |

### JOIN Types Mastery

#### INNER JOIN
Retrieves records with matches in both tables.
```sql
SELECT C.CustomerName, O.OrderID 
FROM customers C 
INNER JOIN orders O ON C.CustomerID = O.CustomerID;
```

#### LEFT JOIN
Retrieves all records from left table with matching records from right table.
```sql
SELECT C.CustomerName, O.OrderID 
FROM customers C 
LEFT JOIN orders O ON C.CustomerID = O.CustomerID;
```

#### RIGHT JOIN
Retrieves all records from right table with matching records from left table.
```sql
SELECT C.CustomerName, O.OrderID 
FROM customers C 
RIGHT JOIN orders O ON C.CustomerID = O.CustomerID;
```

#### CROSS JOIN
Returns all records from both tables (Cartesian product).
```sql
SELECT * FROM customers CROSS JOIN orders;
```

#### SELF JOIN
Joins a table with itself using aliases.
```sql
SELECT C.CustomerName AS name1, T.CustomerName AS name2 
FROM customers C, customers T 
WHERE C.CustomerID <> T.CustomerID;
```

#### FULL OUTER JOIN
Note: Not supported in MySQL. Retrieves all records when there's a match in either table.

---

## 💼 Business Intelligence Applications

### Retail & E-Commerce
- Customer segmentation and targeting
- Product performance analysis
- Inventory management optimization
- Sales trend identification
- Supply chain visibility

### Global Research & Demographics
- Population distribution analysis
- Geographic trend identification
- Health and wellness metrics
- Urban planning support
- Economic development research

### Marketing & Sales
- Campaign targeting by geography
- Customer behavior analysis
- Product categorization
- Sales volume tracking
- Revenue optimization

---

## 📈 Key Achievements

✅ Completed 40+ real-world SQL query scenarios  
✅ Mastered all major JOIN operations  
✅ Demonstrated complex multi-table queries  
✅ Applied aggregation functions for business insights  
✅ Implemented subqueries for advanced filtering  
✅ Analyzed datasets with 1000+ records  
✅ Extracted actionable business intelligence from databases  

---

## 🎓 Training & Certification

**Program**: Data Technician Training - SQL & Database Module  

**Databases Used**:
- Northwind Traders (Microsoft sample database)
- World Database (geographic and demographic data)
- Sakila Database (film rental data)

**Focus Areas**: 
- Relational database fundamentals
- SQL query syntax and optimization
- JOIN operations and relationships
- Data aggregation and analysis
- Database design principles
- Real-world business scenarios

**Completion Date**: December 2025 - January 2026

---

## 🔧 Tools & Technologies

- **MySQL Workbench** - Database management and query execution
- **MySQL Server** - Relational database management system
- **SQL** - Structured Query Language for data manipulation
- **Database Design** - ER diagrams, normalization, relationships

---

## 💡 Best Practices Applied

### Query Optimization
- Use of appropriate indexes
- Efficient JOIN conditions
- Minimizing subquery complexity
- Proper use of WHERE vs HAVING
- SELECT only needed columns

### Code Quality
- Consistent naming conventions (aliases)
- Readable formatting and indentation
- Meaningful column aliases
- Commented complex queries
- Error handling considerations

### Data Integrity
- Understanding of primary/foreign key relationships
- Proper use of JOIN types
- Data validation through WHERE clauses
- Awareness of NULL handling
- Transaction considerations

---

## 📚 Additional Learning Resources

### Interactive Learning
- **SQLBolt**: Interactive SQL tutorial series
- **MySQL Basics YouTube Series**: Video tutorials
- **HackerRank SQL Challenges**: Practice problems

### Practice Databases
- **Northwind Database**: Retail business scenarios
- **World Database**: Geographic and demographic data
- **Sakila Database**: Film rental industry

---

## 🤝 Connect With Me

*Add your professional links here (LinkedIn, Portfolio, Email, etc.)*

---

## 📝 Repository Structure
```
sql-projects/
│
├── northwind-traders/
│   ├── basic-queries/
│   ├── join-operations/
│   ├── advanced-analytics/
│   └── README.md
│
├── world-database/
│   ├── demographic-analysis/
│   ├── geographic-queries/
│   ├── population-studies/
│   └── README.md
│
├── database-concepts/
│   ├── relationships.md
│   ├── join-types.md
│   └── optimization.md
│
└── README.md
```

---

## 🎯 Query Complexity Progression

| Level | Query Type | Example Scenario |
|-------|-----------|------------------|
| **Beginner** | Simple SELECT | Retrieve all customers |
| **Intermediate** | Filtering & Sorting | Find high-value products |
| **Advanced** | Single JOINs | Link products to suppliers |
| **Expert** | Multi-table JOINs | Complete order overview with 3+ tables |
| **Master** | Subqueries & Aggregation | Sales volume breakdown with grouping |

---

**Note**: All queries were tested and executed successfully in MySQL Workbench using real-world business databases. The projects demonstrate practical SQL skills applicable to data analyst, business intelligence, and database developer roles.
