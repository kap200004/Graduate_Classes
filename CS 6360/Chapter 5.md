# The Relational Data Model and Relational Database Constraints
## Relational Model Concepts
- The relational model represents the database as a collection of relations. Informally, each relation resembles a table of values. 
- When a relation is thought of as a table of values, each row in the table represents a collection of related data values. A row represents a fact that typically corresponds to a real-world entity or relationship. 
- In the formal relational model terminology, a row is called a tuple, a column header is called an attribute, and the table is called a relation. 
- The data type describing the types of values that can appear in each column is represented by a domain of possible values. 
### Domains, Attributes, Tuples, and Relations
- A domain $D$ is a set of atomic values. 
- Atomic means that each value in the domain is indivisible as far as the formal relational model is concerned. 
- A domain is given a name, data type, and format. 
- A relation schema, $R$, denoted by $R(A_{1}, \dots, A_{n})$ is made up of a relation name $R$ and a list of attributes. 
- $D$ is called the domain of $A$ and is denoted by $dom(A)$. 
- The degree of a relation is the number of attributes $n$ of its relation schema. 
- a relation of the relation schema, also denoted $r(R)$, is a set of $n$-tuples. Each $n$-tuple is an ordered list of $n$ values.
- NULL values represent attributes whose values are unknown or do not exist for some individual entities. 
### Characteristics of Relations
#### Ordering of Tuples in a Relation
- A relation is defined as a set of tuples. 
- Mathematically, elements of a set have no order among them, hence, tuples in a relation do not have any particular order. 
#### Ordering of Values Within a Tuple and an Alternative Definition of a Relation
- An $n$-tuple is an ordered list of $n$ values, hence, ordering of values is important. 
- A relation does not need to be an ordered tuple in the case of using a tuple as a mapping, where each element is a tuple of name, value pairs. When the attribute name and value are included together in a tuple, it is known as self-describing data. 
#### Values and Nulls in the Tuples
- Each value in a tuple is an atomic value, hence composite and multivalued attributes are not allowed. This model is sometimes called the flat relational model. Hence, multivalued attributes must be represented by separate relations, and composite attributes are represented only by their simple component attributes in the basic relational mode. 
- The exact meaning of a NULL value governs how it fares during arithmetic aggregations or comparisons. For example, a comparison of two NULL values leads to ambiguities. 
- It is best to avoid NULL values as much as possible. 
#### Interpretation (Meaning) of a Relation
- Some relations may represent facts about entities, whereas other relations may represent facts about relationships. 
- An alternative interpretation of a relation schema is as a predicate; in this case, the values in each tuple are interpreted as values that satisfy the predicate. 
- Closed world assumption- states that the only true facts in the universe are those present within the extension of the relations. 
### Relational Model Notation
- The uppercase letters $Q, R, S$ denote relation names. 
- The lowercase letters $q,r,s$ denote relation states. 
- The letters $t, u, v$ denote tuples. 
- An attribute $A$ can be qualified with the relation name $R$ to which it belongs by using the dot notation $R.A$. 
- Both $t[A_{i}]$ and $t.A_{i}$ (and sometimes $t[i]$) refer to the value $v_{i}$ in $t$ for attribute $A_{i}$. 
## Relational Model Constraints and Relational Database Schemas
- Constraints on databases can generally be divided into three main categories: 
	- Constraints that are inherent in the data model. We call these inherent model-based constraints or implicit constraints. 
	- Constraints that can be directly expressed in the schemas of the data model. We call these schema-based constraints or explicit constraints. 
	- Constraints that can not be directly expressed in the schemas and therefore must be enforced by the application program. We call these application-based, or semantic constraints, or business rules. 
- For example, the constraint that a relation cannot have duplicate tuples is an inherent constraint. 
- Schema based constraints include domain constraints, key constraints, constraints on NULLs, entity integrity constraints and referential integrity constraints. 
### Domain Constraints
- Domain constraints specify that within each tuple, the value of each attribute $A$ must be an atomic value from the domain $dom(A)$. 
### Key Constraints and Constraints on NULL Values
- By definition, all elements of a set are distinct, hence, all tuples in a relation must also be distinct. This means that no two tuples can have the same combination of values. 
- Usually there are other subsets of attributes of a relation schema $R$ with the property that no two tuples in any relation state $r$ of $R$ should have the same combination of values for these attributes. 
- Any such subset of attributes that can not be the same for any two tuples in a relation is called a superkey of the relation schema $R$. 
- A superkey SK specifies a uniqueness constraint. 
- Every relation has at lease one default superkey, the set of all its attributes. 
- A key $k$ of a relation schema $R$ is a superkey of $R$ with the additional property that removing any attribute $A$ from $K$ leaves a set of attributes $K'$ that is not a superkey of $R$ any more. In other words, it is a minimal superkey.
- In general, any superkey formed from a single attribute is also a key. 
- A key with multiple attributes must require all its attributes together to have the uniqueness property. 