# **Finding Lane Lines on the Road** 


**Finding Lane Lines on the Road**

The goal of this project are the following: In this project, we will use the tools to identify lane lines on the road.  we will  develope a pipeline on a series of individual images, and later apply the result to a video stream (really just a series of images). Check out the [Video clip](./examples/P1_example.mp4) "P1_example.mp4" (also contained in this repository) to see what the output should look like after using the helper functions below. 

<video controls="controls">
  <source type="video/mp4" src="./examples/raw-lines-example.mp4"></source>
  <p>Your browser does not support the video element.</p>
</video>



---

### Reflection

### 1.The pipeline:

The pipeline consisted of 7 steps:I'd like to include images to show how the pipeline works, here is how to include an image: 


1.  First read  the orginal image
 <p align="right">
<img src="./test_images/solidYellowLeft.jpg" alt="orginal image " width="500" height="300" />
<p align="right">


2.  Then I converted the images to grayscale

 <p align="right">
<img src="./examples/grayscale.png" alt="grayscale image " width="500" height="300" />
<p align="right">
  
3.  I applied on the grayscale image a gussian filter with the kernel of size 5.

 <p align="right">
<img src="./examples/blur.png" alt="blur image " width="500" height="300" />
<p align="right">
  
4.  After determining the min and max thresholds for the canny transformation, I found the edges.

 <p align="right">
<img src="./examples/canny.png" alt="canny image " width="500" height="300" />
<p align="right">
  
5.  on the canny image, the region of the interest was drwan by using vertices.
 <p align="right">
<img src="./examples/RoI.png" alt="RoI image " width="500" height="300" />
<p align="right">
  

6.  Based on the region of the interest and with help of the hough_lines function the lane lines were extracted.

 <p align="right">
<img src="./examples/lines_img.png" alt="lines_img image " width="500" height="300" />
<p align="right">
7.  At the end I added the weights of the original image and the lane line image.
 <p align="right">
<img src="./examples/weighted_img.png" alt="weighted_img image " width="500" height="300" />
<p align="right">

In order to draw a single line on the left and right lanes, I modified the hough_lines() function by sperating slopes and intercepts belonging to the left  or right lane line using np.plolyfit then to calculate the coordinates of the first and end points of each lane line I averaged them on the zero axis and the make_coordinate function was used to calculate the coordinates of the left and right lane lines.





  
### 2. Identify potential shortcomings with your current pipeline

<video width="960" height="540" controls>
  <source src="./test_videos/solidWhiteRight.mp4}">
</video>
One potential shortcoming would be what would happen when curves will be tilted.

Another shortcoming could be in determination of vertices and regulation of parameters. 


### 3. Suggest possible improvements to your pipeline

A possible improvement would be in curven when auto goes left or right.

Another potential improvement could be to automatic determination of parameters and verices.

