![[CV-2223_Class6_Object_Recognition_by_BOW.pdf]]

## Notes
### Motivation

- *Caltech-101 Dataset*: Object recognition in Caltech-101 About *40 to 800 images per category, 9K in total*. Most categories have about *50 images*. Images are of *variable sizes, with typical edge lengths of 200-300 pixels*.
- **Original: of Bags of ...**
	- *Document classification*: 
		- Classify a text by the words it contains
		- Orderless document representation: frequencies of words from a dictionary
	- *Texture recognition*
		- Texture is characterized by the repetition of basic elements or textons 
		- For stochastic textures, it is the identity of the textons, not their spatial arrangement, that matters
### Bag of Words
* *IDEA*: describe objects as bag-of-words, would it work?
- *Process*
	- ![[Pasted image 20240113000435.png|300]]
	1. *Extract features*
		- ![[Pasted image 20240113000509.png|300]]
		* Detect *points of interests* *or* just *regular points* over the image (grid)
		*  Using *SIFT* to detect keypoints or a pyramid histrogram of visual words (*PHOW*)
		* Dense SIFT: *extract all points detected*
		*  *PHOW features* - large speed-up due to the uniform scale and sampling!
	1. *Learn a dictionary*: frequency of similar features in our bag
		- ![[Pasted image 20240113000601.png|400]]
		- *Construct the visual vocabulary (dictionary)*
			- Apply *clustering* to group similar visual features
			- The *cluster center* is the one selected as the *codeword*
			- With this we can *construct the histogram of visual words* (*codewords*)
	2. *Image representations*: Quantize features using visual vocabulary and represent images by frequencies of “visual words”
		* ![[Pasted image 20240113000337.png|400]]
		* Centers from the clustering becomes *codevectors*
		* A *vector quantizer* takes a *feature vector* and *maps it to the index of the nearest codevector* in a codebook
			* ![[Pasted image 20240113001857.png|400]]
		* *Choosing the vocabulary size*
			* *Too small*: visual words not representative of all patches
			* *Too large*: quantization artifacts, overfittig
		* *Spacial histograms per zone*
			* Construct the histogram trying to keep spatial information from the image, saving patches encoding more than just features
			* ![[Pasted image 20240113003014.png|350]]
			* ![[Pasted image 20240113003222.png|400]]
		* *Quantizing with the codebook*
			- Having a new input image to test
			- Encode the descriptors obtained from the image
			- Compare the encodings with the codewords in the visual dictionary
	3. Classification
- *Complete process*:
	- ![[Pasted image 20240113000807.png|300]]
### Discriminative methods for classification
- **Support Vector Machine**
	- *Linear classifiers*
		- A linear function (hyperplane) to separate positive and negative examples
	- Defining which is *the margin between positive and negative example*
	- Instead of fitting all points, *focus on boundary points*.
	- ![[Pasted image 20240113003424.png|400]]
	- *Quadratic Optimization problem*
		- ![[Pasted image 20240113003652.png|300]]
	- Solve a *dual formulation* of the optimization problem using *Lagrangian multipliers* 
		- Using Lagrangian multipliers to find the  minimum of a convex function with linear constraints
		- We can une the *kernel trick*
		- ![[Pasted image 20240113004206.png|400]]
	- Applicate the optimal hyperplane
	- Solve the dual problem
	- Recovering the optimal hyperplane
	- Select alphas that are not almost zero, and this are the suport vectors
	- ![[Pasted image 20240113004750.png|400]]
	- *Remarks*
		- The solution is sparse: t*he number of support vectors can be very small compared to the size of the training set*
		- *Only support vectors are important for prediction of future points*. *All other points can be forgotten*.
	- *Allowing some miss-classifications* called as soft-margin, and the parameter C control the amount of outliers you allow, *trade off between robustness and correcteness*
- **Apply SVM in non linear separable data**
	- ![[Pasted image 20240113005323.png|350]]
	- ![[Pasted image 20240113005532.png|400]]
	- Apply the *kernel trick* $\rightarrow$ map data from its original feature space to another dimensional space where it is linearly separable.
	-![[Pasted image 20240113005203.png|400]]
	- *Kernel*: For a given mapping from the space of objects to some feature space, the *kernel of two objects and is the inner product of their images in the features space*
	- If you *change the kernel* (transformed in dimension), then you *don't need to use the transformed data*, so you don't need to know explicitly to which space transform the data.
		- *Kernel benefits*
			- Allow SVMs to handle nonlinearly separable data sets 
			- Incorporate prior knowledge
			- Can be defined on inputs that are not vectors (such as strings, graphs...) 
			- Provide a mathematical formalism for combining different types of data (critical in biological applications).
		- *Kernel dangers*
			- As the number of variables under consideration increases, the number of possible solutions also increases, but exponentially. 
			- Consequently, it becomes harder for any algorithm to select a correct solution.
		- ![[Pasted image 20240113010036.png|500]]
- *Multi-class classification*
	- You create *multiple binary classifiers isolating one of each specific class*, technique *one vs. the rest* or *multiple one vs. one*
	- ![[Pasted image 20240113010728.png|400]]
	- *One-versus-all:* 
		- *Winner-takes-all strategy*: the classifier with the highest output function assigns the class (continuous decision values). 
		- It is important that output functions are calibrated to produce comparable scores 
	- *One-versus-one*: 
		- *Max-wins voting strategy*: every classifier assigns the instance to one of the two classes, then the vote for the assigned class is increased by one
- *Algorithm: SVMs for image classification*
	1. Pick an *image representation* (in our case, bag of features) 
	2. Pick a *kernel function* for that representation 
	3. *Compute the matrix of kernel* values between every pair of training examples 
	4. Feed the kernel matrix into your favorite SVM solver to *obtain support vectors and weights* 
	5. *At test time*: compute kernel values for your test example and each support vector, and combine them with the learned weights to *get the value of the decision function*
- **Continuous process with classification**
	- ![[Pasted image 20240113011825.png|400]]
- **Practical difficulties**
	- One would like to use a kernel function that 
		- Is likely to allow the data to be separated 
		- But without introducing too many irrelevant dimensions. 
	- How is such a *function best chosen*? 
		- *The only realistic answer is trial and error*.
		- Typically, begin with a simple SVM, and then experiment with a variety of ‘standard’ kernel functions.
- **Evaluation done through Precision recall**
	- Experiments by doing *Cross-validation*
	-  Precision: fraction of retrieved objects that are $relevant = P(relevant|retrieved)$  
	- Recall: fraction of relevant objects that are $retrieved = P(retrieved|relevant)$
-  **Results of Bags of Words for Object Recognition**
	- ![[Pasted image 20240113012415.png]]