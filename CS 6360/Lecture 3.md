### Categories of Data Models
1. Conceptual (high-level, semantic) data models: 
   Provide concepts that are high level . 
2. Implementation data models:
   Also called representational, used by many commercial DBMS implementations. 
3. Physical data models:
   provide concepts that describe details of how data is stored on the computer, such as a search key, addresses and registers. 
4. Self-Describing Data Models:
   Combine the description of data with the data values. Examples include XML, key-value stores, and some NoSQL systems. 
- The database schema is the description of a database. Describes the structure, data types, and the constraints on the database. 
- Database state is really the contents of the database at some point in time.
- Initial Database state refers to the database state when it is initially loaded in to the system, at power on. 
- Valid state- a state that satisfies the structure and constraints of the database. 
- Schema is also called intension, state is also called extension. 
### Three-Schema Architecture
- The Three-schema architecture is used to support DBMS characteristics of program-data independence and support of multiple views. 
	- External view-describe what a certain type of user see, or how they view the database. 
	- Conceptual Schema- sometimes called logic, the description of the database or schema. 
	- Internal Schema- sometimes called the physical, how data is stored on the computer. 
- Mappings among schema: 
	- External/Conceptual mapping- the DBMS maps query commands directly to the conceptual schema. 
	- Conceptual/Internal mapping- mapping the logical description to the actual physical hardware. 
### Database Independence
- Logical independence- we can change the conceptual schema, without needing to make changes to the external schema. Helps support multiple views of the data. 
- Physical data independence- the capacity to change the internal schema, without having to change the conceptual. 
- Data independence- when a schema at a lower level is changed without having to change the higher level, only the mapping between the two. 
### DBMS Languages
- DDL- data definition language, used to create the database schema. 
- DML- data manipulation language, used to query, add, delete. 
	- Used to specify database retrievals and updates. 
	- DML commands can be embedded in a general-purpose programming language like C++. 
	- Alternatively, stand-alone DML commands can be applied directly, called a query language. 
- High level, nonprocedural language- just specifies what we want, does not describe how to get it. SQL relational language is an example. Also called declarative. 
- Low Level or Procedural Language- retrieve data one record-at-a-time. Constructs such as looping are needed to view multiple records, along with positioning pointers. 
### DBMS Interfaces
- The DBMS has different interfaces: 
	- The stand-alone query language interface: used to enter SQL queries. 
- Programmer interfaces for embedding DML in programming languages. 
- User-friendly interfaces: 
	- Menu-based, forms-based, graphics-based, etc. 
- Mobile interfaces: interfaces allowing users to perform transaction sing mobile apps. 
- Interface for the DBA:
	- Used to create user accounts and grant authorizations.
	- Used to set system parameters, can change schemas or access paths. 
	- Can be used to monitor the usage and performance of the database system. 
- A Centralized DBMS:
	- Combines everything into a single system including the DBMS software, hardware, application programs, and user interface processing software. 
- 2-tier Client Server Architectures: 
	- Used to allow specialized servers with specialized functions, such as printer servers, file servers, DBMS servers, and web servers. 
	- Clients provide appropriate interface through a client software module to access and utilize the various server resources. 
	- These may be diskless machines. 
- DBMS Server
	- Provides database query and transaction services to the clients. 
	- Applications running on clients utilize and API to access server databases via a standard interface. 
- Three Tier Client-server Architecture
	- The client may have a web interface or GUI that accesses an application server, or webserver, that in turns accesses the Database server. This is done for security and reliability. 
### Overview of Database Design Process
- Two reports come out of requirements collection and analysis: 
	- Functional requirements- All functions, services, methods that the database will provide. 
	- Data requirements- all elements that describe our miniworld. 
- In this class we will use the entity-relationship, or, ER model. Other models include the unified modeling language or UML. 
- The ER model describes data as: 
	- Entities- which we draw as rectangles. 
	- Relationships- we draw with diamonds, describe how the entities relate with one another. 
	- Attributes- we draw these in ovals, these are the attributes of our entities. 