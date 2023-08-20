### Introduction
- Concept learning can be formulated as a problem of searching through a predefined space of potential hypotheses for the hypothesis that best fits the training examples.
- In many cases this search can be efficiently organized by taking advantage of a naturally occurring structure over the hypothesis space- a general-to-specific- ordering of hypothesis.
- Much of learning involves acquiring general concepts from specific training examples.
- Each such concept can be viewed as describing some subset of objects or events defined over a larger set.
- Alternatively, each concept can be though of as a Boolean-valued function defined over this larger set.
- Concept learning- inferring a Boolean-valued function from training examples of its input and output.

### A Concept Learning Task
- To begin, we let each hypothesis be a vector of constraints on a number of attributes.
- For each attribute, the hypothesis will either:
	 - indicate by a ? that any value is acceptable for this attribute.
	 - specify a single required value for the attribute, or
	 - indicate by a $∅$ that no value is acceptable.
- If some instance x satisfies all the constraints of hypothesis h, then h classifies x as a positive example (h(x) = 1).
- The most general hypothesis- that every sample is a positive example- is represented by < ?, ?, ?, ? >.
- The most specific possible hypothesis- that no sample is positive- is represented by < $∅, ∅, ∅, ∅$ >.

### Notation
- The set of items over which the concept is defined is called the set of instances, which we denote by X. X is every combination of attributes.
- The concept or function to be learned is called the target concept, which we denote by c.
- In general, c can beany Boolean-valued function defined over the instances X; that is c: X -> {0, 1}.
- The learner is presented a set of training examples, each consisting of an instance x from X, along with is target concept value c(x).
- We will often write the ordered pair < x, c(x) > to describe the training example consisting of the instance x and its target concept value c(x).
- We use the symbol D to denote the set of available training examples.
- We use the symbol H to denote the set of --all possible hypotheses-- that the learner may consider regarding the identity of the target concept.
- H is determined by the human designer's choice of hypothesis representation.
- The goal of the learner is to find a hypothesis h such that h(x) = c(x) for all x in X.

### The Inductive Learning Hypothesis
- Inductive learning algorithms can at best guarantee that the output hypothesis fits the target concept over the training data.
- Lacking any further information, our assumption is that the best hypothesis regarding unseen instances is the hypothesis that best fits the observed training data.
- The inductive learning hypothesis- Any hypothesis found to approximate the target function well over a sufficiently large set of training examples will also approximate the target function well over other unobserved examples.
### Concept Learning as Search
- Given data with n attributes with x possible values for each attribute, the instance space is $x^n$.
- A similar calculation shows that there are $(x+2)^n$ -syntactically- distinct hypothesis within H. Notice, however that every hypothesis containing one or more $∅$ symbols represents the empty set of instances. Therefore, the number of -semantically- distinct hypothesis is only $(x+1)^n$.

### General-to-Specific Ordering of Hypotheses
- A very useful structure that exists for any concept learning problem is the general-to-specific ordering of hypotheses.
- A hypothesis that imposes fewer constraints on the instances it classifies as positive is said to be more general than a hypothesis that imposes more.
- For any instance x in X and hypothesis h in H, we say that x -satisfies- h if and only if h(x) = 1.
- Given hypotheses $h_j$ and $h_k$, $h_j$ is more general than or equal to $h_k$ if and only if any instance that satisfies $h_k$ also satisfies $h_j$.
- Let $h_j$ and $h_k$ be Boolean valued functions defined over X. Then $h_j$ is more general than or equal to $h_k$ (written $h_j \ge_g h_k$) if and only if:
  - $(∀_x ∈ X)[(h_k(x) = 1)→(h_j(x) = 1)]$
- Instances satisfied by two hypothesis may intersect, but unless one set of instances is subsumed by the other set of instances, neither hypothesis is more general than the other.
- Formally, the $\ge_g$ relation defines a partial order over the hypothesis H.
- When we say the structure is a partial (as opposed to total) order, we mean there may be pairs of hypotheses such that neither is more general than the other.

### Find-S Finding a Maximally Specific Hypothesis
--The Algorithm--
```python
def find_s():
	1. Initialize h to the most specific hypothesis in H
	2. For each positive training instance x
		1. For each attribute constraint a in h
			1. If the constarint a is satisfied by x
				1. do nothing
			2. Else
				1. replace ai in h by the next more general constraint that is satisfied by x. 
	3. return h
```
- To use the general-to-specific ordering, we can begin with the most specific possible hypothesis in H, then generalize this hypothesis each time it fails to cover an observed positive training example. 
- We say that a hypothesis "covers" a positive example if it correctly classifies the examples as positive. 
- The first step of Find-S is to initialize h to the most specific hypothesis in H. 
- In particular, none of the $\emptyset$ constraints in h will be satisfied by the first positive example, so each is replaced by the next more general constraint that fits the example; namely, they attribute values for the training example. 
- Next, the second training example that is positive forces the algorithm to further generalize h, this time substituting a ? in place of any attribute value in h that is not satisfied by the new example.
- The Find-S algorithm simply ignores every negative example. 
- In the general case, as long as we assume that the hypothesis space H contains a hypothesis that describes the true target concept c and that the training data contains no errors, then the current hypothesis h can never require a revision in response to a negative example. 
- Recall that the current hypothesis h is the most specific hypothesis in H consistent with the observed positive examples. Because the target concept c is also assumed to be in H and to be consistent with the positive training examples, c must be more general than or equal to h. 
- By definition of more general than, the target concept c will never cover a negative example, thus neither will h. 
- Find-S is guaranteed to output the most specific hypothesis within H that is consistent with the positive training examples. 
- However, Find-s has no way to determine whether it has found the only hypothesis in H consistent with the data.

### Version Spaces and the Candidate-Elimination Algorithm
The Key idea in the Candidate-Elimination algorithm is to output a description of the set of all hypotheses consistent with the training examples. 

#### Representation
- Definition: A hypothesis h is consistent with a set of training examples D if and only if h(x) = c(x) for each example < x, c(x) > in D. 
	- $Consistent(h, D) \equiv (\forall<x,c(x)> \in D) ~h(x) = c(x)$
- Notice the key difference between this definition of consistent and the earlier definition of satisfies. 
- The Candidate-Elimination algorithm represents the set of all hypotheses consistent with the observed training examples. 
- This sub set of hypotheses is called the version space with respect to the hypothesis space H and the training examples D, because it contains all plausible versions of the target concept. 
- Definition: The version space, denoted $VS_{h, D}$ with respect to hypothesis space H and training examples D, is the subset of hypotheses from H consistent with the training examples in D. 

#### The List-Then-Eliminate Algorithm
- The list then eliminate algorithm first initializes the version space to contain all hypothesis in H, then eliminates any hypothesis found inconsistent with any training example. 
- The version space of candidate hypotheses thus shrinks as more examples are observed, until ideally just one hypothesis remains that is consistent with all the observed examples. 

#### A more Compact Representation for Version Spaces
- The candidate-elimination algorithm works on the same principle as the list then eliminate algorithm. However, it employs a much more compact representation of the version space. 
- In particular, the version space is represented by its most general and least general members. 
- The List then eliminate Algorithm:
```python
def ListThenEliminate():
	VersionSpace = initialize_version_space_to_H()
	for each example in D:
		remove from VersionSpace any hypothesis for which h(x) != c(x)
	return VersionSpace

```
- The Candidate-Elimination algorithm represents the version space by storing only its most general members and its most specific. 
- Given only these two sets S and G, it is possible to enumerate all members of the version space ass needed by generating the hypotheses that lie between these two sets in the general-to-specific partial ordering over hypotheses. 
- Definition: The general boundary G, with respect to hypothesis space H and training data D, is the set of maximally general members of H consistent with D. 
- Definition: The specific boundary S, with respect to hypothesis space H and training data D, is the set of minimally general members of H consistent with D. 
- Version Space Representation Theorem: Let X be an arbitrary set of instances and let H be a set of Boolean-valued hypotheses defined over X. Let $c : X -> \{0, 1\}$  be an arbitrary target concept defined over X, and let D be an arbitrary set of training examples. For all X, H, c, and D such that S and G are we defined: $VS_{H,D} = \{h \in H|(\exists_{s} \in S)(\exists_{g} \in G)(g \ge_{g} h \ge_{g} s)\}$
- By the definition of S, s must be satisfied by all positive examples in D. Because h is more general than s, h must also be satisfied by all positive examples in D. 
- Similarly, by definition of G, g cannot be satisfied by any negative examples in D, and because g is more general than h, h cannot be satisfied by any negative examples in D. 

#### The Algorithm
```python
Initialize G to the set of maximally general hypotheses in H
Initialize S to the set of maximally specific hypotheses in H
for each example d in D:
	if d is a positive example: 
		remove from g any hypothesis inconsistent with d
		for each hypothesis s in S:
			if s is inconsistent with d:
				remove s from S
				Add to S all minimal generalizations h of s such that h is consitent with d and some member G is more general than h. 
				remove from s any hypothesis that is more general than another hypothesis in S
	else:
		Remove from S any hypothesis inconsistent with d
		for each g in G:
			if not consistent(g, D):
				remove g from G
				Add to G all minimal specializations h of g such that h is consistent with d and some member of S is more specific than h. 
				remove from G any hypothesis that is less general than anothe r hypothesis in G
```
- Positive training examples may force the S boundary of the version space to become increasing general. 
- Negative training examples play the complimentary role of forcing the G boundary to become increasingly specific. 
- As further training data is encountered, the S and G boundaries will move monotonically closer to each other, delimiting a smaller and smaller version space of candidate hypotheses. 

### Remarks on Version Spaces and Candidate Elimination
#### Will the Candidate-Elimination Algorithm Converge to the Correct Hypothesis?
- The version space learned by the Candidate-Elimination algorithm will converge toward the hypothesis that correctly describes the target concept, provided 1) there are no errors in the training examples, and 2) there is some hypothesis in H that correctly describes the target concept. 
- The target concept is exactly learned when the s and G boundary sets converge to a single, identical hypothesis. 
- Given Sufficient additional training data, the learner will eventually detect an inconsistency by noticing that the S and G boundary sets eventually converge to an empty version space. 
- Such an empty version space indicates that there is no hypothesis in H consistent with all observed training examples. 

#### What Training Example Should the Learner Request Next? 
- Clearly, the learner should attempt to discriminate among the alternative competing hypothesis in its current version space, and therefore choose an instance that would be classified positive by some of these hypotheses but negative by others. 
- By doing so the learning can begin the shrink the version space by making G more specialized, and S more generalized depending on the classification of the example. 
- In general, the optimal query strategy for a concept learner is to generate instances that satisfy exactly half the hypotheses in the current version space. 
- When this is possible, the size of the version space is reduced by half with each new example. 

#### How can Partially Learned Concepts Be Used? 
- We can classify a new example using a partially learned target concept by noting, that if an example satisfies every hypothesis in the version space, we can confidently label it a positive example. 
- Notice that this condition will be met if and only if the instance satisfies every member of S, because every other hypothesis in the version space is at least as general as some member of S. 
- An efficient test for if every hypothesis in the version space classifies an example by negative is to test if every hypothesis in G classifies it as negative. 
- Those instances whose classification is most ambiguous are precisely the instances whose true classification would provide the most new information for refining the version space. 
- If we assume that all hypotheses in H are equally probable a priori, then the proportion of hypothesis that classify an example as positive can be interpreted as the probability that this instance is positive given the training data. 

### Inductive Bias
#### A Biased Hypothesis Space
- Suppose we wish to assure that the hypothesis space contains the unknown target concept. The obvious solution is to enrich the hypothesis space to include every possible hypothesis. 
- Sometimes there are not hypothesis consistent with our training data, the reason being that we have biased the learner to consider only one certain kind of hypothesis type. Sometimes we require a more expressive hypothesis. 

#### An Unbiased Learner
- The obvious solution to building an unbiased learner, is to provide a hypothesis space capable of representing every teachable concept, that is, it is capable of representing every possible subset of the instances X. 
- The set of all subsets of X is called the power set of X. 
- Let X be the size of the instance space (possible instances), the power set of x contains $2^x$ possible hypotheses. 
- Let us define a new hypothesis space H' that can represent every subset of instances. 
- One way to define such an H' is to allow arbitrary disjunctions, conjunctions, and negations of our earlier hypotheses. By doing so we can use the candidate elimination algorithm without having to worry that our hypothesis is not expressive enough. 
- However we run into a new problem, our concept learning algorithm is not completely unable to generalize beyond the observed examples. 
- The problem here is that with this very expressive hypothesis representation, the S boundary will always be simply the disjunction of the observed positive examples, while the G boundary will always be the negated disjunction of the observed negative examples. 
- In order to converge to a single, final target concept, we will have to present every single instance in X as a training example. 

#### The Futility of Bias-Free Learning
- A fundamental property of inductive inference: a learner that makes no a priori assumptions regarding the identity of the target concept has not rational basis for classifying nay unseen instances. 
- Because inductive learning requires some form of prior assumptions, or inductive bias, we can characterize different learning approaches by the inductive bias they use. 
- We define the inductive bias of L to be the set of assumptions B such that for all new instances $x_{i}$:
	- $(B \cap D_{c} \cap x_{i} )\vdash L(x_{i}, D_{c})$ where the notation $y \vdash z$ indicates that z follows deductively from y (i.e., that z is provable from y). 
- Thus, we define the inductive bias of a learner as the set of additional assumptions B sufficient to justify its inductive inferences ad deductive inferences. 
- The inductive bias of Candidate-Elimination algorithm: the target concept c is contained in the given hypothesis space H. 
	- From this we can deduce that any unseen instance that satisfies all of the hypotheses in S, must satisfy c. 
- Characterizing inductive systems by their inductive bias allows modelling them by their equivalent deductive systems. 
- One advantage of viewing inductive inference systems in terms of their inductive bias is that it provides nonprocedural means of characterizing their policy for generalizing beyond the observed data. 
- A second advantage is that it allows comparison of different learners according to the strength of the inductive bias they employ. 
- A learner that has a stronger inductive bias than another learner will classify more instances than the other. Of course, the correctness of such classifications will depend completely on the correctness of this inductive bias. 
- More strongly biased methods make more inductive leaps, classifying a greater portion of unseen instances. 