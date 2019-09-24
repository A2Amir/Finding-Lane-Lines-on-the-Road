# **Finding Lane Lines on the Road** 


**Finding Lane Lines on the Road**

The goal of this project are the following:

In this project, we will use the tools to identify lane lines on the road.  we will  develope a pipeline on a series of individual images, and later apply the result to a video stream (really just a series of images). Check out the video clip "raw-lines-example.mp4" (also contained in this repository) to see what the output should look like after using the helper functions below. 

<video controls="controls">
  <source type="video/mp4" src="./test_videos/solidWhiteRight.mp4"></source>
  <p>Your browser does not support the video element.</p>
</video>
![Video](./test_videos/solidWhiteRight.mp4)


---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 6 steps.

1.First, I converted the images to grayscale
2.I applied on the grayscale image a gussian filter with the kernel of size 5.
3.After determining the min and max thresholds for the canny transformation, I found the edges.
4.on the canny image, the region of the interest was drwan by using vertices.
5.Based on the region of the interest and with help of the hough_lines function the lane lines were extracted.
6.at the end I added the weights of the original image and the lane line image.


In order to draw a single line on the left and right lanes, I modified the hough_lines() function by sperating slopes and intercepts belonging to the left  or right lane line using np.plolyfit then to calculate the coordinates of the first and end points of each lane line I averaged them on the zero axis and the make_coordinate function was used to calculate the coordinates of the left and right lane lines.

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when curves will be tilted.

Another shortcoming could be in determination of vertices and regulation of parameters. 


### 3. Suggest possible improvements to your pipeline

A possible improvement would be in curven when auto goes left or right.

Another potential improvement could be to automatic determination of parameters and verices.

