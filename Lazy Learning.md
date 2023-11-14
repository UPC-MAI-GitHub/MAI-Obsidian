![[T7_2023_students.pdf]]

## Notes
 * **Eager learning:** the majority of computation occurs at training time 
	 * Must create a global approxiamtion
	 * *Algorithms*:
		 * Radial basis function networks
		 * ANN
		 * ID3
* **Lazy learning**:
	* Any machine learning process that *defers the majority of computation to consultation time*
		* Creates many local approximations
		* Can represent more complex fucntions
	* *Training time:*  Is the time prior to consultation during which the system makes inferences from training data in preparation for consultation time
	* *Inference (consultation) time*: the time between when an object is presented to a system for an inference to be made and the time when the inference is completed
	* Delays *generalization until a query is made to the system*. --> work well in unseen data
	* *Advantages*:
		* Target function *approximated locally*
		* *Solve* multiple problems *simultaneously*
		* Successfully *deals with changes* in the problem domain 
		* Suitable for *complex and incomplete domain* problems
	* *Disadvantages*
		* Requires a large space to store the entire training (mainly data samples)
		* Fast in training but *slow in consult
	* *Algorithms*
		* k-nearest neighbour
		* Case-based reasoning
* **Nearest Neighbour**
	* In a data collection *M*, the nearest neighbor to a data object *q* is the data object $M_i$, which minimizes $dist(q, M_i)$,
		* Distances measure is defined for the objects in question
		* the fact that the object $M_i$ is the nearest neighbor to $q$ does not imply that $q$ is the nearest neighbor to $M_i$
	* *Process*
		* Get some example *set of cases with known outputs*
		* When you see a *new case*, *assign its output to be the same as the most similar* known case
	* *Task*: given  some set of training data, and a query point $x_q$, predict $f(x_i)$
		* Find the nearest member of the dataset to the query
		* Assign the nearest neighbour output to the query
	* *Voronoir diagram*
		* Mathematically *divide a space into a number of regions*
		* Regions are called *Voronoi cells*
		* A Voronoi diagram is the computational geometry concept that represents *partition of the given space onto regions, with bounds determined by distances to a specified family of objects* 
		* The *partitioning of a plane with n points into convex polygons such that each polygon contains exactly one generating point and every point in a given polygon is closer to its generating point than to any other*
		* ![[Pasted image 20231114104145.png]]
* **Instance based learning**
	* Similar to nearest neighbors but:
		* It *normalizes all attributes* in range \[0,1\]
		* *Handles missing attributes*
	* Approximating discrete or real valued target functions
	* Produces local approximations
	* *Key idea*: Store training samples, when a test examples is given find the closest matches
	* *Distance measure*: typically euclidean
	* *Number of neighbors*: one
	* Local approximations
	* IBL algorithms are *incremental* and their goals include: 
		* *Maximizing classification accuracy* on subsequently presented instances
	* Instance-base learning is a carefully focused case-based learning approach that contributes evaluated algorithms for: 
		* selecting good cases for classification
		* reducing storage requirements, 
		* tolerating noise, and
		* learning attribute relevance
	* IBL algorithms assume that *“similar instances have similar classifications"*
		* ![[Pasted image 20231114105057.png]]
	* *IBL Algorithms*
		* *IB1* is identical to the nearest neighbor algorithm, except that
			* it normalizes its attributes’ ranges, 
			* processes instances incrementally, and
			* has a simple policy for tolerating missing values. 
		* *IB2* is identical to IB1, except that 
			* it saves only misclassified instances 
		* *IB3* is an extension of IB2 that employs a “wait and see” evidence gathering method to determine which of the saved instances are expected to perform well during classification
* **K-Nearest Neighbour**
	* typically euclidean distance
	* Number of neighbors to consider: *K*
	* Find the neighbors by: *vote using k-nn* or take average (for regression)
	* *Training method*: saving examples
	* *Prediction time*
		* Find the k training examples that are closest to the test example $x$
		* *Classification*: The output is a class membership. Predict the *most frequent* class among those $y_i$’s
		* *Regression*: The output is a value. Predict the *average* of among the $y_i$’s
	* *Improvements*: 
		* Weighting examples from the neighborhood 
		* Measuring “closeness” 
		* Finding “close” examples in a large training set quickly
	* *Advantages*
		* Training is very fast
		* Can learn complex target functions
		* Don't lose information
	* *Disadvantages*
		* Slow at query time
		* Needs lot of storage
		* Easily fooled by irrelevant attributes
	* *Issues to consider*
		* Binary classification: helpful yo choose k to be an odd number to avoid tied votes
		* Small K captures fine stricture of the problem
		* The principle of “majority voting” for deciding the class labels can be problematic when the class distribution is skewed
		* Irrelevant features within a large feature set, tend to degrade performance
		* Nearest neighbor easily misled when X has a high- dimension
		* Low-dimensional intuitions do not extend to high dimensions
	* In the weighted approach one can extend the k-nearest neighbour method from k to all data items. 
		* The alternative to keep to k elements is called a local weighted method 
		* The extension to all data items is called global weighted method
	* *The curse of dimensionality*
		*  When dimensionality increases, the volume of the space increases so fast that the available data becomes sparse. 
		* The number of features is too large relative to the number of training samples
* **Case Based Reasoning**
	* *CBR* is an* advanced instance-based learning* applied to more complex instance objects 
	* A methodology to model human reasoning and thinking
	* Objects may include *complex structural descriptions* of cases and adaptation rules 
	* The power comes from the *organisation and content of the cases* themselves 
	* *How do we solve the problems*
		* By knowing the steps to apply
		* Not always applying causal knowledge
		* How does an expert solve problems?
		* Heuristic knowledge
		* Remembering how we solved a similar problem before
	* *CBR*
		* Memory-based probelm solving
		* Reusing past experiences
	* *CBR in a nutshell*: 
		* Store previous experience (cases) in memory 
		* To solve new problems: 
			* Retrieve similar experience about similar situations from the memory 
			* Reuse the experience in the context of the new situation : complete or partial reuse, or adapt according to differences 
			* Store new experience in memory (learning)
			* ![[Pasted image 20231114113603.png]]
	* *Process with 4 cases*
		* A *new problem* to be solved is *introduced in the problem space* 
		* During retrieval, a *new problem is matched against problems of the previous cases* by computing a* similarity function*, and the most similar problem and its stored solution are found
		* *If the proposed solution does not meet the necessary requirements of a new* problem situation, *adaptation occurs* (reuse phase) and a new solution is created 
		* *Revise the proposed solution*: alter the retrieved solution(s) to reflect differences between new case and retrieved case(s)
		* A *received solution and a new problem together form a new case* that is incorporated in the case base during the learning step (retain phase) 
		* In this way CBR system evolves into a better reasoner as the capability of the system is improved by extending of stored experience
	* *Main assumptions*
		* Similar problems have similar solutions
		* *The world is a regular place*:what holds true today will probably hold true tomorrow
		* *Situations repeat*: if they do not, there is no point in remembering them
	* *Tasks of CBR*
		* Classification
		* Synthesis
	* *Case Representation*
		* Flat feature-value list
		* Simple case structure is sometimes sufficient for problem solving 
		* Easy to store and retrieve in a CBR system 
		* Object Oriented representation –
			* Case: collection of objects (instances of classes) in the sense of OO 
			* Required for complex and structured objects 
		* For special tasks: 
			* Graph representations: case = set of nodes and arcs 
			* Plans: case = (partially) ordered set of actions 
			* Predicate logic: case = set of atomic formulas 
		* The choice of representation is 
			* Dependent on requirements of domain and task – Structure of already available case data
	* *Similarity*
		* *Purpose of similarity*: 
			* Select cases that can be adapted easily to the current problem
			* Select cases that have (nearly) the same solution than the current problem 
		* Basic assumption: similar problems have similar solutions 
		* *Degree of similarity = utility /reusability solution*
		* Goal of similarity modeling: provide a good approximation 
			* Close to real reusability 
			* Easy to compute 
	* *Modeling similarity*
		* Function to compare two cases sim: Case x Case -> [0..1] 
		* Local similarity measure: similarity on feature level 
		* Global similarity measure: similarity on case or object level 
			* Combines local similarity measures 
			* Takes care of different importance of attributes (weights) 
		* (Sub-)Graph isomorphism for graph representations
		* Logical inferences
	* *Data storage*
		* Efficient case retrieval is essential for large case bases 
		* Different approaches depending 
			* On the case representation 
			* Size of the case base 
		* Organisation of the case base: 
			* Linear lists, only for small case bases – 
			* Index structures for large case bases 
				* Kd-trees, Retrieval nets, discrimination nets, ... 
		* How to store cases: 
			* Databases: for large case bases or if shared with other applications –
				* Main memory: for small case bases, not shared
	* *Solution adaptation*
		* Substitution 
			* change some part(s) of the retrieved solution
			* simplest and most common form of adaptation 
		* Transformation 
			* alters the structure of the solution
		* Generative 
			* replays the method of deriving the retrieved solution on the new problem 
			* most complex form of adaptation










	![[Lazy Learning 2023-11-14 10.23.42.excalidraw]]