![[CV-2324_Class3_HOG.pdf]]

## Notes

- **Template Matching**
	- *Goal:* find the template of a part of the image (*template*) in the same image
	- *Method:* Compare the template patches of the image
	- *Main challenge:* find a good similarity measure
	- **Using filters**
		- *Goal:* find the template in the image with filter applied
		- *Method 1* 
			- *Sum Square Difference* $$h[m,n] = \sum_{k,l} (g[k,l] - f[m+k,n+l]){^2}$$
			- ![[Pasted image 20231010142346.png]]
			- It works fine. But it has *problems with local brightness changes*.
			- ![[Pasted image 20231010142417.png]]
		- *Method 2:*
			- *Convolutional filtering the image with the template* $$h[m,n] = \sum_{k,l} (g[k,l])(f[m+k,n+l])$$
			- Where $f = image$  and $g = template$ template
			- *It doesn't work* because it *needs normalization*
			-  ![[Pasted image 20231010143902.png]]
		- *Method 3:* 
		- *Convolutional filtering the normalized image* $$h[m,n] = \sum_{k,l} (g[k,l])(f[m+k,n+l]-\bar{f})$$
		- $\bar{f}=$ mean of $f$
		- We get *true detections* but *also noisy detections* (Sensitive to high contrast areas)