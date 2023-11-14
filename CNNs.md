![[CV-2324_Class7_CNNs.pdf]]

## Notes

* *Convolutional Neural Networks*
	* AI and machine learning almost all people are working with this for CV. 
* *CNN*
	* Layers 
	* Optimization
* *Applications*
	* Supervised and unsupervised learning 
	* Recent years a lot of interest in Object Recognition
	* Object detection
	* Generative AI
* *history of CNN and AI*
	* 1943 McCulloc and Pitss - neural model with a circuit
	* 1958 Rosemblatts perceptron
	* 1959 Adeline 
	* 1986 back propagation
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
* *Benefits of CNNs*
	* Transfer learning
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