![[CV-2223_Class11_Image_Segmentation.pdf]]
![[U-NET_unwrapped.pdf]]

## Summary
- **U-net advantages**
	- *Flexible* and can be used for any *rational image masking task* 
	- *High accuracy* (given proper training, dataset, and training time) 
	- Doesn’t contain any fully connected layers 
	- *Faster than the sliding-window* (1-sec per image) 
	- Proven to be very *powerful segmentation tool in scenarios with limited data* 
	- Succeeds to achieve very *good performances on different biomedical segmentation* applications. 
- **U-net disadvantages** 
	- *Larger images need high GPU memory*. 
	- *Takes significant amount of time to train* (relatively many layers) 
	- *Pre-trained models not widely available* (it's too task specific) 
- **Mask-RCNN** – Still SoA for Instance segmentation
![[Pasted image 20240115030730.png|500]]
![[Pasted image 20240115030746.png|500]]
## Notes
### Transfer Learning
* **Taxonomy**
	* Advantages of ANN: 
		* *Self-learned high-level features represe*
		* *Modularity*
		* *Transfer Learning*
	* **Transfer Learning**
		* Ability of a system to r*ecognize and apply knowledge and skills learned in previous tasks* to novel tasks (*in new domains*)
		* Successful *models are immensely data-hungry* and rely on *huge amounts of labeled data* to achieve their performance.
		* A model is asked to behave in a new situation on tasks different from what it was trained for.
		* *Transfer Learning Methods*
			* *Understanding CNNs:*
				* *Lower convolutional layers capture low-level image features*, e.g. edges, while *higher convolutional layers capture more and more complex details*, such as body parts, faces, and other compositional features. 
				* *Classification is done by FC* layers that explain how edges and shapes are combined. 
				* For a *new task*, *use the off-the-shelf features of a state-of-the-art CNN pre-trained* on ImageNet and train a new model on these extracted features
			* *Fine-Tunning:*
				* Using the knowledge acquired in a domain an adapt it to a new one:
					* ![[Pasted image 20240115005053.png|350]]
		* *Taxonomy of Transfer Learning*
			* ![[Pasted image 20240115005159.png|500]]
			* *Domain adaptation*
				* *Learning from a simulation and applying the acquired knowledge to the real world* is an instance of transfer learning, 
				* As the feature spaces between source and target domain are the same, but the marginal probability distributions between simulation and reality are different. This difference diminishes as simulations get more realistic.
			* *Multitask learning:*
				* *Input*: A lot of labeled data in a source domain and the target domain that coincide. 
				* *Goal*: Classifying the target and source domain data simultaneously. 
				* *Assumption*: The source domain and target domain data share some common features, which can help classifying sharing knowledge. 
				* *Main Idea*: *To train simultaneously both tasks*. And *learning multiple objectives* from a shared representation.
				* *Generaliztion* by sharing the domain information between complementary tasks
				* ![[Pasted image 20240115013153.png|300]]
			* *Define importance of each task*
				* *Weighted uniformly the losses*
				* *Manually tuned the looses*
				* *Dynamic weighed of the losses*
			* ![[Pasted image 20240115013627.png|300]]
* **Example**
	* *Interesting problem*: Food recognition
		* *Challenges*
			* *Intra-class variations*
			* *Ambiguous definitions*
			* *Inter-flass similarituies*
			* *Mixed terms*
			* *Need for huge datset*
			* *Bad labeled*
			* ![[Pasted image 20240115012531.png|300]]
		* *Fine grained* recognition problem.
			* ![[Pasted image 20240115012618.png|300]]
		* *Datasets*
			* *Food 101*: 1000 images, 101 classes
			* *FoodX-251*: 140K images, 251 class
			* *Food1K*: 370K images, 1000 classes
		* Current results in this tasks are relatively low compared the ones used in non-specific object detection tasks.
		* The food recognition allow to share domain information between complementary tasks
			* ![[Pasted image 20240115014228.png|400]]
		* Using multi-task learning in food recognition
			* *Estimating food category, ingredients, cuisine type, dish name*
			* The *loss is a weighted sum* of each individual task loss
			* ![[Pasted image 20240115014751.png|500]]
### Image segmentation
- Image segmentation has been one of the trending topics in CV research in the recent years
- **Semantic**
	- *Assign a category to every pixel in the image*
	- ![[Pasted image 20240115015538.png|100]]
	- Not strict assignation of a concrete class to the pixels
	- We need every pixel labelled in the ground truth
	- ![[Pasted image 20240115015810.png|400]]
	- It helps to solve other tasks such as 
		- *monocular depth estimation*
		- *road scene understanding*
		- *To help partially sighted people by highlighting important objects in their glasses*
		- *robot object manipulation*
		- *medical analysis*: segmentation of tumors, dental cavities, ...
	- Classical segmentation methods:
		- *Active contour*
		- *Canny edge detector*
		- *Histogram-based methods* $\longrightarrow$ selective search
	- Nowadays semantic segmentation is based on *Deep Learning*
	- Examples of tasks
		- ISBI 2012: Predict the class label of each pixel, Stacks of *Electron microscopy (EM) images*
			- The winner t*rained a network in a sliding-window (local region (patch) around that pixel)* 
			- The network can localize, the training data in terms of patches is much larger that the number of images
			- Is a slow method because each patch should be passed through the network.
			- ![[Pasted image 20240115021414.png]]
		- SBI 2015- separation of touching objects of the same class
			- Light microscopic images (recorded by phase contrast microscopy)
- **Image Segmentation with U-net**
	- U-net learns segmentation in an *end-to-end setting*
	- *Touching objects of the same class*
	- *Uses very few annotated images* (approx. 30 per application)
	- It combines localization and the use of context at the same time.
	- *\# of parameters learned by convolution layer* is  $\longrightarrow$ $𝒏𝟐𝑵𝑴$
	- *Group convolutional layer*
		- *Input and kernel are split into 𝒈 groups* across channel dimension 
		- *Each group then performs* the convolutions *independently*
			- ![[Pasted image 20240115022519.png|500]]
	- How to **recover the original size** after a convolution?
		- *Dilation*: **deconvolutional layers** (backwards convolution).
		- Although it uses *additional memory* and *learning parameters*
		- ![[Pasted image 20240115023008.png|200]]
		- *Inserts spaces between the kernel element* to increase the effective size of kernel 
		- Same as the convolutional layer except it has *additional parameter, dilation rate, that controls the spacing*
		- Each layer is defined using following parameters: 
			- \# Input channels ($C_1$) 
			- \# Output channels (#C_2) 
			- Kernel size ($w_1\times h_1$) 
			- Padding 
			- Stride 
			- *Dilation rate* $(𝑟)$
		- ![[Pasted image 20240115023323.png]]
	- **U-Net architecture**
		- ![[Pasted image 20240115030625.png]]
	- *Trainins U-Net*
		- *Activation and Loss function:* Softmax and Categorical Cross Entropy 
	- *Problems:* early layers not semantic, *late layers lose fine details infomration*
	- *Skip conections* solve the problem of information loss.
		- ![[Pasted image 20240115023641.png|300]]
	- *Additional techniques*
		- *Data augmentation* by doing *deformations*
			- Random elastic deformation of the training samples. 
			- Shift and rotation invariance of the training samples. 
			- They use random displacement vectors on 3 by 3 grid. 
			- The displacement are sampled from Gaussian distribution with standard deviation of 10 pixels
- **Instance**
	- When we try to *identify and segment the specific important objects* in an image
	- We can use architectures like *Mask R-CNN*
		- It replaces the ROI Pooling module with a more *accurate ROI Align module*. 
		- Additional *branch that predicts the actual mask of an object/class*
		- ![[Pasted image 20240115024243.png|200]]
		- Faster R-CNN/Mask R-CNN leverages a Region Proposal Network (RPN) to generate regions that potentially contain an object. 
		- Each of the regions is ranked based on its “objectness score” (i.e., how likely it is a given region could contain an object), and the top N regions are kept (N=300 based on He 2017). 
		- *Each of the N most ROIs goes through the 3 branches* 
			- *Label prediction* 
			- *Bounding box prediction*
			- *Mask prediction*
		  - *Output*:
			  - Mask size is $15 \times 15$ 
			  - During prediction, keep the top 100 detection boxes 
			  - L is the number of class labels in the dataset (i.e, 90): 
			  - Output from the mask module will be $100 \times 90 \times 15 \times 15$
			  - After performing a forward pass we can loop over each of the detected bounding boxes, find the class label index with the largest corresponding probability, and use index lookup 
			  - After performing the lookup we now have instance Mask, a $15\times15$ mask that represents the pixel-wise segmentation of the $i-th$ detected object.
			  - Scale the mask back to the original dimensions using *nearest neighbor interpolation*. 
			  - Why nearest neighbor interpolation? *nearest neighbor interpolation will preserve all original values of the image during resizing without introducing new values*. While nearest neighbor interpolation is less appealing to the human eye, such as bilinear or bicubic interpolation, for example
			  - ![[Pasted image 20240115025927.png|400]]
- **Panopic**
- **Evaluation**
