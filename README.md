# **Finding Lane Lines on the Road** 
[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)

<img src="examples/laneLines_thirdPass.jpg" width="480" alt="Combined Image" />

Overview
---

When we drive, we use our eyes to decide where to go.  The lines on the road that show us where the lanes are act as our constant reference for where to steer the vehicle.  Naturally, one of the first things we would like to do in developing a self-driving car is to automatically detect lane lines using an algorithm.

In this project you will detect lane lines in images using Python and OpenCV.  OpenCV means "Open-Source Computer Vision", which is a package that has many useful tools for analyzing images.


The Project
---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report

**Example**

Before processing:
![Preprocess](./test_images/solidWhiteCurve.jpg)

After processing:

![Processed](./test_images_output/solidWhiteCurve.jpg)

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 6 steps. First, I converted the images to grayscale, then I applied smoothing.

After that, image went through Canny edge detection and got cut so that only highway was left. 

With that image, since only lane lines were visible, I extracted the coordinates of the lines through Hough Transform.

Using those coordinates, I drew lines over the lanes.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by creating 4 arrays

that holds x and y coordinates of the right and left lane. Slope of the right lane was bigger than 0.5, while the left lane's slope was

smaller than -0.5. Using that, I sorted them out but added an upper limit for the slope to filter out outliers. After I found the slope

I found the starting and ending points and drew a line through them. 


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when lanes curve.

Currently, polifyt is of the first degree and cannot draw curved lines.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to use higher degree polyfit to draw curved lines.

Another potential improvement would be to use clustering algorithm instead of polyfit. That would include points within certain radius

where radius would be the distance between dashed lines.


