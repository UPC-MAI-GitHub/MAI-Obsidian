![[T5_2023_students.pdf]]

## Notes
* The main goal is to move *from high dimensional* spaces to *low-dimensional spaces* to be able to visualize the data distribution
* data > information > knowledge > wisdom ----> pieces of data (unorganized) > basic level of order of data > medium level of order > (Almost) perfect order
* How to go from data to wisdom?
	* Wisdom doesn't require necessarily a large amount of data
	* *Wisdom.* The ability to use your *knowledge* and *experience* to make good decisions and judgements
* *"Less (info) is more (meaaning)"* 
* A plot can be a mess if we have than the required information to plot. 
* **Visualization** is the study of the visual representation of the data, its main goal is to *communicate the information clearly and effectively* through graphical means
* We can visualize either the *data or a model* (a projection of the data)
* **Visualize data of High Dimensionality**
	* *Eliminate dimensions* -> redundant/uninformative variables
	* *Divide and conquer* -> have multiple visualizations of low dimensionality (smaller combinations of the variables visualized together)
	* *Latent and projection models*
		* Use distances
			* $dx =$ Distance in the original space
			* $dy =$ Distance in the projection space
			* $h =$ Neighborhood function
		* *Projection* -> dimensionality compresion (scaling), similitude information coding 
		* *Clustering* -> inding grouping structure in data (PCA)
		* *Self-Organizing Map (SOM) & Generative Topographic Mapping (GTM)* -> combina latent representation and clustering 
	* Visualization must be done in *<4-D* representation trying to *preserve relations* between multi-dimensional points.
		* *Imposible* to preserve information integrally
	* We have linear vs non linear projections
* **Self-Organizing Maps**
	* *Artificial Neural Network* with only two layers that works in a *unsupervised* way. Belongs to *competitive learning* networks
		* Cooperative learning
		* Competitive learning
		* Discretization
		* Capability to generalize
		* K-means is a special case of SOM
	* Simplified models of the cortical maps of the brain.
	* *Process* -> Link ideas (points) in low-dim (2D) representation as their are linked in a high-dim versions of the data.
		* SOM map a multi-dimensional input space onto a *topology preserving* map of neurons

	* *Neighboring areas* in these maps represent neighboring areas in the sensory input space
	* *Applications*
		* Clustering
		* Dimensionality reduction
		* Classification
		* Feature extraction (self-organized feature map)
		* Visualization
	* *SOM 1-D* -> completely interconnected for determining “winner” unit
	* *SOM 2-D* -> connections omitted, only neighborhood relations shown 
	* The *activations* are done by neighbors -> *neighbors become sensitive to the same input* patterns
	* Block distance is used to preserve relations
	* The *size of the neighbors* are *reduced iteratively*
	* Each neuron is assigned a *weight vector with the same dimensionality of the input space* -> *Distance* is calculated *between the input pattern and each neuron* in the network (e.g. Euclidean Distance)
	* **Training**
		* The “winner” neuron and its neighborhood *adapts to make their weight vector more similar to the input pattern that caused the activation*
		* The magnitude of the *adaptation is controlled via a learning parameter* which decays over time
		* *Error*
			* *Quantization error*: measure how well the neurons represent the input patterns (there always be a difference between the original patters and the neuron represents it (loss of info)). It is calculated by *summing all the distances between each input pattern and the neuron to which is mapped*
			* *Topological error*: evaluate complexity of the output space. A high topological error may indicate that the classification problem is complex. 
		* *Training process* 
			* Neurons *initialized randomly*
			* *Unfolding*: Neurons are “spread out” and pulled towards the general area (in the input space) where they will stay
			* *Fine tunning*: SOM match the neurons as far as possible to the input patterns, thus decreasing the quantization error
	* **Algorithm**
		* Choose a random wieght vector
		* For each input choose random X
		* Compute distance between patters and all neurons
		* Determine the winner neuron
		* Update all weight vectors according to the neighborhood of the winner neuron
		* If the convergence criterion is met stop
			* else, narrow neighborhood function and learning parameter and repeat from step 2
	* *Neighborhood function* -> indicates how *closely neurons i and k in the output layer are connected to each other*. Usually, a *Gaussian function* on the distance between the two neurons in the layer is used
* **Multi dimensional Analysis**
	* **Multi-dimensional scaling**: analysis is to* find a spatial configuration of objects* when all that is known is some *measure of their general (dis)similarity*.
		* Plot a map of the original space in a low dimensional space with topoly preserved
		* Exploratory data analysis
		* *Reduces large amount of data*
		* *Attempt to find a structure in a set of distances*. By assigning instances to specific locations in space.  Distances between points in space match dis/similarities as closely as possible
		* *Similarities, dissimilarities, distances, or proximities* reflects amount of dis/similarity or distance between pairs of objects
		* Classification of the MDS models
			* Type of proximities: 
				* Metric/quantitative
				* Non-metric/qualitative
				* Number of proximity matrices 
				* Proximity matrix is the input for MDS 
					1) Classical MDS: One proximity matrix (metric or non-metric) 
					2) Replicated MDS: Several matrices 
					3) Weighted MDS/Individual Difference Scaling: Aggregate proximities and individual differences in a common MDS space
			* *Classical MDS*
				* Uses euclidean distance to model data proximities in a geometrical space
				* Relate the euclidean distances to the observes proximities by a transformation fucntion
			  