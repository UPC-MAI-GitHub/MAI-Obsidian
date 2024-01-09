![[T4_2023_students.pdf]]

## Summary
* **Factor analysis
	* *Reduce the complexity* of data 
	* Data reduction makes it possible to identify the *latent variables* which exist *underneath* a set of *variables* which are actually *observed* 
	* These *latent variables* can then be used for further *analysis* to make sense of *relationships in the data*
	* Understand what constructs underlie the data
* **PCA**: 
	* Proper to dimension reduction
	 * *Finds the directions of maximum variance*
	* *Focus on uncorrelated and Gaussian components*
	* Reduce the data into smaller number of components
* **ICA** 
	* Proper to blind source separation or classification using Independent components when class id of training data is not available
	* Finds the directions of *maximum independence*
	* Focus on *independent* and *non-Gaussian* components  
## Notes

### Factor analysis
- Introduced by Karl Pearson 1901 - Pearson Correlation Coefficient, Chi-square test and PCA
- *Statistical method* used to *describe variability* among *observed variables*, *correlated variables* in terms of potentially  lower number of *unobserved variables* called *factors*.
- FA searches for such joint variations in response to unobserved *latent variables*
- The observed variables are *modeled as linear combinations of the potential factors*, plus error terms 
- *Usage*:
	- Explore data patterns
	- Reduce the number of variables
- *Goal*: summarize patterns of correlations among unobserved variables
	- Investigate whether a number of variables of interest are linearly related to a smaller number of unobservable factors (factors are relatively independent one from another).
	- Correlations used as descriptive (PCA) or indicative (FA)
- *Observed variables:* observed and directly measured.
- *Latent  variables*: Not directly observed, but **inferred** *from other variables*
- *Correlated variables:* grouped together and separated form other variables with low or no correlation
- *Dimensionality reduction*
	- *Project* high dimensional data onto a lower dimensional sub-space *using linear and non-linear transformations*
- *General steps of FA*
	-  Selecting and measuring a set of variables in a given domain 
	- Data screening in order to prepare the correlation matrix to perform PCA or FA 
	- Factor Extraction 
	- Factor Rotation to increase interpretability 
	- Interpretation 
	- Further Steps: Validation and Reliability of the measures
- Consider a *good factor* when:
	- Make sense
	- Easy to interpret
	- Simple structure
	- Lacks complex leadings
- *Disadvantages*
	- No statistical criterion to compare the linear combination
	- After extraction there is a infinite number of rotations available
	- FA is often used to "save" poorly conceived research
- *Types of FA*
	- **Exploratory factor analysis**: 
		- Used to *identify relationships among items and group items* that are part of unified concepts
		- *Summarize data* by grouping correlated variables
		- Investigating sets of *measured variables related to theoretical constructs*
	- **Confirmatory factor analysis**
		- CFA is a more *complex approach*
		- Used when factor structure is known or at least theorized
		- Testing generalization of factor structure to new data
- *Applications*
	- Identification of underlying factors
	- Screening (filtering) of variables
### Independent Component Analysis
* *Non-Orthogonal coordinate*
* ICA
	* Finds the directions of *maximum independence*
	* Focus on *independent* and *non-Gaussian* components 
	* Higher-order statistics 
	* Non-orthogonal transformation
* What ICA could be used for?
	* Most measures quantities are mixture of variables
	* *Cocktail party problem*: separate what everybody is saying in a room full of people speaking
	* Separation of Independent signals
		* Similar to blind source separation
* ICA is a method for finding *underlying factors* or components *from multivariate* (multi- dimensional) *statistical data*
* *Goal*: *decompose* multivariate data into a *linear sum of statistically independent components*
* Basis coefficients are statistically independent
* The goal in the algorithm is to find a matrix W (separation matrix) such that the entries are as independent as possible.
* *Separation technique:*
	* *Central limit theorem*: if two random (non-Gaussian) signals are added, the resulting signal will be more Gaussian than the original two random signals
	* *ICA separation concept*: 
		* Central Limit Theorem (in reverse)
		* Maximizing Non-gaussianity
			* Meassure of non gaussianity by Kurtosis
			* K(z) = 0   -> gaussian
			* K(z) < 0   -> subgaussian
			* K(z) > 0   -> supergaussian
		* Probability Density Definition
		* Expected value definition
* *Independent component*: a *variable that cannot be estimated from other* variables, it is independent
* ICA maximizes independence between signals 
* Sensor Requirement 
	* *The number of separated signals cannot be larger than the number of inputs*.
* ICA Applications:
	* Blind source separation (BSS)
	* Image denoising 
	* Medical signal processing – fMRI, ECG, EEG 
	* Modelling of the hippocampus and visual cortex 
	* Feature extraction, face recognition 
	* Compression, redundancy reduction 
	* Watermarking 
	* Clustering 
	* Time series analysis (stock market, microarray data) 
	* Topic extraction 
	* Econometrics: Finding hidden factors in financial data
### Principal Component Analysis
* *Orthogonal coordinate*
* PCA
	* *Finds the directions of maximum variance*
	* *Focus on uncorrelated and Gaussian components*
	* Second-order statistics 
	* Orthogonal transformation
* Components are calculated as *linear combinations* of the original variables. The linear combinations are *uncorrelated* (*orthogonal*) one with another
* *Goal*: account for *as much of the total variance* as possible (find new representation (basis) to filter the noise and reveal hidden dynamics)
* The *first principal component* accounts for the *greatest possible statistical variability* (entropy/covariance) in the data.
* What PCA Does?
	* Is an *orthogonal linear transformation that transfers the data to a new coordinate system* such that the greatest variance by any projection of the data comes to lie on the first coordinate and so on.
	* *Basic steps*:
		* Find new axes 
		* Decide on which are significant 
		* Form a new coordinate system defined by the significant axes 
		* Map data to the new space (Compressed Data)
	* *Covariance of 2 attributes* $$cov(A_1,A_{2)}= \frac{\sum_{i=1}^{n} (x_i-\bar{x})(y_i-\bar{y})}{n-1}$$
		* *Positive variance* both dimensions increase together
		* *Negative variance* as one dimension increases the other decreases (move inversely proportional)
		* *Zero covariance* dimensions are independent to each other
	* *Eigenvectors* are vectors which can be replaced by *eigenvalues* (a single value) in a matrix multiplication and the same result is obtained 
		* Only square matrixes have eigenvectors, but not all square mat have them.
		* A $n\times n$ matrix can have at most $n$ eigenvectors which all are perpendicular (orthogonal)
	* **Covariance matrix**
		* Computed covariance between all attributes in data
		* Eigenvectors can be used as a new bases for a n-dimensional vector space
* *Complete steps for PCA*
	1. *Subtract the mean* from data
	2. Calculate the *covariance matrix* 
	3. Calculate the *eigenvectors and eigenvalues* of the covariance matrix 
	4. *Choose components* and *construct a new feature vector* 
	5. Derive the *new data set* 
	6. *Reconstruct* the old data back
* Order eigenvectors by eigenvalue, highest to lowest. In general, you get n components. To reduce dimensionality to $p$, ignore $n-p$ components at the bottom of the list.
* Number of principal components to keep:
	* Can ignore the components of lesser significance
	* You do lose some information, but if the eigenvalues are small, you don’t lose much 