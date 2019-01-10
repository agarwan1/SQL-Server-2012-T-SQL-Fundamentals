SQL Introduction
*SQL stands for Structured Query Language. SQL is a standard language that was designed to query and manage data in relational database management systems (RDBMSs).
*An RDBMS is a database management system based on the relational model (a semantic model for representing data), which in turn is based on two mathematical branches: set theory and predicate logic. 
*To the degree that SQL is based on the relational model, it is based on a firm foundation—applied mathematics.
*The relational model is language-independent. That is, you can implement the relational model with languages other than SQL—for example, with C# in a class model. 

ANI and ISO standard language
*SQL is both an ANSI and ISO standard language based on the relational model, designed for querying and managing data in an RDBMS.
*1987. Since 1986, the American National Standards Institute (ANSI) and
the International Organization for Standardization (ISO) have been releasing revisions for the SQL standard every few years.
*Interestingly, SQL resembles English and is also very logical. Unlike many programming languages,which use an imperative programming paradigm, SQL uses a declarative one. That is, SQL requires you to specify what you want to get and not how to get it, letting the RDBMS figure out the physical mechanics required to process your request.

DDL, DML and DCL
*SQL has several categories of statements, including Data Definition Language (DDL), Data Manipulation Language (DML), and Data Control Language (DCL). DDL deals with object definitions and includes statements such as CREATE, ALTER, and DROP. DML allows you to query and modify data and includes statements such as SELECT, INSERT, UPDATE, DELETE, TRUNCATE, and MERGE.
**TRUNCATE is a DDL statement, but in fact it is a DML statement. DCL deals with permissions and includes statements such as GRANT and REVOKE.

Set Theory
*Set theory, which originated with the mathematician Georg Cantor, is one of the mathematical branches on which the relational model is based.
*By a “set” we mean any collection M into a whole of definite, distinct objects m
(which are called the “elements” of M) of our perception or of our thought.
*A set should be considered a single entity.Your focus should be on the collection of objects as opposed to the individual objects that make up the collection.
*A set should be considered a single entity.
*When you write T-SQL queries against tables in a database (such as a table of
employees), you should think of the set of employees as a whole rather than the individual employees.
*Distinct means that every element of a set must be unique. Jumping ahead to tables in a database, you can enforce the uniqueness of rows in a table by defining key constraints. Without a key, you won’t be able to uniquely identify rows, and therefore the table won’t qualify as a set. Rather, the table would be a multiset or a bag.
*Phrase of our perception or of our thought implies that the definition of a set is subjective. Consider a classroom: One person might perceive a set of people, whereas another might perceive a set of students and a set of teachers. Therefore, you have a substantial amount of freedom in defining sets. When you design a data model for your database, the design process should carefully consider the subjective needs of the application to determine adequate definitions for the entities involved.
*object - the definition of a set is not restricted to physical objects such as cars or employees but rather is relevant to abstract objects as well, such as prime numbers or lines.
*The order in which set elements are listed is not important. The formal notation for listing set elements uses curly brackets: {a,b, c}. Because order has no relevance, you can express the same set as {b, a, c} or {b, c, a}.
*Jumping ahead to the set of attributes (called columns in SQL) that make up the header of a relation (called a table in SQL), an element is supposed to be identified by name—not by ordinal position.
*Similarly, consider the set of tuples (called rows by SQL) that make up the body of the relation; an element is identified by its key values—not by position. Many programmers have a hard time adapting
to the idea that, with respect to querying tables, there is no order among the rows. <b>In other words, a query against a table can return table rows in any order unless you explicitly request that the data be sorted in a specific way, perhaps for presentation purposes.</b>

Predicate Logic
*A predicate is a property or an expression that either holds or doesn’t hold—in other words, is either true or false.
*The relational model relies on predicates to maintain the logical integrity of the data and define its structure.
*One example of a predicate used to enforce integrity is a constraint defined in a table called Employees that allows only employees with a salary greater than zero to be stored in the table. <b>The predicate is “salary greater than zero” (T-SQL expression: salary > 0).</b>
*In set theory, you can use predicates to define sets. As an example of a finite set defined with a predicate, the set {0, 1, 2, 3, 4, 5, 6, 7, 8, 9} can be defined as the set of all elements for which the following predicate holds true: “x is an integer greater than or equal to 0 and smaller than or equal to 9.”

Relational Model
*The goal of the relational model is to enable consistent representation of data with minimal or no redundancy and without sacrificing completeness, and to define data integrity (enforcement of data consistency) as part of the model. An RDBMS is supposed to implement the relational model and provide the means to store, manage, enforce the integrity of, and query data. The fact that the relational model is based on a strong mathematical foundation means that given a certain data model instance (from which a physical database will later be generated), you can tell with certainty when a design is flawed, rather than relying solely on intuition.

Propositions, Predicates, and Relations
*“Relational” actually pertains to the mathematical term relation. In set theory, a relation is a representation of a set.
*In the relational model, a relation is a set of related information, with the counterpart in SQL being a table—albeit not an exact counterpart. A key point in the relational model is that a single relation should represent a single set (for example, Customers). It is interesting to note that operations on relations (based on relational algebra) result in a relation (for example, a join between two relations).
*Relation is made of a header and a body. The header consists of a set of
attributes (called columns in SQL), where each element is identified by an attribute name and a type name. The body consists of a set of tuples (called rows in SQL), where each element is identified by a key.

Design Data Model for Database
*When you design a data model for a database, you represent all data with relations (tables).
*Start by identifying propositions that you will need to represent in your database.
*A proposition is an assertion or a statement that must be true or false. For example, the statement, “Employee Itzik Ben-Gan was born on February 12, 1971, and works in the IT department” is a proposition.
*If this proposition is true, it will manifest itself as a row in a table of Employees. A false proposition simply won’t manifest itself. This presumption is known as the close world assumption (CWA).
*formalize the propositions. You do this by taking out the actual data (the body
of the relation) and defining the structure (the heading of the relation)—for example, by creating predicates out of propositions. You can think of predicates as parameterized propositions. The heading of a relation comprises a set of attributes. Note the use of the term “set”; in the relational model, attributes are unordered and distinct. An attribute is identified by an attribute name and a type name.
For example, the heading of an Employees relation might consist of the following attributes (expressed as pairs of attribute names and type names): employeeid integer, firstname character string, lastname character string, birthdate date, departmentid integer.
*A type is one of the most fundamental building blocks for relations. A type constrains an attribute to a certain set of possible or valid values.
*For example, the type INT is the set of all integers in the
range –2,147,483,648 to 2,147,483,647. 
A type is one of the simplest forms of a predicate in a database because it restricts the attribute values that are allowed.

For example, the database would not accept a proposition where an employee birth date is February 31, 1971 (not to mention a birth date stated as something like “abc!”). Note that types are not restricted to base types such as integers or character strings; a type could also be an enumeration of possible values, such as an enumeration of
possible job positions. A type can be complex. Probably the best way to think of a type is as a class—encapsulated data and the behavior supporting it. An example of a complex type would be a geometry type that supports polygons.

Missing Values
*That is, in two-valued predicate logic, a predicate is either true or false. If a predicate is not true, it must be false. 
*Use of two-valued predicate logic follows a mathematical law called the law of excluded middle. However, some say that there’s room for threevalued (or even four-valued) predicate logic, taking into account cases where values are missing.
*A predicate involving a missing value yields neither true nor false—it yields unknown. Take, for example, a mobile phone attribute of an Employees relation. Suppose that a certain employee’s mobile phone number is missing. How do you represent this fact in the database?
*In a three-valued logic implementation, the mobile phone attribute should allow a special mark for a missing value. Then a predicate comparing the mobile phone attribute with some specific number will yield unknown for the case with the missing value. Three-valued predicate logic refers to the three possible logical values that can result from a predicate—true, false, and unknown.
*Some people believe that three-valued predicate logic is non-relational, whereas others believe that it is relational. Codd actually advocated four-valued predicate logic, saying that there were two different cases of missing values: missing but applicable (A-Mark), and missing but inapplicable (I-Mark).
*An example of “missing but applicable” is when an employee has a mobile phone, but you
don’t know what the mobile phone number is. An example of missing but inapplicable is when an employee doesn’t have a mobile phone at all. 
*According to Codd, two special markers should be used
to support these two cases of missing values. SQL implements three-valued predicate logic by supporting the NULL mark to signify the generic concept of a missing value. Support for NULL marks and three-valued predicate logic in SQL is the source of a great deal of confusion and complexity, though one can argue that missing values are part of reality. In addition, the alternative—using only twovalued predicate logic—is no less problematic.

Constraints
*The ability to define data integrity as part of the model. Data integrity is achieved through rules called constraints that are defined in the data model and enforced by the RDBMS.
*Examples
**Simplest - Assigning an attribute type with its attendant "nullability" (Whether it supports or doesn't support NULL marks).
**Constraints are also enforced through the model itself. 
**Allow zero to countable infinity children per employee. (Employees - empid and EmployeeChildren - empid, childname)
**candidate keys, which provide entity integrity - A candidate key is a key defined on one or more attributes that prevents more than one occurrence of the same tuple (row in SQL) in a relation. A predicate based on a candidate key can uniquely identify a row (such as an employee). You can define multiple candidate keys in a relation. 
******For example, in an Employees relation, you can define candidate keys on
employeeid, on SSN (Social Security number), and others. 
Typically, you arbitrarily choose one of the candidate keys as the primary key (for example, employeeid in the Employees relation), and use that as the preferred way to identify a row. All other candidate keys are known as alternate keys.
**foreign keys, which provide referential integrity. 
*******A foreign key is defined on one or more attributes of a relation (known as the referencing relation) and references a candidate key in another (or possibly the same) relation.
This constraint restricts the values in the referencing relation’s foreign key attributes to the values that appear in the referenced relation’s candidate key attributes. 
For example,suppose that the Employees relation has a foreign key defined on the attribute departmentid, which references the primary key attribute departmentid in the Departments relation. This means that the values in Employees.departmentid are restricted to the values that appear in Departments.departmentid.

Normalization
Normalization rules (also known as normal forms). Normalization is a formal mathematical process to guarantee that each entity will be represented by a single relation.
In a normalized database, you avoid anomalies during data modification and keep redundancy to a minimum without sacrificing completeness.
*1NF - The tuples (rows) in the relation (table) must be unique, and attributes should be atomic. This is a redundant definition of a relation; in other words, if a table truly represents a relation, it is already in first normal form. You achieve unique rows by defining a unique key for the table.
Atomicity of attributes is subjective in the same way that the definition of a set is subjective. If the application needs to manipulate the parts of the employee’s name separately
(such as for search purposes), it makes sense to break them apart; otherwise, it doesn’t.
An attribute might not be atomic enough based on the needs of the application, an attribute might also be subatomic. For example, if an address attribute is considered atomic for a particular application, not including the city as part of the address would violate the first normal form.
*2NF - The second normal form involves two rules. One rule is that the data must meet the first normal form. 
The other rule addresses the relationship between non-key and candidate key attributes. 
For every candidate key, every non-key attribute has to be fully functionally dependent on the entire candidate key. 
In other words, a non-key attribute cannot be fully functionally dependent on part of a candidate key. 
To put it more informally, if you need to obtain any non-key attribute value, you need to provide the values of all attributes of a candidate key from the same tuple. You can find any value of any attribute of any tuple if you know all the attribute values of a candidate key.
**Violation of 2NF - The Orders relation contains the following attributes: orderid, productid, orderdate, qty, customerid, and companyname. The primary key is defined on orderid and productid. The second normal form is violated in Figure 1-1 because there are non-key attributes that depend on only part of a candidate key (the primary key, in this example). For example, you can find the orderdate of an order, as well as customerid and companyname, based on the orderid alone.
To
conform to the second normal form, you would need to split your original relation into two relations:
Orders and OrderDetails (as shown in Figure 1-2). The Orders relation would include the attributes orderid, orderdate, customerid, and companyname, with the primary key defined on orderid. The OrderDetails relation would include the attributes orderid, productid, and qty, with the primary key defined on orderid and productid.
*3NF - The data must meet the second normal form. Also, all non-key attributes must be dependent on candidate keys non-transitively. Informally this rule means that all non-key attributes must be mutually independent. In other words, one non-key attribute cannot be dependent on another non-key attribute.
To meet the third normal form, you need to add a Customers relation (shown in Figure 1-3) with the attributes customerid (as the primary key) and companyname. Then you can remove the companyname attribute from the Orders relation.
“Every non-key attribute is dependent on the key, the whole key, and nothing but the key—so help me Codd.”

The Data-Life Cycle
*Data is usually perceived as something static that is entered into a database and later queried.
*Data is actually more similar to a product in an assembly line, moving from
one environment to another and undergoing transformations along the way.
Here’s a quick description of what each acronym represents:
*OLTP: online transactional processing
*DSA: data staging area
*DW: data warehouse
*BISM: Business Intelligence Semantic Model
*DM: data mining
*ETL: extract, transform, and load
*MDX: Multidimensional Expressions
*DAX: Data Analysis Expressions
*DMX: Data Mining Extensions

Online Transactional Processing



page 8 

nolock 
transactional 
