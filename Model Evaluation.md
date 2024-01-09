![[T9_2023_students.pdf]]

## Summary
- **Introduction to Model Evaluation**
    - *Why Evaluate?*: Understanding model performance for reporting results, making decisions, and assessing real-life applicability; comparing and tuning models.
    - *Model Evaluation and Selection*: assessing model performance using metrics and techniques, and choosing the best model through probabilistic measures and resampling methods.
- **Evaluation Metrics**
    - *Predictive Efficacy Measures*: Includes precision (accuracy of positive predictions), recall (coverage of actual positives), F1-Score, specificity/sensitivity, and confusion matrix for detailed error analysis.
    - *ROC Analysis Metrics*: Precision-Recall Curves and ROC curves, providing insight into performance across varying thresholds, especially useful in imbalanced datasets. *Threshold are the values we use to determine when a class or positive or negative.*
- **Evaluation Techniques**
	- *Methodologies*:  not testing models on training data, ensuring unbiased datasets, and considering factors like classification cost and data distribution.
	- *Specific Techniques*: Includes holdout test-set methods with various splits for training, validation, and testing, as well as cross-validation approaches for different dataset sizes and handling data imbalance.

## Notes
### Introduction to model evaluation
* *Why do we evaluate?*
	* *Know how well a model works*
		* Reporting results
		* Make scientific/business decisions
		* Can it be used in real-life?
	* *Model comparison*
		* Choose the best models
		* Tune model's parameters
* *Model evaluation:* asses model performance (asses model property/properties)
	* Evaluation metrics
	* Evaluation techniques
* *Model selection:* choose among candidate models
	* Probabilistic measures
	* Resampling methods
### Evaluation metrics
* Measures relating to *predictive efficacy*
	* *Precision:* percentage of accurate predictions (how many of predicted as positive where correctly classified)
		* Not useful in cases where there is a large class skew (deviation)
	* *Recall:* How many of the accurate predictions did we capture (how many actually positive samples where predicted as positive)
	* *F1-Score:* $2\frac{precision\cdot recall}{precision+recall}$
	* *Specificity/ sensitivity*
	* *Confusion Matrix*: comparison of the model predictions and the true labels class by class. With de CM we have the: *True positives*, *False Positives*, *False Negatives*, *True Negatives*
	* *Others:* Accuracy, Error rate, TP rate, FP rate
	* ![[Pasted image 20231128112616.png|500]]
* Metrics based on *ROC Analysis*
	* In this context: *Threshold* are the values we use to determine *when a class or positive or negative*. (e.g. prediction > 0.5 positive else negative)
	* *Precision-Recall Curves*:  plots the precision vs. recall as a threshold on the confidence of an instance being positive is varied (*Well suited for tasks with lots of negative instances*)
		* ![[Pasted image 20231128112855.png|450]]
	* *A Receiver Operating Characteristic (ROC)*:
		* curve plots the TP-rate vs. the FP-rate as a threshold on the confidence of an instance being positive is varied
			* ![[Pasted image 20240108030414.png|450]]
### Evaluation techniques:
* **Don’t test your model on data it’s been trained with!!!**
* Provide *more reliable estimates of the accuracy* of the models learned by an algorithm
* Testing on *biased datasets* can lead to *inaccurate estimation* of performance
* Test set large enough to ve valid for reporting model performance
* *Considerations*:
	* Classifications cost: is it better for the problem to have less errors in the positive or in the negative class?
	* What is de distribution of classes in my data
	* Some interest in a subset of high-confidence predictions
* **Holdout test-set**
	* *Naïve approach*
		* $D = D_{train}\cup D_{test}$
		* Use $D_{train}$ to learn the model
		* Use $D_{test}$ to compute performance of the method
	* *Three-way split*
		* $D = D_{train}\cup D_{validation}\cup D_{test}$
		* Use $D_{train}$ to learn the models
		* Use $D_{validation}$ to decide which model adapts better to the problem
		* Use $D_{test}$ to compute performance of the method
	* *How to perform the split?*
		* *Training:* typically $60\%-80\%$ of the data
		* *Validation set:* Often $20\%$ of the data
		* *Test set:* typically 20%-30% of the data
		* *Time based* - If time is important
* **Cross-validation**
	* Use when holdout plan is difficult to design
	* Also when the data is small
	* *Process*
		* Iteratively interchange the elements in the train and test set, make sure after all the iterations all datapoints has one has test set round and the other it has been used as train dataset.
		* Evaluate performance on each iteration.
	* *How many folds are needed?* (*Commonly* 5-fold or 10-fold)
		* *Large dataset*: 3-fold
		* *Small dataset:* bigger L
		* *Leave-One-Out*: (L=N). N is the number of examples. 
		* 
	* **Imbalance:**
		* Is is possible to build a model with imbalanced data?
		* This creates problems for training and evaluating a model
		* Types
			* Between-*class*
			* Within-*class*
			* *Intrinsic* and *Extrinsic*
			* *Relativity*
			* *Rarity*
		* *How to deal with imbalance?*
			* *Sampling methods*: 
				* *Modify data distribution* (final evaluation must be always with the original distribution)
					* Undersampling the majority class (randomly remove)
					* Oversampling the minority class (repeat minority points)
					* Assign larger weights to samples from the smaller classes
						* Commonly, linearly by class size $w_c=\frac{n}{n_c}$
							* $n_c=$ size of class $c$
							* $n = \sum\limits_{c}n_c$ 
			* *Const-sensitive methods*
			* *Kernel and Active Learning Methods*
* **Overfitting**: overfit the training data when a model describes features that arise from noise or variance in the data, rather than following the general pattern from data distribution. *Train accuracy high, test accuracy low* - *low train error, high test error*
	* Leads to *loss of accuracy in out-of-sample data* (**don't achieve Generalization**)
	* *Just training data memorization*
	* Possible causes:
		* The *model is too complex* (many features)
		* Not enough data
		* Redundant data (*no diversity*)
	* *Avoid by:*
		* Using low variance learners
		* Minimum description lenght technique
		* Pruning (cutting) - *dimensionality reduction* 
		* *Regularization* - penalize too much complexity
		* Stopping criteria
* **Underfitting**: both *train and test accuracy* are *low*, high error.
	* The model is to simple for the problem
		* Too features
		* The use of features is not 'complex'
		* ![[Pasted image 20240108102424.png]]
