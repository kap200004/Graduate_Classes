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
