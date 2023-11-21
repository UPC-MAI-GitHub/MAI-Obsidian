![[09-syntactic-parsers.pdf]]

## Notes
* **Syntactic parsers**
	* *Backgroud*
		* *Performance* depends on:
			* Grammar expressivity -> combination of symbols
			* Coverage -> words
			* Parsing Strategy -> bottom up, top-down
			* Rule application order -> largest rule, most likely rule
			* Ambiguity management -> probabilities, semantic, pragmatics
		* *The problem of repeating derivations*
			* Top-bottom and bottom-down leads to repeated derivations when backtracking
	* *Chart-based methods*
		* Avoid redoing derivations  and build the chart by using dynamic programming
		* Derivations are represented as a names directed graph
		* *Chart*
			* *Nodes*: positions between words of the input sentence
			* *Edges*: dotted rules subsumming sequence of words of the input sentence
		* The chart can be represented as a dynamic table.
		* *CKY - most popular hcat-based method*
			* Dynamic programming, chomsky normal form, passive bottom-up, probabilistic
		* *Chomsky Normal Form (CNF)*
			* Any Context Free Grammar (CFG) can be converted into CNF
			* A CFG $G=(N,\Sigma, R, S)$ expressed in CNF is as follows
				* $N$: set of non-terminal symbols
				* $\Sigma$: set of terminal symbols
				* $R$ set of rules which take two forms
					* $X \rightarrow Y_1Y_{2}$ $for $X, Y_1, Y_2 \in N$
					* $X\rightarrow \alpha$ for $X \in N$ and $\alpha \in \Sigma$
					* $S \in N$ is a start symbol
			* *CNF conversion*:
				* Convert *hybrid rules*: replace terminal with the new non-terminals
					* $INF\_VP \rightarrow to\; VP \Longrightarrow$
					* $INF\_VP \rightarrow TO VP$
					* $TO \rightarrow to$
				* Convert *non-binary* rules:
					* $S\rightarrow CP\; NO\;PP \Longrightarrow$
					* $S\rightarrow VP\;X$
					* $X\rightarrow NP\;PP$
				* Convert *unit productions*: $A\rightarrow^{*}B$ and $B\rightarrow\alpha\Longrightarrow A\rightarrow\alpha$
					* $NP\rightarrow$ and $N\rightarrow dog \Longrightarrow NP\rightarrow dog$
			* *Exercise 1* $\longrightarrow$ [[Exercises about Syntactic Parsers]]
			* *CKY algorithms*
				* Chart content: Maximum probability of a subtree with root $X$ spanning words $i . . . j$: $$\pi(i, j, X)$$
				* Backpath to recover which rules produced the maximum probability tree: $$\psi(i, j, X)$$ 
				* The goal is to compute: 
					* $max_{t\in \tau(s)}p(t) = \pi(1, n, S)$ 
					* $\psi(1, n, S)$ 
					* It is possible to use it without probabilities to get all parse trees (with higher complexity
					* ![[Pasted image 20231116152742.png]]
				* 
