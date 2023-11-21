![[T8_2023_students.pdf]]

## Notes

* *Where to focus the attention? What aspects of the problem are important/ncessary to solve it?*
* **High-dimensional data**
	* H-dim data produces
		* lots of parameters
		* large input space
		* Curse of dimensionality and risk of overfitting
	* *Filter data to keep only the necessary part of the information* $\longrightarrow$ Dimensionality reduction
	* The required number of samples (to achieve the same accuracy) grows exponentially with the number of variables
	* The classifier’s performance usually will degrade for a large number of features
	* ![[Pasted image 20231121102213.png]]
* **Feature selection**
	*  Process that chooses an *optimal subset of features* according to a certain criterion
	* A search problem for finding an optimal or suboptimal subset of m features out of original M features.
	* *Advantages*
		* For excluding irrelevant and redundant features, 
		* it allows reducing system complexity and processing time,
		* Often improves the prediction accuracy.
		* Allows data visualization
		* Remove noise
	* ![[Pasted image 20231121103033.png]]
	* *Ways to do feature selection*
		* *Search strategies*
		* Criteria
		* Principle for selection
		* 