![[T6_2023_students.pdf]]


## Notes

* *What is supervised learning?*
	* Inferring a function from labeled training data
	* $D(x,y) \rightarrow f(x_i)\rightarrow y_i$
	* where $x$ is the input and $y$ is the output
	* ![[A Gentle Introduction to Supervised Machine Learning 2023-11-07 10.13.36.excalidraw]]
	* **Tasks of Machine learning** 
		* *Prediction*: medical diagnosis, spam mail $\longrightarrow$ *Supervised Learning*
			* *Regression* $\longrightarrow$ numerical data (continuous variable), real-value output
			* *Classification* $\longrightarrow$ discrete, nominal, categorical data
		* *Understanding*: market basks, discovering astronomical features $\longrightarrow$ *Unsupervised Learning*
		* *Control*: flying helicopters $\longrightarrow$ *Reinforcement Learning*
	* **When to use**
		* *There is a patters*
		* *The problem doesn't have a formal matematical definition*
		* *We have* **data**
	* **Generalization**
		* A model that performs the best on future examples
		* We hope that future data will remember past data in a way that while let us use the past data to construct a model that will perform well in the future
	* **What ML algorithm to choose?**
		* What do you want to predict?
		* What kind of data can you get?
		* What is the relative costs of different types of errors? 
		* How does the available data relate to future data?
	* **Common Jargon**
		* *Rows*: features /attributes/ dimensions
		* *Columns*: instances / examples / samples
		* *To be predicted* target/ outcome/ response/ label
		* *Other features*: independent variables /covariates/predictors/regressors
	* **In supervised learning**:
		* A model that maps input data to the output label
		* Infinite number of models (lines can be defined) $\rightarrow$ Hypothesis set
		* The learning process  for selecting the most appropriate parameters
		* ![[Pasted image 20231107105137.png]]
		* *Elements of supervised learning*
			* *Data* $\rightarrow$ $x,y$ (input and target output)
			* *Model* $\rightarrow$ Hypothesis set (possible/candidate models), Learning algorithm
			* *Prediction* $\rightarrow$ Model outputs
		* *Linear regression* Fond a model defined by the parameters $w_0,w_1$ so that the prediction $f(x_i;w_0,w_1)$ is as close as possible to $y_i$, so we try to minimize the distance between them, and that is called *the learning process* $$minimize \frac{1}{N}\sum\limits_{i=1}^{N}(f(x_i;w_0,w_{1)}-y_i)^2$$
		* This function of minimization is often called the *cost function / loss function / error measure*
	* **Parameter space**
		* Descent optimization methods
		* The parameters space is a representation that help us to track the progress of our algorithm performance. According to the accuracy and cost function of our model we can track if the parameters are good enough.
		* The idea is to get the parameters convergence when the model represents the data in the best possible way.
		* ![[Pasted image 20231107112817.png]]
		* *How to find the minimum in an automated way?*
			* Start with some starting point (guess)
			* Update the parameters iteratively so that we reduce the cost function
			* Stop when the cost function is not reduced anymore
			* The cost function space can be represented as surface where the goal is go reach the global minima
			* ![[Pasted image 20231107113148.png]]
			* *Descent methods*
				* Determine the route to get the global minima by descending in the cost function surface by updating the parameters
				* *While* the *criterion* is not *satisfied*
					* Determine a *descent direction* $\Delta x = -\nabla f(x)$
					* Chose a step size $t>0$
					* *Update parameters*
				* ![[Pasted image 20231107113534.png]]
				* ![[Pasted image 20231107113549.png]]
				* ![[Pasted image 20231107113642.png]]
				* ![[Pasted image 20231107113717.png]]
				* ![[Pasted image 20231107113754.png]]
				* The *gradient* of a function is the multi-variate extension of the derivative for a single variable 
				* Observe that the *optimum* is located in the other half space 
				* Note that *not all direction on that space are descent directions*
				* Observe that we can find a direction with higher value pointing to any point between the green and orange level sets 
				* Observe that the direction with steepest descent is precisely $\Delta x = -\nabla f(x)$ 
				* **Learning rate** (Gradient steepest descent)
					* If *t* is too *small*, *gradient descent* will be *slow* 
					* If *t* is too *large*, *gradient descent* can *overshoot the minimum*. It may *fail to converge* or even *diverge* 
						* ![[A Gentle Introduction to Supervised Machine Learning 2023-11-07 11.43.59.excalidraw]]
					* There is no need to decrease t over time 
					* Gradient descent can converge even if t is fixed
	* **Application of the learning model**
		* We train a model with our training data, hoping it will perform well with new data.
		* *Evaluation strategy*
			* Devide the *training data* in two
				* *Train set* $\rightarrow$ learn the model
				* *Test set* $\rightarrow$ compute the performance os the method
			* We can still divide the *Train data* in two
				* *Train set* $\rightarrow$ learn the models
				* *Validation set* $\rightarrow$ decide which of the models adapts better to the problem
	* **Whirlwind tour on ML terms**
		* **Model algorithms**
			* *Learn a simple Gaussian*
				* Probability, random variables, distributions; estimation, convergence and asymptotics, confidence interval.
			* *Learn a mixture of Gaussians (MoG)*
				* Likelihood, Expectation-Maximization (EM); generalization, model selection, cross-validation; k- means, Hidden Markov odels (HMM)
			* *Learn any Density*
				* Parametric vs. non- Parametric estimation, Sobolev and other functional spaces; l-2 error; Kernel density estimation (KDE), optimal kernel, KDE theory
			* *Predict continuous variable (Regression)*
				* Linear regression, regularization, ridge regression, and LASSO; local linear regression; conditional density estimation.
			* *Predict discrete variable (Classification)*
				* Bayes classifier, naive Bayes, generative vs. discriminative; perceptron, weight decay, linear support vector machine; nearest neighbor classifier and theory
		* **Basic concepts of Machine Learning General theory and model frameworks of Machine Learning**
			* *Loss functions*
				* Maximum likelihood estimation theory; l-2 estimation; Bayessian estimation; minimax and decision theory, Bayesianism vs frequentism
			* *Models to use*
				* AIC and BIC; Vapnik-Chervonenskis theory; cross-validation theory; bootstrapping; Probably Approximately Correct (PAC) theory; Hoeffding-derived bounds
			* *Learn fancier combined models*
				* Ensemble learning theory; boosting; bagging; stacking
			* *Learn fancier Non-linear models*
				*  Generalized linear models, logistic regression; Kolmogorov theorem, generalized additive models; kernelization, reproducing kernel Hilbert spaces, non-linear SVM, Gaussian process regression
			* *Learn fancier compositional models*
				* Recursive models, decision trees, hierarchical clustering; neural networks, back propagation, deep belief networks; graphical models, mixtures of HMMs, conditional random fields, max-margin Markov networks; log-linear models; grammars
			* *Reduce or relate features*
				* Feature selection vs dimensionality reduction, wrapper methods for feature selection; causality vs correlation, partial correlation, Bayes net structure learning
			* *Create new features*
				* principal component analysis (PCA), independent component analysis (ICA), multidimensional scaling (MDS), manifold learning, supervised dimensionality reduction, metric learning
			* *Reduce or relate data*
				* Clustering, bi- clustering, constrained clustering; association rules and market basket analysis; ranking/ordinal regression; link analysis; relational data
			* *Treat Time Series*
				* ARMA; Kalman filter and stat-space models, particle filter; functional data analysis; change-point detection; cross-validation for time series
			* *Treat non-ideal data*
				*  covariate shift; class imbalance; missing data, irregularly sampled data, measurement errors; anomaly detection, robustness
			* *Optimize parameters*
				* Unconstrained vs constrained/Convex optimization, derivative-free methods, first- and second-order methods, backfitting; natural gradient; bound optimization and EM
			* *Optimize linear functions*
				* computational linear algebra, matrix inversion for regression, singular value decomposition (SVD) for dimensionality reduction
			* *Optimize with constraints*
				* Exact graphical model inference, variational bounds on sums, approximate graphical model inference, expectation propagation
			* *Evaluate deeply-nested sums*
				* Exact graphical model inference, variational bounds on sums, approximate graphical model inference, expectation propagation
			* *Evaluate large sums and searches*
				* Generalized N-body problems (GNP), hierarchical data structures, nearest neighbor search, fast multiple method; Monte Carlo integration, Markov Chain Monte Carlo, Monte Carlo SVD
			* *Treat even larger problems*
				* Parallel/distributed EM, parallel/distributed GNP; stochastic subgradient methods, online learning
			* *Apply to real world*
				* Overview of the parts of the ML, choosing between the methods to use for each task, prior knowledge and assumptions; exploratory data analysis and information visualization; evaluation and interpretation, using confidence intervals and hypothesis test, ROC curves; where the research problems in ML are