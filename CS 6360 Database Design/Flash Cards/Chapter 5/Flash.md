TARGET DECK: CS 6360

START
Basic
Front:
What is a domain $D$?
Back:
A domain $D$ is a set of atomic values
Tags:
Definitions
END

$START
Basic
Front:
What three things can be given to a domain to define it? 
Back:
1. Name
2. Datatype
3. Format
Tags:
Domain
END

$START
Basic
Front:
What is the degree or arity of a relation? 
Back:
The number of attributes.
Tags:
Definitions
END

$START
Basic
Front:
A relation schema $R$ is denoted by what? 
Back:
$R(A_{i},\dots A_{n})$ where $R$ is the name of the relation and $A_{i}$ is the name of a role played by some domain $D$ in the relation schema. 
Tags:
Definitions
END

$START
Basic
Front:
What is the cartesian product definition about some relation $r$ on an relation schema $R$? 
Back:
$r(R)\subseteq dom(A_{1})\times dom(A_{2})\dots \times dom(A_{n})$
Tags:
Relations
END

$START
Basic
Front:
What are four characteristics that make a relation different from a file or a table? 
Back:
1. Ordering of Tuples in a Relation- A relation is defined as as set of tuples. Elements of a set have no order among them. 
2. Ordering of Values within a Tuple- an $n$-tuple is an ordered list of $n$ value, however we can give a more general definition of a relation where a tuple can be considered as a set of (\<attribute>, \<value>) pairs, here each pair gives the value of the mapping from an attribution $A_{i}$ to a value $v_{i}$ from dom($A_{i}$). Order is not important because the attribution name appears with its value. 
3. Values and Nulls- Each value in a tuple is an atomic value, no composite and multivalued attributions, and null values are allowed. 
4. Interpretation of  Relation- The relation schema can be interpreted as a declaration or a type of assertion about an entity, while each tuple in the relation can be interpreted as a fact. 
Tags:
Relation vs File Records 
END

$START
Basic
Front:
What is known as self-describing data?
Back:
When an attribute name and value are included together in a tuple. 
Tags:
Definitions
END

$START
Basic
Front:
What are the three meanings a null value can have?
Back:
1. Value unknown
2. Value exits but is not available. 
3. Attribute does not apply to this tuple. 
Tags:
Null
END

$START
Basic
Front:
The relational model represents facts about  \_\_\_\_\_  uniformly as relations.
Back:
Entities and relationships
Tags:
Relational Model
END

$START
Basic
Front:
What are the three main categories that constraints on databases can be divided into? 
Back:
1. Inherent model-based constraints or implicit constraints- those that are inherent in the data model.
2. Schema-based constraints or explicit constraints- constraints that can be directly expressed in the schemas of the data model. . 
3. Application-based or Semantic constraints or business rules- those that cannot be directly expressed in the schemas of the data model, and hence must be expressed an enforced by the application programs. 
Tags:
Constraints
END

$START
Basic
Front:
What are the five types of schema-based constraints?
Back:
1. Domain constraints
2. key constraints
3. constraints on nulls
4. Entity integrity constraints
5. Referential integrity constraints
Tags:
Constraints
END

