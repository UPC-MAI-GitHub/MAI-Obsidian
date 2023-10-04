![[CV-2324_Class1_3IntroFilters.pdf]]

## Notes
### Digital images
- *Light carries coded information* about the world and we can perceive it with our sight
- *Digital cameras* can parse this information to a matrix with values of color intensities and brightness (proportional to the number of photons captures by the sensor)
- Kinds of digital images:
	- Natural images
	- X-rays
	- MRI
	- Electron microscopy
	- Light microscopy
- Intensities for a 8-bit digital image [0-255]
- *Sample 2D space* on a regular grid
- *Quantize* each sample (round to the nearest integer)
- Digital image represented as
	- Matrix
	- Histogram
- *Colored images*: filtering the light in its three primary colors (Red, Green, Blue). Once all three colors are recorded, are combined them to create the full spectrum.
	- Representation Tensor with *3 matrix*
### Image properties
- *Resolution*
	- Sensor: *amount of real world space parced in a pixel*
	- Image resolution: *number of pixels*
- *Image magnification*: increase the resolution (no. of pixels) of the image maintaining the visual characteristics of its content.
- *Image reduction*: decrease resolution by deleting some pixels without loosing the general info of the image
- *Photometric resolution*: number of different pixel values (intensity levels)  on each color channel.
- A *histogram* of an image represents the *frequencies of pixel intensities*.
	- A measure of image quality
	- *Manipulate the histogram*
		- Contrast enhancement: increase the amount of values present in the image (not the size)
			- Minimum-maximum contrast stretch
				$$BV_{out} = \left( \frac{BV_{in}-min_k}{max_k-min_k} \right) quant_k$$
				- $BV_{out}$ *original pixel value*
				- $quant_k$ *range of the posible values (e.g. 255)*
				- $min_k$ *minimum posible value*
				- $max_k$ *maximum posible value*
				- $BV_{out}$ *output pixel value*
			- Percentage linear contrast stretch
### Linear filters
- Computing a *function of the local neighborhood* at each pixel in the image
- **Uses**
	- Soft blur, smoothing 
	- Enhance an image (remove noise) 
	- Extract information: Sharpen or accentuate details (texture, edges) 
	- Detect patterns (feature detection and matching)
* **Common types**
	* *Noise*
		* Salt and pepper (random occurrences, black n white pixels)
		* Impuse noise (random white pixels)
		* Gaussian Noise (intensity variation using a gaussian normal dist.)
			* The impact of sigma is the distribution of values
	* *Noise reduction*
		* Average all the values in the neighborhood of each pixel
		* Moving average and weighted moving average
			* Uniform weights [1,1,1,1,1]
			* Non-uniform weights [1,4,6,4,1]
			* Moving average in 2D is similar to the correlation - convolution operation
			* ![[Pasted image 20231003142042.png]]
			* Weighted 2D 
			* ![[Pasted image 20231003142106.png]]
		* **Correlation filtering**
			* Replace each pixel with a linear combination of its neighbors. (Weights = Kernel = Mask)
			* ![[Pasted image 20231003142221.png]]
			* The *size of filter* influence in the *amount of blur* we get
		* **Gaussian filter**
			* Use a gaussian shape to distribute weihgts in the 2D filter (kernel) to have a softer smooth in the blur after filtering an image 
			* Removes high-frequency components from the image (“low-pass filter”).
			* *Parameters*
				* Sigma --> $\sigma$
				* The value of sigma (standar deviation) control the amount of smoothing
				* ![[Pasted image 20231003143007.png]]
		* **Sharpening**
			* Get the details of the image
			* Detecting edges
## Udacity videos notes
- Smooth images (blured) - equal to a smoothed function
- ![[Digital images, image properties & linear filters 2023-10-02 19.36.33.excalidraw]]
- Image as a function from $R^2{\rightarrow}R$ such that $f:[a,b]\times[c,d]\rightarrow [min,max]$
- Color images $$f(x,y) = \begin{bmatrix}  r(x,y) \\  g(x,y) \\ b(x,y) \\ \end{bmatrix}$$
- $f$ --> gives intensity or value at position $(x,y)$
	- ![[Digital images, image properties & linear filters 2023-10-02 19.54.00.excalidraw]]
- A value at each location can be a vector $(r,g,b)$
	- ![[Digital images, image properties & linear filters 2023-10-02 20.05.52.excalidraw]]
	- Range in $x$ times range in $y$ equals to intensity value ![[Digital images, image properties & linear filters 2023-10-02 19.54.00.excalidraw]]
	- ![[Digital images, image properties & linear filters 2023-10-03 00.51.20.excalidraw]]
	- As images are function we can apply them operations or other functions, like noise function.
		- Salt and peper
		- Gaussian Noise
		- ![[Pasted image 20231003010935.png]]
		- Effect of sigma in gaussian noise
		- ![[Pasted image 20231003011143.png]]
		- ![[Pasted image 20231003011439.png]]
- Smoothing images
	- ![[Pasted image 20231003011730.png]]
	- ![[Pasted image 20231003011712.png]]
	- ![[Digital images, image properties & linear filters 2023-10-03 01.20.17.excalidraw]]
	- Weighted average, where nearby pixels contribute more that the ones with more distance to the pixel ![[Drawing 2023-10-03 02.07.59.excalidraw]]
	- ![[Digital images, image properties & linear filters 2023-10-03 02.14.03.excalidraw]]
	- ![[Digital images, image properties & linear filters 2023-10-03 02.15.50.excalidraw]]
	- *Correlation filter* ![[Digital images, image properties & linear filters 2023-10-03 02.16.41.excalidraw]]
	- *cross correlation - no uniform weights* ![[Pasted image 20231003021739.png]]
	- **Gaussian Filter** ![[Digital images, image properties & linear filters 2023-10-03 02.20.22.excalidraw]]
	- ![[Digital images, image properties & linear filters 2023-10-03 02.22.48.excalidraw]]
	- ![[Pasted image 20231003022400.png]]
	- ![[Digital images, image properties & linear filters 2023-10-03 02.25.16.excalidraw]]






