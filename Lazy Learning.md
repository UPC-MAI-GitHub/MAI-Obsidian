![[T7_2023_students.pdf]]

## Summary
- **NN - IBL**
    - *Eager vs. Lazy Learning*: eager- significant computation at training time and global approximation. Lazy learning - computation to consultation time and  local approximations.
    - *Lazy Learning Characteristics*: It's suitable for complex and incomplete domain problems, allowing for more complex function representation, but is slower in consultation and requires substantial storage.
	    - *Nearest Neighbour*: Determines the nearest data object to a query point using distance measures, useful in dividing a space into Voronoi cells.
	    - *Instance-Based Learning (IBL)*: Similar to nearest neighbour but normalizes attributes, handles missing attributes, and focuses on storing training samples for matching test examples.
	- *K-Nearest Neighbour*
	    - *Basics and Application*: Uses Euclidean distance and considers a small number of neighbours (K). Training involves saving examples, and predictions are based on class membership or average value in regression.
	    - *Considerations and Challenges*: Effective for large datasets with a limited number of features, but can be slow in querying and influenced by irrelevant attributes. Normalization and careful selection of K are important to address high dimensionality challenges.
- **CBR** 
	* CBR is a technique for *solving problems based on experience* 
	* CBR problem solving involves *four phases* 
		* *Retrieval, Reuse, Revise, and Retain* 
	* Different techniques for: 
		* *Representing the knowledge*, in particular, the cases 
		* Realizing the four phases 
	* CBR has several *advantages over tradition Knowledge-based Systems* 
	* Several *applications* 
		* *Classification, diagnosis, decision support, planning, configuration, design, ...*
## Notes
### Introduction to Lazy learning
 * **Eager learning:** the majority of computation occurs at training time 
	 * Must create a global approxiamtion
	 * Generalize before seeing a query
	 * *Algorithms*:
		 * Radial basis function networks
		 * ANN
		 * ID3
* **Lazy learning**:
	* Any machine learning process that *defers the majority of computation to consultation time*
		* Creates many *local approximations*
		* Can represent *more complex functions*
	* *Training time:*  Is the time prior to consultation during which the *system makes inferences from training data* in preparation for consultation time
	* *Inference (consultation) time*: the time between when an object is presented to a system for an inference to be made and the time *when the inference is completed*
	* Delays *generalization until a query is made to the system*. --> work well in unseen data
	* *Advantages*:
		* Target function is *approximated locally*
		* *Solve* multiple problems *simultaneously*
		* Successfully *deals with changes* in the problem domain 
		* Suitable for *complex and incomplete domain* problems
	* *Disadvantages*
		* Requires a large space to store the entire training (mainly data samples)
		* Fast in training but *slow in consult
	* *Algorithms*
		* K-Nearest Neighbour
		* Instance Based Learning
		* Case-based reasoning
### Nearest Neighbour
* In a data collection *M*, the nearest neighbour to a data object *q* is the data object $M_i$, which minimizes $dist(q, M_i)$,
	* *Distances measure* is defined for the objects in question
	* The fact that the object $M_i$ is the nearest neighbour to $q$ does not imply that $q$ is the nearest neighbour to $M_i$
* *Process*
	* Get some example *set of cases with known outputs*
	* When you see a *new case*, *assign its output to be the same as the most similar* known case
* *Task*: given  some set of *training data*, and a *query point* $x_q$, *predict* $f(x_i)$
	* *Find the nearest member* of the dataset to the query
	* Assign the *nearest neighbour output* to the query
* *Voronoir diagram*
	* Mathematically *divide a space into a number of regions*
	* Regions are called *Voronoi cells*
	* A Voronoi diagram is the computational geometry concept that represents *partition of the given space onto regions, with bounds determined by distances to a specified family of objects* 
	* The *partitioning of a plane with $n$ points into convex polygons such that each polygon contains exactly one generating point and every point in a given polygon is closer to its generating point than to any other*
	* Different metrics arise a different Voronoi diagram.
	* ![[Pasted image 20231114104145.png|550]]
#### Instance Based Learning
* Similar to nearest neighbors but:
	* It *normalizes all attributes* in range \[0,1\]
	* *Handles missing attributes*
* Approximating *discrete* or *real valued target functions*
* Produces *local approximations*
* *Key idea*: Store training samples, when a test examples is given find the closest matches
* *Distance measure*: typically *euclidean*
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
	* ![[Pasted image 20231114105057.png|350]]
* *IBL Algorithms*
	* *IB1* is identical to the nearest neighbor algorithm, except that
		* it normalizes its attributes’ ranges, 
		* processes instances incrementally, and
		* has a simple policy for tolerating missing values. 
	* *IB2* is identical to IB1, except that 
		* it saves only misclassified instances 
	* *IB3* is an extension of IB2 that employs a “wait and see” evidence gathering method to determine which of the saved instances are expected to perform well during classification
### K-Nearest Neighbour
* Typically *Euclidean distance*
* Number of neighbors to consider: *K* (Typically small and odd)
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
	* *Don't lose information*
* *Disadvantages*
	* Slow at query time
	* Needs lot of storage
	* Easily *fooled by irrelevant attributes*
* *Consider to use it when*
	* Have *lots of data*
	* *No more than 20 feats* per instance
	* instances maps to points in $R^n$
* Keep *data in normalized* form
	* *Z-score Normalization* $$x'_t\equiv\frac{x_t-\bar{x_t}}{\sigma_t}$$
		* Where $x_t\equiv$ mean of $t^{th}$ attributes
		* $\sigma_{t}\equiv$ standard deviation of $t^{th}$ attributes
	* *Linear* or *Min-Max Normalization* $$x_{t'}\equiv \frac{x_t-min}{max-min}$$
		* $min\equiv min$ of $t^{th}$ attributes 
		* $max\equiv max$ of $t^{th}$ attributes 
* *Issues to consider*
	* *In Binary classification*: helpful to *choose k to be an odd* number to *avoid tied votes*
	* *Small K $\rightarrow$ fine structure*
	* *Large K $\rightarrow$ less sensitive to noise*
	* The principle of “majority voting” for deciding the class labels can be problematic when the class distribution is skewed (asymetric)
	* Irrelevant features within a large feature set, tend to degrade performance
	* Nearest neighbor easily misled when X has a high-dimension
	* Low-dimensional intuitions do not extend to high dimensions
* In the *weighted approach* one can extend the k-nearest neighbour method from k to all data items. (e.g inverse of the square of the distance)
	* The alternative to keep to *k elements* is called a *local weighted method* 
	* The extension to *all* data items is called *global weighted method*
* *The curse of dimensionality* (**makes poor generalization**)
	*  When dimensionality increases, the volume of the space increases so fast that the available data becomes sparse. 
	* The number of features is too large relative to the number of training samples
### Case Based Reasoning
* *CBR summary* 
	* CBR is a technique for *solving problems based on experience* 
	* CBR problem solving involves *four phases* 
		* *Retrieval, Reuse, Revise, and Retain* 
	* Different techniques for: 
		* *Representing the knowledge*, in particular, the cases 
		* Realizing the four phases 
	* CBR has several *advantages over tradition Knowledge-based Systems* 
	* Several *applications* 
		* *Classification, diagnosis, decision support, planning, configuration, design, ...*
* Roots in work of *Roger Sank 1983*
* *CBR* is an *advanced instance-based learning* applied to more complex instance objects 
* A methodology to *model human reasoning and thinking*
* Objects may include *complex structural descriptions* of cases and adaptation rules 
* The power comes from the *organisation and content of the cases* themselves 
* *How do we solve the problems*
	* By knowing the steps to apply
	* Not always applying causal knowledge
	* How does an expert solve problems?
	* Heuristic knowledge
	* *Remembering how we solved a similar problem before*
* *CBR*
	* Memory-based probelm solving
	* Reusing past experiences
* *CBR in a nutshell*: 
	* Store previous experience (cases) in memory 
	* To solve new problems: 
		* *Retrieve similar experience* about similar situations from the memory 
		* *Reuse the experience* in the context of the new situation : complete or partial reuse, or *adapt according to differences* 
		* *Store new experience* in memory (learning)
		* ![[Pasted image 20231114113603.png]]
* *Process with 4 phases*
	* A *new problem* to be solved is *introduced in the problem space* 
	* During **retrieval**, a *new problem is matched against problems of the previous cases* by computing a *similarity function*, and the most similar problem and its stored solution are found
	* *If the proposed solution does not meet the necessary requirements of a new* problem situation, **adaptation** occurs (reuse phase) and a *new solution is created* 
	* **Revise** the proposed solution: alter the retrieved solution(s) to reflect differences between new case and retrieved case(s)
	* A *received solution and a new problem together form a new case* that is incorporated in the case base during the learning step (**retain** phase) 
	* In this way CBR system evolves into a better reasoner as the capability of the system is improved by extending of stored experience
* *Main assumptions*
	* Similar problems have similar solutions
	* *The world is a regular place*: what holds true today will probably hold true tomorrow
	* *Situations repeat*: if they do not, there is no point in remembering them
* *Tasks of CBR*
	* Classification (good for CBR)
	* Synthesis (Harder for CBR)
* *Case Representation*
	* *A case is not a rule!!!*
	* *Flat feature*-value list
		* Simple case structure is sometimes sufficient for problem solving 
		* Easy to store and retrieve in a CBR system 
	* *Object Oriented* representation –
		* Case: collection of objects (instances of classes) in the sense of OO 
		* Required for complex and structured objects 
	* For *special tasks*: 
		* *Graph* representations: case = set of nodes and arcs 
		* *Plans*: case = (partially) ordered set of actions 
		* *Predicate logic*: case = set of atomic formulas 
	* The *choice of representation* is 
		* *Dependent* on requirements of* domain and task* – Structure of already available case data
* *Similarity* (Most important concept in CBR)
	* *Similarity of cases*
		* Similarity for each feature (importance of features may be different - weights)
	* *Purpose of similarity*: 
		* Select cases that can be adapted easily to the current problem
		* Select cases that have (nearly) the same solution than the current problem 
	* Basic assumption: similar problems have similar solutions 
	* *Degree of similarity = utility /reusability solution*
	* Goal of similarity modeling: provide a good approximation 
		* Close to real reusability 
		* Easy to compute 
* **Retrieve** *: Modeling similarity*
	* Function to compare two cases sim: Case x Case -> [0...1] 
	* *Local similarity measure: similarity on feature leve*l 
	* *Global similarity measure: similarity on case or object level*
		* Combines local similarity measures 
		* Takes care of different importance of attributes (weights) 
	* (Sub-)Graph isomorphism for graph representations
	* Logical inferences
* *Data storage*
	* *Efficient case retrieval* is essential for large case bases 
	* Different approaches depending 
		* On the case representation 
		* Size of the case base 
	* *Organisation of the case base*: 
		* Linear lists, only for small case bases – 
		* *Index structures for large case bases* 
			* Kd-trees, Retrieval nets, discrimination nets, ... 
	* How to store cases: 
		* Databases: for large case bases or if shared with other applications –
			* Main memory: for small case bases, not shared
* **Reuse**
	* *Ways to choose*
		* *Single* retrieved solution
		* *Multiple* retrieved solutions
			* *Vote/Average* ---> weighted(ranking, similarity)
		* *Iterative retrieval* --> solve components of the solution one at a time
	* *Solution adaptation* (*manual*/*automated*)
		* *Null-adaptation* - just copy the retrieved solution
		* *Substitution* 
			* change some part(s) of the retrieved solution (simplest/most common)
		* *Transformation* 
			* alters the structure of the solution
		* *Generative* 
			* replays the method of deriving the retrieved solution on the new problem 
			* most complex form of adaptation
* **Revise**
	* Verification of the solution by computer simulation
	* Verification/evaluation of the real solution
	* *Criteria for revision*
		* Correctness of the solution
		* Quality of the solution
* **Retain**
	* What ca be learned from the query example?
		*  *New experience* to be retained as new case 
		* *Improved similarity assessment*, importance of features 
		* *Organization* / Indexing of the case base to improve efficiency 
		* Knowledge for *solution adaptation* 
		* Forgetting cases (*learn to forget*) 
			* For efficiency or because out of date
			* Deleting an old case 
				* Old is not necessarily bad (leaves a gap?)
* *Advantages*
	* solutions are *quickly* proposed 
	* *derivation* from scratch is avoided 
	* domains do *not need to be completely understood*
	* cases *useful for open-ended/ill-defined* concepts 
	* highlights *important features*
* *Disadvantages*
	* *old cases may be poor* 
	* library may be *biased*
	* most appropriate cases *may not be retrieved* 
	* *retrieval/adaptation knowledge* still needed
* *Advantages of CBR over other techniques*
	* Reduces the knowledge acquisition effort 
	* Requires less maintenance effort 
	* Improves problem solving performance through reuse 
	* Makes use of existing data, e.g., in databases 
	* Improve over time and adapt to changes in the environment 
	* High user acceptance










![[Lazy Learning 2023-11-14 10.23.42.excalidraw]]