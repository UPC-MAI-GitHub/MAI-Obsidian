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
- *Image magnification*: increase the resolution of the image maintaining concordance.
- *Image reduction*: deleting some pixels without loosing the general info of the image
- *Photometric resolution*: different pixel values on each color channel.
- A *histogram* of an image represents the *frequencies of pixel intensities*.
	- A measure of image quality
	- *Manipulate the histogram*
		- Contrast enhancement: increase the amount of values present in the image (not the size)
			- Minimum-maximum contrast stretch
			- Percentage linear contrast stretch
### Linear filters














