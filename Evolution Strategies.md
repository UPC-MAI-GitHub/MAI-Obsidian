![[ESs.pdf]]

## Notes
* **The nozzle experiment**
	* *Optimization of a Two-Phase Nozzle with an ES*
	* The animation below depicts a (1 + 1)-ES optimizing the shape of a two-phase nozzle. This is one of the 'classics' in the field.
	* [Hans-Paul Schwefel](http://ls11-www.informatik.uni-dortmund.de/people/schwefel/) performed the original experiments and collected the data, [Uli Hermes](http://ls11-www.informatik.uni-dortmund.de/people/hermes/) created the 3D-model.
	* Before   ![[Pasted image 20231123103338.png]]
	* After ![[Pasted image 20231123103323.png]]
	* 32% of increase in efficiency!
	* Given the task of *determining the internal shape of a two-phase jet nozzle with maximum thrust* under constant starting conditions, H.-P. Schwefel was one of the first to use gene duplication and deletion.
	* Since no simulation model was available at the time an experimental optimization had to be performed, using a so-called *(1+1) Evolution Strategy*. The nozzles were built of conical pieces such that no discontinuity within the internal shape was possible. In this way every nozzle shape could be represented by its overall length and the inside diameters at the borders between the segments (every 10mm). For technical reasons the incoming diameter of the first segment had to be 32mm and the smallest diameter was fixed to 6mm resulting in an convergent-divergent structure of the nozzles.
	* The *genotype of each nozzle had the following form*:
		* $$Z_1, Z2_, D{-nc}, ..., D{-1}, D{1}, ..., D{nd}$$, where $Z_1$ and $Z_2$ denote the number of segments in the convergent (divergent, respectively) part of the nozzle, i.e. the number of segments in front of or behind the smallest diameter.
		* D{-nc}, ..., D{-1} designate the diameters in the convergent part and D{1}, ..., D{nd} those in the divergent part of the nozzle.
* **The gaussian distribution**
	*  Represent the distribution of a dataset in a shape bell, mathe matically defined as:
		* ![[Pasted image 20231123103954.png]]
		* Take into account the independence of variables
		* ![[Pasted image 20231123104020.png]]
		* Observations from a bivariate normal distribution, a contour ellipsoid, the two marginal distributions, and their histograms 
		* ![[Pasted image 20231123104054.png]]
		* From the linear algebra point of view
			* The principal directions (a.k.a. PCs) of the hyperellipsoids are given by the eigenvectors $u_i$ of , which satisfy $\sum u_{i}= \lambda_{i}u_i$.
			* The lengths of the hyperellipsoids along these axes are proportional to $\sqrt{\lambda_i}$ (note $\lambda_i$), where $\lambda_i$ are the eigenvalues associated with $u_i$ 
			* ![[Pasted image 20231123104640.png]]
	* *Multivariate Gaussian*
		* Examples from a class are noisy versions of an ideal class member (a prototype): 
			* Prototype: modeled by the mean vector 
			* Noise: modeled by the covariance matrix 
		* The quantity $$d(x):= \sqrt{(x-\mu)^{T_{\Sigma^-1}}(x-\mu)}$$ is called the *Mahalanobis distance* for $x$ 
		* Very important! the number of parameters is $\frac{d(d+1)}{2}+d$
		* *Positive definiteness*
			* For a Gaussian distribution to be well-defined, $\Sigma$ has to be real symmetric and positive definite (p.d.): 
				* for all non-null vectors $x\in R^d$, $x{^{T}\Sigma x}>0$ must hold true. 
				* alt., all eigenvalues must be positive (note they are real)
				* ![[Pasted image 20231123105302.png]]
				* ![[Pasted image 20231123105328.png]]
* **Evolution  strategies**
	* *Main characteristics*
		* Continuous search space $R{^n}$ ($n$ objective parameters) 
		* Various $ad$ $hoc$ recombination operators
		* Deterministic $(\mu,\lambda)$-replacement 
		* Generation of an offspring surplus: $\lambda\gg\mu$ 
		* Emphasis on mutation: $n$-dimensional Gaussian 
		* Self-adaptation of mutation parameters (first self-adaptive EA!)
	* *Representation*
		* *Exam questions here your generate one of many contrary teo a previous technique that always generate 2 out of 2*
		* Defining a ES $\longrightarrow (\mu/\rho,\lambda)$
		* Three parts of an individual
			* object variables $x\in R{^n}$ to compute fitness $F (x)$ 
			* Standard deviations $\sigma\in R^{n_{\sigma}}_{+}$ to express variances 
			* Rotation angles $\alpha\in(-\pi,\pi]^{n_\sigma}$ to express covariances (all Gaussians are zero mean)
	* *Mutation*
		* *Simple self-adaptive mutation*
			* ![[Pasted image 20231123110945.png]]
			* Geometrical view - Self-adaptive mutation ($n=2$)
				* ![[Pasted image 20231123111108.png]]
		* *diagonal self-adaptive Mutation*
			* ![[Pasted image 20231123111445.png]]
		* *Correlated self-adaptive mutation*
			* ![[Pasted image 20231123111950.png]]
		* *Long normal mutation*
			* ![[Pasted image 20231123112307.png]]
	* *Recombination*
		* Usually introduced as the first operator (before mutation)
		* *Generates an intermediate population* size of $\lambda$ by generating one individual at a time out of $\rho$ parents by looping $\lambda \gg \mu$ times (generation of a surplus) 
		* Typically $\rho=2$ (dual) or $\rho=\mu$ (global recombination): 
			* *dual*: the two parents are chosen at random, per individual 
			* *global*: one parent is held fixed and the other is chosen anew per each gene
		* Applied to both objective and strategy parameters (and often differently) 
		* Two basic ways: choose *randomly (discrete)* and *average (intermediate)*
		* *Example*
			* ![[Pasted image 20231123112617.png]]
	* *Replacement*
		* Strictly deterministic, rank-based 
		* The $\mu$ best are treated equally 
		* $(\mu,\lambda)$ selection: 
			* offspring surplus $\lambda\gg\mu$ 
			* important (necessary?) for self-adaptation 
			* useful for moving optima, noisy F , ... 
		* Very strong selective pressure
		* *The crucial claim (Schwefel ’87 ’92)*
			* Self-adaptation of strategy parameters works!
			* without exogenous or centralized control 
			* needs *mutation of all parameters*
			* needs generation of a surplus and $(\mu,\lambda)$ replacement 
			* needs *recombination of all parameters *
			* default (recommended) settings: 
				* $\mu=15, \lambda$ ∝ $7\mu = 105$
				* dual discrete recombination on objective parameters 
				* global intermediate on strategy parameters