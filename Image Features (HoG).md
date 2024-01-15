![[CV-2324_Class3_HOG.pdf]]

## Notes
### Template matching
- *Goal:* find the template (part extracted from the image) in the same image
- *Method:* Compare the template patches of the image
- *Main challenge:* find a good similarity measure
- **Using filters**
	- *Goal:* find the template in the image with filter applied
	- *Method 1: Sum Square Difference* $$h[m,n] = \sum_{k,l} (g[k,l] - f[m+k,n+l]){^2}$$
		- ![[Pasted image 20240112124707.png|500]]
		- What will happen if the local brightness changes?
			- It works fine. But it has *problems with local brightness changes*.
		- ![[Pasted image 20240112124752.png|500]]
	- *Method 2: Convolutional filtering the image with the template* $$h[m,n] = \sum_{k,l} (g[k,l])(f[m+k,n+l])$$
		- Where $f = image$  and $g = template$ 
		- *It doesn't work* because it *needs normalization*
		-  ![[Pasted image 20240112125046.png|350]]
	- *Method 3: Convolutional filtering the normalized image* $$h[m,n] = \sum_{k,l} (g[k,l])(f[m+k,n+l]-\bar{f})$$
		- $\bar{f}=$ mean of $f$
		- We get *true detections* but *also noisy detections* (Sensitive to high contrast areas)
		- ![[Pasted image 20240112125231.png|550]]
	- *Method 4: Normalized Cross-Correlation*
		- ![[Pasted image 20240112125440.png|400]]
		- ![[Pasted image 20240112125626.png|525]]
		- ![[Pasted image 20240112125749.png|525]]
	-  Summary of Similarity or *Distance measures performance*
		- *Sum Square Difference:* fast, but sensitive
		- *Correlation:* less sensitive to illumination
		- *Zero-mean correlation:* less sensitive to mask values
		- *Normalized Cross correlation:* less sensitive to mask variance
	- When template matching sill not work?
		- When other variations come to the table, like size or orientation of either the image or the template. 
### Image descriptors: what are and why we need them?
* **Problems where features (image descriptions) can help**
	* *Image Description:* automatically construct a description in order to *describe objects and discriminate between categories* of image content
		* *Algorithm:* 
			* *Training*: 
				1. Define the image descriptor 
				2. Represent each image of the training set by its descriptor 
				3. Store the descriptors and class labels of the training samples (labeled images) 4. Build a model 
			*  *Test*: 
				1. Given a test example extract its descriptor 
				2. Apply the model (compare with the training examples to decide its label)
	* *Image retrieval:* Given an image (query image), the image retrieval consists of *sorting the rest of images according to the similarity* to the query image
		* *Algorithm*
			1. *Define the image descriptor* (something from the image to be measured -  color, distance, etc.)
			2. *Extract the image descriptors* of the database images (Compute the measurement over all the images)
			3. Given a *query image, extract its descriptor vector* (apply same measurement to the query image)
			4. *Sort* the database images *according to the similarity* with the query image descriptor.
* **Image Features**
	* *Image descriptors or features:* allow to *describe and represent the image by quantities* (color, shape, regions, textures and motion) closer to the visual characteristics perceived by humans.
	* How to choose a *proper descriptor*?
		* The *descriptor* (or feature vector) should describe the image in a way that is *invariant to all the image changes* (color, illumination, noise, scale) that are suitable to our application.

### A particular kind of image descriptor (HOG)
* Discriminate by *global shape and appearance*
	* The image gradient at each pixel is a *vector with magnitude and direction*
		* ![[Pasted image 20240112132355.png|150]]
	* Would the *gradient magnitude* be a *good descriptor*?
		* *No, it is affected by illumination changes*
	* The **gradient direction** is not affected by this type of changes
* **Histogram of Oriented Gradients (HOG)**
	* The *gradient orientation* is an *angle* 
	* *Count occurrences* of gradient orientation in a patch 
	* Quantize to *8 bins*, each bins cover *45 degrees* $\longrightarrow \frac{360}{45}= 8$ 
	* We can use the histogram and a visual representation of the histogram
		* ![[Pasted image 20240112133147.png|300]]
	* *Algorithm to compute HOG*
		* *Divide the image* into small connected regions called cells. 
		* *Compute a local histogram for each cell* weighted by gradient magnitude. 
		* Simply *concatenate the histogram* of all the cells.
	* *Contrast - normalization*
		* Get invariance to changes in illumination and shadowing
		* Compute a *measure of intensity across a larger region* than a cell (a *block*) 
		* *Normalize* all cells within the block with this intensity value $\longrightarrow$ *L2 normalization*
		* ![[Pasted image 20240112134045.png]]
	* Can we say that the *HOG* is able to describe *local shape and appearance*?
		* YES!
	* Does the HOG descriptor carry information about the gradient or edge positions?
		* Local *object appearance and shape* within an image can be *described by the distribution of intensity gradients or edge directions*.
### Solving image retrieval
* *Given an image (query), find all similar images in the database*
	* Having the HOG descriptor, use a classifier to create a model able to separate the feature space contained in the descriptors of our images database
	* Classifier Example: K-Nearest Neighbor
* *For retrieval:* Database images do not necessarily have labels.
* *Sort based on distance/similarity*: $d(template, image)=d(HOG(template), HOG(image))$
### Pedestrian detection with HOG

* *Why is the problem difficult?* •
	* Wide *variety* of *articulated poses*
	* Variable *appearance*/clothing 
	* Complex *backgrounds* 
	* Unconstrained *illumination* 
	* *Occlusions* 
	* Different *scales*
* *Steps*
	* Compute *HOG descriptor* for all *training samples*
		* We get the: *Averaged positive examples*, *Predominant direction*, *Histograms of gradients*
	* Apply *correlation* with a *pedestrian template*
		* *Positive* weights show edge orientations *highly correlated with the pedestrians images*. 
		* *Negative* weights show edge orientations *non correlated* with image regions containing a pedestrian (*horizontal edges in the region of the legs*)
	* *Apply the sliding window technique all over the image* and compute the HOGs distances
	* Compute the *maximum over the distances*.
		* If there is a region highly correlated with the pedestrian template, we did a match