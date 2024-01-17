##### Filters & Edges
1. *Test on smoothing filters: "Values should be ..."*
	- **Positives** 
3. *Test on smoothing filters: "Amount of smoothing ... to mask size"*
	- **Proportional**
5. *Test on smoothing filters: "Remove ...-frequency" components; "...-pass filter". Complete the sentence*
	-  **High - Low**
6. *Test on derivatives: "Sum to ... -> no response in constant regions". Complete the sentence*
	- **1**
7. *Test on derivatives: "... values at points of high contrast". Complete the sentence*
	- **Large** 
8. *Do you know any finite difference filters?*
	- **All the above **
9. *How can we detect edges using derivatives*
	- **Edge correspond to extrema o derivative (max by absolute value)**
	- **Derivatives allow to allocate high image gradients**
10. *What is the effect of image noise for calculating edges? (multiple corect answer)*
	- **Image noise prevents the proper localization of edges.**
	- **Image noise produces a high derivative filter response. **
11. *Why Deivative of Gaussian filter is useful?*
	- **Because it is the combination of two filters in a single one useful for edge detection**
##### Template Matching and HoG
1. *What of the following cases is template matching better for?*
	-  **Find icons in a computer screen** 
2. *Test on template matching (multiple corect answer):*
	- **Match can be meaningful, if scale, orientation and general appearance is light **
	- **We use filters as templates of what we want to find in the image. **
3. *Nomalized cross-corelation is*
	- **Less sensitive to mask variance **
1. *What are some deformations pixel/patch based template matching can’t handle? (multiple corect answer):*
	- **Scale, Rotation, Shearing, Flipped **
3. *The gradient stucture is characteistic of*
	- **Local shape and appearance **
4. *Illumination changes affects:*
	- **Gradient magnitude**
5. *HOG desciptor carries infomation about*
	- **the edge positions**
6. *KNearest Neighbors for retieval: “The feature vector of an image is a point in our …. space. The query is … vector in our … space”. Complete with:*
	- **Feature - an unlabeled - feature**
7. *Pedestian detection based on HOG applies:*`
	- **Sliding window strategy to extract and compare patches**
##### SIFT
1. *The key properties of a good local feature are:*
	- **Repeatability, saliency, compactness and efficiency and locality** 
2. *The aperture problem appears when*
	- . **There is no change along the edge direction **
3. *The distinctive image interest points are:*
	-  **Corners** 
4. *We can say that a point is located along an edge:*
	-  **When one eigenvalue of M is much larger than the other. **
5. *Nearest neighbor distance ratio NNDR is used to*
	-. **Robustly find good matchings and discard ambiguous ones**
6. *RANSAC algoithm allows to*
	- **Find a set of good corespondences and a transfomation model **
7. *The oiginal SIFT desciptor uses 16x16 patches and 4x4 aray of 8 bin histograms. Thus, each SIFT desciptor is made up of:*
	- **4 × 4 × 8 = 128 non-negative numbers **
8. *Which are the differences and similaities between HOG and SIFT desciptors? (multiple corect answer).*
	- **SIFT is local desciptor and HOG is a global desciptor **
	- **SIFT is used for finding point corespondence between images whereas HOG is used for template matching**

##### Face Detection and Recognition
1. *The objectives of Viola & Jones method are:*
	- **Fast algoithm (real-time) for accurate detection of faces**2. *Rectangle features are:*
	-  **Haar-like features to detect edges, lines, center-suround stuctures**
3. *Integral Image*
	-  I**s intended to efficiently compute rectangle sums**
4. *AdaBoost (multiple corect answer):*
	- **Combines several weak classifiers to build a single strong classifier**
	- **Defines weak classifiers in each iteration to be devoted to misclassified examples**
5. *Cascade of classifiers is a*
	-  **Method to speed-up the detection process.**
6. *Indicates which of these sentences are true (multiple cotrect answer*
	- **The Eigenfaces are a set of basis faces which best represent the differences between the training faces.**
	- **The statistical criterion for measuring the notion behind Eigenfaces is: best representation of the differences between the training faces**.
	- **We can store each face as a set of weights for the previously computed basis faces.**
7. *Eigenfaces is based on:*
	- **PCA** 
8. *LDA is a:*
	- **Supevised method**
9. *PCA is a:*
	- **Unsupevised method**
10. *Is LDA always better than PCA for face recognition?*
	- -**No*