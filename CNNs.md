![[CV-2324_Class7_CNNs.pdf]]

## Notes
### AI, Machine Learning & Deep Learning
* **Related fields to the topic of Convolutional Neural Networks**
	* *Arificial Intelligence*
	* *Machine Learning*
	* *Deep Learning*
	* *Data Science*
	* *Others*
*  In the recent years a lot of research in the AI field, and specifically about Convolutional Neural networks
* CNN are being used in most of the learning paradigms: *Supervised*, *Unsupervised*, *Reinforcement* learning
* Object recognition has raised a lot of research, still nowadays topics of *computer vision cover a wide variety of the AI research*
* ![[Pasted image 20240113020915.png|200]]
- *Deep Learning - Where does it comes from?*
	* *History of CNNs*
		* 1943 McCulloc and Pitss - neural model with a circuit
		* 1958 Rosemblatts perceptron
		* 1959 Adeline 
		* 1986 back propagation
		*  *1998 AT&T Bell Laboratories on digit recognition resulted in good accuracy in detecting handwritten postcodes from the US Postal Service using CNNs.*
* Nowadays we have the important *factors to succeed in several CV tasks*: 
	* *Data*
		* Tons of data are collected daily
		* Also, several big labeled datasets have been already created for multiple tasks
		* Datasets around the tens of millions of instances
	* *Computation resources*
		* The hardware has evolved and provided great results in the efficiency of how computations are made
		* This contributes in general to the power of computation available to create models (*GPUs*, *TPUs*)
	* *Models*
		* Several tasks of CV has had an incredible evolution with amazing results in the efficacy of algorithms solving them
### What is a Convolutional Neural Network? 
* *Classical Methods* vs *Deep Learning* in Cv tasks
	* ![[Pasted image 20240113022134.png|500]]
* The learning process:
	* It involves creating a method able to receive a data point process it ans estimate and output related to the input in some way
	* Fitting a model to the data involve a parameter search and evaluate the performance according to specific metrics.
	* For classification task: The model is intended to find a hyperplane to separate the classes present in the data
		* Usually it involves a score function, a loss function and a optimization process.
		* With images, project data involves to adjust models to be able to manage the nature of images
* **CNNS**
	* Where presented with an important application in 1998 by LeCun using them to solve a problem of handwritten characters recognition
	* Since then a lot of evolution to this algorithm has happened
		* More layers
		* New layer types
		* New optimization methods
		* New training processes
	* From 1998 to 2012 CNNs were not too successful until due to the IMAGENET change the potencial of this algorithm was showed
	* CNN involves several *layer types*
		* *Convolutional layers*: in charge of feature extraction from the images by applying several filters iteratively
		* *Pooling layers*: in charge of dimensionality reduction and preserving the important features
		* *Non-linear activation layers*: as with ANN this layers introduces no linearity to the response of the layer so it allows to attack non-linear separation problems
		* *FC layers*: At the end of the CNN a MLP (fully connected layers) are used to make the classification process.
	* The *weights in CNNs* (*Convolutional filters*) are matrices which are used in the convolutional process of the network
		* ![[Pasted image 20240113023915.png|300]]
	* Several CNN famous architectures were proposed due to the: SVRC IMAGENET challenge
		* AlexNet
		* GoogLeNet
		* VGG
		* MSRA
		* ResNet
		* ![[Pasted image 20240113024321.png|300]]
* **Loss function and Optimization**
	* For Binary classification we can use *Binary Cross-Entropy*
	* For multi-class classification we can use *Cetegorical Cross Entropy*
	* Tor multi-label clasification we can use *Binary Cross-Entropy* per output in the network
	* The optimization algorithm commonly used is *Gradient Descent* that using back propagation it accelerates the computation of gradients
		* This computation help us to identify how each variable (weight) incluence the loss
		* The main goal of the optimization is being able to reach the global maxima in the parameter space
		* Other used optimization algorithms
			* *Momentum SGD*
			* *ADAM*
			* *Adagrad*
	* When monitoring performance
		* We have to be aware about overfitting and underfitting
			* ![[Pasted image 20240113030120.png|350]]
			* Ways to *reduce overfitting*:
				* *Reduce the number of parameters*
				* *Introduce weight decay*
				* Early stopping
				* *Data augmentation*
				* Others: *dropout, batch normalization*
	*  *Benefits of CNNs*
		* *Transfer learning:* convolutional filters learned in some task for extracting general features can be reused to fit a model for a similar task, saving computational cost, and time
		* Loss function and Optimization
		* Binary classification uses binary cross entropy
		* Multi-class  classification we use single label classification
		* multi-label classification uses binary cross entropy, one per class
		* Minimize loss function
		* Optimization is done by gradient descent and retro propagation using a learning rate to verify thel amount of charge in the parameters
		* optimization methods include: sgd, momentum SGD, ADAM, 
		* Monitoring Loss and accuracy
		* We have to take care about overfitting and underfitting
		* reduce overfitting we can reduce parameters or weight decay, early stopping, dropout
	* *Trends in DL*
		1. *Transfer Learning*: The use of pre-trained models and transfer learning techniques was becoming more widespread, as they can significantly reduce the amount of data required to train effective models.
			* Multi-task learning 
		2. *Uncertainty modeling:* refers to the process of quantifying and managing uncertainty or ambiguity in the predictions or decisions made by machine learning models 
			* Uncertainty-aware MTL 
			* Learning with noisy labeling 
		 3. *Self-Supervised Learning*: methods train models on unlabeled data, which can be particularly useful in cases where labeled data is scarce. 
		4. *Meta-Learning*: Meta-learning techniques were explored to enable models to learn how to learn, which can lead to faster adaptation to new tasks. 
			* Continual learning 
		5. *Generative AI* and Generative Adversarial Networks (GANs): GANs were being used for a variety of applications, from image generation to data augmentation and domain adaptation. 
			* Uncertainty-aware data augmentation 
			* NeRFs 
			* Stable diffusion
		6. *Efficiency and Model Compression*: There was a growing interest in making deep learning models smaller, faster, and more energy-efficient, particularly for edge computing and mobile applications. 
			* Scaling by hierarchical DL models 
			* Fine-grained recognition 
		7. *Multimodal Learning*: Combining information from different sources, such as text and images, to create more comprehensive models for understanding and generating content. 
			* Oncology, Food ontology 
		8. *Explainable AI (XAI)*: The need for understanding and interpreting deep learning models became more critical, especially in fields like healthcare and finance where model explainability is crucial. 
			* Robust Explainable models 
		9. *Federated Learning:* This approach allows for training models across decentralized data sources without sharing raw data, preserving privacy. It gained traction, particularly in applications involving sensitive or proprietary data. 
		10. *AI for Healthcare*: Deep learning was increasingly applied to medical image analysis, drug discovery, and patient diagnosis, with a focus on improving healthcare outcomes. 
			* Our projects: food data analysis, omics data,
			    
* *About DL and CNNs*
	* Nowadays everybody is doing deep learning
	* DL need data resources and models
	* A lot of data is available nowadays
	* Labeled Datasets are important to be able to train CNNs 
	* Real Data 
	* Simulated data
	* not only more datasets but also bigger ones with a lot of variety in the cases they contain 
	* ImageNet has been a break point for datasets creation 
	* Also the increase in the computational power (GPUs) has contributed a lot to the DL success
	* what is NN
	* white ANN there is no more hand-crafted feature extraction
	* After the automated feature extraction, the classification process start. 
	* The overall performance is evaluated with a score function 
	* the score function tries to distribute the probability between clases 
	* Protect data in the feature space 
	* image classification we can convert likelihood (nor necessarily sum up to 1) to probabilities (sum up to one)
	* Layers allow to don’t have a linear representation of our data, we compute 
	* Deep learning has neural network architectures with a large amount of layers
	* The activation functions are important to estimate non linear properties in data 
	* What CNNS propose is extract information in a more intelligent way for images, trying to keep spatial information. This also produce a reduction in the number of parameters allowing us to introduce more layers.
	* we can mix convolution layers, other kinds like pulling layers or activation function, also with normalization layers 
	* Training a CNN consist in systematically update hyperparamers in a way it allows the necessary features to classify images between the present classes in the training data. 
	* Here the parameters are the learned convolutional filters 
- *Applications*
	- object recognition
	- lip reading
	- high-end surveillance
	- facial recognition
	- object-based searches
	- license plate readers, 
	- traffic violations detection, 
	- breast tomosynthesis diagnosis
	- Others