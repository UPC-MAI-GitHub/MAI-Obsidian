![[Certainty Factors -MESIIA.pdf]]

## Notes

* ![[Certainty Factors 2023-11-29 11.21.19.excalidraw]]
* **Introduction**
	* *Certainty factors*: quasi-probabilistic model founded on the classics probability theory
	* Defined in the *MYCIN* expert system. this was a backward chaining expert system (AI) used to identify bacteria causing severe infections.
* **Motivation**
	* *Bayesian model*:
		* Based on probabilities makes some assumptions (not always appropriate)
		* $p(c|e) = x \Rightarrow p(\neg c|e) = 1-x$
		* $Prob(conclusion + negation(conclusion)) = 1$
* **Certainty Factors**
	* Two measures computation
		* *Measure of Belief*:  $$MB(c,e) = \begin{cases} 1 & \text{if } p(c)=1 \\  \frac{max(p(c|e), p(c))-p(c)}{1-p(c)} & \text{if } p(c) \neq 1\end{cases}$$
		* *Measure of Disbelief*: $$MB(c,e) = \begin{cases} 1 & \text{if } p(c)=0 \\  \frac{p(c) - min(p(c|e), p(c))}{1-p(c)} & \text{if } p(c) \neq 0\end{cases}$$
		* *Properties of MB and MD*
			* Values in [0,1]
			* If $MB(c,e) > 0 \Rightarrow MD(c,e) = 0$. In this case the evidences increase the belief about the conclusion $c$. 
			* If $MD(c,e) > 0 \Rightarrow MB(c,e) = 0$. In this case the evidences decrease the confidence about $c$.
	* *Certainty Factors Model* $$e\xrightarrow[]{MB(c,e),MD(c,e)} e$$ $$CF(c,e) = \frac{MB(c,e)-MD(c,e)}{1-min(MB(c,e), MD(c,e))}$$
	* IF  evidence *e* THEN conclusion *c* {*$CF_{rule}$*}
	* *Properties*
		* $CF$ is in $[-1,1]$
		* if $CF(c,e)>0$$, evidence increases the belief about $c$
		* if $CF(c,e) < 0$, evidence decreases the belief about $c$
	*  The certainty factor assigned by a rule is *propagated through the rule*. This involves establishing the net certainty of the rule consequent when the evidence in the rule antecedent is uncertain:$$CF(c)=CF(e)\times CF(c,e)$$
		* *Example*: IF *sky is clear* THEN the forecast is *sunny* {$CF_{rule} 0.8$}, and the current certainty factor of *sky is clear* is $0.5$ then $CF(c) = 0.5\times 0.8 = 0.4$. Result interpreted as *It may be sunny.*
	* *Combination rules*
		* *Conjunctive rules*
			* If evidence *e1* AND evidence *e2*  THEN conclusion *c* {$CF$}
			*  Certainty of conjunctions is: $$CF(e_1\cap e_2\cap ... \cap e_n) = min(CF(e_1), CF(e_2),...,CF(e_n))$$
			* *Example*
				* IF *sky is clear* AND the forecast is *sunny* THEN action is 'wear sunglasses' {$CF_{rule} 0.8$}, and the current certainty factor of *sky is clear* is $0.9$ and the certainty of the forecast of *sunny* is $0.7$ then $CF(c, e_1\cap e_{2) =} min(0.9,0.7)\times 0.8 = 0.7 \times0.8 = 0.56$. 
		* *Disjunctive rules*
			* If evidence *e1* OR evidence *e2*  THEN conclusion *c* {$CF$}
			*  Certainty of disjunctions is: $$CF(e_1\cup e_2\cup ... \cup e_n) = max(CF(e_1), CF(e_2),...,CF(e_n))$$
			* *Example*
				* IF *sky is overcast* OR the forecast is *rain* THEN action is 'take an umbrella' {$CF_{rule} 0.9$}, and the current certainty factor of *sky is overcast* is $0.8$ and the certainty of the forecast of *rain* is $0.5$ then $CF(c, e_1\cup e_{2) =} max(0.8,0.5)\times 0.9 = 0.8 \times0.9 = 0.72$.
		* When the same consequent is obtained as a result of the execution of two or more rules, the *individual certainty factors of these rules must be merged* to give a *combined certainty factor* for a hypothesis. We must take into account the sign of the two CF that are being combined. The combination rule is *commutative* and *associative*. *Applied just in pairs*. $$combinedCF(CF_1(c), CF_2(c))=\begin{cases}CF_1+CF_2(1-CF_1) & CF_1>0\;and\;CF_2>0\\ CF_1+CF_2(1+CF_1) & CF_1<0\;and\;CF_2<0\\ \frac{CF_1+CF_2}{1-min(|CF_1|,|CF_2|)} & otherwise \end{cases}$$
		* ![[Certainty Factors 2023-11-29 12.32.24.excalidraw]]
* **Bayesian vs Certainty factors**
	* The *certainty factors* theory provides a practical *alternative to classic Bayes theorem* in probability. 
	* The *heuristic manner of combining certainty factors* is different from the manner in which they would be combined if they were probabilities. 
	* The certainty theory is not “mathematically pure” but does *mimic the thinking process of a human expert*
* **Probabilistic Reasoning vs Certainty Factors**
	* The *probabilistic method* is likely to be the most appropriate *if reliable statistical data exists*.
	* In the *absence of any of the specified conditions*, the *probabilistic* approach might be too arbitrary and even *biased* to produce meaningful results. 
	* Although the *certainty factors* approach lacks the mathematical correctness of the probability theory, it *outperforms probabilistic reasoning* 
* ![[exercisesCF.pdf]]
* *Resolutions*
	* *Judge*
		* ![[Certainty Factors 2023-11-29 14.19.38.excalidraw]]