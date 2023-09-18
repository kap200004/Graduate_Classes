## Using High-Level Conceptual Data Models for Database Design
- Once the requirements have been collected and analyzed, the next step is to create a conceptual schema for the database, using a high-level conceptual data model. The is called conceptual design. 
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