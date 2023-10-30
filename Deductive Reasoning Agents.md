![[MAS_Lec3-IntelligentAgents.pdf]]

## Notes
### Agent Architectures
* *Pattie Maes (1991):*  an agent can be decomposed into a set of modules that should be made to interact. It must solvehow the sensor data and the internal state determine actions to perform and the next internal state.
* *Leslie Kaebling:* a particular modulas decomposition for particular task.
* **Classes of architectures**
	* *Symbolic reasoning agents* (1956)
		* Agents decide via symbol manipulation nd explicit logical reasoning.
		* Agents are knowledge-based systems (symbolic AI)
		* Agents contain an explicitly represented symbolic model of the world
		* *Issues*
			* Translate the real world into an accurate, adequate symbolic description, in a time for it to be useful.
			* Once we have a symbolic representation how to get agents to reason with this information. (Knowledge representation, automated reasoning, planning)
		* *Special cases*
			* *Deductive reasoning agents*: Agents decide what to do using theorem proving. Use logic to encode a theory stating the best action given any situation.
			* Having:
				* $\rho$ : theory (set of rules)
				* $\Delta$: logical database (describes the current state of the world) 
				* $Ac$: set of actions an agent can perform
			* we can ser $see:E->Per$ the next part happening is $next:\Delta\times Per \rightarrow\Delta$ then perform an action.
	* *Reactive agents* (1985)
	* *Hybrid agents* (1990)
		* Combination between reasoning and reactive architectures.
### Agent-oriented programming
- Introduced by Yoav Shoham in 1990
- A programming paradigm *based on societal view of computation*.
	- Program agents in terms of *intentional notions (beliefs, desire, intention)*
- *Agent0* agent-oriented programming language, it 