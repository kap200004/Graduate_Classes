# The Enhanced Entity-Relationship (EER) Model
- The enhanced ER model is expanded to include concepts from *semantic* data modeling, rather than just the conceptual data modeling offered by the ER model. 
## Subclasses, Superclasses, and Inheritance
- The EER model includes all the modeling concepts of the ER model, and additionally includes the concepts of subclass and superclass and the related concepts of specialization nd generalization. 
- The EER model also includes the concept of union type, which is used to represent a collection of entities that is the union of objects of different entity types. 
- In many cases an entity type has numerous subgroupings or subtypes of its entities that are meaningful and need to be represented explicitly because of their significance to the database application. 
- Subtypes, or subclasses are entities that are a subset of entities that belong to a superclass. 
- Subclasses are represented like any other entity but with a line connecting them to their superclass. 
- The subclass member is the same as the entity in the superclass, but in a distinct specific *role*. 
- When we implement the subclass or superclass in a database system, we may represent a member of the subclass as a distinct database object that is related via the key attribute to its superclass entity. 
- An entity cannot exist in the database merely by being a member of a subclass; it must also be a member of the superclass. Such a member can be included optionally as a member of any number of subclasses. 
- It is not necessary that every entity in a superclass be a member of some subclass. 
- Because an entity in the subclass represents the same real-world entity from the superclass, it should possess values for its specific attributes as well as values of its attributes as a member of the superclass. 
- We say that an entity that is a member of a subclass inherits all the attributes of the entity as a member of the superclass. The entity also inherits all the relationship in which the superclass participates. 
## Specialization and Generalization
### Specialization
- Specialization is the process of defining a set of subclasses of an entity type; this entity type is called the superclass of the specialization. 
- The set of subclasses that forms a specialization is defined on the basis of some distinguishing characteristic. For example, the set of subclasses secretary, engineer, and technician is a specialization of the employee superclass that distinguishes among employee entities base on the job type. 
- In an EER diagram, the subclasses that define a specialization are attached by lines to a circle that represents the specialization, which is connected in tur to the superclass. 
- The subset symbol on each line connecting a subclass to the circle indicates the direction of the superclass/subclass relationship. 
- Attributes that apply only to entities of a particular subclass are attached to the rectangle representing the subclass. These are called specific attributes of the subclass. 
- A subclass may participate in specific relationship types, or relationships specific to the subclass.
- There are two main reasons for including class/subclass relationships and specializations: 
	- Certain attributes may apply to some but not all entities of the superclass entity type. 
	- Some relationship types may be participated in only by entities that are members of the subclass. 
### Generalization
- We can think of a reverse process of abstraction in which we suppress the differences among several entity types, identify their common features, and generalize them into a single superclass of which the original entity types are subclasses.
- We use the term generalization to refer to the process of defining a generalized entity type from the given entity types that are subclasses. 
## Constraints and Characteristics of Specialization and Generalization Hierarchies
### Constraints on Specialization and Generalization
- In some cases, entities may belong to subclasses in each of the specialization. A specialization may also consist of a single subclass only. In these cases, we do not use the circle notation. 
- In some specializations, we can determine exactly the entities that will become members of each subclass by placing a condition on the value of some attribute of the superclass. These subclasses are called predicate-defined subclasses. 
- For example, if the employee entity type has an attribute job_type, we can specify the condition of membership in the Secretary subclass by the condition job_type = Secretary, which we call the defining predicate of the sub class. 
- We display a predicate-defined subclass by writing the predicate condition next to the line that connects the subclass to the specialization circle.
- If all subclasses in a specialization have their membership condition on the same attribute of the superclass, the specialization itself is called an attribute defined specialization, and the attribute is called the defining attribute of the specialization. 
- When we do not have a condition for determining membership in a subclass, the subclass is called user-defined.  
- Three other constraints may apply to a specialization: 
	- Disjointness constraint- specifies that the subclasses of the specialization must be disjoint sets. A specialization that is attribute defined implies disjointness. We represent this by putting a d in the superclass circle. 
	- Overlapping- when the same real-world entity may be a member of more than one subclass of the specialization. This case is displayed by placing an o in the circle. 
	- Completeness- may be total or partial. A total specialization constraint specifies that every entity in the superclass must be a member of at least one subclass in the specialization. This is shown in EER diagrams by using a double line to connect the superclass to the circle. A single line is used to display a partial specialization, which allows an entity not to belong to any of the subclasses. 
- In general, a superclass that was identified through the generalization process usually is total, because the superclass is derived from the subclasses and hence contains only th entities that are in the subclasses. 
- Certain Insertion and Deletion rules apply to specialization as a consequence of these constraints: 
	- Deleting an entity from a superclass implies that it is automatically deleted from all the subclasses to which it belongs. 
	- Inserting an entity in a superclass implies that the entity is mandatorily inserted in all predicate-defined (or attribute-defined) subclasses for which the entity satisfies the defining predicate. 
	- Inserting an entity in a superclass of a total specialization implies that the entity is mandatorily inserted in at least one of the subclasses of the specialization. 
### Specialization and Generalization Hierarchies and Lattices
- A subclass itself may have further subclasses specified on it, forming a hierarch or a lattice of specializations. 
- A specialization hierarchy has the constraint that every subclass participates as a subclass in only one class/subclass relationship; that is, each subclass has only one parent, which results in a tree structure. 
- In contrast, for a specialization lattice, a subclass can be a subclass in more than one class/subclass relationship. 
- In such a specialization lattice or hierarchy, a subclass inherits the attributes not only of its direct superclass, but also of all its predecessor superclasses all the way up to the root of the hierarchy or lattice. 
- A leaf node is a class that has no subclasses of its own. 
- If an attribute or relationship originating in the same superclass is inherited more than once via different paths in the lattice, then it should be included only once in the shared subclass. 
- 