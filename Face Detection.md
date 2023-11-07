
![[CV-2324_Class5_Face_detection.pdf]]
## Notes
- Face detection is easy for humans but difficult for computers
- *Viola & Jones Method*
	- Pattern recognition problem
		- Feature extraction -> Which features to classify?
		- Training a classifier
		- Test the classifier
		- Use rectangular features of different sizes, shapes and positions
		- These features help to detect edges, lines and center-surround structures
		- The feature vecture is very large
		- Integral image, a fast way to compute the rectangle features
		- some of the features can be redundant
- *Adaboost: Feature selection and classification*
	- Strong classifiers from simple classifiers
	- Published in 1999
	- Decision stumps
	- Strong classifier: the combination of all our weak classifiers
	- Weighting strategy
		- The sum of weights is going to be one.
	- Weak learner
- *Cascade of classifiers*
	- Each classifier of the classifier is an adaboost
