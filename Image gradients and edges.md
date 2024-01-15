![[CV-2324_Class2_Edges.pdf]]


## Summary
- Compute a *function of the local neighborhood* at each pixel in the image 
	- Function specified by a “*filter*” or mask saying how to *combine values from neighbors*. 
- **Uses of filtering**: 
	- *Enhance an image* (denoise, resize, etc) 
	- *Extract information* (texture, edges, etc) 
	- *Detect patterns* (feature detection and matching)
## Notes

### General summary
* *Filters allow local image neighborhood to influence* our description and *features*
	* *Smoothing* to *reduce noise*
	* *Derivatives* to *locate contrast, high image gradient* 
* Different *edge detectors*: 
	* **Sobel & Prewitt**: *fast but sensitive to noise* 
	* **Convolution** + **Derivative of **Gaussian**: 
		* *Less fast but more robust*
		* Using different *sigma allows to smooth more or less* 
			* Also the definition of the *edge detection* (more or less detail)
		* Zero-crossing with a *Laplacian* – *assures closed contours* 
	* **Canny edge detector**: classical edge detector 
		* Assures  *continuous and thin contours* due to the hysteresis and the thinning steps. 
		* Needs parameters
### Edge detection
- *Goal*: *map image from 2D* array of pixels *to* a set of *curves* or *line segments* or *contours*. Locating structural features.
	- Define the silhouette and are *very informative about the content of the image*.
- *Causes of an edge*
	- *Depth discontinuity*: object boundary
	- *Reflectance change*: appearance information, texture
	- *Cast shadows*
	- *Change in surface orientation*: shape
- **Edges/gradients and invariance**
	- Use *gradients to measure the changes* in an image and *detect edges*
	- An *edge* is a *place of rapid change* in the image *intensity* function.
	- We use derivatives to detect changes in an image
	- ![[Pasted image 20240112020236.png]]
	- The *gradient* of an image is the vector: And points in the direction of most rapid change in intensity. *Change in X or Y or in both.*
	- ![[Pasted image 20240112020531.png]]
	* **First Derivatives**
		- *Partial derivatives* to measure changes en *X* or *Y* axis
		- For discrete data (as images) $\longrightarrow$ *Finite difference filters*:
			- Common operators
			- ![[Pasted image 20240112021127.png|250]]
			- *Capturin finite differences by using*: **Filters**
			- ![[Pasted image 20231003144529.png|300]]
			- *Prewitt* filters uses uniform weights
			- *Sobel filter*, by *using non-uniform weights*, gives *more importance to the closest neighbors*
		- The gradient direction is given by the inverse of *tangent* of the gradients
			- ![[Pasted image 20240112021719.png]]
		- The *edge strength* is given by the *gradient magnitude*
			- ![[Pasted image 20240112021735.png]]
		- Which aspect (*magnitude* or *direction*) is *invariant* to image contrast?
			- Direction
	- **Second derivatives**
		- Given an *edge*, the first derivative has an extreme, and the *second derivative has a zero-crossing* in the edge and *extremes before and after* the edge.
		- ![[Pasted image 20240112021843.png]]
		- Helps to *detect diagonal neighbors*
		- To *apply in discrete data* (such an images): **Laplacian**
			- ![[Pasted image 20240112022125.png|500]]
			- Including *diagonal neighbors*
				- ![[Pasted image 20240112022317.png|150]]
- **Histogram of edge maps**
	- For $x$ and $y$
	- ![[Pasted image 20240112022411.png]]
- Why are they *positive* and *negative*? 
	- Because there are gradients in different (oposite) directions
- Why the maxima is in 0?
	- Most of the image reflect no changes (not the hole image is changes)
- **Improving edge identification**
	- We can use *filters to smooth and remove noise* to process the signal of edges detection to *better identify the edges*
		- ![[Pasted image 20240112023005.png|500]]
		- ![[Pasted image 20240112023245.png|500]]
		- *For discrete data, Derivative of Gaussian is a simple filter:*
			- ![[Pasted image 20240112023525.png|400]]
	- *Even better identification of edges with the Laplacian of Gaussian (LoG)*
	- ![[Pasted image 20240112023753.png|500]]
	- ![[Pasted image 20240112023635.png|500]]
- **Sigma parameter** on the derivatives for edge detection *influence*:
	- **Larger sigma values** --> *Large scale edges detected* (less definition in the identification)
	- **Smaller $\sigma$ values** --> *finer features detected*
- **Steps to get the edges**
	1. *Smoothing*: suppress noise (e.g. by applying a *Gaussian filter*) 
	2. *Edge enhancement*: filter for contrast detection (e.g. applying finite difference *filters as Sobel*)
	3. *Edge localization* 
		-  Determine which *local maxima from filter output* are actually edges vs. noise. 
		- *Binarization (thresholding)*: all pixels with output value 
			- higher than a threshold --> 1, 
			-  lower than the threshold --> 0.
- **Canny Edge Detector**
	- **Steps**
		- Filter image with *Derivative of Gaussian filter* 
		- Find *magnitude and orientation* of gradient 
		- *Non-maximum suppression*: 
			- Thin wide “ridges” down to single pixel width 
		- *Linking and thresholding* (hysteresis): 
			- Define two thresholds: low and high
			- *Hysteresis thresholding*: Use a *high threshold to start* edge curves, and a *low threshold to continue them*.
	- **Limitations of Canny**
		- *Canny* detector only *focuses on local changes* and it *has no semantic understanding*.
		- *Low level edges vs perceived contours*
		- ![[Pasted image 20231003151904.png|550]]
	- *Hysteresis thresholding*
		- ![[Pasted image 20240112025108.png|550]]
- The *canny edge operator* is probably quite sensitive to noise?
	- True - derivatives accentuate noise
	- False - the gradient is computed using a derivative of Gaussian operator which removes noise
	- Mostly false - it depends upon the chosen value of sigma (Correct)
- ![[Image gradients and edges 2023-10-04 11.04.47.excalidraw]]
**Relation of filters with CNNs**
	- ![[Pasted image 20240112025817.png]]
## Udacity videos notes

- ![[Image gradients and edges 2023-10-03 22.47.16.excalidraw]]
- ![[Pasted image 20240112030227.png]]
- The Max operator is not linear, cause the outputs does not increment linearly according to the input
- **Inpulse function**
	- considered as the bulding block of functions
	- small simple signal whose area is 1
	- having an black box with an impulse at the input of the box, we can see which are the output impulses
	- we can use impulses to process images
	- *Impulse filter*
		- it flips the entire respose
			- ![[Image gradients and edges 2023-10-03 22.54.58.excalidraw]]
			- ![[Image gradients and edges 2023-10-03 22.56.50.excalidraw]]
- **Correlation vs Convolution**
	- ![[Pasted image 20231003225911.png]]
	- ![[Image gradients and edges 2023-10-03 23.01.39.excalidraw]]
	- Convolution properties
		- *Conmmutative* $f*g=g*f$
		- *Associative* $(f*g)*h* = f*(g*h)$
		- *Identity* $e = [...,0,0,0,1,0,0,0,...]$ ---> $f*e=f$
		- *Derivatives* $\frac{\partial}{\partial x}(f*g) = \frac{\partial f}{\partial x}*g$
	- *Computational complexity* $N^2W^2$
	- With *separability* of some kernels we can reduce the computational complexity to $2WN^2$
	- *Boundary issues* when convolving
		- ![[Image gradients and edges 2023-10-03 23.14.08.excalidraw]]
		- *Clip*: outside boundary is black
		- *Wrap around*: putting patterns of the image around
		- *Copy edge* : extend out the same value
		- *Reflection*: reflect the image out
	- Code to blur in matlab
```matlab
% Explore edge options
pkg load image;

%% Load an image
img = imread('fall-leaves.png');  % also available: peppers.png, mandrill.png
imshow(img);

%% TODO: Create a Gaussian filter
filter =  fspecial('gaussian', [7 7], 28.6);
size(filter)

%% TODO: Apply it, specifying an edge parameter (try different parameters)
imshow(imfilter(img, filter,'circular'))		 
```
- **Linear filters**
	- ![[Image gradients and edges 2023-10-03 23.34.17.excalidraw]]
	- ![[Image gradients and edges 2023-10-03 23.34.42.excalidraw]]
	- ![[Image gradients and edges 2023-10-03 23.36.02.excalidraw]]
	- ![[Image gradients and edges 2023-10-03 23.36.18.excalidraw]]
	- ![[Image gradients and edges 2023-10-03 23.40.01.excalidraw]]
- **Median filter**
	- Help to remove noise from an image.
	- ![[Image gradients and edges 2023-10-03 23.45.14.excalidraw]]
	- ![[Image gradients and edges 2023-10-03 23.45.48.excalidraw]]
	- ![[Image gradients and edges 2023-10-03 23.46.37.excalidraw]]
- **Edge detection**
	- Reduced images to just the lines defining the main objects in the image.
	- *Origin of edges*
		- surface normal discontinuity
		- depth discontinuity
		- surface color discontinuity
		- illumination discontinuity
	- Map an image to a reduced set of lines
	- Look for a neighborhood with a strong signs of change
		- Neighborhood size
		- How to detect change
	- **Derivatives and edges**
		- *edge* is a place of *rapid change*
		- Finding *edges* is like finding *peaks in the derivatives*
		- Differential operators --> kernel that compute the gradient function over an image
		- Derivatives measures changes in the $x$ and $y$ directions
		- ![[Pasted image 20231004003211.png]]
		- ![[Pasted image 20231004003238.png]]
		- ![[Image gradients and edges 2023-10-04 00.38.46.excalidraw]]
		- To do it in a *computer* we have to use *finite differences* to approximate the derivatives
			- Finite differences over $x$ that causes that vertical stripes are better identified![[Pasted image 20231004004224.png]]
			- ![[Pasted image 20231004090332.png]]
	- **Sobel operator**
		- ![[Pasted image 20231004091007.png]]
		- ![[Pasted image 20231004091121.png]]
		- ![[Image gradients and edges 2023-10-04 09.13.39.excalidraw]]
```matlab
r = 5
% Gradient Direction
function result = select_gdir(gmag, gdir, mag_min, angle_low, angle_high)
    % TODO Find and return pixels that fall within the desired mag, angle range
    result = (gmag > mag_min) == ((gdir > angle_low) & (gdir < angle_high));
endfunction

pkg load image;

%% Load and convert image to double type, range [0, 1] for convenience
img = double(imread('octagon.png')) / 255.; 
imshow(img); % assumes [0, 1] range for double images

%% Compute x, y gradients
[gx gy] = imgradientxy(img, 'sobel'); % Note: gx, gy are not normalized

%% Obtain gradient magnitude and direction
[gmag gdir] = imgradient(gx, gy);
imshow(gmag / (4 * sqrt(2))); % mag = sqrt(gx^2 + gy^2), so [0, (4 * sqrt(2))]
imshow((gdir + 180.0) / 360.0); % angle in degrees [-180, 180]

%% Find pixels with desired gradient direction
my_grad = select_gdir(gmag, gdir, 1, 30, 60); % 45 +/- 15
imshow(my_grad);  % NOTE: enable after you've implemented select_gdir
```

- With *noise* in the image it *difficult* the task of *finding edges* so its *recommendable* to *smooth* the image first, smooth gradient.
- ![[Image gradients and edges 2023-10-04 10.00.18.excalidraw]]
- ![[Image gradients and edges 2023-10-04 10.02.36.excalidraw]]
- ![[Image gradients and edges 2023-10-04 10.39.39.excalidraw]]
- ![[Image gradients and edges 2023-10-04 10.39.02.excalidraw]]
- ![[Pasted image 20231004104138.png]]
- **Canny edge detector**
	- Gradients --> thining (non-max supression) --> 
	- Hysteresis thresholding
		- ![[Image gradients and edges 2023-10-04 10.46.18.excalidraw]]
```matlab
% For Your Eyes Only
pkg load image;

frizzy = imread('frizzy.png');
froomer = imread('froomer.png');
imshow(frizzy);
imshow(froomer);

% TODO: Find edges in frizzy and froomer images
frizzy_e = edge(rgb2gray(frizzy), 'canny');
froomer_e = edge(rgb2gray(froomer), 'canny');
% TODO: Display common edge pixels
imshow(frizzy_e & froomer_e)
```
- ![[Image gradients and edges 2023-10-04 11.04.47.excalidraw]]
- ![[Pasted image 20231004110620.png]]