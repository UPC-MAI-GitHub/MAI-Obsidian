![[1- lecture 1.pdf]]

## Notes

- Planning involves thinking
- Acting 
	- Without planning
		- immediate actions
		- well-trained behaviors
		- actions of freely adaption
	- After planning
		- new situations
		- complex situations
		- environment imposes high risk/cost (CEO of a company)
		- collaborating with others
	- *People plan only when strictly necessary*
- **Planning** -> *set of steps to follow* (Deliberation process to generate the steps)
	- ![[Introduction and Planning Definition 2023-09-27 11.38.21.excalidraw]]
	- **Attributes**
		- Clear goal
		- Managerial function (direction to move)
		- Pervasive (for all levels of functioning)
		- Continuous process (update the plane continuously)
		- Intellectual process (mechanism to make decisions)
		- Futuristic
		- Decision making
	- **AI Planning** -> computational study of the deliberation process
		- Goals
			- Understanding intelligence (rational behavior)
			- Create autonomous intelligent machines
	- **Domain**
		- **Specific**: specific representations and techniques adapted to the problem (lot of work)
		- **Independent**:use generic representations and techniques (not much effort, not very efficient)
		- *Independent complements the specific*
	- **True or false**
		- True
		- False
		- True
		- True
		- False
- **Conceptual model**
	- Definition -> *representation of a system* to *know, understand or simulate* an instances of the model
		- Theoretical method for describing the elements of a problem
		- ![[Pasted image 20230927120448.png]]
	- ![[Pasted image 20230927120516.png]]
- **State Transition System
	- ![[Introduction and Planning Definition 2023-09-27 12.07.03.excalidraw]]
	- S: set of states
	- A: set of actions
	- $\gamma$: transition function
	- *Ontology (logical)* to define a environment a set of actions that can be performed
		- Anything note stated is assumed to be false
	- **Defining actions**
		- Name (can have arguments)
		- Pre-condition list (all conditions need to be true to apply the action)
		- Delete list (facts that become false after applying the action)
		- Add list (facts that became true after applying the action)
	- *Actions update the states*
	- State-Transitions systems can be *represented by a labelled graph*
		- **Nodes**->*states*
		- **Arcs**->*actions*
		- ![[Pasted image 20230927123126.png]]
		- ![[Introduction and Planning Definition 2023-09-27 12.27.24.excalidraw]]
	- **Plan execution**
		- **Planner**: given the *initial state* produces a *plan to achieve the objective*
		- **Controller**: given the *plan* generate an *action*
		- **State-transition system**: evolves as actions are executed and events occur
	- **Dynamic Planning** (updates of the plan based on the observations)
		- Real world differs from the described model
		- Needs:
			- plan supervision
			- plan revision
			- *re-planning*
			- closed loop between planning and controller execution
- **Planning and Search**
	- **Search problem**: Decide actions and states considering granularity/abstraction level
	- Environment assumptions
		- finite
		- discrete
		- fully observable
		- deterministic (always same action same output)
		- static
	- **Search nodes**
		- *Nodes in the search tree*
			- Data structure:
				- State
				- Parent node (predecessor in the search tree)
				- Path cost (total cost of the path leading to this node)
				- Depth depth in the tree
			- *General tree search algorithm*
	```
	function treeSearch(problem, strategy) 
	fringe  { new searchNode(problem.initialState) } loop 
		if empty(fringe) then return failure
		node -<- selectFrom(fringe, strategy) 
		if problem.goalTest(node.state) then return pathTo(node) 
		fringe <- fringe + expand(problem, node)```
```

