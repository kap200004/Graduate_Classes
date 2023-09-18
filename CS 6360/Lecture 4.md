# Chapter 3: Data Modeling Using the Entity-Relationship Model
- Entity- thing in real world with independent existence. 
- Attributes- particular properties that describe the entity. 
- Entity type- a collection or set of entities that have the same attributes. 
- We draw a rectangle for representing our entity types when we are diagramming an ER model. 
- We draw the attributes of our entity types in ovals connected by lines to their entity. 
## Types of Attributes
- Simple versus composite- simple attributes are represented in a single oval, but attributes that are made of other attributes are represented as a a single oval with lines to other ovals that represent the simple attributes that make up the composite. 
- Single-valued vs multivalued- some attributes will have more than one value, for those, we draw the attribute as a double oval. 
- Stored vs derived- if an attribute is not physically in the table, but will be computed or derived from other attributes, we represent it with a dashed oval. 
- We underline the name of the attribute to represent uniqueness. 
- Partial key- could be part of a key, combined with another attribute or entity can be unique. We represent it by underlining the name of the attribute with a dashed line. 
- Value set constraints specify the set of values that may be assigned to an attribute for each individual entity. 
## Relationship Types, Relationship Sets, Roles, and Structural Constraints
- We represents relationships with diamonds that connect two related entity types. 
- Degree of relationship type- The degree of relationship refers to how many different entities are involved in that relationship. 
- Sometimes relationships have entity types, this occurs when every entity involved in the relationship have a contract to agree to some attribute.
- Role names signify the role that a participating entity plays in each relationship instance. It is usually not needed as the entity type names and relationship type names usually imply the semantic role. It is necessary when an ambiguity arises, and the roles are not so clear. 
- Recursive relationships are defined by the scenario where the same entity type participates more than once in a relationship type in different roles. In these cases we must specify role names since it is not possible to imply role when both sides of the relationship has the same entity type and relationship type. 
### Constraints on Binary Relationship Types
- Cardinality Ratio for a binary relationship specifies the maximum number of relationship instances in which that entity can participate. 
- We have three types of cardinality relationships: 
	- one to one, or 1:1
	- one to many, or 1:n
	- many to many, or n:m
- Participation constraints specify whether each entity in an an entity type must participate in a relationship set or not. There are two types of participation constraints, partial and total. 
- For total relationships, we draw a double line, for partial we draw only a single line. 
## Weak Entity Types
- Weak entities are represented as double rectangles, they do not have key attributes of their own and are identified by being related to specific entities from another entity type. 
- This does not mean that weak entities don't have a key, but that the parent entity's key is part of it. 
- Weak entities have an identifying relationship, and always has a total participation constraint. 
- If the parent entity is deleted, all related weak entities are deleted too. 
* A relationship that is used to identify a weak entity is represented with a double diamond. There must be one involved with a weak entity. 
- Sometimes you will have a weak entity type that has more than one identifying relationship. 