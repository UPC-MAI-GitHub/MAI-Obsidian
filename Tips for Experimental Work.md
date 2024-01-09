![[Exp_Tips_2023-24.pdf]]

## Notes
* **Experimentation**
	1. Has a *goal(s)* and *conjecture(s)* about the expected results 
	2. Involves *algorithm design* and *implementation* 
	3. Needs *problems/data to run* the algorithm on 
	4. Needs establishing *what is variable* and *what is held fixed* 
	5. Needs running the algorithm(s) on the problem(s) and *collect the results* 
	6. Needs *evaluating* 
* **Possible Goals**
	* Get a *good solution* for a given problem 
	* Show that an *algorithm is applicable* to a problem or class thereof 
	* Show that an *algorithm is better than another one in some respect* 
	* Find *“optimal” setup for parameters* of a given algorithm 
	* Understand algorithm behavior: 
		* how *it scales up* with problem size 
		* how it *performs under extreme conditions*
		* how *performance is influenced by parameters* (criticality)
* **What algorithm is beter?**
	* Depends what are you looking for, time or performance (assuming you have the resources)
		* ![[Pasted image 20231123121244.png]]
	* Very good on very specific situations or fairly good on average?
		* ![[Pasted image 20231123121402.png]]
* **Goog scientific work**
	* *Clear* statement of target *problem*, *goals* and *scope*
	* *Large enough tests* (number, difficulty, representativeness) 
	* *Statistical analysis* of results 
	* *Reproducibility* 
	* *Insightful discussion of the results* 
	* Conclusions: what have we *achieved*, what have we *learned*, *whys* and *why nots*, *strenghts* and *limitations* 
	* *Future work*: open problems, avenues for future investigation
* **Using real vs. synthetic problems/data**
	* *Problems*
		* *Advantages* well-chosen problems (coming from real-world), comparison to previous work 
		* *Disadvantages* not owner, might miss important absent information, problem feasibility?
	* *Data*
		* *Advantages* allow systematic comparison: repetitions, sizes, hardness, ...; can target very specific issues; can be shared 
		* *Disadvantages* not the “real thing”; might be too simplistic/hard; hid- den biases?
* **Tips for Experimental work**
	* *never draw any conclusion from a single run!* 
		* perform *sufficient* number of *independent runs* 
		* use *statistical measures* (means, standard errors) 
		* use *statistical tests to assess reliability of conclusions* (t-test, F-test, Wilcoxon, ...) 
	* *always do a fair competition!* 
		* use *same amount of resources for the competitors* 
		* use *same performance measures*