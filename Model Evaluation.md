![[T9_2023_students.pdf]]

## Notes
* **Introduction to model evaluation**
	* *Know how well a model works*
		* Reporting results
		* Make scientific/business decisions
		* Can it be used in real-life?
	* *Model comparison*
		* Choose the best models
		* Tune model's parameters
	* *Model evaluation:* asses model performance 
		* *Evaluation metrics*
			*  Measures relating to *predictive efficacy*
			* Metrics based on *ROC Analysis*
			* *Precision:* percentage of accurate predictions
			* *Recall:* How many of the accurate predictions did we capture
			* *F1-Score:* $2\frac{precision\cdot recall}{precision+recall}$
			* *Specificity/ sensitivity*
			* *Confusion Matrix*: comparison of the model predictions and the true labels class by class. With de CM we have the: *True positives*, *False Positives*, *False Negatives*, *True Negatives*
			* *Others:* Accuracy, Error rate, TP rate, FP rate
			* ![[Pasted image 20231128112616.png]]
			* *Precision-Recall Curves*: curve plots the precision vs. recall as a threshold on the confidence of an instance being positive is varied
			* ![[Pasted image 20231128112855.png]]
		* *Evaluation techniques:* provide more reliable estimates of the accuracy of the models learned by an algorithm
		* *Considerations*:
			* Classifications cost: is it better for the problem to have less errors in the positive or in the negative class?
			* What is de distribution of classes in my data
			* Some interest in a subset of high-confidence predictions
	* *Model selection:* choose among candidate models
		* Probabilistic measures
		* Resampling methods
		* 