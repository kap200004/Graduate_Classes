## Introduction
* New types of database systems, often referred to as big data storage systems, or NOSQL systems, have been created to manage data for social media applications that do not store only textual or numeric information like traditional database applications. 
* Data warehouses are used in many companies to extract and analyze useful business information from very large databases to support decision making.
* Database- a collection of related data. 
* Data- known facts that can be recorded and that have implicit meaning. 
* A database has the following implicit properties: 
	* A database represents some aspect of the real world, sometimes called the miniworld or the universe of discourse. Changes to the miniworld are reflected in the database. 
	* A database is a logically coherent collection of data with some inherent meaning. 
	* A database is designed, built, and populated with data for a specific purpose. It has an intended group of users. 
* Database management system (DBMS)- a computerized system that enables users to create and maintain a database. It facilitates the process of defining, constructing, manipulating, and sharing databases among various users and applications. 
* The database definition or descriptive information is called meta-data. 
* An application program accesses the database by sending queries or request for data to the DBMS.
* A query typically causes some data to be retrieved. 
* A transaction may cause some data to be read and some data to be written into the database. 
* We will call the database and DBMS software together a database system. 
## An Example
* A database is organized as files, each of which stores data records of the same type. 
* To define a database, we must specify the structure of the records of each file by specifying the different types of data elements to be stored in each record. 
* We must also specify a data type for each data element within a record. 
* Records in various files may be related. 
* Queries and updates must be specified in the query language of the DBMS to be processed. 
* Design of a new application for an existing database or design of a brand new database starts off with a phase called requirements specification and analysis.
* These requirements are documented in detail and transformed into a conceptual design. 
* The design is then translated to a logical design that can be expressed in a data model implemented in a commercial DBMS. 
* The final state is physical design, during which further specifications are provided for storing and accessing the database. 
## Characteristics of the Database Approach
* In traditional file processing, each user defines and implements the files needed for specific software application as part of programming the application. 
* Because each user requires some data not available from the other user's files, a redundancy in defining and storing data results in wasted storage space and in efforts to maintain common up-to-date data occurs. 
* The main characteristics of the database approach versus the file-processing approach are the following: 
	* Self-describing nature of a database system. 
	* Insulation between programs and data, and data abstraction. 
	* Support of multiple views of the data. 
	* Sharing of data and multiuser transaction processing. 
### Self-Describing Nature of a Database System
* The database system contains not only the database itself but also a complete definition or description of the database structure and constraints. 
* This is stored in the database catalog. Data in the database catalog is known as meta-data. 
* In traditional file processing, data definition is typically part of the application programs themselves, but a DBMS will work with any number of database applications. 
* DBMS software can access diverse databases by extracting the database definition from the catalog and using these definitions. 
### Insulation between Programs and Data, and Data Abstraction
* In traditional file processing, any changes to the structure of a file may require changing all the programs that access that file. 
* By contrast, DBMS access programs do not require such changes in most cases, as the structure of data files is stored in the DBMS catalog separately from the access programs. We call this program-data independence. 
* The characteristic that allows program-data independence and program-operation independence is called data abstraction. 
* A data model is a type of data abstraction that is used to provide a conceptual representation. 
### Support of Multiple Views of the Data
* A view may be a subset of the database or it may contain virtual data that is derived from the database files but is not explicitly stored. 
* A multiuser DBMS whose users have a variety of distinct applications must provide facilities for defining multiple views. 
### Sharing of Data and Multiuser Transaction Processing
- The DBMS must include concurrency control software to ensure that several users trying to update the same data do so in a controlled manner so that the result of the updates is correct. 
- A transaction is an executing program or process that includes one or more database accesses, such as reading or updating database records. 
- The DBMS must enforce several transaction properties: 
	- Isolation- ensures that each transaction appears to execute in isolation from other transactions. 
	- Atomicity- ensures that either all the database operations in a transaction are executed or none are. 
## Actors on the Scene
- We call actors on the scene those whose jobs involve the day-to-day use of a large database. 
- We call actors behind the scene those who work to maintain the database system environment but who are not actively interested in the database contents as part of their daily job. 
### Database Administrators
- Administering the database environment and the DBMS is the responsibility of the database administrator. 
- The DBA is responsible for:
	- Access to the database. 
	- Coordinating and monitoring the database use. 
	- Acquiring hardware and software resources as needed. 
- The DBA is accountable for problems such as security breaches and poor system response time. 
### Database Designers
- Database designers are responsible for identifying the data to be stored in the database and for choosing appropriate structures to represent and store this data. 
- In many cases the designers are on the staff of the DBA. 
### End users
- End users are the people whose jobs require access to the database for querying, updating, and generating reports. 
- The database primarily exists for use by the end users. 
- There are several categories of end users:
	- Casual end users- occasionally access the database. 
	- Naïve or parametric end users- Their main job function revolves around constantly querying and updating the database using standard types of queries called canned transactions. 
	- Sophisticated end users- include engineers, scientists, business analysts, and others who thoroughly familiarize themselves with the facilities of the DBMS. 
	- Standalone users- maintain personal databases by using ready-made program packages that provide easy-to-use menu-based interfaces. 
### System Analysts and Application Programmers
- System analysts determine the requirements of end users and develop specifications for standard canned transactions that meet those requirements. 
- Application programmers implement these specifications as programs. 
## Workers Behind the Scene
- Workers behind the scene include:
	- DBMS system designers and implementers. 
	- Tool developers- design and implement tools that facilitate database modeling and design. 
	- Operators and maintenance personnel- responsible for the actual running and maintenance of the hardware and software environment. 
- They typically do not use the database contents for their own purposes. 
## Advantages of Using the DBMS Approach
### Controlling Redundancy
- In traditional file processing groups that have to implement their file structure independently may further duplicate some or all of the same data in their own files. 
	- This leads to duplication of effort and wasted storage space. 
	- Inconsistencies can arise because updates are applied independently by each user group. 
### Restricting Unauthorized Access
- A DBMS should provide a security and authorization subsystem, which the DBA uses to create accounts and to specify account restrictions. 
- The DBMS should enforce these restrictions automatically. 
### Providing Persistent Storage for Program Objects
- Program objects or classes can be stored in databases, rather than discarded once a program terminates. 
- Object-oriented database systems are compatible with programming languages, and the DBMS software automatically performs any necessary conversions to persistently store program objects on disk. 
- Impedance mismatch problem-an older issue where data structures provided by the DBMS were incompatible with the programming language's data structures. 
### Providing Storage Structures and Search Techniques for Efficient Query Processing
- Database systems must provide capabilities for efficiently executing queries and updates. 
- Auxiliary files called indexes are often used for the purpose of speeding up disk search. 
- The DBMS often has a buffering or caching module that maintains parts of the database in main memory buffers.
- The query processing and optimization module of the DBMS is responsible for choosing an efficient query execution plan for each query based on the existing storage structures. 
### Providing Backup and Recovery
- A DBMS must provide facilities for recovering from hardware or software failures. 
- The backup and recovery subsystem is responsible for recovery. 
- The recovery subsystem makes sure that the database is restored to the state it was in before a computer system failure occurs. 
### Providing Multiple User Interfaces
- A DBMS should provide a variety of user interfaces for different types of users. 
### Representing Complex Relationships Among Data
- A DBMS must have the capability to represent a variety of complex relationships among the data, to define new relationships as they arise, and to retrieve and update related data. 
### Enforcing Integrity Constraints
- Most database applications have certain integrity constraints that must hold for the data. 
- A DBMS should provide capabilities for defining and enforcing these constraints. 
- Referential integrity constraint- a constraint that requires all records in one file to be related to a record in another file. 
- The uniqueness constraint is also known as the key constraint and requires that a record have a unique value for some attribute. 
- Rules that pertain to a specific data model are called inherent rules of the data model. 
### Permitting Inferencing and Actions Using Rules and Triggers
- Deductive database systems- database systems that provide capabilities for defining deduction rules for inferencing new information from the stored database facts. 
- A trigger is a form of a rule activated by updates to a table, sending messages, and so on. 
- Stored procedures are invoked when certain conditions are met. 
### Additional Implications of Using the Database Approach
- The database approach permits the DBA to define and enforce standards among database users in a large organization. 
- Developing a new applications takes very little time. Once a database is up and running, substantially less time is generally required to create new applications using DBMS facilities. 
- Modern DBMSs allow certain types of evolutionary changes to the structure of the database without affecting the stored data and the existing application programs. 
- As soon as one user's update is applied to the database, all other users can immediately see this update. 
- Lower costs of operation and management due to eliminating redundancies and wasteful overlap. 
## When Not to Use a DBMS
- There are a few situations in which a DBMS may involve unnecessary overhead costs that would not be incurred in traditional file processing. 
- Under the following circumstances, it may be more desirable to develop customized database applications: 
	- Simple, well-defined database applications that are not expected to change at all. 
	- Stringent, real-time requirements for some application programs that may not be met because of DBMS overhead. 
	- Embedded systems with limited storage capacity. 
	- No multiple-user access to data. 