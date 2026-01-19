# Basics
- Database security involves protecting the database from unauthorized **access**, **changes** or **deletion**. 
## Confidentiality: 
- Requires that ONLY authorized users have access to information to preserve the privacy of users
- To address this, we implement appropriate encryption across the development stack. This includes hashing passwords, protecting against SQL injection attacks, implementing time-outs for repeated unsuccessful attempts, etc.
## Integrity 
- Requires that ONLY authorized users be allowed to modify data consistency
- Incorrect data can be harmful to users and applications
## Availability: 
- Requires that information can be accessible by authorized users when needed 
	- Security attacks can sometimes cause a database to be rendered unusable
# Security Threats: 
- We begin by defining what a **security threat** truly is, such that: 
	1) Any situation that can harm the system by **compromising privacy**, **confidentiality**, or by **damaging the database** itself
	2) A **vulnerability** that **allows a threat to occur**, like inappropriate access control or loopholes in firewall protection 
	3) Security threats can happen **accidentally** or **deliberately** 
## Examples of Accidental/Structural Security Threats:
### User Errors: 
- A user unintentionally requests an operation/data for which they should not have the required authorization
### Communication System Errors: 
- The backend sends a message to the wrong user, resulting in unauthorized disclosure of database contents and/or structure 
- Connecting a user to a session that belongs to another user with different access privileges 
### Operating System or Database Server Errors: 
- Overwriting files or destroying parts of the database by accident
- Fetching the wrong files or data and sending them to a user 
- Failure to erase files or data that should be deleted 
## Examples of Deliberate Security Threats: 
### Sources: 
- A user **intentionally gains unauthorized access and/or performs unauthorized operations** on the database for personal gain 
- An **unhappy employee who works on the backend**
- **Industrial spies seeking information for competing parties** 
### Methods: 
- **Wiretapping** of communication lines
- Electronic eavesdropping by **monitoring electrical signal traffic** 
- **Reading display screens/printouts** that were left **unsupervised** 
- **Impersonation** of authorized users or users with more privileges than standard
- **Writing programs to bypass the DBMS and access stored data directly** 
- Writing programs to **perform unauthorized operations** 
- **SQL injection** attacks to **derive information about hidden data through clever querying**

# Security Plans: 
- Define **physical security** and **information system access control** to control access to resources and data
- Implement **physical security measures** to the building hosting the database
- **Proper installation and configuration of DBMSs**
- **Creating and securing user accounts** and using **different levels of privileges to delegate administrative power** 
- **Developing and enforcing standards for external apps** that access the the database
- **Encrypting sensitive data** 
- Ensuring that **network connections to the database are secure** in themselves
- Establish **appropriate audit mechanisms** for the database
- **Identify and guard against security threats** and **apply security controls and security updates** as needed 
# Information System Access Control: 
- Authorization: 
	- Defines **who has access to the system and what specific data** 
	- Defines **what operations a specific user can perform** 
- Identification: 
	- **Refers to the way in which users are identified** (userID, biometrics, etc.)
- Authentication: 
	- **Verifies the identity of a user by validating it against the user profile** (which is kept secure on the DB end)
- Accountability: 
	- Refers to the need to **capture and maintain logs that can be used for traceability** when security incidents occur
# Levels to DB Security Implementation: 
1) **Database Level**: Database users and authorization
2) **Application Level**: Information management and processing
3) **Operating System Level**: Data storage and protection
4) **Network Level**: Data transmission
5) **Physical Level**: Computer equipment protection
6) **Human Level**: Social engineering protection
## Database Level: 
- By default, a **DB system creator (or admin) is a superuser**, who has **global privileges to the DB system**, including:
	- Can perform the SELECT, INSERT, UPDATE, and DELETE operations to **access tables**
	- Can import files
	- Can perform the CREATE, ALTER, INDEX, and DROP operations to **modify tables**
	- Able to view any entry/table
	- Can alter, create, or execute routines such as stored procedures
	- Assertion, checks, and triggers
	- Can GRANT permissions to another user; can grant specific permissions for specific tables/columns/rows
- General users:
	- General users have no global privileges on the DB system; only have SELECT, INSERT, and UPDATE privileges 
	- Have global privileges on their own specific DB, including the GRANT operation
# Security Mechanisms: 
## View(s)
-  A view is a relation defined/fetched by a query 
- We can increase security by using views for access control, which allows us to **hide structures and data that the user should not otherwise be able to see**
- Increase logical interdependence between data by creating general presentations of data
- Increase physical interdependence amongst data by partitioning
- **Value-dependent view**: 
	- Restricts data by a specific WHERE clause, which creates the view
```SQL
CREATE VIEW CSMajor AS
	(SELECT sid, lname, fname, credits
	FROM student
	WHERE major = 'CS');
```
- **Value-independent view**: 
	- Restricts data by a specific columns of the base tables
```SQL
CREATE VIEW MajorView AS
	(SELECT sid, lname, fname, major 
	FROM student);
```
## Other Mechanisms: 
- **Access control management**: 
	- Limit access per DB object (table, view, attributes), per user, per operation
- **Security log**: 
	- Keep a record of all attempted security violations 
- **Audit trail**: 
	- Records all access to the DB, including requestors, operations performed, workstation used, time of access, data entries and values involved. 
- **Triggers**:
	- Sets up the audit trail for a table, by recording all changes, the time they were made, and the identity of the user who made them 
- **Encryption**: 
	- Should be used whenever data is communicated to other sites
	- Encryption involves a significant overhead, and so we often only encrypt passwords
	- A more efficient approach to hashing is to do it at the application level 
# Access Control Policy (ACP): 
- We define access control to be how we identify the permissions an individual can have/do
- There are three main variations of ACP: 
### Role-Based Access Control (RBAC):
- Group-level permission - "what can users of this role do"
- Permissions per role; users are only granted one role
### Mandatory Access Control (MAC):
- Classification or privacy level 
- Permissions per classification 
### Discretionary Access Control (DAC): 
- Personal permission - "who has access and what they do"
- Permissions per resource; subject to changing often
- The least restrictive ACP
## RBAC: 
- The limitations defined by job responsibilities 
- Users with the same role have the same privileges 
- Not able to assign permissions to users directly; must assign a role to a user 
- Permissions per role are typically never changed
- RBAC typically involves very few roles, is centrally administered, and thus is much easier to manage
- Commonly utilized by large organizations
- Must grant each user the correct role
## MAC: 
- Policy administrators implement organization-wide security policies, which is guaranteed to be enforced for all users 
- Typically viewed as a classification/privacy level
- Often used in military systems, with emphasis on confidentiality and classification of data
- Centralized control access
- Classifies all end users and provides them with labels, which permit them to gain access through security checkpoints according to systemic security guidelines 
- Users do not have the ability to override the policy and thus, cannot grant access to restricted tables to another user 
- Not used much in currently 
## DAC: 
- **Business owner is responsible for deciding who is allowed to do what** on which part of the database
- **Data owner can manage the content they own**. They decide who has access, can add or remove people the access list, and pass permissions to other users. 
- Since an **individual has complete control over any objects they own, DAC is the least restrictive** compared to the other access control policies. 
- **Permissions given to an individual are inherited into other programs they use**, potentially leading to malware being executed without the individual being aware 
- **Permissions per resource are changed often** 
## Choosing Access Control Methodology: 
- If the DB is **storing highly confidential/sensitive information**, we use **MAC or RBAC**
- If the **DB allows only certain people to enter, DAC is the simplest and most popular**
# SQL Data Control Language: 
- Authorization sublanguage allows us to grant and revoke privileges from users
	- We define privilege to be an action, like creating, executing, reading, updating, and deleting, that a user is permitted to perform on database objects
# Operating System Level: 
- Set up virus protection and firewalls
- Do not install adware or spyware 
- Do not use "wizards" to skip the technical installation of software
	- SQLServer - Clicking through the Wizard's automatic installation created a user with no password (and thus a free admin)
- Hide stuff; shut down and lock the machine when it is not in use 
- Execute as little programs as possible - the more programs run, the more chance a DB has of being attacked. We also recognize disabling extra programs and unnecessary features of running programs
- Close all IO ports 
# Network Level: 
- Hide the server from the WWW
- Separate your database server from the web-access server
- Limit connections to database server to only trusted sources by specifying IPs and MACs
- Only allow the world to connect to your application, which is hosted on the trusted application server. Then, only the application can connect to your database. Do not let the world connect directly to your database server. 
- Do not use a default port 
- Separate server for authentication 
- Set up firewalls 
# Physical Level: 
- Always lock everything that can impact your database 
- Lock the everything
- Implement security measures 
- 