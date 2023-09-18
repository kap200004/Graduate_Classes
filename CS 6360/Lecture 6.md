# Relational Data Model and Relational Database Constraints
## Relational Model
- Based on relational algebra and relational calculus. 
- A function is a relation, represents data as a table of values. The table name is the function name. Each row is called a Tuple. 
- A tuple represents a collection of related data values, typically corresponds to a real-world entity or relationship. 
- The domain is a set of valid atomic values for each attribute, each of the values in a  domain must be atomic, or, indivisible. 
- We specify the domain by the data type and range of values. 
## Relation Schema
- A relation schema $R$ is denoted by $R(A_{1}, \dots, A_{n})$. Made up of a relation name $R$ and a list of attributes $A$. 
- Arity, or degree is the number of attributes in a relation. 
- A relation is a set of $n$-tuples, $r=\{t_{1}, \dots, t_{m}\}$. Each $n$-tuple $t$ is an ordered list of $n$ values $t=\{v_{1}, \dots, v_{n}\}$. 
- A set means specifically that there is no important order to the relations in our relation schema. 
- The $NUL L$ value belongs to every domain. we can think of it as $\phi$, unless a constraint is defined that a value can not be null. 
- 