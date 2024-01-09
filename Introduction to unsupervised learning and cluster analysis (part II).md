![[T3_2023_students.pdf]]

## Summary
- Clustering groups objects in a *cluster if they are similar* (or related) to one another and *different* from (or unrelated to) the *objects in other groups*
- Clustering can be *hard* or *soft* 
- There are a variety of approaches, including: 
	- *Hierarchical clustering*: HAC 
	- *Partitional clustering*: k-Means, Fuzzy c-Means 
	- *Model-based clustering*: Expectation Maximization
## Notes
### Partitional clustering
- Usually start with a random (partial) partitioning
- Refines iteratively
- *Partitional algortihms*
	- Construct a partition of *n* objects into a set of *k* clusters given a *set of objects* (training set) and typically must provide the *number of desired clusters*, K.
- *Basic process*
	- Randomly choose K instances as seeds, one per cluster 
	- Form initial clusters based on these seeds 
	- Iterate, repeatedly reallocating instances to different clusters to improve the overall clustering 
	- Stop when clustering converges or after a fixed number of iterations 
- **K-means**
	- *Objective:* *minimize the total sum of the squared distances* of every point to its corresponding cluster centroid
	- It is guaranteed to converge a local optimum
	- Input: real valued vectors
	- **Clusters** based on *centroids*, *center of gravity*, or *mean of points* in a cluster
	- *Reassignment* of instances to clusters is *based on distance* to the current cluster centroids
	- Distances:
		- Euclidean
		- $L_1$ norm (Manhattan)
		- Cosine sym (cos) -  Cosine dist (1-cos)
	- *Algorithm*
		- Decide value of K
		- Select k random instances as initial centroids -> $c$
		- For each instance -> $x$
			- Assign the $x$ to the $c$ where the distances is minimal $d(x_i,c_j)$
		- For each cluster $c$
			- $$c_{j}=\mu(c_j(x_i))=\frac{1}{|c|}\sum\limits_{\vec{x}\in C} \vec{x}$$
		- If none instance has updated its cluster exit, otherwise go to the third step.
	- *Complexity*
		- *Time:*
			- *Distance computation*: $O(m)$, where $m$ is the dimensionality of the vectors
			- *Cluster reassigning*: $O(kn)$
			- *Computing centroids:* $O(nm)$
	- Advantages:
		- Relatively efficient: $O(tkn)$ when $k,t << n$. Where $n=instances$, $t= iterations$, $k=clusters$
		- Often terminates at  a local minimum
	- *Disadvantages*
		- Work for numerical data (mean is defined)
		- Need to specify *k*
		- *Unable to handle noisy data and outliers*
		- *Not suitable to discover clusters in non-convex shapes*
		- Results *influenced* by the initial *random clusters selection*
	- *K-means variations*
		- Can variate in:
			- Method of K initial $c$
			- Dissimilarity computation methods
			- How to recompute cluster centers
			- Handle categorical data (*k-modes* or mixed *k-prototypes*)
- *Crisp clustering*
	- Cluster data by grouping  related attributes in uniquely defined clusters
	 * When clusters are well separated, a crisp classification of data points into clusters make sense. But in many cases, clusters are not well separated and *a borderline data point ends up being assigned to a cluster in an arbitrary manner*   (*Solvable introducing fuzzy*)
- **Bisecting K-means**
	 1. Pick a cluster to split 
	 2. Find two subclusters using the basic k-Means algorithm (bisecting step)
	 3. Repeat step 2 for n times and take the split that produces the clustering with the highest overall similarity
	 4. Repeat steps 1, 2 and 3 until the desired number of clusters is reached
 * *How to choose the cluster to split*
	 * Largest cluster
	 * The most heterogeneous cluster, 
	 * The largest cluster which has a predetermined degree of heterogeneity
 * **Fuzzy C-means**
	 * *Fuzzy*: not absolutely, not only one or cero. (Zadeh (1969))
	 * *Every element of the universe belongs to a fuzzy set*with a degree of membership (from 0 to 1)
	 * Data points are given partial *degree of membership in multiple nearby clusters*. *If the element $x$ belongs to the fuzzy set $f$ with a degree of $g$ it belongs to the complement of $f$ as $1-g$*
	 * *Linguistic terms* can be used (*much more*, *less*, etc..)
	 * *No unique partitioning of the data in a collection of clusters.*
	 * **Objective function**
		 * Goal: optimization of the *objective function*, i
		 * $m$ determines the *degree of fuzzification*
		 * *The degree of membership for an instance $n$ in all the clusters must sum up to $1$
		 * *Components:*
			 * *m* fuzzy exponent, governs the influence of the membership grades
			 * *U* membership matrix 
			 * *V* cluster centers 
			 * *($||x_k-v_i||$)* distance between $x_k$ and $v_i$ 
		 * Minimize the membership function by zeroing the gradient $J_m(U,V)$ with respecto to $V$ and $U$, for $U$ is the center of gravity
	 * *Initial choices*
		 * Number of clusters *c*
		 * Max iterations
		 * Weighting exponent *m*
			 * m=1 (crisp)
			 * m=2 (typical)
		 * Termination measure $||V_t-V_{t-1}||$ (*1-Norm*)
		 * Termination threshold
	 * *Iterative algorithm*
		 * Guess initial clusters 
		 * Alternating optimization
			 * Repeat
				 * Compute matrix $U_t$
				 * Compute asociated cluster centers $V_t$
			 * Until max iterations or $||V_t-V_{t-1}||\leq\epsilon$
			 * $(U,V) \leftarrow (U_t,V_t)$
	 * *Crisp clusters* from *Fuzzy clusters* are formed by selecting the *max value per feature* across clusters and that feature remains for that cluster.
	 * *Advantages*
		 * Unsupervised
		 * Always converges
	 * *Disadvantages*
		 * *Long* computational *time*
		 * *Sensitivity* to the *initial guess*
		 * *Sensitivity* to noise
	 * *Optimal number of clusters*
		 * *Performance index* (best optimized value for running the algorithm with a C number of clusters): 
			 * Average of all vectors
				 * Sum of the within fuzzy cluster fluctuations (small value for optimal c)
				 * Sum of the between fuzzy cluster fluctuations (big value for optimal c)
 * *Hard clustering*: assumes that *each instance* is given a “hard” assignment to *exactly one cluster.* Does not allow uncertainty in class membership or for an instance to belong to more than one cluster.
 * **Soft clustering**:  each instance is assigned a probability distribution across a set of discovered categories, probabilities of all categories must sum to 1.
	 * *Mixture models*
		 * Probabilistic way to do soft clustering
		 * Each cluster: a generative model (Gaussian or multinomial)
		 * Parameters (mean/covariance are unknown)
	 * *Expectation maximization*
		 * It is a *iterative method* for learning probabilistic categorization model from unsupervised data.
		 * Probabilistic method for soft clustering
		 * Automatically discover all parameters for the K “sources”
		 * Typically used to *compute maximum likelihood estimates* (MLE) of parameters of an underlying distribution *from given data set when the data is incomplete or has missing values*
		 * *Applications*
			 * Filling in missing data in samples 
			 * Discovering the value of latent variables 
			 * Estimating the parameters of GMMs 
			 * Estimating parameters of finite mixtures 
			 * *Unsupervised learning of clusters*
			 * *Semi-supervised classification and clustering*
		 * *Main idea:* use probabilities instead of distances
		 * *Goal*
			 * Find the most likely clusters given the data
			 * Determine the probability with which an object belongs to a certain cluster
			 *  Let us assume that we know that there are k clusters 
			 * To learn the clusters, we need to determine their parameters (means and standard deviations)
		 * Assumes a *probabilistic model of categories* that allows computing $P(C|x)$ for each category or cluster $C$$, for a given example $x$$
		 * *Soft version* of *k-means*
		 * *Initially assume random assignment* of examples to categories.
		 * *Algortihm*
			 * **Expectation**: Compute $P(C|x)$ for each example given the current model, and probabilistically re- label the examples based on these posterior probability estimates.
			 * **Maximization**: Re-estimate the model parameters $q$, from the probabilistically relabeled data
			 * *Stops* when log-likelihood saturates (A saturated model is a statistical model that perfectly fits the observed data by assigning a separate parameter for each data point. It saturates the likelihood function by achieving the highest possible likelihood value)
			 * 