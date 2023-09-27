## Using High-Level Conceptual Data Models for Database Design
- Once the requirements have been collected and analyzed, the next step is to create a conceptual schema for the database, using a high-level conceptual data model. This is called conceptual design. 
- The conceptual schema includes detailed descriptions of the entity types, relationships, and constraints using the concepts provided by the high-level data model. 
- The next step in database design is the actual implementation of the database, using a commercial DBMS. This step is called logical design or data model mapping. 
- The last step is the physical design phase, during which the internal storage structures, file organizations, indexes, access paths, and physical design parameters for the database files are specified. 
## Entity Types, Entity Sets, Attributes, and Keys
- The ER model describes data as entities, relationships, and attributes. 
### Entities and Attributes
- An entity is a thing or object in the real world with an independent existence. 
- Each entity has attributes- the particular properties that describe it. For example, an EMPLOYEE entity may be described by the employee's name, age, address, salary, and job. 
- Each entity will have values for its attributes. The attribute values that describe each entity become a major part of the data stored in the database. 
- Several types of attributes occur in the ER model: simple versus composite, single-valued versus multivalued, and stored versus derived. 
#### Composite versus Simple (Atomic) Attributes
- Composite attributes can be divided into smaller subparts, which represent more basic attributes with independent meanings. For example the Address attribute of the EMPLOYEE entity can be subdivided into street address, city, state, and zip code. 
- Attributes that are not divisible are called simple, or atomic attributes. 
#### Single-Values versus Multivalued Attributes
- In some cases an attribute can have a set of values for the same entity- for instance, a Colors attribute for a car, or a college degrees attribute for a person. Cars with one color have a single value, but cars with more colors are multivalued. 
- A multivalued attribute may have lower and upper bounds to constrain the number of values allowed for each individual. 
#### Stored versus Derived Attributes
- In some cases, we can derive an attributed from another attribute, for example, using today's date and somebody's birth date to derive their age. These are called derived attributes and are said to be derivable from some stored attribute. 
#### NULL values
- For some situates, a particular entity may not have an applicable value for an attribute, such as in the case of an apartment attribute for a house address. For such situations, a special value called NULL is used. 
#### Complex Attributes
- Notice that, in general, composite and multivalued attributes can be nested arbitrarily. We call these complex attributes. For example, a person can have more than one residence and each residence can have a single address and multiple phones. 
- We can represent arbitrary nesting by grouping components of a composite attribute between parentheses () and separating the components with commas, and by displaying multivalued attributes between braces. 
### Entity Types, Entity Sets, Keys, and Value Sets
- An entity type defines a collection(or set) of entities that have the same attributes. Each entity type in the database is described by its name and attributes. 
- The collection of all entities of a particular entity type in the database at any point in time is called an entity set. 
- An entity type is represented in ER diagrams as a rectangular box enclosing the entity type name. 
- Attribute names are enclosed in ovals and are attached to their entity type by straight lines. 
- Composite attributes are attached to their component attributes by straight lines. 
- Multivalued attributes are displayed in double ovals. 
- An entity type describes the schema or intension for a set of entities that share the same structure. 
- The collection of entities of a particular entity type is grouped into an entity set, which is also called the extension of the entity type. 
#### Key Attributes of an Entity Type
- An entity type usually has one or more attributes, known as keys or uniqueness constraints, whose values are distinct for each individual entity in the entity set. 
- For the person entity type, a typical key attribute is the social security number. 
- Sometimes several attributes together form a key, meaning that the combination of the attribute values must be distinct for each entity. If a set of attributes possesses this property, the proper way to represent this in the ER model is to define a composite attribute and designate it as a key attribute of the entity type. 
- In the ER diagram, each key attribute has its name underlined inside the oval. 
- An entity type my have more than one key attribute, and it may also have no key, in which case it is called a weak entity type. 
- If two attributes are underlined separately in the ER diagram, then each is a key on its own. 
#### Value Sets (Domains) of Attributes
- Each simple attribute of an entity type is associated with a value set, or domain of values, which specifies the set of values that may be assigned to that attribute for each individual entity. 
- Mathematically, an attribute $A$ of entity set $E$ whose value set is $V$ can be defined as a function from $E$ to the power set $P(V)$, or set of all subsets, of $V$: $A: E\to P(V)$
- We refer to the value of attribute $A$ for entity $e$ as $A(e)$. 
### Initial Conceptual Design of the COMPANY Database
- We find that attributes like Name or Address may be composite attributes; however, if this is not specified in the requirements, we will have to go back to the users to see if any of them will refer to the individual components of name or address. 
## Relationship Types, Relationship Sets, Roles, and Structural Constraints
- Whenever an attribute of one entity type refers to another entity type, some relationship exists. In the ER model, these references should not be represented as attributes, but as relationships. 
- In the initial design of entity types, relationships are typically captured in the form of attributes. As the design is refined, these attributes get converted into relationships between entity types. 
### Relationship Types, Sets, and Instances
- A relationship type $R$ among $n$ entity types $E_{1}, \dots , E_{n}$ defines a set of associations among entities from these entity types. 
- A relationship set is a mathematical relation on $E_{1}, \dots, E_{n}$, alternatively, it can be defined as a subset of the Cartesian product of the entity sets $E_{1} \times E_{2} \dots \times E{n}$. 
- In ER diagrams, relationship types are displayed as diamond-shaped boxes, which are connected by straight lines to the rectangular boxes representing the participating entity types. The relationship name is displayed in the diamond-shaped box. 
### Relationship Degree, Role Names, and Recursive Relationships
#### Degree of a Relationship Type
- The degree of a relationship type is the number of participating entity types. Hence two entities in a binary relationship is a degree of two. 
- A relationship of degree three is called ternary. 
#### Role Names and Recursive Relationships
- The role name signifies the role that a participating entity from the entity type plays in each relationship instance. 
- In some cases, the same entity type participates more than once in a relationship type in different roles. In such cases the role name becomes essential for distinguishing the meaning of the role that each participating entity plays. Such relationship types are called recursive relationships, or self-referencing relationships. 
### Constraints on Binary Relationship Types
- We can distinguish two main types of binary relationship constraints: cardinality ratio, and participation. 
#### Cardinality Ratios for Binary Relationships
- The cardinality ratio for a binary relationship specifies the maximum number of relationship instances that an entity can participate in. 
- For example, the cardinality ratio for DEPARTMENT:EMPLOYEE is 1:N if each department can be related to any number of employees, but an employee can be related to at most one department. 
- The possible cardinality ratios for binary relationship types are 1:1, 1:N, N:1, and M:N. 
- Cardinality ratios for binary relationships are represented don ER diagrams by displaying 1, M, and N on the diamonds. 
#### Participation Constraints and Existence Dependencies
- The participation constraint specifies whether the existence of an entity depends on its being related to another entity via the relationship type. 
- There are two types of participation constraints, partial and total. 
- If a company policy states that every employee must work for a department, then an employee entity can exist only if it participates in at least one works for relationship instance. Thus the participation of employee in works for is called total participation, meaning that every entity in the total set of employee entities must e related to a department entity via works for. 
- Total participation is also called existence dependency. 
- We do not expect every employee to manage a department, so the participation of employee in the manages relationship type is partial, meaning that some or part of the set of employee entities are related to some department via the manages relationship. 
- In ER diagrams, total participation is displayed as a double line connecting the participating entity type to the relationship, whereas partial participation is represented by a single line. 
### Attributes of Relationship Types
- Relationship types can also have attributes ,similar to those of entity types. 
- An example is to include the date on which a manager started managing a department via an attribute Start_date for the Manages relationship type. 
- For a 1:N relationship type, a relationship attribute can be migrated only to the entity type on the N-side of the relationship. 
- In both 1:1 and 1:N relationship types, the decision where to place a relationship attribute, as a relationship type attribute or as an attribute of a participating entity type, is determined subjectively by the schema designer. 
- For M:N relationship types, some attributes may be determined by the combination of participating entities in a relationship instance, not by an single entity. Such attributes *must* be specified as relationship attributes. An example is the hours attribute of the M:N relationship works_on, the number of hours a week an employee currently works on a project is determined by an employee-project combination and not separately by either entity. 
## Weak Entity Types
- Entity types that do not have key attributes of their own are called weak entity types. 
- Entities belonging to a weak entity type are identified by being related to specific entities from another entity type in combination with one of their attribute values. 
- We call this other entity type the identifying type, or owner entity type, and we call the relationship type that relates a weak entity type to its owner the identifying relationship. 
- A weak entity type always has a total participation constraint with respect to its identifying relationship. 
- Not every existence dependency results in a weak entity type, for example, a Driver_License entity cannot exist unless it is related to a Person entity, even though it has its own key, and hence is not a weak entity. 
- A weak entity type normally has a partial key, which is the attribute that can uniquely identify weak entities that are related to the same owner entity. 
- In the worst case, a composite attribute of all the weak entity's attributes will be the partial key. 
- In ER diagrams, both a weak entity type and its identifying relationship are distinguished by surrounding their boxes and diamonds with double lines. 
- The partial key attribute is underlined with a dashed or dotted line. 
- Weak entity types can sometimes be represented as complex (composite, multivalued) attributes. 
- In general, any number of levels of weak entity types can be defined; an owner entity type may itself be a weak entity type. In addition, a weak entity type may have more than one identifying entity type and an identifying relationship type of degree higher than two. 
## ER Diagrams, Naming Conventions, and Design Issues
- 