# **Finding Lane Lines on the Road** 

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe my pipeline.

My pipeline consisted of 5 steps. 
1 Covert the images to grayscale,and save it

2 Apply gaussian filter to the gray images which we got from step1

3 Apply canny function to the images to get the edges

4 Make a mask which cover the area we interest, ignore all the data which not covered by the mask

5 Run Hough transform to the edges inside the mask and draw the line on the image.

6 Mix the line we get with the original image

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by
1 Do a filtering to get all the lines which located in the left side and has the slope smaller then 1 as left side lines group, for the lines which located in the right and has slope bigger then 1 as right side lines group.

2 Calculate the mean value of all the points, and get two new lines

3 Use the slope of these two line to cross with the edge of we interest area 

4 draw the line on the image
  


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when there are some cars inside the image and included in the area which we interest. It will introduce a lot of noise when we calculate the lines  

Another shortcoming could be if the car is doing a sharp U turn, then in the image there will be only one line. For example, if we take a left U turn, the left side line will not be detected in the image. and right side line will occupy whole image.

One more issue might be under current processing method, the line might have a very big jump between last second line and this second line, this could be soled using Kalman filter


### 3. Suggest possible improvements to your pipeline

A possible improvement could be introduce Kalman filter to forbid big jump of lines.

Another potential improvement could be to filted some error points 
