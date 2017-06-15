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

The pipeline consists of several steps. First, I filter images for white and yellow. Then I apply some dilation on the image to reduce the noise. On the filtered out and dilated image, I apply Canny edge filter. Using Hough transformation, I get the lines. The Hough lines are filtered out by slope and size 

In order to draw a single line on the left and right lanes, I average out all left and right lanes by summing up all "slopes" and dividing the sum by total number of left and right hough lanes (positive and negative slopes). To smooth out transition of the lane markers from frame to frame, I kept track of the previous lane positions. If for a given frame I cannot determine lanes, I use the previous frame values to draw the lanes




### 2. Identify potential shortcomings with your current pipeline


There potential shortcoming of the proposed method:

    a) the edge detection of light sensitive
    b) if the algorithm cannot determine lanes for too many frames, it may draw lanes that are way off.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to use a gaussian blur to smooth out noisy patches of white/yellow areas.

Another potential improvement could be to keep track of number of frames for which the algorithm could not establish the lanes
If the situation arises when the lanes are not established for too many consequite frames, make the algorithm adaptive to weed out the lanes. 
