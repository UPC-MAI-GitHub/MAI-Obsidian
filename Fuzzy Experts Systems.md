![[FuzzyES- MESIIA - MatLab.pdf]]

## Notes

* **Logic*
	* *Modus ponens*
		* *Expert systems* : $\longrightarrow$ Rule-based systems
		* *Rules based systems:* Conditions $\longrightarrow$ Inference engine $\longrightarrow$ Conclusion
		* if (p and q) or (not s) then c
	* *Fuzzy experts systems approach*
		* Rule-based system $$p_1 \wedge p_2 \wedge … \wedge p_n \rightarrow q$$
		* Fuzzy sets to define *linguistic variables* 
		* Each premisse is *satisfied at a certain degree* 
		* The *conclusion is derived according to the degree of satisfaction* of the premises 
		* *Many rules can be activated simultaneously, their conclusions are aggregated* 
		* The *conclusion* is a fuzzy set that can be *defuzzified into a numerical value*
	* *Architecture* in a control system
		* ![[Pasted image 20231122115113.png]]
		* *Process:* $$Measurments \rightarrow Fuzzification \rightarrow Inference \rightarrow defuzzification$$
	* *Fuzzy rules*: 
		* Use linguistic variables to determine the *rules* using *if*, *and*, *or* statements
		* For *each possible combination* of values in the conditions, *a rule* can be written. This can be represented in a matrix.
	* *Fuzzification*
		* Goal is to *convert a numerica*l values *into* one or two *linguistic* variables
		* We *find the membership degree* to all the possible linguistic values
		* ![[Fuzzy Experts Systems 2023-11-22 11.58.01.excalidraw]]
	* *Inference*
		* A los of methods to do this process like Mamdami and Sugeno, the most used is Mamdami
		* *Mamdami Process*
			* Evaluate the antecedent for each rule 
			* Obtain each rule’s conclusion 
			* Aggregate conclusions
			* *Example*
				* If $x$ is $A$ and $y$ is $high$ AND $z$ is $short$ $\rightarrow$ $p$ is $good$
				* ![[Fuzzy Experts Systems 2023-11-22 12.18.51.excalidraw]]
			* *Evaluation of the antecedent*
				* The degree of fulfillment of the conditions is calculated. 
				* The membership degree of each of the input values is calculated for each linguistic variable. 
				* The membership values are aggregated.
				* *Aggregation operators*
					* Rules are usually conjuntive
					* *Aggregation*: T-norm $\rightarrow$ *min*/*prod*
					* *Disjunctive*: T-conorm $\rightarrow$ *max*/*bounded sum (probabilistic or)*
			* *Activation of the conclusion*
				*  If the satisfaction degree is c, *the conclusion of the rule is truncated at the level c*. 
				* If *many rules are activated, each one is truncated at the corresponding level.* Then the *results are joined* together.
					* *Union operators* 
						* T-conorms: *max* or *bounded sum*
	* *Defuzzification*
		* The goal is to *reduce a fuzzy set into a single value* in the reference domain. 
		* There are many defuzzification methods.
		* They basically *consider the value of the domain with the highest membership value*. 
		* Sometimes it is also interesting to consider the membership values of the rest of points.
		* *Methods*
			*  *Centre of Area*: *average of all the values in the referece domain*, which are weighted by the corresponding membership degree.
			* *Median of Maximum (MoM)*: *median of the values that correspond to the linguistic term with maximum degree of memberhip*. 
			* Others: 
				* *Largest of Maximum* (Lom): maximum x of the values that correspond to the term with maximum degree of membership 
				* *Smallest of Maximums* (Som): minimum x of the values that correspond to the term with maximum degree of membership
			* ![[Pasted image 20231122130321.png]]
		* *Degree of support of the rules*
			* Degree of support (DoS) of a rule: indicates *the level of importance of the rule*. (**weight of the rule**) 
			* By default the degree is maximum (=1).
			* Other degrees can be used (from 0 to 1). 
			* *The degree of support must be multiplied by the degree of satisfaction of the antecedents in order to calculate the final degree of satisfaction of the rule*(truncating level).
	* *Drawbacks of expert systems*: 
		* *Variable selection is not trivial *
		* A large number of rules must be defined 
		* Changes in the domain must invalidate some rules 
		* The systems are not easily adaptable  Experts spend many time in defining the system
	* *Hierarchical fuzzy systems*
		* The conclusions of one level are used in the following one 
		* In this case, the total number of rules decreases, and also the difficulty of defining the rule blocks. 
		* ![[Pasted image 20231122130843.png]]
	* Difficulties in Hierarchical fuzzy systems: 
		* Define the hierarchy of rules 
		*  Defuzzify or not the conclusion before being used in the following rule block
