
![[CV-2324_Class5_Face_recognition.pdf]]
### Summary
- **PCA for Eigenfaces extraction** 
	- *Non-supervised* feature extraction technique 
	- PCA finds a *linear transformation* of the data into a *lower dimensional space,* such that 
		- The *reconstruction error* according to the Euclidean Distance is *minimum*. 
		- Data do *not lose much information*. 
		- Specially appropriated to reduce the noise of the data 
		- Normally called: Compression-base feature- extraction scheme.
- **LDA**
	- *Supervised feature extraction* technique 
	- Performs *dimensionality reduction* 
	- It finds a *linear transformation of the data that maximize the class separability of the points*. 
	- Creates a new data representation where points of the same class are as close as possible, while points of different classes are as far as possible.
## Notes

### Face Recognition
- *Steps on Face Recognition process:*
	- ![[Pasted image 20240112221408.png|300]]

* *Transform the original high-dimensional data to lower dimensional data* intended to be informative and non-redundant. 
* *Dimensionality reduction*
	* *Linear transformations*
		* *PCA* - Principal Component Analysis
			* Reduce data dimensionality while *retaining as much as possible of the variation* present in the dataset
			* *Transform* a number of *correlated variables into *a smaller number of *uncorrelated variables* (principal components)
			* *First component:* account for as much of the variability in the data s possible
			* After find a new low dimensional new sub space we map the data to the new space
				* The new dimensional space is done by using the *eigenvalues* and the *eigenvectors* and we select the $k$ best ranged according to the eigenvalues
			* *Proportion of Variance* (PoV) explained (or accumulated percent explained) to know how to choose $k$
				* ![[Pasted image 20240112222846.png|200]]
				* We can stop usually at the 90% of the accumulated variance
					* ![[Pasted image 20240112223148.png|300]]
		* *LDA* - Linear Discriminant Analysis
	* *Non-linear transformations*
* *How to define facial features?*
	* Eigenfaces
	* Linear discriminant analysis
* Feature extraction:
	* Is different to dimensional reduction, in the way that instead to create new features from data, you select important features.
* *Linear approaches*:
	* PCA: 
	* *Eigenfaces for face recognition*
	* *Linear discriminnt Analysis*
### Eigenfaces for face recognition
- Think of a *face* as being a *weighted combination of some “component”* or “basis” faces.
- The *eigenfaces* can be can be differently weighted to *represent any face* $x$
	- ![[Pasted image 20240112223533.png|400]]
- *Learning eigenfaces*
	- We take a *set of real training faces* 
	- Then we use *PCA to find (learn) a set of basis faces* which best represent the differences between them. 
	- The *statistical criterion for measuring this notion* is: “best representation of the differences between the training faces” 
	- We can then *store each face as a set of weights for those basis faces*.
		- ![[Pasted image 20240112223838.png|400]]
- *Limitations*
	- Data can be too mixed that the recognition is not successful

### Linear Discriminant Analysis and Fisherfaces
- LDA is a *linear supervised feature extraction* technique 
- Performs *dimensionality reduction *
- It finds a linear transformation of the data that *maximize the class separability of the points*. 
- More concretely, the method seeks for a new *data representation where points of the same class are as close as possible, while points of different classes are as far as possible*.
- ![[Pasted image 20240112225727.png|500]]
- The LDA solution is given by the *eigenvectors of the generalized eigenvector problem*
	- The *linear transformation* is given by a *projection matrix* $U$ whose columns are the *eigenvectors*
	- To *guarantee* the finding of the *low dimensional* space we can apply *PCA* to generate an intermediate space and the we apply *LDA*
		- ![[Pasted image 20240112230345.png|500]]
### Performance PCA vs LDA
- There has been a tendency in the *computer vision community* to *prefer LDA over PCA*. 
- This is mainly because *LDA deals directly with discrimination between classes*, while PCA does not pay attention to the underlying class structure.
- *Experimental results*
	- When the *training set is small*, *PCA* can outperform LDA.
	- When the *training set is large and representative for each class*, *LDA* outperforms PCA.
	- 