
![[CV-2324_Class5_Face_detection.pdf]]

## Summary
- *Viola & Jones* algorithm is a method for *automatic detection of faces* in an image. 
- *Rectangle Haar-like features* provide a description of the *window features of the image* 
- By means of *integral images*, the *rectangle features* can be *computed fast*! 
- Rectangle features are *robust in front of noise* 
- *AdaBoost* is used for feature selection and classification 
- *Cascade of classifiers* allows to obtain a a very *low false negative* rate detecting f*aces at real-time!*

## Notes

### Basic concepts
* *Goal*: identify and locate *human faces* in an image regardless of their *position*, *scale*, in plane *rotation*, *orientation*, *pose* and *illumination*
- Face detection is easy for humans but difficult for computers
- *Face detection:* identify where are the faces in an image
- *Face recognition:* Scroll through the image in sections to identify a face.
- Regular strategy: sliding window
	- When using the *sliding window* technique we create a large number of regions to analyse (*Not efficient*)
	- More *non-face* regions than *face* regions
### Visual Features
- **Viola & Jones Method**
	- *Fast* algorithm
	- *Real-time* detection (video processing)
	- *Concepts associated to the method*
		- **Rectangular features** (Haar-like features)
			- A *feature* could be seen as a *function* that transforms an image into a value
			- A feature set is a set of different features extracted from images with objects of interest (Faces, in this case)
				- Different *sizes*, *shapes* and *positions* of the regions with respect to the window.
				- ![[Pasted image 20240112215125.png|300]]
			- *Visual Features* (edges, corners)
			- *Rectangular features*: ones that are appropiate to identify face structrure and sub-structures
				- For a $24x24$ detection region, the number of possible rectangle features (A and B) is over $180,000$
				- ![[Pasted image 20240112211600.png|300]]
				- Which information are that providing?
				- ![[Pasted image 20240112211954.png|300]]
		- *Integral images*
			- A method to *compute rectangle features* in a *fast way*
			- ![[Pasted image 20240112213213.png|200]]
			- Any rectangular sum can be *computed in constant time*, and it is *independent of the size* of the rectangular area.
			- Whi this we just need to scale the parameters of the features
			- ![[Pasted image 20240112213510.png|200]]
		- *AdaBoost*
		- *Cascade of classifiers*
	- *Pattern recognition* problem
		- *Feature extraction* -> Which features to classify?
			- Given the *set of masks,* a *feature vector* of the window is built
			- The feature vector *describes the content* of the window
			- This can be done using the *integral image*
			- ![[Pasted image 20240112212324.png|400]]
			- Remove *noisy features*
		- *Training a classifier*
		- *Test the classifier*
	- Use rectangular features of different sizes, shapes and positions
	- These features help to detect edges, lines and center-surround structures
	- The feature vecture is very large
	- Integral image, a fast way to compute the rectangle features
	- some of the features can be redundant

- *Cascade of classifiers*
	- Each classifier of the classifier is an adaboost


### Ensemble learning
- *Adaboost: Feature selection and classification* (Freund & Schapire,1999)
	- *Strong classifiers from simple classifiers*
	- *Strong classifier*: the combination of all our weak classifiers
		- ![[Pasted image 20240112214629.png|500]]
	- Strong classifier: the combination of all our weak classifiers
	- Weighting strategy
		- Focus on *difficult samples* by *adding a weight* to each sample
		- The sum of weights is going to be one.
	- Weak learner
	- ![[Pasted image 20240112214851.png|350]]
	- *Error measured* by 
		- *False Positive*
		- *False Negative*
### Cascade of classifiers
- Method to *speed-up the detection process.*
- *Start* with simple classifiers which *reject many of the negative* sub-windows while *detecting almost all positive* sub-windows
- Each stage only process regions classified as faces by the previous stages.
- ![[Pasted image 20240112215420.png|500]]
- Basic *evaluation concepts*: 
	- Probability of detection (POD) or *Correct Detection Rate* (DR) or True Positive Rate:  $$DR = \frac{TP}{TP+FP} = \frac{TP}{p}$$
	- *False alarm rate* (FA) or False Positive rate: $$FA = \frac{FP}{TN+FP}=\frac{FP}{N}$$
- *Chain classifiers that are progressively more complex* and have lower false positive rates
	- ![[Pasted image 20240112215834.png|400]]
- *Steps to build a Cascade*
	- Each classifier of the cascade is an AdaBoost 
	- The first classifier C1 is the simplest one 
	- Following classifiers are more complex to refine the results of previous classifiers.
- *Training a cascade*
	- Set target detection and false positive rates for each stage. 
	- Keep adding features to the current stage until its target rates have been met. 
	- Test on a validation set. 
	- *If the overall false positive rate is not low enough, then add another stage*. 
	- Use false positives from current stage as the negative training examples for the next stage.