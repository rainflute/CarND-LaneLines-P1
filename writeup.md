# **Finding Lane Lines on the Road** 

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

* The pipeline takes a colorful image and apply gray scale to keep just one color channel
* Apply Gaussian Smoothing
* Set thresholds and apply Cany Edge Detection to find edges
* Set a four sided mask to apply to the image
* Apply Hough transform and draw the lines
* Draw the lines on the original image

More details on draw_lines():

The modification I made is to calculate the slope and y-intercept for each line. Looking at the images, the range of the slopes should roughly in the range of (-1, -0.5) and (0.5, 1). After excluding the lines whose slopes are out of range, I seperate the lines into 2 groups, one for left line and the other one for right line. Then, I calculate average slopes and y-intercepts of both right lines and left linse and use the avarege as the final lines. Finally, I draws the left line and right line in the masked area.

### 2. Identify potential shortcomings with your current pipeline

The pipeline works pretty fine when the road is darka and line is white. The pipeline sometimes misses the line if the road is grey and line is yellow, like what is in the challenge video.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to use a yellow mask and white mask to filter yellow lines and white lines and apply them on the top of the greyscale image before applying Gaussian Smoothing
