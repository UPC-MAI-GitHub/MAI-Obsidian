![[T8_2023_students.pdf]]

## Summary

- Feature selection has different elements 
	- *Searching* for the *best subset* of features 
		- Forward, Backward, Bidirectional, or Random generation 
	- *Selection Criteria* 
		- Heuristic, Exhaustive, or Non deterministic search
	- *Criteria for evaluating* different subsets 
		- Information, distance, dependency, or accuracy measures 
	- *Principle for selecting* (selection algorithms) 
		- Filters, Wrappers, or Embedded algorithms
## Notes
### Introduction to Feature Selection
* Where to *focus the attention*? What aspects of the problem are *important*/*necessary* to solve it?
* **High-dimensional data**
	* H-dim data produces
		* *lots of parameters*
		* *large input space*
		* *Curse of dimensionality* and risk of *overfitting*
	* *Filter data to keep only the necessary part of the information* $\longrightarrow$ **Dimensionality reduction**
	* The *required number of samples* (to achieve the same accuracy) *grows exponentially* with the number of variables
	* The classifier’s performance usually will degrade for a large number of features
	* ![[Pasted image 20231121102213.png]]
* **Feature selection**
	*  Process that chooses an *optimal subset of features* according to a certain criterion
	* A **search problem** for finding an optimal or suboptimal subset of $m$ features out of original $M$ features.
	* *Advantages*
		* For excluding irrelevant and redundant features (**Reduce dimensionality**)
		* It allows reducing system complexity and processing time (**Reduce complexity/cost of the data**)
		* Often improves the prediction accuracy. (**Improves performance**)
		* Allows data visualization (**Allows visualization**)
		* Remove noise
	* ![[Pasted image 20231121103033.png]]
### Feature Selections Perspectives
- *Searching* (best subset of feats) $\rightarrow$ Directions / Strategies
- *Criteria*  (evaluating different subsets) $\rightarrow$  measures of (Information / Distances / Dependence / Consistency /Accuracy) 
- *Principle for selecting* (adding, removing, changing feats during search) $\rightarrow$ filter / wrapper / embedded
- Selection can be binary $\rightarrow 1=$ *selected* feat / $0=$ *discarded* feat
- A total of $2{^M}$ subsets where $M$ is the number of features in the data
- **Search**
	- *Strategies*:
		- *Exhaustive*: 
			- With $n$ features examines $\binom{n}{d}$ *(all) possible* subsets of size $d$. 
			- *Select* the subset that performs *the best*.
			- Space complexity $O(2^M)$
			- Only Exhaustive search can *guarantee optimality*
		- *Heuristic*:
			- Employ a heuristic to carry out the search
			- Find non-optimal subsets
			- Max subsets generated $O(M)$ 
		- *Non-deterministic*:
			- Combines: *Exhaustive* + *Heuristic*
	- *Directions*
		- *Forward* (Sequential Forward Generation- SFG) 
			- Starts with an empty set
			- Add features iteratively according to an update strategy
			- Stop criterion
		- *Backward* (Sequential Backward Generation- SBG)
			- Starts with a full set of feats
			- Remove feats iteratively according to an update strategy
			- Stop criterion
		- *Bidirectional* (Bidirectional Generation- BG) 
			- Search in both directions concurrently (SFT + SBG)
			- At each step, consider all additions and removals of one variable, and select the best result
			- Stops in two cases:
				- One search finds the best subset before it reaches the middle
				- Both searches achieve the middle
		- *Random* (Random Generation - RG)
			- Randomly add feats to the subset
			- Stop criterion
- **Criteria**
	- *Information measures:* measure uncertainty
		- *Shannon's entropy:* $-\sum\limits_{i}P(c_i)log_2P(c_i)$
		- *Information Gain:* $IG(A) = I(D)-\sum\limits_{j=1}^{p}\frac{|D_j|}{|D|}I(D^A_j)$
	- *Distance measures:* measure of separability, discrimination or divergence. Most typical derived from distance between the class conditional density functions
		- *Euclidean:* $\sqrt{\sum\limits_{i=1}^{m} (x_i-y_i)^{2}}$
		- *Manhattan:* $\sum\limits_{i=1}^{m} |x_i-y_i|$ 
		- *Chebyshev:* $max_{i}\;|x_i-y_i|$
	- *Dependency measures*: measures of association or correlation
		- *Pearson Correlation Coefficient:* $\rho(X,Y) = \frac{\sum_{i}(x_y-\bar{x})(y_i-\bar{y})}{\Large[\sum_i(x_i-\bar{x})^2\sum_i(y_i-\bar{y})^2\Large]^{\frac{1}{2}}}$
	- *Consistency Measures:* find a minimum number of feats that separate classes as the full dataset can.
		- *Chernoff*
		- *KLK*
	- *Accuracy Measures*: evaluation relies on the classifier or learner, the subset that yields the best predictive accuracy is chosen
		- *Accuracy*
		- *Chi-squared*
		- *Information Gain*
- **Principle for selecting**
	- *Filter*: feature evaluation function (rank, k-selections)
		- Measure uncertainty, distances, dependence or consistency is usually *cheaper than measuring the accuracy* of a learning process
		- Simplicity and low time complexity (handle large size data)
	- *Wrapper*: the *performance of the classifier* is used to evaluate subsets
		- internal statistical validation to *control the overfitting*
		- allow learning model to fully explote its biases
	- *Embedded*: perform variable selection in the course of model training
		- Features selected during training
		- Not requiere training and validation set partitioning
		- Achieve a *faster solution* by avoiding the re-training of a predictor for each feature subset explored
### Aspects in feature selection
* *Output of feature selection*
	* **Feature Ranking Techniques**
		* A *ranked list of features* ordered according to evaluation measures
		* We can return the *relevance of features*
		* With the rank we can *choose the first $m$ features* to generate the learning model
	* **Minimum Subset of techniques**
		* The number of relevant feats is usually unknown
		* Techniques to retrieve the proper number of features to keep. At least the same performance as with the full set
* *Evaluation*
	* **Goals**
		* *Inferability*: improvement of the prediction of unseen examples with respect to the direct usage of the raw training data
		* *Interpretability*: generating more understandable structure representation that can explain the behavior of the data
		* *Data reduction*: better and simpler to handle data with lower dimensions in terms of efficiency and interpretability
	* **Assesments**
		* Accuracy
		* Complexity
		* Number of features selected
		* Speed of the FS method
		* Generality of the features selected
* *Drawbacks*
	* Resulted subsets are dependent on the training size
	* Feature reduction not always is the best option, it can affect model performance too
	* Backward removal strategy is very slow for large-scale datasets.
	* Sometime there is not to much reduction in the final subset of features
### Most Representative Feature Selection

* *The major components to categorize:*
	* Search direction
	* Search strategy
	* Evaluation measure