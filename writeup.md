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

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I blurred the images with gaussian kernal. After that, I detected edges from images using Canny operation and then created a mask to choose the region which only contains the lane lines before the car. Finally, I found the lane lines on the road with the help of Hough Transform function. 

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by fitting the full lane lines based on the segment points identified with Hough Transform. First, I splitted the identified points into left and right two parts. Then, I separately fitted the full lane line using OpenCV fitLine function. At last, I drawn the full lane lines on the image. 

![image2][/test_images_output/solidWhiteCurve.jpg]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when missing most parts of the lane lines in the video causing by illumination etc. 

Another shortcoming could be that the location of the mask region is fixed in the pipeline. It would fail when the car changes its direction of forward motion. 


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to use the symmetry of the lane lines to make the detection pipeline more robust. 

Another potential improvement could be to adaptively adjust the location of the mask region according to the car's direction of forward motion. 
