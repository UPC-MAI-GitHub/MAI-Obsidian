![[CV-2324_Class1_2IntroCV.pdf]]

## Notes

### What is CV?
- *CV* --> discover *what is present in an image* scene
- CV --> camera linked to a computer
- **Goals**
	- *Get the story behind the image*
	- *Obtain data for other tasks (navigation)*
- Humans can interpret images without so much effort
- 1/3 humain brains resources to process information from eyes
### Brief story of CV
- Summary
	- *1966* Marvin Minsky: l*inking a camera* to a computer and getting the computer to describe what it saw
	- *1960*’s: *interpretation of synthetic worlds* as a composition of 3D objects (depth perception). 
	- *1970*’s: some progress on interpreting selected images (*object contours* and *labelling parts* for seg.) 
	- *1980*’s: *ANNs* come and go; shift toward geometry and increased mathematical rigor 
	- *1990*’s: *face recognition*; statistical analysis in vogue 
	- *2000*’s: broader recognition; *large annotated datasets* available; *video processing* starts 
	- *2010*’s: ANN is back to stay, *Deep learning*. 
	- *2030*’s: *autonomous vehicles?*, robot uprising?
- Marr's approach
	- Sequence of data transformation
		- ![[Pasted image 20240112001540.png]]
		- *INVERSE PROBLEM:* Recover some unknowns given insufficient information to fully specify the solution.
	- The *vision environment in complex*: *not accessible*, *continuous*, *non deterministic*
### Problems/Tasks of CV
- *Gap between pixels and meaning* (*digital image* $\longrightarrow$ *a matrix of numbers*)
- Low level *feature extraction* (edger, corners)
- *Stereo vision*: infer 3d structure of the scene
- *Shape from texture*: infer surface orientation analyzing texture statistics
- *Scene reconstruction*: get a 3D model from one or more images
- *Image segmentation*: divide image pixels into multiple segments to simplify representation/object recognition
- *Image registration*:  transform different sets of images into one coordinate system
- *Motion estimation*: determine motion vectors from frame to frame
- *Human pose estimation*: track specific points on the human body
- *Object and person recognition*: identify objects
- *Scene and context categorization*: statements of objects and actions or facts passing in a scene
### Why is CV hard?
- *Variation of point of view*
- *Illumination*
- *Scale*
- *Cluttered background*
- *Movement*
- *Occlusion*
- *Intra-class variation* (variations in the same kind of objects)
- *Ambiguity of the implicit perception*: Many 3D scenes can give the same 2D scene (*misleading perspective* caused by near and far objects)
### Applications
- *Data extraction* from images
	- OCR (optical character recognition)
- *Safety* and *autonomous driving*
- Cultural inheritance
	- *Restoration*
- Security and *surveillance*
- *Medical Imaging* and health
- Comfort and *fun*
### Videos to watch
- “How computer vision works”: https://www.youtube.com/watch?v=OcycT1Jwsns 
- “What Is Computer Vision & Why Does It Matter?”: https://www.youtube.com/watch?v=OnTgbN3uXvw

## Udacity videos notes
- Why to study CV?
	- Images become ubiquitous in production and consumption, therefore the applications to manipulate images are becoming core
	- Extract info from: surveillance, 3D medial imaging models, motion capture
- CV Applications
	- Face detection
	- Text detection on images
	- Object detection in supermarkets
	- Capturing the shape of people for 3D modeling
	- Smart Cars - Self driving cars
	- Sport rules analysis on real time
	- Videogames --> kinnect
- Why is this so hard?
	- Squares *A* and *B* are of the *same color*, even when *your brain tells you otherwise*
	- ![[Pasted image 20231003222831.png]]
	- 