![[MAS_Lec2-IntelligentAgents.pdf]]

## Notes
- **What is an agent?**
	- No commonly accepted definition
	- *Agent* must be *autonomous*
	- Possible definition: An *agent* is a *computer system* that is *situated in* some *environment*, and that is capable of *autonomous actions* in this environment in order *to meet its delegated objectives*.
	- Agent must choose *what* and *when* to perform an action.
- *Autonomy is adjustable* (spectrum from too much or too little autonomy)
- **Examples of Agents**
	- Simple agents
		- Control systems
			- Thermostat
		- Software demons
			- UNIX biff program
- **Agent & Environment**
	- ![[Intelligent Agents - Properties & Abstract Architecture 2023-10-06 23.13.53.excalidraw]]
	- **Properties of Environments**
		- The *environment affects* the *agents*
		- Categories over different dimensions
			- *Fully observable* vs *Partially observable* 
				- *Fully*: agent can obtain *complete, accurate, up-to-date* info about the *environment's state*. 
				- Most *moderately complex environments are partially observable* (e.g. the everyday physical world)
				- The more accessible environment is, the simpler it is to build agents to operate in it.
				- *Ex1: Agents playing a game card*, they can communicate with their team but not with the opponents, an agent can only see its own cards
					- *I think* this is a *partially observable* for agents
				- *Ex2: agents playing tic-tac-toe*, they can see the entire board, and know the rules of the game. 
					- *I think* this is a *fully observable* for the agents
			- *Deterministic* vs *Non-deterministic* 
				- *Deterministic:* any action has a single guaranteed effect -- *same state, same result*
				- *Non-deterministic*: we call them *stochastic* if we quantify the non-determinism using probability theory. This represent a *big problem for agents*.
			- *Static* vs *Dynamic*
				- *Static:* can be measured to remain *unchanged if no actions* are done *by the agents*.
				- *Dynamic*: has other processes operating on it that *changes the state beyond the agent's control*.
			- *Discrete* vs *Continuous*
				- *Discrete:* fixes and finite number of actions and precepts in the environment (e.g. chess game). For simplicity a discrete environment is often assumed.
				- *Continuous:* (e.g. taxi driving)
			- *Episodic* vs *non-episodic*
				- *Episode:* single *experience of the agent with* the *environment*.
				- *Episodic:* *current agent decisions affect only the current episode*, not the future ones. No necessity to consider long-term consequences.
				- *Non-episodic:* *agent decisions affect* the current a possible *future episodes*.
- **Intelligent Agents**
	- It is difficult to define intelligence itself.
	- An *intelligent agent* is expected to show
		- *Reactivity*: agent must maintain an *ongoing interaction* with the environment and respond on time to changes in it. (e.g. stimulus -> response rules)
		- *Proactivity:* taking the initiative to achieve goals, agents are means to do things for us.
		- *Social abilities:* ability to *interact* with other agents and possibly humans via: 
			- *Cooperation:* Achieve a *shared goal working together*. May be because an agent can achieve it alone or because cooperation leads to a *better result*.
			- *Coordination:* *management* of *interdependencies* between activities.
			- *Negotiation:* reach *agreement* in matters of *common interest*.
		- *Mobility:* in the environment
		- *Learning:* *improve* over time.
		- *Rationality:* act to achieve its goals and not to preven them to happen.
		- *Veracity:* not able to communicate false information.
- **Abstract Architectures for Agents**
	- Assume the environment (non-deterministic) may be in any of a finite set $E$ of discrete states: $$E=\{e,e',...\}$$ 
	- Agents are assumed to have a collection of possible actions, which transform the state of the environment: $$Ac = \{\alpha, \alpha',...\}$$
	- A run $𝑟$ of an agent in an environment is a sequence of environment states and actions: $$r:e_0\xrightarrow{\alpha_{0}}e_1\xrightarrow{\alpha_1}e_2\xrightarrow{\alpha_2}e_3\xrightarrow{\alpha_3}\dots\xrightarrow{\alpha_{u−1}}e_u$$ So, $R = \{r,r',\dots\}$  set of all possible finite sequences of actions and states. $R^{Ac} \subseteq R$ subset of actions in a sequence. $R^{E}\subseteq R$ subset of the states in a sequence.
	- *State transformer* function is a behavior of the environment: $$\tau:R^{Ac}\rightarrow 2^E$$
	- *History dependent:* the next state could not only depend on the agent's next action but in its previous actions or the previous states of the environment.

	- So, an *agent* can be sen as a function which maps runs to actions $$Ag:R^E\rightarrow Ac$$ 
	- *System:* pair containing an *agent and an environment* $\langle Ag,Env\rangle$. Any system will have associated a set of runs $R(Ag,Env)$.
	- An *environment* can be defined by $Env=\langle E,e_0,\tau\rangle$ where 
		- $e_0$: initial state
		- $\alpha_{0}= Ag(e_0)$
		- $e_{u}\in\tau((e_0,\alpha_0,\dots,\alpha_{u-1}))$ *and* $\alpha_{u}= AG((e_0,\alpha_0,\dots,e_u))$ 
	-  Behaviorally equivalent agents with respect to 𝐸𝑛𝑣 iff $$R(Ag_{1},env)=R(Ag_{2},env)$$
- **Purely Reactive Agents**
	- Decide what to do without any reference of the history, entirely on the present. *P.R. Agents* formally defined as: $$Ag:E\rightarrow Ac$$
	- a *thermostat* is a purely reactive agent $$Ag(e)=\begin{cases}\text{off} & \text{if } e=\text{temprarure Ok} \\ \text{on} & \text{otherwise} \end{cases}$$
- **Agents with state**
	- State is an internal data structure in this kind of agents
		- ![[Pasted image 20231007131735.png]]
	- *Perception:* agent's ability to observe its environment $$see:E\rightarrow Per$$
	- *Next:* maps a previous internal state with perceptions to an new internal state, indicating *how the agent updates its world perception* $$next:I\times Per\rightarrow I$$
	- *Action:* mapping from internal states to actions $$action:I\rightarrow AC$$
	- *Agent's contro  process:*
		1. Agent starts at some initial internal state $𝑖_0$ 
		2. Observes its environment state 𝑒, and generates a percept $𝑠𝑒𝑒(𝑒)$ 
		3. Internal state of the agent is then updated via $next$ function, becoming $𝑖_1 = 𝑛𝑒𝑥𝑡(𝑖_0,𝑠𝑒𝑒(𝑒))$ 
		4. The action selected by the agent is 𝑎𝑐𝑡𝑖𝑜𝑛 ($𝑖_1$) . This action is then performed. 
		5. Goto (2).
- **Tasks for agents**
	- How to tell agents what to do without telling them how to do it.
	- *Utility functions:*
		- 