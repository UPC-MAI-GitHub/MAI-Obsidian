![[IntroLinguisticVariables- MESIIA.pdf]]

## Notes
![[Fuzzy Logic 2023-11-15 12.20.06.excalidraw]]
* Having the 2 bottles of water above the one with probability label has a high probability that it is good water, but 0.2 that it will really affect you. But the one with the possibility label is about high possibility of good water, but 0.2 of not that good water but it will not affect you
* To introduce *flexibility to the probability theory* we have to ways
	* Certainty Factors
	* Possibilistic approach
* **Fuzzy Logic**
	* A model of approximate reasoning
	* Invented in 1965 by Prof. Lotfi Zadeh
	* Classical way *boolean or crisp sets*: any object belongs to the set (1) or not (0). The membership to a set is strict, without doubt.
	* *Fuzzy sets*:  any object belongs to a set up to a certain degree, between 0 and 1. The membership function takes values in the real domain. $\mu_{c}:X\rightarrow[0,1]$ 
	* *Sets* and *Logic* dual concepts
	* *Membership functions*: define the degree of fulfillment of a predicate in a fuzzy set
		* ![[Pasted image 20231115123321.png]]
		* Membership functions ca take *different forms*, but it must be *convex*
			* *More used ones*
				* Triangular
				* Trapezoidal
			* *Others*
				* sigmoidal ones
		* We can define a *triangular* or a *trapezoidal* function with tuples 
			* Trapezoidal $(a,b,c,d)$
				* $a$ is the value where the membership starts to increase from 0 
				* $b$ is the value where the membership arrives to 1 
				* $c$ is the value where the membership starts to decrease from 1 
				* $d$ is the value where the membership arrives to 0 again
	* *Operators* - Mamdani method
		* Negation (complement) --> N(x) = 1-x
			* Boundaries: $N(0)=1$ , $N(1) = 0$
			* Monotonicity: if $x<y$ then $N(x)>N(y)$
			* Involution: $N(N(x))=x$
		* Conjunction (intersection): $P(c)$ *and* $Q(x)$
			* T-norms: $T(x,y) = min(x,y)$
		* Disjunction $P(x)$ *or* Q(x)
			* T-conorms: $S(x,y) = max(x,y)$
	* *Linguistic Variables*
		* There is a *fixed set of linguistic values* for the variable. {short, medium, tall} 
		* Each term has an *implicit semantics that must be made explicit* 
		* In fuzzy systems, *each term has an associated fuzzy membership function* on a reference domain (ºC) 
		* Some *conditions can be added to the membership functions* of the terms (e.g. add up 1 in each point)
		* It is recommended that the *membership values of each point in the reference domain add up to 1*. Then it satisfies the property of Fuzzy Partition. 
		* With this restriction, *two consecutive terms must have the intersecion at the level 0.5* of membership.
	* Type-2 Fuzzy sets: *consider that the definition of the membership function is also fuzzy.*
		* ![[Pasted image 20231115125914.png]]
	* *Excercise*
		* ![[Pasted image 20231115125943.png]]
	| x   | $\mu_{close}(x)$ | $\mu_{near}(x)$ | $\mu_{access}(x)$ | $\mu_{far}(x)$ |
	| --- | ---------------- | --------------- | ----------------- | -------------- |
	| 55  | 0                | 0.25            | 0.75              | 0              |
	| 8    | 1                | 0               | 0                 | 0              |
	| 95  | 0                | 0               | 0.84              | 0.16           |
	| 105 | 0                | 0               | 0.5               | 0.5               |



