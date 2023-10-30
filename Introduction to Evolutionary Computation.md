![[IntroEC.pdf]]

## Notes

* **Natural Selection**
	```Python
	if organism_that_reproduce:
		variability_of_traits = offspring_inherit_traits_from_their_progenitors()
		selective_pressure = limited_resources()
	then: 
		individuals_that_die = less_adapted_traits_individuals
		ind_that_prosper_and_reproduce = more_adapted_traits_inds
		
```
	* *Selective pressure*
		* access to food/water
		* Climate conditions
		* Breeding areas
		* Predators
	* *NS Origins*
		*  1831 - 2nd Galapagos expedition
		* 1839 - Charles Darwin Galapagos publication
		* 1859 - Darwin publishes *On the Origin of the Species*
		* 1865 - *Mendel* experiments on *Plant Hibridization*
* Interaction of different *biological processes* operating over *individuals* and *species* ----> *EVOLUTION*
	* Reproduction
	* Mutation
	* Competition
	* Selection
* **Evolution**
	* *Evolution* is *change* (structural, physiological, behavioral) which occurs over time *through interaction with the environment*. the change in *random* & unpredictable
	* Caused mainly by --> Natural selection, mutation
	* *Mutation* ->Error when DNA is being copied, maybe because a chane in protein.
	* Evolution has *no goal*
	* *After a mutation* changes an individual, the *environment determines if the change gives the individual an advantage*. If the new trait is helpful, the mutated individual is *more likely to survive*, reproduce and pass the new trait to offspring.
	* Other sources of genetic variations:
		* *Genetic drift* happens when random events cause gene frequencies to vary between generations 
		* *Gene flow* (or migration) is the movement of genes in a species from one population to another as the result of inter-breeding.
		* *Symbiosis* is the cooperative (close and often long-term) interaction between different organisms. 
	* Evidence for descent with modifcation
		* *Biogeography*: evolution od the same specie depending in its location
		* *Functional morphology*: Adaptation depending on the use the individual give to its physical characteristics
		* *Paleontology*
		* *Comparative embryology*: early embryos of very different organisms closely resemble each other
		* *Animal and plant breeding*
		* *Molecular biology*: The *biochemistry* of a *bat is much closer to that of a whale*, rather than that of a bird … not expected unless bat and whale have a more recent common ancestor than bat and bird
	* *Modern exaples of natural selection "in action"*
		* *Rabbits & myxomatosis* --> rabbits in australia
* **The evolutionary cycle in Nature**
	* ![[Introduction to Evolutionary Computation 2023-10-26 11.12.59.excalidraw]]
* **Biological terms used in Evolutionary Computation**
	* *Genotype*: The molecular basis of inheritance as defined by genes and chromosomes. 
	* *Phenotype*: The actual appearance of the living beings. 
	* *Species*: A group of organisms capable of inter-breeding and producing fertile offspring. 
	* *Chromosome* (or individual): a candidate solution to the problem to be optimized. 
	* *Gene*: single variable to be optimized. 
	* *Locus* (plural loci): the specific location of a gene or position on a chromosome. 
	* *Allele*: possible assignment of a value to a variable (a locus in a gene). 
	* *Fitness function*: capability of an individual of certain genotype to reproduce.
* **Evolutionary Algorithm**
	* *Computer simulation* in which a *population of abstract representations* of candidate solutions (individuals) to an optimization problem *are stochastically selected, recombined, mutated, and then removed or kept*, based on their *relative fitness* to the problem.
		1. maintain population of individuals 
		2. select individuals according to fitness
		3. breed (“recombine/cross over”) them & mutate the offspring
		4. form a new generation using the offspring and the old one
```Python
t := 0 
Initialize P(t) 
Evaluate P(t) 
WHILE NOT (termination condition) DO 
	t := t+1 
	Select P'(t) from P(t-1) 
	Recombine and/or Mutate P'(t) 
	Evaluate P'(t) 
	Form P(t) by using P'(t) and P(t-1) 
END
```

* **Evolutionary Algorithms
	* ***The main components of an EA**
		* *coding function* to represent potential solutions as valid chromosomes
		* *fitness function* to evaluate the goodness of individuals
		* *initialization method* to create the initial population 
		* *selection operator* to determine which individuals will undergo variation  
		* *replacement strategy* to decide which individuals will be allowed in the next generation 
		* *genetic variation* operators (mutation, recombination) to perform the variation 
		* *termination criterion* to stop the process
	* *Behaviour of components*
		* *Selection, replacement and fitness* **DECREASE** diversity in a population 
		* Genetic operators (*mutation, recombination*) **INCREASE** diversity in a population
		* *exploration* < --- > *exploitation*
	* **Fitness Functions**
		* A function that help us to model the features and patterns our population should follow trough evolution.
		* *Termination criteria*
			* Maximum number of generations 
			* Maximum number of fitness function evaluations 
			* Avg/max (relative) fitness function improvement below some tolerance (over a period of time) 
			* Diversity below some tolerance (idem)
			* Closeness to optimum below some tolerance
	* **The COP (counting ones problem)**
		* A string of $n$ binary variables, $x \in \{0,1\}{^n}$: <-- *search space*
		* $F(x)=\sum\limits_{i=1}^{n}f(x_i)$
		* Goal: maximize the number of ones in the string
		$$F(X) = $$
	* **Replacement Strategies**
		* Suppose we maintain a population $\mu \geq 1$ individuals. At each generation they produce $\lambda \geq 1$ offspring. Two strategies:
			* $(\mu + \lambda)$ - Strategy            *"steady-state"* <--- combine $\mu$(population) with $\lambda$(offspring) to generate a new population  
			* $(\mu, \lambda)$ -strategy, $\lambda \geq \mu$     *"generational"* <--- in this case instead of combine, $\lambda$ replace $\mu$
	* **Taxonomy of methods**
		* ![[Introduction to Evolutionary Computation 2023-10-26 12.26.16.excalidraw]]
* **Various techniques**
	* *Genetic Algorithms (GA)* model standard genetic evolution 
	* *Genetic Programming (GP)*, based on genetic algorithms, but individuals are computer programs 
	* *Evolutionary Programming (EP)*, derived from the simulation of adaptive behavior in evolution (i.e. phenotypic evolution). 
	* *Evolution Strategies (ES)*, geared toward modeling the strategic parameters that control evolution itself (“evolution of evolution”) 
	* *Learning Classifier Systems (LCS)* aim at knowledge representation 
	* *Differential Evolution (DE)*, similar to genetic algorithms, differing only in the reproduction mechanism used 
	* *Neuro Evolution (NE)*, specifically aiming at evolving neural networks
	* *Differences between them*
		* Genetic Algorithms (*bitstrings*)
		* Evolutionary Programming (*finite-state automata*)
		* Evolution Strategies (*real-valued vectors*) 
		* Genetic Programming (*computer programs*) 
		* Neuro Evolution (*neural networks*) 
		* Learning Classifier Systems (*if-then rules*)
* **EA vs derivative based methods**
	* EAs can be *much slower* (but they are *any-time* algorithms)
	* EAs are* less dependent on initial conditions* (still we need several runs) 
	* EAs can use a*lternative error functions*: 
		* Not continuous or differentiable 
		* Including structural terms 
	* EAs do *not get easily stuck* in local optima 
	* EAs are *better “scouters”* (global searchers) 
	* EAs are *worse “tuners”* (local searchers)
* **Hybrid algorithms**
	* EA used to find a good set of initial solutions
	* Hopefully a very good solution is on the basin of attraction of one of these points 
	* Iteration leads to “Lamarckian” evolution