![[CV-2324_Class1_2IntroCV.pdf]]

## Notes

### What is CV?
- CV --> dicover what is present in an image scene
- CV --> camera linked to a computer
- Goals
	- Get the story behind the image
	- Obtain data for other tasks (navigation)
- Humans can interpret images without so much effort
- 1/3 humain brains resources to process information from eyes
### Brief story of CV
- Summary
	- 1966 Marvin Minsky: linking a camera to a computer and getting the computer to describe what it saw
	- 1960’s: interpretation of synthetic worlds as a composition of 3D objects (depth perception). 
	- 1970’s: some progress on interpreting selected images (object contours and labelling parts for seg.) 
	- 1980’s: ANNs come and go; shift toward geometry and increased mathematical rigor 
	- 1990’s: face recognition; statistical analysis in vogue 
	- 2000’s: broader recognition; large annotated datasets available; video processing starts 
	- 2010’s: ANN is back to stay, Deep learning. 
	- 2030’s: autonomous vehicles, robot uprising?
- Mark's approach
	- Sequence of data transformation
		- Image analysis
		- Surface inference
		- 3D reconstruction
		- ![[Pasted image 20230919145143.png]]
		- *INVERSE PROBLEM:* Recover some unknowns given insufficient information to fully specify the solution.
	- The environment in complex
### Problems/Tasks of CV
- Gap between pixels and meaning
- Low level feature extraction (edger, corners)
- *Stereo vision*: infer 3d structure of the scene
- *Shape from texture*: infer surface orientation analyzing texture statistics
- *Scene reconstruction*: get a 3D model from one or more images
- *Image segmentation*: divide image pixels into multiple segments to simplyfy representation
- *Image registration*:  transform different sets of images into one coordinate system
- *Motion estimation*: determine motion vectors from frame to frame
- *Human pose estimation*: track specific points on the human body
- *Object and person recognition*: identify objects
- *Scene and context categorization*
### Difficulties of CV
- Variation of point of view
- Illumination
- Scale
- Cluttered background
- Movement
- Occlusion
- Intra-class variation (variations in the same kind of objects)
- Ambiguity of the implicit perception
### Applications
- Data extraction from images
	- OCR (optical character recognition)
- Safety and autonomous driving
- Cultural inheritance
	- Restauration
- Security and surveillance
- Medical Imaging and health
- Confort and fun
### Videos to watch
- “How computer vision works”: https://www.youtube.com/watch?v=OcycT1Jwsns 
- “What Is Computer Vision & Why Does It Matter?”: https://www.youtube.com/watch?v=OnTgbN3uXvw