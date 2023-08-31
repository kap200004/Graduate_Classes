# Chapter 2 Database System Concepts and Architecture
## Introduction
* A client module is typically designed so that it will run on a user workstation or personal computer. 
* The other kind of module, called a server module, typically handles data storage, access, search, and other functions. 
## Data Models, Schemas, and Instances
* Data abstraction generally refers to the suppression of details of data organization and storage and the highlighting of the essential features for an improved understanding of data. 
* A data model-- a collection of concepts that can be used to describe the structure of a database-- provides a necessary means to achieve this abstraction. 
* By structure of a database we mean the data types, relationships, and constraints that should hold for the data. 
* Most data models also include a set of basic operations for specifying retrievals and updates on the database. 
### Categories of Data Models
* We can categorize data models according to the types of concepts they use to describe the database structure. 
* Between High-level and low-level data models is a class of representational data models, which provide concepts that may be understood by end users but that are not too far removed from the way data is organized within the computer. 
* Conceptual data models use concepts such as entities, attributes, and relationships. 
* An entity represents a real-world object or concept. 
* an attribute represents some property of interest that further describes an entity. 
* a relationship among two or more entities represents an association among two or more entities. 
* Representational data models represent data by using record structures and hence are sometimes called record-based data models. 
* An access path is a structure that makes the search for particular database records efficient, and is represented in physical data models. 
* An index is an example of an access path that allows direct access to data using an index term or a keyword. 