### 2022

* **Question 1.** Define the convolution. What is it definition and for what purposes it is used? Give 2 examples of operators for image processing using convolutions and explain their purpose and constraints.
	* *Answer*: A mathematical operation that *combines two functions to produce a third function*. In image processing, it involves *overlaying a kernel (a small matrix) onto an image and computing the sum of the products of the overlapping elements*. The kernel *moves across the image*, performing this operation at every location, resulting in a new, transformed image. Used to *enhance or extract information from the original image*.
	* The *main purposes* of convolution in image processing are:
		* - *Edge Detection*: highlighting the edges in an image.
		- *Image Smoothing and Noise Reduction*: certain kernels can blur an image, helping in reducing noise and minor imperfections.
		- *Feature Extraction*:  identify specific characteristics in an image (textures or specific shapes.)
	- *Examples*
		- - **Sobel Operator**:
		    - *Purpose*:  edge detection. It works by emphasizing edges in different orientations, typically horizontal and vertical.
		    - *Constraints*: sensitive to noise and it doesn't capture edges that are not vertical or horizontal.
		- **Gaussian Blur**:
		    - *Purpose*: image smoothing and noise reduction.
		    - *Constraints*: if not used carefully it can be loss of important details. The extent of blurring is controlled by the standard deviation.
* **Question 2.** What is the Canny edge detector? How is it defined and what are its advantages and disadvantages with respect to other edge detectors?
	* *Answer:* Algorithm in image processing for *edge detection*. It is a *multi-stage algorithm* designed to detect a wide range of edges in images effectively. Steps:
		1. **Noise Reduction**: smoothed using a Gaussian filter to reduce noise
		2. **Find magnitude and orientation of gradient**: filtering with a Sobel kernel in both horizontal and vertical directions to get the first derivative.
		3. **Non-Maximum Suppression**:  edges are thinned by applying non-maximum suppression, retains only the points that are local maxima in the direction of the gradient.
		4. **Hysteresis Thresholding**:  suppressing all the edges that are weak and not connected to strong edges. 
	- *Advantages*: Accuracy, Good at Noise Suppression, Edge Localization (non-max sup + hysteresis)
	- *Disadvantages*: *computationally more intensive* than simpler methods like the Sobel. *Focuses on local changes* and it *has no semantic understanding*. *Parameter Sensitivity*.Difficulty in Detecting Weak Edges*
	- *Comparisons*
		1. **Sobel Operator**: simpler and faster but less accurate, especially in noisy environments.
		2. **Prewitt and Roberts Operators**: simpler but do not perform as well in terms of noise suppression and edge localization.
		3. **Laplacian of Gaussian (LoG)**:  is more sensitive to noise compared to the Canny detector and does not include the concept of hysteresis thresholding.

* **Question 3.** Which methods for template matching do you know? What is their definition and their properties?
	* *Answer*: 
		* *Sum Square Difference*: measures disparity between templare and target computing SSD of pixel intensities at each position. No robust to local changes in brightness$$h[m,n] = \sum_{k,l} (g[k,l] - f[m+k,n+l]){^2}$$
		* *Convolutional Filtering:* the template is compared with the target image by sliding it over the target image and calculating the cross-correlation score for each position. The position with the highest score indicates the best match. Needs image normalization. Sensitive to noise. $$h[m,n] = \sum_{k,l} (g[k,l])(f[m+k,n+l])$$ $$h[m,n] = \sum_{k,l} (g[k,l])(f[m+k,n+l]-\bar{f})$$
 
		* *Normalized Cross correlation:* improvement over simple cross-correlation, normalizing the scores based on the intensity variations, thus making it more robust to changes in lighting and contrast. ![[Pasted image 20240112125440.png|400]]
	* *Comparison*
		*  *Sum Square Difference:* fast, but sensitive
		- *Correlation:* less sensitive to illumination
		- *Zero-mean correlation:* less sensitive to mask values
		- *Normalized Cross correlation:* less sensitive to mask variance
	
* **Question 4.** What is the dimensionality of the HOG descriptor corresponding to? How do you construct a HOG descriptor and what are its purposes in image analysis?
	* *Answer:* (HOG) descriptor is a feature descriptor. The dimensionality of a HOG descriptor corresponds to the *number of bins in the histograms of oriented gradients*, (typically 8 bins covering 45° each) which are calculated over specific regions of an image. So $N$ orientation binsand $n$ number  of cells vertically and $m$ number of cells horizontally the dimension of the descriptor would be $N\times n\times m$
	* *Process:*
		* *Divide the image* into small connected regions called cells. 
		* *Compute a local histogram for each cell* weighted by gradient magnitude. 
		* Simply *concatenate the histogram* of all the cells.
		* *Block normalization:* Compute a *measure of intensity across a larger region* than a cell (a *block*) *Normalize* all cells within the block with this intensity 
* **Question 5.** Explain the main steps of the Eigenface analysis? What is the use of the eigenvectors and eigenvalues?
	* *Answer*: It involves using Principal Component Analysis (PCA) to reduce the dimensionality of large face image datasets
	* *Process:*
		* *Image preparation*: all faces grayscale. Resize and Aling faces
		* *PCA*
			* *Compute the average face* (mean of data)
			* *Substract* the average face from all others in the data
			* *Covariance Matrix* computation
			* Compute eigenvalues rank them with their corresponding eigenvectors (*eigenfaces*).
			* Each face in the data can be *represented as a linear combination* of the eigenfaces
		* Use Face recognition
* **Question 6.** What is a CNN? Explain why it is a) convolutional, b) neural, and c) deep network. What is the loss function? What loss functions do you know and what is their difference? What is the purpose of a loss function in a CNN and how is it used in the training process?
	* *Answer:*   A Convolutional Neural Network (CNN) is:

	- *Convolutional*: Uses convolutional layers to efficiently capture spatial relationships in image data through filter operations.
	- *Neural*: Based on artificial neurons with learnable weights and biases, mimicking the human brain's processing.
	- *Deep Network*: Contains multiple layers that enable learning of hierarchical feature representations.

	- **Loss Function**:
		- *Purpose*: Quantifies the difference between the model's predictions and actual targets, guiding the training process.
		- *Common Types*:
		    - *Mean Squared Error (MSE)*: For regression tasks.
		    - *Cross-Entropy Loss*: For classification tasks (binary or multi-class).
	- **Use in Training**: Directs model optimization by minimizing the loss through adjusting network parameters.
* **Question 7.** What is the Yolo CNN? Explain the pseudo-algorithm of Yolo. What are its advantages and disadvantages with respect to the RCNN?
	* *Answer*: The YOLO (You Only Look Once) CNN is a fast, real-time object detection system.
	* **Pseudo-Algorithm**:
		1. **Resize** the input image.
		2. **Divide** the image into a grid.
		3. **Predict** bounding boxes (with confidence scores) and class probabilities for each grid cell.
		4. **Discard** low-confidence boxes.
		5. **Apply** non-maximum suppression to refine bounding boxes.
	* *Advantages over R-CNN*
		- *Faster*: Single pass detection, ideal for real-time applications.
		- *Global Context*: Considers entire image during detection, reducing background errors.
	- *Disadvantages with R-CNN*:
		- *limited the number of nearby objects* that model can predict
		- *Less Flexible*: In handling varying object sizes and aspect ratios.  
		- *Struggles to generalize to objects in new or unusual aspect ratios*
* **Question 8.** Regarding the Bag-of-Words method, is the k-means algorithm used and why? How do you validate the Bag-of-Word object recognition?
	* *Answer:* , k-means clustering is used to group extracted local features into clusters, forming a vocabulary of "visual words". It reduces the complexity of feature space and creates a standardized representation across different images.
	*  Cross-validation, using metrics like accuracy, precision, recall, and F1-score derived from a confusion matrix. 
* **Question 9.** What is the difference between the Deep learning methods applied for object recognition and image segmentation? How do you validate the semantic segmentation methods?
	* *Answer:* Deep learning for object recognition involves *identifying and classifying objects in an image*, often *providing their locations with bounding boxes* using CNN. In contrast, image segmentation, specifically *semantic segmentation, classifies each pixel into a category, providing detailed, pixel-level segmentation*, using models like FCNs or U-Net.
	* Semantic segmentation methods are validated using metrics like *pixel accuracy, Intersection over Union (IoU), and Dice Coefficient*. Techniques like cross-validation and visual inspections, comparative analysis with other models.
* **Question 10.** Indicate three methods for object detection using Deep learning. Make a comparison between them.
	* *Answer:* In deep learning for object detection, R-CNN excels in accuracy but is slow, YOLO is very fast but less accurate for small or clustered objects, and SSD balances speed and accuracy, performing well across various object sizes. YOLO and SSD are more suited for real-time applications, while R-CNN is preferred when high accuracy is essential.
	* R-CNN is preferred for applications where accuracy is paramount. YOLO is ideal for real-time processing. SSD is a good compromise when both speed and accuracy are needed.

### 2020

**Question 1.** Define the Mean Filter and explain which is the main parameter of the filter. How does changing the values of the parameters affect the smoothing functionality?

**Question 2.** What are the advantages of HOG over template matching algorithm? Explain the main differences between the descriptors HOG and SIFT. Give some examples of Computer Vision problems which can be solved using them?

**Question 3.** Which are the main steps in the panoramic image creation? Explain the details of every step and specify the methods that can be used for them.

**Question 4.** Define the Integral Image used by Viola & Jones method and explain why it is useful. In the Viola & Jones method, what are cascade of classifiers useful for? Indicate the main steps of Viola & Jones method.

**Question 5.** Explain the main differences between PCA and LDA. What are these methods useful for? Can we say that one of the methods is better than the other? Justify the answer.

**Question 6.** What is a CNN? Explain why it is a) convolutional, b) neural, and c) deep network. What is the loss function? What loss functions do you know and what is their difference? What is the purpose of a loss function in a CNN and how is it used in the training process?

**Question 7.** Define and compare different texture descriptors you know. What Computer Vision problems can be solved using texture descriptors?

**Question 8.** Regarding the Bag-of-Words method, what is the purpose of the spatial histograms and how do you use it to construct image descriptors. How do you apply it in case of multi-class object recognition? How do you validate the Bag-of-Word object recognition?

**Question 9.** What is the difference between the Deep learning methods applied for object recognition and image segmentation? How do you validate the semantic segmentation methods?

**Question 10.** Indicate three methods for object detection using Deep learning. Make a comparison between them.

### 2018

**Question 1.** Explain what Prewitt and Sobel operators are useful for and what it is the difference between these operators

**Question 2.** Let r1 and r2 be the autovalues associated to the autocorrelation matrix at a certain point. How can you know if the point is significative?

**Question 3.** Explain the main steps in the panoramic image creation. Give the main idea of the methods which are applied in each of the steps.

**Question 4.** Define the Integral Image used by Viola & Jones method and explain why it is useful. In the Viola & Jones method, what are cascade of classifiers useful for?

**Question 5.** Explain the main differences between PCA and LDA. What are these methods useful for? Can we say that one of the methods is better than the other? Justify the answer.

**Question 6.** What is the difference between top-down and bottom-up segmentation? Give some examples in which context and what kind of objects you would segment with top-down and in which - with bottom-up segmentation approaches. Which methods do apply better the Gestalt principles? What disadvantages do you see to each of both strategies (top-down and bottom-up)?

**Question 7.** What is the difference and resemblance of Local Binary Patterns compared to the Bank of filters based on Derivatives of Gaussian? What advantages and disadvantages do you see for both approaches? What parameters do they have and how these determine the behavior of the technique?

**Question 8.** What problem is the BOW method solving? How are the words and the vocabulary obtained? How does the size of the vocabulary affect the performance of the algorithm?

**Question 9.** What are the CNNs? What kind of layers can they have? What are the parameters of the CNN? What is the depth of a CNN and how it affects the performance of the algorithm?