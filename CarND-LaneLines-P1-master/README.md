# Finding Lane Lines on the Road

<img src="examples/laneLines_thirdPass.jpg" width="480"/>


## Finding Lane Pipeline

In this work we'll try to detect lane in test images and video using OpenCV Library.


To find Lane we'll use Canny to detect edges in a pre-process gray image, with these Edges we going to use Hough Transformation to find lines, which we'll use to draw lines in image. 


### To reach our objective we going throught some steps:

* Create a Grayscale image
* Apply blur to avoid noise
* Find Edges Using Canny
* Define Vertices to create a Region of Interest
* Use Hough Transformation to find Lines
* Merge Lines and original image
* Create a pipeline function
* Test with test images


## 1. Reflection

My pipeline consisted of 3 parts:

### Part One

First, I converted the images to grayscale, then I applied blur to avoid noise in the edges detection process. With the processed image I used Canny detection to find edges, this returned many irrelevant edges, so I defined vertices to make a region of interest. After that, I used Hough transformation to get lines from these edges. Finaly I drawed this lines in the original image. 

### Part Two

In the second part, I changed draw_lines testing each row to see if the slope was positive or negative, then I've created 2 groups of lines basead in yours slopes. Then, I calculated start and ends points to make lines with a standar lenght. Finally, I used numpy to get mean and make  the function return only 2 lines with opposites slopes.

### Part Three

In final part, I tested and tuned the parameters looking for the best fit in images and videos, the results were very satisfatory, but I couldn't performed well with the challenge video, I belive that more advanced and complex algorithims are needed to find lanes in that conditions. 


## 2. Potential shortcomings 


In situation where many edges were detected, the function Draw_lines calculated the mean of these lines, and the result could be wrong, this happens and can be very visible in the challenge video. 


## 3. improvements

I changed the Draw_lines function to consider only lines with slope inside a determined range, which is the most likely values to slope, avoiding unecessary lines detection.

I did a fine tuning in the parameters to find the optimum balance to the challlenge video, this rerturned a better result. 

## 3. Possible improvements

Use Color Selection together to the actual method to improve lanes detection and improve the algorithm to avoid or fit to curves. 

Make the algoritim consider a mean of n last lines to calculate the next line will smooth and help avoid errors.

