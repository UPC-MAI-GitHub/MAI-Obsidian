![[CV-2324_Class8_Object detection.pdf]]
## Notes
* **Algorithms**
* In the recent years, *CV research* have been pretty mush about *Object detection/Recognition/Segmentation*
* *Object detection*
	* This task involve the *identification of the class* or classes of some objec/s present in an image
	* It also involves the *spatial localization* of the objects typically using a box to frame it.
	* The *object detection task*
		* A common approach to this problem is the use of a *CNN with a Fully Connected Layers* having in the final layer *2 output heads* one for the *classification* part, and the other for he *localization*.
			* ![[Pasted image 20240113210924.png|300]]
		* To be able to recognize just one object per image our output would be $4+c$ or $4 + c + 1$
			* This containing the box location of the bounding box using the $x,y$ coordinates of the upper left and bottom right corners,  (this make *4* numbers), then $c$ is representing the number of classes  $[ax,ay,bx,by, c_1,...,c_n,P]$ if we have the $P$, we are using the $4 + c + 1$ version of the label that indicates if it is an object present or not usning the value of $P$. If this value is equal to *one* then all other values should contain info, if this value is *zero* then all other values are *don't cares* 
			* ![[Pasted image 20240114024240.png|300]]
		  - To make the network able to recognize multiple object of the same category or multiple objects of different we can use the *anchor box* approach where we define *multiple anchor boxes per location* in the image and estimate in there is an object of the trained classes in some of the anchor boxes, this approach would produce multiple detection's per object so we use the *non-max suppression* technique to get the final predictions. So the labels on training images should be $[N\times[ax,ay,bx,by,c_1,...,c_{n,}P]]$  where $N$ is the number of objects present in the image
			  - ![[Pasted image 20240114024309.png|500]]
		  - *This can be done is also called object detection proposals*
			  - ![[Pasted image 20240114024445.png|250]]
  - **Datsets**
	  - There are multiple datasets to train models for object detection
		  - *MS Coco*: 80 object catergories, $>200K$ labelled images
		  - *PASCAL VOC*
		  - *Others*
- **Architectures**
	- **R*-CNN*
		- ![[Pasted image 20240114024822.png|400]]
		- R-CNN combines *CNN* with *region proposals* techniques
		- This is a *2 stages* methodology
			- *First stage:* 
				- *Generate* category independent *proposals*, $>2000$  per processed image
					- This is get by using a *selective search* strategy which is a *Hierachical Grouping* approach were similar regions are joined based on colour, texture, size, and shape compatibility.
					- At each iteration, larger segments are formed and added to the list of region proposals in a bottom-up approach.
			- *Second stage:* 
				- *Extract the fixed-length vector* (4096-dimensional) from the output feature map *based on each region proposal location* (This saves computations are we are not looking all possible windows for an object, only those where there is a region proposal)
					- In order to extract the vector, *process the image with a Convolutional Neural Network* (only the CNN part) with each region proposals to get the predefined size tensor of feature maps from the last CNN layer
					- Before to passing to the prediction process regression process the extractions are re-scaled to a fixed $n \times n$ size while maintaining the previously fixed depth (4096). 
				- A *prediction process* is performed, originally a group of SVMs to get the categories *classification* and separately the region proposal extractions as processed in a *regression* models to get the objects location.
					- In this process *non-maximal suppression* is applied to keep the best predictions 
			- ![[Pasted image 20240114025719.png|300]]
		- *Disadvantages*
			- *Huge amount of time to train and run* mainly because of the huge amount of proposals (>2000) to  generate (selective search) and process (CNN). *Not real-time* usable (around 47 seconds to process a prediction).
			- *Selective search* is not a learning algorithm so it *doesn't improves over training*.
			- It has to *train three different models separately* - the *CNN to generate image features*, the *classifier* that predicts the class, and the *regression model* to tighten the bounding boxes. This makes the pipeline extremely hard to train.
	- **Fast R-CNN**
		- Introduces a methodology to share computation process for all region proposals *No need to recompute features for every box independently*
			- ![[Pasted image 20240114034403.png|300]]
			- With this method we save computation *processing all the proposals all at once* (*Convolutional Sliding Window algorithm*) and using a *Multi-Layer Perceptron* with two heads to make the *classification* and *regression* parts.
				- *Classification head:* softmax probability estimates over $K$ object classes plus a catch-all “background” class 
				- *Regression head:* another layer that outputs $4\times K$ real-valued numbers: $4$ for each of the $K$ object classes.
			- As shown in the first image, while we share computation in the feature extraction, we sill need to perform the prediction class per *Region of Interest (RoI)* proposal.
				- *RoI pooling layer:* Max pooling to *convert the features inside any valid region* of interest (region proposal) *into a small feature map with a fixed spatial* extent of $H\times W$
					- ![[Pasted image 20240114035618.png|200]]
		- *Multi-task Loss*
			- Due to the nature of the task the labels are the ones used for object detection, that means $[N\times[ax,ay,bx,by,c_1,...,c_{n,}P]]$ here the $N$ could be either the number objects or the number of divided anchor boxes defined in the model. The we have an *appropriate loss function* to deal with this type of data. 
				- ![[Pasted image 20240114041313.png|400]]
			- *Multi-task loss $L$* on each labeled RoI to jointly train for *classification* and *bounding-box regression*: also proved a task influence, so multitask help training.
				- ![[Pasted image 20240114041553.png|400]]
		- *Architecture overview*
			- ![[Pasted image 20240114041901.png|600]]
		- *Improvments*
			- *Fast R-CNN replaced the one-vs-rest SVM* classifiers with a *softmax layer on top of the CNN* to output a classification (*introduce competition among classes*).
			- *Adds a linear regression layer* parallel to the softmax layer to output bounding box coordinates.
		- *Results*
			- Is reduces drastically training and test time
				- *Train approx 10 times less*
				- *Test, up to 100 times less*
	- **Faster R-CNN**
		- This improved version *gets rid of the selective search* to perform the region proposals. Instead the *CNN* is used to first *propose region estimations* and *then* perform the usual *Fast R-CNN prediction* part.
		- *Faster R-CNN* adds a *Fully Convolutional Network* on top of the features of the CNN creating the *Region Proposal Network (RPN)*. 
			- Timing : 10ms per image for the proposal vs 2s of the selective search
				- ![[Pasted image 20240114042919.png|350]]
		- The *RPN* works as an attention mechanism that indicates *Fast R-CNN* where to look (make predicitons)
			- At each sliding-window location (center of the window called anchor), we simultaneously *predict multiple k region proposals*, called *anchor boxes*, with *different sizes and aspect ratios* (k=9, 3 sizes and 3 ratios)
			- For a feature map of a size $W\times H$ (typically ∼2,400), there are $W\times H\times k$ *anchors in total*
				- ![[Pasted image 20240114043458.png|300]]
			- *RPN Loss*:
				- Similar to the one used in *Fast R-CNN* but this time just a binary element for the classification part as the *RPN* is only intended to identify if *there is object ot not*, not in predict the object's class.
				- The regression loss is activated only for positive anchors $p*_i=1$ and is disabled otherwise $p*i = 0$
				- ![[Pasted image 20240114044224.png|400]]
		- *Trainins process:* (There are 2 options, here is the most used)
			1. CNN network is initialized with an ImageNet-pre-trained model, RPN fine-tuned end-to-end for the region proposal task. 
			2. Train a separate detection network (same on Imagenet) by Fast R-CNN using the proposals generated by the step-1 RPN 
			3. Use the detector network to initialize RPN training fixing x the shared convolutional layers and only fine-tune the layers unique to RPN 
			4. Keeping the shared convolutional layers fixed, we fine-tune the unique layers of Fast R-CNN
		* *Results*
			* Approx *10 times faster* than *Fast R-CNN*
		* *Mask R-CNN*
			* Adds extra ouput heads to perform *object/instance segmentation* over images (proper labels needed for training)
				* ![[Pasted image 20240114045008.png|400]]
	* **YOLO**
		* *Idea*: No bounding box proposal.
		* Introduces a *One stage* methodology
		* A single regression problem, *straight from image pixels to bounding box coordinates and class* probabilities.
			* ![[Pasted image 20240114045330.png|400]]
		* *This system models detection task as a regression problem. It divides the images into an $S\times S$ grid and for each grid cell predicts $B$ bounding boxes, a confidence value for those boxes, and $C$ class probabilities. This predictions encoded as an $S\times S \times (B\times 5 + c)$ tensor.* (**From YOLO paper**) 
		* *General idea*
			* Divide the image into $7\times 7$ cells. 
			* Each cell trains a detector. 
			* The detector needs to predict the object’s class distributions. 
			* The detector has $B$ bounding-box predictors to predict bounding-boxes and confidence scores.
			* ![[Pasted image 20240114050324.png|300]]
		* Each grid cell also predicts $C$ *conditional class probabilities*, $Pr(Class_i|Object)$, regardless of the number of boxes $B$.
			* At test time *conditional class probabilities* and *individual box confidence* predictions are multiplied to *decide if there is an object or not* in the region
				* ![[Pasted image 20240114050754.png|500]]
		* *Loss function*
			* One predictor to be “responsible” for predicting an object based on which prediction has the highest current IOU with the ground truth. 
			* This leads to specialization between the bounding box predictors.
			* *Each predictor gets better at predicting certain sizes, aspect ratios, or classes of object, improving overall recall.*
				* ![[Pasted image 20240114051314.png|400]]
		* *Training process*
			* *Pretrain first 20 convolutional layers* on the ImageNet 1000-class competition dataset. 
			* *Add* four *convolutional layers* and two *fully connected layers* with randomly initialized weights. 
			* *Optimize sum-squared error*, but it weights localization error equally with classification error which may not be ideal => introduced parameters to weight.
			* Many grid *cells do not contain any object pushing the “confidence” scores* of those cells towards *zero*, often overpowering the gradient from cells that do contain object
		* *Advantages*
			* *Extermely Fast*
				* Since the whole detection pipeline is a single network, it can be optimized end-to-end directly on detection performance ~ *45 fps, real time*
			* Learn *Generalizable representations*
		* *Limitations*
			* *Each grid cell only predicts B boxes and can only have one class* (limits the number of nearby objects that model can predict) 
			* It s*truggles to generalize to objects in new or unusual aspect ratios* or configurations 
			* Loss function treats errors the same in small bounding boxes versus large bounding boxes (partially addressed using square roots).
		* Several *YOLO new versions* have been released since the original publications with a lot of *improvements*
	* **SSD**
		* *Single Shot Detector* is an architecture with a similar idea to *YOLO*
			* It also uses *Data augmentation* and *Hard Negative Mining*
			* ![[Pasted image 20240114052559.png|300]]
		* A *One stage* strategy
			* *Based on a standard architecture (VGG)* used for high quality 
				* Add convolutional feature layers to the end of the truncated base network, allowing *predictions of detections at multiple scales.*
		* *Default boxes* are *similar* to the anchor boxes used in *Faster R-CNN*, but *applied to several feature maps of different resolutions*
		* *Matching strategy*
			* Difference training SSD vs Typical Detector withregion proposals, is that *ground truth information needs to be assigned to specific outputs* in the fixed set of detector outputs: -
			* Need to determine which default boxes correspond to a ground truth detection and train the network accordingly.
			* *Matched* each ground truth box to the default box with the best *Jaccard overlap,* 
				* Then match *default boxes to any ground truth with Jaccard overlap* higher than a threshold (0.5).
			* Overall objective loss fucntion
				* ![[Pasted image 20240114053601.png|400]]
		* *Hard Negative Mining*
			* *Imbalance Issue*: *Excessive negative predictions* compared to actual objects. 
			* SSD's Approach: *Sorts negatives by confidence loss and selects those with the highest loss*.
			* Balanced Ratio: *Maintains* a maximum *3:1 ratio of negatives to positives*. 
			* Outcome: *Enhances training speed and stability*.
		* *Advantages*
			* The *matching strategy* simplifies the learning problem, allowing the network to *predict high scores for multiple overlapping default boxes* rather than requiring it to pick only the one with maximum overlap.
		* *Limitations*
			* Sensitive to the bounding box size. 
				* Much *worse performance on smaller objects than bigger objects* (small objects may not even have any information at the very top layers)
* Thanks to the usage of *transformers, DETR* has a simpler architecture and does not need post- processing on the outputs.
* **Evaluation**
	* It uses *Intersection over Union (IoU)* to measure the quality of the localization estimations versus the ground truth label
		* If the *IoU* is over a given threshold then the prediction is a true positive, but *choosing the threshold can be quite tricky* so to see how the model works along multiple thresholds the *average precision process* is applied.
			* ![[Pasted image 20240114032649.png]] ![[Pasted image 20240114032706.png|350]]
	* Validation is done using the *Mean Average Precision (mAP)*
		* mAP metrics calculates the average precision (AP) for each class individually across all of the IoU thresholds. Then the metric averages the mAP for all classes to arrive at the final estimate.
		* Draw a *series of precision recall curves with the IoU threshold set at varying levels* of difficulty (90%, 80%, etc)
		* ![[Pasted image 20240114033239.png|400]]
		* 