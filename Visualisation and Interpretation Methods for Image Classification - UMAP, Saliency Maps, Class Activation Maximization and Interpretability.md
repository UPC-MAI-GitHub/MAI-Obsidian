![[2023-2024_Class8_Visualization_and_Interpretability.pdf]]
## Notes

* **What To do when NN is not learning**
	* Look at the *model*
	* Look at the *Data*
### Visualization of High-dimensional Data
* *Visualization* is *important* 
	* See how mixed/separated data is
	* See relationships
	* *How to do*: high-dimensional space $\longrightarrow$ low-dimensional space
	* ![[Pasted image 20240113035815.png|400]]
* **PCA**:
	* Method to optimally *summarize large multi-dimensional* datasets 
	* *Goal*: find a *smaller number of dimensions (ideally 2) which retain most of the useful information in the data* 
	* Builds a recipe for converting large amounts of data into a single value, called a *Principal Components* (PC)
		* Principal components are orthogonal
		* Account for as much variance as possible
	* Seeks directions efficient for *representing data in all its variance*
		* Data is porjected in a new low-dimensional space created from *eigenvalues* and *eigenvectors*
	* Reduces the dimensions of data 
	* *Accelerates the execution time of the algorithms*
	* Reduce noise! efficient 
	* *Disadvantages:*
		* *Assumes Linear* decomposition 
		* Assumes Orthogonal axes 
		* Represents a transformation consisting of a rotation, affine rescaling and translation 
		* *Is not discriminative*.
* *t-SNE*
	* T-Distributed Stochastic Neighbour Embedding
	* *Non-linear scaling* to represent changes at different levels
	* Optimal separation in 2-dimensions
	* *Unsupervised learning*
	* *Preserve neighbors when moving to low-dimensional space*
	* *Goal*: Finds a low-d representation that is faithful to the high-d model
	* Parameter *Perplexity* = expected *number of neighbors within a cluster*, the model is really sensitive to this parameter
		* Prefixed parameter, used to compute the *variance of data* 
	* Distances scaled relative to perplexity neighbors
	* Compute the distances in the low-dimensional space
	* *Steps to optimize similarity measures*
		1. t-SNE models a point being selected as a neighbor of another point in both higher and lower dimensions.
			1. It starts by calculating a pairwise similarity between all data points in the high- dimensional space using a Gaussian kernel. 
			2. The points that are far apart have a lower probability of being picked than the points that are close together.
			3. Points are mapped to a low-dimensional space *minimizing the divergence* between probability distribution of the high and low dimensional data (Minimization via gradient descent)
	* *Disadvantages:*
		* Can’t cope with noisy data 
		* Loses the ability to cluster
* *UMAP*
	* Kind of *combination of PCA and t-SNE*, get the best of both worlds
	* In order to construct the initial high-dimensional graph, UMAP builds something called a "*fuzzy simplicial complex*". 
	* This is really just a representation of a weighted graph, with edge weights representing the likelihood that two points are connected. 
	* To determine connectedness, UMAP extends a radius outwards from each point, connecting points when those radii overlap. 
	* Choosing this radius is critical - too small a choice will lead to small, isolated clusters, while too large a choice will connect everything together. ì UMAP overcomes
	* *Advantages*
		* UMAP is quite a bit *quicker* than tSNE 
		* UMAP can preserve *more global structure* than tSNE 
		* UMAP can *run on raw data* without PCA preprocessing 
		* UMAP can *allow new data to be added to an existing projection*
	* *Hyperparameters really matters*
	* *Random noise doesn’t always look random*
	* You may need more than one plot (UMAP is stochastic) 
### Interpretation Methods for Image Classification
* Zeiler and Fergus proposed a *method able to recognize what features in the input image an intermediate layer of the network is looking for*.
*  **Deconvolutional Network (DeconvNet):** it inverts the operations from a particular layer to the input using the activation of that specific layer.
	* *Silency Maps*
		* Deconvolution is used as the inverse of convolution (with the transposed version of the same filters), 
		* Unpooling as the inverse of pooling
		* Inverse ReLU removing the negative values as the inverse of itself.
			* ![[Pasted image 20240113043440.png|300]]
		* R*esults of the reconstruction* of the input image from the activations of the fifth layer.
			* ![[Pasted image 20240113043522.png|400]]
		* Is the model truly identifying the location of the object in the image, or just using the surrounding context? 			
			* The examples show the model is localizing the objects within the scene, as the probability of the correct class drops when the object is occluded.
			* ![[Pasted image 20240113043701.png]]
* **Class Activation Maps (CAM)**
	* *Class Activation Maximization* is another explanation method for interpreting convolutional neural networks (CNNs) introduced by Zhou et al. 2016.
	* They proposed a network where the fully connected layers at the very end of the model has been replaced by a layer named *Global Average Pooling (GAP)* and combined with a *class activation mapping* (CAM) technique.
	* *Steps*
		* The *GAP averages the activations of each feature map, concatenates and outputs them as a vector*. 
		* Then, a *weighted sum of the resulted vector is fed to the final softmax loss layer*
		* *Compute a weighted sum of the feature maps of the last convolutional layer* to obtain the class activation maps
	* *Evolution Technique* $\longrightarrow$ 
		* *Grad-CAM*:  is a more versatile version of CAM that can produce visual explanations for any arbitrary CNN, even if the network contains a stack of fully connected layers too (e.g. the VGG networks).
		* *Guided Grad-CAM*: by adding an element-wise multiplication of guided-backpropagation visualization.
### Interpretability and Explainability of CNNs
- *Help building trust*
	- Humans are reluctant to use ML for critical tasks 
	- Fear of unknown when people confront new technologies 
- *Promote safety*
	- Shift in distributions 
	- Explain model’s representation (i.e. important feature) providing opportunities to remedy the situation 
-  Allow for *contestability*:
	- Black-box models don't decompose the decision into submodels or illustrate a chain of reasoning
- *AI does not give the reasons for the decision* and it can matter. 
	- *Interpretability*: establish a cause and effect relationship
	- *Explainability:* explain internal mechanism of ML and DL in human terms
- As ML penetrates critical areas such as medicine, *the inability of humans to understand these models seems problematic*.
- *Informing feature engineering*: Create new features using transformations of your raw data or other features to improve model accuracy
- *Directing Feature data collection:* *Understand the value of the features* that you already have and, therefore, decide what new values will be more helpful
- An algorithm for making hiring decisions should simultaneously *optimize productivity, ethics, and legality*.
- *Fairness*: Concern that interpretations must be produced for assessing whether *decisions* produced automatically *by algorithms conform to ethical standards*
- *Safety*: Make sure the system is taking safe decision
- **Types of interpretability techniques**
	- ![[Pasted image 20240113050421.png|400]]
	- *Decomposability*: addresses what the model is doing at
	- *Algorithmic Transparency:* addresses whether the model has any desirable properties which are easy to understand.
	- *Pos hoc interpretability:* 
		- natural language explanations
		- visualizations of learned representations or models
		- explanations by example
	- Case-based reasoning approaches for interpreting generative models
	- One model might be trained to generate predictions, and a separate model, such as a recurrent neural network language model, to generate an explanation. 
	- Neural image captioning in which the representations learned by a discriminative CNN are coped by a second model to generate captions.
	- ![[Pasted image 20240113050827.png|500]]