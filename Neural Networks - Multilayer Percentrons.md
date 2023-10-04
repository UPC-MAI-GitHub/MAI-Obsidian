![[slides-MultilayerPerceptrons.pdf]]

## Notes
### Introduction
### Linear Regresion
### General Machine Learning Issues
### Single-layer Perceptrons
- Rosenblatt's perceptron
- *Logistic regression*
	- *Classification* problems
		- Possible classes to get $Y\in \{0,1\}$
		- ![[Neural Networks - Multilayer Percentrons 2023-09-21 10.24.25.excalidraw]]
	- *Model representation*: a single-layer perceptron with one logistic output unit 
		- $h_{\theta} (x) = f (\theta' \cdot x)$ 
		- $f(z) = \frac{1}{1+e^{-z}}$ is the logistic function
		- ![[Neural Networks - Multilayer Percentrons 2023-09-21 10.28.01.excalidraw]]
	- *Interpretation*: Probability that $y=1$ given a certain $x;\theta$ $$h_{\theta}(x)=P(y=1|x;\theta)$$ $$\log\left(\frac{P(y=1|x;\theta)}{P(y=0|x;\theta)}\right)= \theta'\cdot x$$
	- *Cost function*: Cross-entropy (negative log-likelihood)
		- If $y_{i=0}$ then just $p_2$
		- if $y_i=1$ then just $p_1$
		$$J(\theta,D) = \sum_{i=0}^{N}-y^{i}\cdot log(h_{\theta}(x^{i}))+ \sum_{i=1}^{N}-(1-y^{i})\cdot log(1-h_{\theta}(x^i))$$
		- cross-entropy is convex with reference to the parameters
	- *Optimization*: Gradient Descent
	$$\frac{\partial J(\theta_t,D)}{\partial \theta} = X' (h_{\theta_t}(X)-Y)$$

### Multi-layer Perceptrons
* *Definition*: multiple perceptron conected in layers
	* input *layer* -> hidden *layers* -< output *layer*