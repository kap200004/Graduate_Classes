TARGET DECK: CS 6364

START
Basic
Front:
Informed vs Uninformed Algorithms
Back:
Informed- the agent can estimate how far it is from the goal, and uninformed have no such available estimation.
Tags:
Informed and Uninformed Search
<!--ID: 1725321715634-->
END

START
Basic
Front:
What is the four-phase problem-solving process for a problem solving agent?
Back:
1. Goal Formulation
2. Problem formulation- The agent devises a description of the state and actions necessary to reach the goal. 
3. Search- the agent simulates sequences of actions in its model, searching until it finds a sequence of actions that reaches the goal. Known as the solution.
4. Execution- the agent executes the actions in the solution.
Tags:
Problem Solving Process
<!--ID: 1725321715646-->
END

START
Basic
Front:
In a fully observable, deterministic and known environment, the solution to any problem is? 
Back:
A fixed sequence of actions. 
Tags:
Search
<!--ID: 1725321715651-->
END

START
Basic
Front:
What 6 things make up the formal definition of a search problem?
Back:
- State Space- a set of states that the environment can be in. 
- Initial State- a state the agent begins in. 
- A set of one of more goal states. 
- Actions available to the agent. 
- A transition model which describes what each action does and returns the state that results from doing action a in state s. 
- A action cost function that gives the numeric cost of applying action a in state s to reach state s'. 
Tags:
Search Problem
<!--ID: 1725321715657-->
END

START
Basic
Front:
In a search tree, the nodes and edges correspond to what? 
Back:
The nodes correspond to state and the edges correspond to actions.
Tags:
Search
<!--ID: 1725321715660-->
END

START
Basic
Front:
What is the frontier?
Back:
The set of reached but unexpanded nodes. 
Tags:
Search 
<!--ID: 1725321715664-->
END

START
Basic
Front:
What is a reached node?
Back:
Any state that has had a node generated for it has been reached (whether it has been expanded or not). 
Tags:
Search
<!--ID: 1725321715669-->
END

START
Basic
Front:
What is best-first-search?
Back:
In this search, we decide which node from the frontier to expand next by choosing a node $n$ with minimum value of some evaluation function $f(n)$. 
Tags:
Search
<!--ID: 1725321715673-->
END

START
Basic
Front:
We get different more specific algorithms by changing what in the best-first search function? 
Back:
By employing different $f(n)$ functions, we get different specific algorithms. 
Tags:
Search
<!--ID: 1725321715677-->
END

START
Basic
Front:
What are the four components that represent a node in the search tree?
Back:
1. node.state- the state to which the node corresponds. 
2. node.Parent- the node in the tree that generated this node. 
3. node.Action- the action that was applied to the parent's state to generate this node. 
4. node.Path-Cost: the total cost of the path from the initial state to this node. 
Tags:
Search
<!--ID: 1725489812452-->
END

START
Basic
Front:
What are the four operations on the search frontier?
Back:
1. is-empty(frontier)
2. pop(frontier)- removes the top node from the frontier
3. top(frontier)- returns but does not remove the top node from the frontier
4. add(node, frontier)- inserts a node to its proper place in the queue
Tags:
Search
<!--ID: 1725489812459-->
END

START
Basic
Front:
What are the four ways we can measure a search algorithms performance?
Back:
1. Completeness- Is the algorithms guaranteed to find a solution where there is one, and to correctly report failure when there is not? 
2. Cost optimality: Does it find a solution with the lowest path cost of all solutions?
3. Time complexity
4. Space complexity
Tags:
Search
<!--ID: 1725489812464-->
END

START
Basic
Front:
What are the three terms that can be used to measure the complexity of a search algorithm for a graph that is represented only implicitly?
Back:
1. d- the depth or number of actions in an optimal solution. 
2. m- the maximum number of actions in an optimal solution. 
3. b- the branching factor
Tags:
Search
<!--ID: 1725489812467-->
END

START
Basic
Front:
What is the appropriate strategy when all actions have the same cost?
Back:
Breadth-first search
Tags:
Search
<!--ID: 1725489812471-->
END

START
Basic
Front:
What is the appropriate queue for breadth first search?
Back:
FIFO
Tags:
Search
<!--ID: 1725489812476-->
END

START
Basic
Front:
With breadth-first search, what can we do that is more efficiently with the reached list and why? Goal checking? 
Back:
Rather than the states we can use reached to only store a node rather than the state because once we have reached the node, we can never find a shorter path to it, thus we can also do early goal checking. 
Tags:
Search
<!--ID: 1725489812480-->
END

START
Basic
Front:
Derive the time and space complexity of breadth first search.
Back:
$1+b+b^{2}+b^{3}\dots b^{d}=O(b^{d})$. 
Tags:
Search
<!--ID: 1725489812484-->
END

START
Basic
Front:
When is breadth first search cost optimal?
Back:
When all of the actions have the same cost.
Tags:
Search
<!--ID: 1725489812487-->
END

START
Basic
Front:
Why is breadth-first search complete in infinite state spaces? 
Back:
Because it is a systematic search strategy that will not trail off in one direction. 
Tags:
Search
<!--ID: 1725489812492-->
END

START
Basic
Front:
What is the breadth-first search algorithm?
Back:
```python
BreadthFS(problem):
	node = problem.initial
	if Is_goal(node.state) return node
	frontier = Queue(node)
	reached[node] = True
	while len(frontier) > 0:
		node = frontier.pop()
		for child in node.children():
			state = child.state
			if Is_goal(state):
				return child
			if not reached[child]:
				reached[child] = True
				frontier.add(child)
	return Null
```
Tags:
Search
<!--ID: 1725489812495-->
END

START
Basic
Front:
What is the uniform cost search algorithm?
Back:
```python
UCS(problem, eval_function):
	node = problem.initial
	frontier = PriorityQueue(oder=eval_function).add(node)
	reached[node.state] = node
	while len(frontier) > 0:
		node = frontier.pop()
		if Is_goal(node.state): return node
		for child in Expand(problem, node):
			state = child.state
			if state not in reached or child.Path_cost < reached[state].Path_cost:
				reached[state] = node
				frontier.add(node)
	return Null
		
```
Tags:
Search
<!--ID: 1725489812498-->
END

START
Basic
Front:
Why is uniform-cost search complete and cost-optimal? 
Back:
It is cost-optimal because the first solution it finds with have a cost that is at least as low as the cost of any other node in the frontier, it is optimal because it considers all paths systematically in order of increasing cost, never getting caught in a single infinite path. 
Tags:
Search
<!--ID: 1725489812502-->
END

START
Basic
Front:
When is DFS complete and cost-optimal?
Back:
It is never cost-optimal, it is complete for finite state spaces that are trees. 
Tags:
Search
<!--ID: 1725489812506-->
END

START
Basic
Front:
What is the space complexity of DFS?
Back:
$O(bm)$
Tags:
Search
<!--ID: 1725489812510-->
END

START
Basic
Front:
What are two methods that may be used to keep depth-first search from wandering down an infinite path?
Back:
1. Depth-limited search
2. Iterative deepening
Tags:
Search
<!--ID: 1725489812514-->
END

START
Basic
Front:
What is depth-limited search? Is it complete, what is the complexity?
Back:
Depth limited search is DFS where we treat a level $l$ as the maximum depth. If we pick a poor choice for $l$, however, it is not complete, and we will never find the solution. The complexity is $O(b^{l})$ for the time and still $O(bl)$ for the space complexity. 
Tags:
Search
<!--ID: 1725489812517-->
END

START
Basic
Front:
Sometimes we can choose a good length $l$ for depth-limited search if we know what?
Back:
If we know the diameter of the state-space graph, which is the most actions needed to reach any state.
Tags:
Search
<!--ID: 1725489812521-->
END

START
Basic
Front:
How does iterative deepening search solve the problem of picking a good $l$? What is its complexity and completeness? Optimality?
Back:
By trying all values of $l$. It has a space complexity of $O(bd)$ and a time complexity of $O(b^{d})$. It is complete. It is optimal on state-spaces with actions that all cost the same.
Tags:
Search
<!--ID: 1725489812525-->
END

START
Basic
Front:
What is a heuristic function in search? 
Back:
$h(n) =$ estimated cost of the cheapest path from the state at $n$ to the goal state.
Tags:
Heuristic Search
<!--ID: 1725489812528-->
END

START
Basic
Front:
What is greedy best-first search?
Back:
Greedy best first search expands the node with the lowest $h(n)$ value, thus it is just best first search where $f(n)=h(n)$. 
Tags:
Heuristic Search
<!--ID: 1725489812533-->
END

START
Basic
Front:
What is the evaluation function of A* search?
Back:
$f(n)=g(n)+h(n)$
Tags:
Heuristic Search
<!--ID: 1725911467597-->
END

START
Basic
Front:
What is the optimality and completeness of $A^{*}$ search?
Back:
It is complete, of course that is when all action costs are greater than 0. It's optimality is dependent on if the heuristic is admissible and consistent. 
Tags:
Heuristic Search
<!--ID: 1725913917931-->
END

START
Basic
Front:
What is an admissible heuristic?
Back:
An admissible heuristic is one that never overestimates the cost to reach a goal. 
Tags:
Heuristic Search
<!--ID: 1725913917945-->
END

START
Basic
Front:
What is a consistent heuristic? 
Back:
A heuristic is consistent if $h(n)\leq c(n, a, n')+h(n')$. 
Tags:
Heuristic Search
<!--ID: 1725913917956-->
END

START
Basic
Front:
What are some properties of A* with consistent heuristic?
Back:
The first time we reach a state it will be on an optimal path, so we never have to re-add a state to the frontier, and we never have to change an entry in reached. 
Tags:
Heuristics
<!--ID: 1725913917965-->
END

START
Basic
Front:
Prove that admissible heuristics are optimal.
Back:
If the algorithm returns a path of cost $C$ greater than $C^{*}$, then there must be some node $n$ which is unexpanded on the path that costs $C^{*}$
$$ \begin{aligned}
f(n) > C^{*} \text{ otherwise n would have been expanded} \\ f(n) = g(n)+h(n) \text{ by definition}\\ f(n) = g^{*}(n)+h(n) \text{ because n is on an optimal path} \\ f(n) \leq g^{*}(n)+h^{*}(n) \text{ if admissible} \\ f(n) \leq C^{*} \text{ a contradiction}
\end{aligned}

$$
Tags:
<!--ID: 1725913917971-->
END



