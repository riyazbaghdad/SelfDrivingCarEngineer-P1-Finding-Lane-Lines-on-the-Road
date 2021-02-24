# **Finding Lane Lines on the Road** 
[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)

<img src="examples/laneLines_thirdPass.jpg" width="480" alt="Combined Image" />

Overview
---

When we drive, we use our eyes to decide where to go.  The lines on the road that show us where the lanes are act as our constant reference for where to steer the vehicle.  Naturally, one of the first things we would like to do in developing a self-driving car is to automatically detect lane lines using an algorithm.

In this project you will detect lane lines in images using Python and OpenCV.  OpenCV means "Open-Source Computer Vision", which is a package that has many useful tools for analyzing images.  

# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 6 steps.

- Convert Image to Grayscale.
- Apply Gaussian Blur to lower the noises and smooth the image.
- Apply Canny Edge detection to extract the edges.
- Identify the coordinates of the polygon to extract the Region of interest
- Apply Hough line transform on the ROI image to to detect and mark the line segments of the lane.
- Apply/Draw the transform lines on the original image and display the detected lane lines on the image.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by creating a helper function "draw_lines_helper()" that identifies the left and right line lane points, averages the hough lines points and extrapolates the line segments using the equation of straight line(y = mx + c). Finally, the new lines are drawn on the original image. 


### 2. Identify potential shortcomings with your current pipeline

Potential shortcomings:

- The algorithm is unreliable when the lanes are sightly curved due to fixed parameters and also the extrapolation is calculated based on the general equation of line.
- The parametes are hard coded and hence not robust on new data.
- The data doesnot contain any scenarios where other cars could possibly 
block the view of lanes infront of us. Provided the case, the lane lines 
may not be clear and could potentially lead to fatal issues.
- Clearly Hough Transform fails on highly curved turns.


### 3. Suggest possible improvements to your pipeline

Possible improvements:

- To fix the hardcoded parameters issue, one could employ Neural networks to 
detect the lane lines, however we need to provide tons of data. If done it 
could possibly fix the curved line detection issue as well.




