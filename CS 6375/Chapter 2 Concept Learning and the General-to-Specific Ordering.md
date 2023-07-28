### Introduction
* Concept learning can be formulated as a problem of searching through a predefined space of potential hypotheses for the hypothesis that best fits the training examples.
* In many cases this search can be efficiently organized by taking advantage of a naturally occuring structure over the hypothesis space- a general-to-specific- ordering of hypothesis.
* Much of learning involves acquiring general concepts from specific training examples.
* Each such concept can be viewed as describing some subset of objects or events defined over a larger set.
* Alternatively, each concept can be though of as a boolean-valued function defined over this larger set.
* Concept learning- inferring a boolean-valued function from training examlesof its input and output.

### A Concept Learning Task
* To begin, we let each hypothesis be a vector of constraints on a number of attributes.
* For each attribute, the hypothesis will either:
	 * indicate by a ? that any value is acceptable for this attribute.
	 * specify a single required value for the attribute, or
	 * indicate by a $∅$ that no value is acceptable.
* If some instance x satisfies all the constraints fo hypothesis h, then h classifies x as a positive exampe (h(x) = 1).
* The most general hypothesis- that every sample is a positive example- is represented by < ?, ?, ?, ? >.
* The most specific possible hypothesis- that no sample is positive- is represented by < $∅, ∅, ∅, ∅$ >.

### Notation
* The set of items over which the concept is defined is called the set of instances, which we denote by X. X is every combination of attributes.
* The concept or function to be learned is called the target concept, which we denoty by c.
* In general, c can beany boolean-valued function defined over the instances X; that is c: X -> {0, 1}.
* The learner is presented a sset of training examples, each consisting of an instance x from X, along with is target concept value c(x).
* We will often write the ordered pair < x, c(x) > to describe the training example consisting of the instance x and its target concept value c(x).
* We use the symbole D to denote the set of available training examples.
* We use the sybol H to denote the set of **all possible hypotheses** that the learner may consider regarding the identity of the target concept.
* H is determined by the human designer's choice of hypothesis representation.
* The goal of the learner is to find a hypothesis h such that h(x) = c(x) for all x in X.

### The Inductive Learning Hypothesis
* Inductive learning algorithms can at best guarantee that the output hypothesis fits the target concept over the training data.
* Lacking any further information, our assumption is that the best hypothesis regarding unseen instances is the hypothesis that best fits the observed training data.
* The inductive learning hypothesis- Any hypothesis found to approximate the target function well over a sufficiently large set of training examples will also approximate the target function well over other unobserved examples.
* 
### Concept Learning as Search
* Given data with n attributes with x possible values for each attribute, the instance space is $x^n$.
* A similar calculation shows that there are $(x+2)^n$ *syntatically* disting hypothesis within H. Notice, however that every hypothesis containing one or mroe $∅$ symbols represents the empty set of instances. Therefore, the number of *semantically* distinct hypothesies is only $(x+1)^n$.

### General-to-Specific Ordering of Hypotheses
* A very useful structure that exists for any concept learning problem is the general-to-specific ordering of hypotheses.
* A hypothesis that imposes fewer constraints on the instances it classifies as positive is said to be more general than a hypothesis that imposes more.
* For any instance x in X and hypothesis h in H, we say that x *satisfies* h if and only if h(x) = 1.
* Given hypoteses $h_j$ and $h_k$, $h_j$ is more general than or equal to $h_k$ if and only if any instance that satisfies $h_k$ also satisfies $h_j$.
* Let $h_j$ and $h_k$ be boolean valued functions defined over X. Then $h_j$ is more genral than or equal to $h_k$ (written $h_j \ge_g h_k$) if and only if:
  * $(∀_x ∈ X)[(h_k(x) = 1)→(h_j(x) = 1)]$
* Instnaces satisfied by two hypothesis may intersect, but unless one set of instances is subsumed by the other set of instances, neither hypothesis is more general than the other.
* Formally, the $\ge_g$ relation defines a partial order over the hypothesis H.
* When we say the structure is a partial (as opposed to toal) order, we mean there may be pairs of hypotheses such that neither is more general than the other.

### Find-S Finding a Maximally Specific Hypothesis
