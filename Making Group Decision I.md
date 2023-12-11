![[MAS_Lec7-Making-Group-Decision.pdf]]
## Notes
* **Notes on environment formal definition**
	* ![[Making Group Decision I 2023-11-29 14.45.11.excalidraw]]
	* A *MAS* contains a number of agents that:
		* Communicate
		* Act in the environment
		* Have "spheres of influence"
		* Linked by relationships
* **Types of agreement**
	* *Multi-agent encounters* (game-like character)
		* Agents simultaneously choose an action to perform, an outcome $\Omega$ will result
		* The actual outcome depends on the combination of actions
		* assume each agent has just two possible actions $Ac=\{C,D\}$ where $C=cooperate$ and $D=defect$, the environement behavior given by state transformer fucntion $\tau$: $$\tau:  A_i \times A_{j=}\Omega$$
		* *Example*
			* ![[Pasted image 20231129150659.png]]
		* *Rational action*: considering the preferences of the agent, a rational action is what the agent is more devoted for (after computing its preferences)
		* *Payoff matrices*: mtrices two compute the convinience of a set of actions taken by the different agents
			* ![[Pasted image 20231129151117.png]]
		* *Solution concepts*
			* How to act?
				* *Dominant strategy*
					* Rational agent *never* play a dominant strategy
				* *Nash equilibrium strategy*
					* Two strategies *s1* and *s2* are in Nash equilibrium if:
						* under the assumption that agent *i* plays *s1*, agent *j* can do no better than play *s2*
						* under the assumption that agent *j* plays s2, agent *i* can do no better than play *s1*
					* Neither agent has any incentive to deviate from Nash equilibrium
					* In a game like this you can find the NE by cycling through the outcomes, asking if either agent can improve its payoff by switching its strategy.
						* ![[Pasted image 20231129152120.png]]
					* There are scenarios with either *more than one NE* or *any NE*
					* *Mixed Strategy for NE*: probability statimation of the outcome
						* ![[Pasted image 20231129152538.png]]
						* 
				* *Pareto optimal strategies*
				* *Strategies that maximize social welfare*
					*  A mixed strategy has the form 
						* Play $α1$ with probability $p1$ 
						* play $α2$ with probability $p2$ 
						* play $αk$ with probability pk. 
						* Such that $p1+p2+··· +pk =1$
				* *Pareto Optimality*:
					* There is no other outcome that makes one agent better off without making another agent worse off.
					* If an outcome is Pareto optimal, then at least one agent will be reluctant to move away from it (because this agent will be worse off).
	* *Voting*
	* *Coalition forming*
	* *Allocating resources (auctions)*
* **Utilities and preferences**
	* *Capture preferences* by *utility functions*
	* *Utility functions lead to preferences orderings over outcomes*
		* ![[Pasted image 20231129150114.png]]
	* 