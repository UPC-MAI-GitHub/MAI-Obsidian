![[Session2_Support_Work1_2023.pdf]]

## Notes

### DBSCAN
- **Density-Based Clustering**
- We are able to use *SKLEARN*
- **Characteristics**
	- Local cluster criterion.
	- Density-connected points or explicitly costructed function.
	- Discover clusters of arbitrary shape
	- Handle noise
	- One scan
	- Need density parameters
- **Process**: partition points into dense regions separated by not-so-dense regions.
	- **Density at point** *p*: number of points within a circle of radius *Eps* 
	- **Dense Region**: A circle of radius *Eps* that contains at least *MinPts* points
- **Characterization of points**
	- *Density* = number of points within a specified radius (Eps) 
	- A point is a *core point* if it has more than a specified number of points (MinPts) within Eps
	- A *border point* has fewer than MinPts within Eps, but is in the neighborhood of a core point 
	- A *noise point* is any point that is not a core point or a border point
	- ![[Pasted image 20231003132401.png]]
- ![[Pasted image 20231003132449.png]]
-  Parameters must be specified by the user 
	- ℇ = physical distance (radius)
		-  value can be chosen by using a k-distance graph
		- If ℇ is chosen much too small, a large part of the data will not be clustered 
		- If too high value, majority of objects will be in the same cluster 
		- In general, small values of ℇ are preferable 
		- ℇ-Neighborhood: Objects within a radius of ℇ from an object (epsilon-neighborhood) 
		- Core objects: ℇ-Neighborhood of an object contains at least MinPts of objects
		- ![[Pasted image 20231003132758.png]]
	- minPts = desired minimum cluster size 
		- derived from the number of dimensions D in the data set, as minPts ≥ D + 1 
		- minPts = 1 does not make sense, as then every point on its own will already be a cluster 
		- minPts must be chosen at least 3. Larger is better. 
		- larger the dataset, the larger the value of minPts should be chosen 
- **Algorithm**
	1. Create a graph whose nodes are the points to be clustered 
	2. For each core-point c create an edge from c to every point p in the e-neighborhood of c 
	3. Set N to the nodes of the graph; 
	4. If N does not contain any core points terminate 
	5. Pick a core point c in N 
	6. Let X be the set of nodes that can be reached from c by going forward; 
		1. create a cluster containing XÈ{c} 
		2. N=N/(XÈ{c}) 
	7. Continue with step 4
- **Score**
	- Works well
		- Resistant to noise
		- Can handle clusters of different shapes and sizes
	- Not work well
		- Varying densities
		- High dimensional data
- *Time complexity* $O(n^2)$ ($n$  number of objects to be clustered)
* *Space complexity* $O(n)$
### Birch
- **Balanced**
