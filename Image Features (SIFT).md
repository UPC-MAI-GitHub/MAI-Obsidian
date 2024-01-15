![[CV-2324_Class4_SIFT.pdf]]

## Summary
- **SIFT**: Robust *matching technique*
	- *Fast and efficient*—can run in real time 
	- Can *handle changes in rotation and viewpoint* (Up to about 60 degree out of plane rotation) 
	- Can *handle significant changes in illumination* (sometimes even day vs. night) 
	- Based on *Histograms of Gradients* in patches for robustness to small shifts and translations
- *Partially invariant to occlusion*, clutter
## Notes
* *Are HOG descriptors invariant to scale and rotation variations?*
* *Are all pixels equally important?*
* *How much information we need in order to detect/recognize objects?*
### Informative vs. Non-informative regions for object Recognition
#### Local features
* Based on the appearance of the object at *particular interest points*
* *Main Components* for local features relation between different images
	* **Detection**: Identify the interest points in the image. 
	* **Description**: Estimate vector feature descriptor of the interest patch (surrounding each interest point). 
	* **Matching**: Determine correspondence between descriptors in two views
* *Desired properties*
	* *Repeatability/Precision*: The same feature can be found in several images despite geometric and photometric transformations
	- *Saliency:* Each feature has a distinctive description 
	- *Compactness and efficiency:* A few features vs. all image pixels 
	- *Locality:* A feature occupies a relatively small area of the image, robust to clutter and occlusion.
- **Local Invariant Features**
	- Between descriptors in two views
		- ![[Pasted image 20240112144515.png|500]]
#### Description of Interest Points
- **Autocorrelation function**
	- ![[Pasted image 20240112144740.png|300]]
	- We should easily *recognize the point by looking through a small window* 
	- *Shifting the window* in any direction *should give a large change* in intensity
	- Definition: *Corners are distinctive image interest points*
	- How to make it less computationally complex and reduce computation consumption?
		- ![[Pasted image 20240112145157.png|400]]
		- We can use *eigenvalues and eigenvectors* to reduce invariance effects when there are shifting between the compared images
			- The *eigenvalues* reveal the *amount of intensity change*
			- The *eigenvectors* give the *direction of maximum and minimum change*
- **Harris Corners**: 
	- Cornerness score $$f = \frac{\lambda_1\lambda_2}{\lambda_1+\lambda_2}$$
	- *Application*
		- ![[Pasted image 20240112150220.png]]
	- *Properties*
		- Rotation invariant: YES!
		- Scale invariant: Yes only if perform automatic scale selection
- **Automatic Scale selection**
	- Compute the derivatives $(I_x,I_y)$ with different $\sigma$, and find the scale that gives local maxima of the cornerness function f in both position and scale.
	- ![[Pasted image 20240112151102.png|400]]
	- Testing different values in a graphic
	- Once you found the areas of selection you can rescale them to a fixed size
#### Description of Local Patches
- **SIFT Detector** - *Scale Invariant Feature transform*
	- Built a *pyramid of scales*
		- Level 1 is the original image, level 2 to a subsampled image and so on.
		- This technique reduces computational cost
		- ![[Pasted image 20240112171311.png|400]]
	- *Some methods in the process*
		- Select some *candidate keypoints* using *scale-space extrema detection*. 
		- Instead of checking each possible patch R for each possible scale, *we select some interest candidate points*. 
			- For that issue, images are first convolved at each scale with Gaussian filters
		- The *Difference-of-Gaussian images* are computed from the difference of blurred images.
		- *Candidate keypoints* are identified as *local maxima or minima of the Difference-of-Gaussian* images across scale
	- *Process Steps:*
		- *Select some candidate keypoints* using scale-space extrema detection. 
		- The candidate keypoints are *tested for significance* by a two- step procedure: 
			1. Test if the *absolute value of the Difference-of-Gaussian* image D at the minimum or maximum $x$^ is greater than a threshold: $|D(x$^$)|>\gamma$. This allows to *reduce sensitivity to noise. *
			2. Test if the *autocorrelation of the Difference-of-Gaussian images $D$ at $x$^  indicates significance*. This step allows to remove badly localized candidates (i.e. at a straight edge).
		* ![[Pasted image 20240112172230.png|500]]
	* *Rotation invariant*
		* *Rotate patch according to its dominant gradient orientation* 
			* It can be shown that the *dominant direction* is given by the *first eigenvector* $(e1$, if $|l1|>|l2|$, and $e2$, vice versa) of $M$. 
		* This puts the patches into a canonical orientation
	* *Illumination invariant*
		* Define *SIFT* descriptors based on *gradient direction*
		* Uses *histogram of gradients* (relative to computed orientation) to describe pixels around the keypoint 
		* Gradients are computed in the corresponding scale-space image.
		* ![[Pasted image 20240112173113.png|300]]
		* ![[Pasted image 20240112173307.png|300]]
	* *Issues*
		* Not robust to *non-linear* illumination transformations
		* Not robust for images with images that do not get a lot distorted due to rotations or viewpoint changes.
* **ORB Feature descriptor** - *Oriented FAST(Features from Accelerated Segment Test) and Rotated BRIEF (Binary Robust Independent) elementary feature)*
	* *Advantages
		* No licensing restrictions 
		* Fast, computational efficient 
		* Real time and low power device
	* *Disadvantages and Solutions*
		* *No quality measure* (“cornerness”). *Solution*: use Harris cornerness measure 
		* *Not scale invariant*. *Solution*: use SIFT scale invariance (scale pyramid of the image). 
		* *Not rotation invariant.* *Solution*: calculate intensity centroid.
	* *FAST corner detection*: Compare intensity between center pixel and those in circular ring around the center
		* ![[Pasted image 20240112174110.png]]
#### Matching local Features
- To generate candidate matches, *find patches that have the most similar appearance* (e.g., lowest Sum of Squared Distance (SSD)). Simplest approaches: 
	- Compare all them 
	- *Take the closest* (or closest k, or within a thresholded distance). 
- *Ambiguous matches*: Nearest neighbor distance ratio (NNDR)
	- We may *use a threshold* (dashed circle in the figure) *to select the candidate matches*. 
	- The useful range of thresholds can vary a lot depending on the kind of image.
	- To add robustness to matching, we can consider the ratio: $\frac{d1}{d2}$, where 
		- $d_1$ =distance to best match (nearest neighbor) 
		- $d_2=$distance to second best match (the second nearest neighbor). • 
	- If *ratio* is *low*, first match looks *good*. If ratio is *high*, it could be *ambiguous match*.
	- ![[Pasted image 20240112175637.png|400]]
- **Robust feature-based alignment for Panorama creation.**
	- *Steps*
		1. Extract features (detect and describe) 
		2. Find some useful matches (putative matches) 
		3. Compute the best transformation (affine, translation,…) 
		4. Apply this transformation for panorama creation
	* Take into account that: 
		* With the least squares method we assume that the noise follows a Gaussian distribution.
		* Here the noise are the matchings that do not follow the motion model called outliers. 
		* More robust versions of least squares are required when the outliers degrade the model. This may happen if the number of outliers is large.
	* *RANSAC (Random Sample Consensus) method
		* Fitting a line (model) is easy if we know which points belong and which do not. 
		* If we had a proposed line (model), we could guess which points belongs to that line (model): these are called inliers
		* Randomly pick some points to define your line (model). Repeat enough times until you find a good one. 
		* A good one means one that have many inliers. 
		* *Algorithm*
			1. Select a random subset of of k correspondences (hypothetical inliers). 
			2. A transformation model is fitted to this random subset. 
			3. All other data are then tested against the fitted model. 
				- Those points that fit the estimated model well, according to some model- specific loss function, are considered as part of the consensus set. 
				- The estimated model is reasonably good if sufficiently many points have been classified as part of the consensus set. 
			4. This procedure is repeated a fixed number of times (S). 
				*  Each time producing either a model which is rejected because too few points are part of the consensus set, or a refined model together with a corresponding consensus set size. 
				*  In the latter case, we keep the refined model if its consensus set is larger than the previously saved model.
	* ![[Pasted image 20240112182535.png]]
	* ![[Pasted image 20240112182626.png|300]]
	* ![[Pasted image 20240112182703.png|500]]