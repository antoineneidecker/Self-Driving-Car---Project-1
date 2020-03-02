#Project 1 Report

### 1. The Pipeline

My pipeline consists of 5 steps:


1. First, the first step is to apply a greyscale and slightly blur the image in order to filter the slight changes in colour gradient, and be left with only the sharp ones. This makes it easier for the Canny filter to pick up on the lanes in the image and discard the most other small lines.

2. The next step is to apply a Canny filter on our image. This filter brings out the sharp increases in gradient (i.e. the edges).

3. We then apply a mask on the image to isolate the lower portion of the image where we will find the lane lines. 

4. We now apply a Hough Filter in order return the lines on the pictures. 

5. Now that we have the main lines isolated, we need to find the two main lane lines, on either side of the car. We do this in several steps (in the draw_lines method). First we remove all lines with slopes between 0.4 and -0.4. These values have been chosen as they are too shallow to be lane lines. Then, we take a look at the remaining slopes. We first separate the slopes in two groups, the ones greater and the ones smaller than the mean slope. We then aim to remove the outliers. We do this by taking the standard deviation of each group and removing any line which is one standard deviation over the mean. We finally return the mean slope of each group. Now that we have the slope of the left lane and the right lane, we must find a point along which we will draw the line. We do this by looking at the magnitude of the different hough lines and choosing the two longest lines (one with a positive slope and the one with a negative slope*). We then return the midpoint of each lines. To get the cartesian equation of the line, we solve for the y-intercept term. Finally, we we define boundaries for drawing top and bottom parts of the lane. 


We now have our lanes and return them superposed on the input image.


*Keep in mind that we are working in a reversed coordinate frame (with respect to the traditional Cartesian coordinate system). Here the origin is at the top left of our plane. Therefore positive and negative slopes are also reversed.

### 2. Shortcomings

This model didn't apply well on the challenge test. It actually didn't run because of the following. I suspect the values we chose for the Canny filter, were not appropriate in this low contrast setting. This caused the filter to discard the lane lines and ran into the case where it didn't find any lines at all! This made the code crash. One possible solution would be to do some adaptive analysis of the image (for instance with Otsu's thresholding method) and apply the appropriate parameters to the Canny filter at every frame.

Another shortcoming is that this method does not take into account curved lanes. This is definitely a shortcoming which may encounter a lot of problems on the road.



### 3. Improvements

A possible improvement would be to incorporate the slope found in the previous frame in order to estimate the one in the current frame. 


I suspect that a better solution to this problem could stem from CNNs which could be trained to recognise curved lines and lines in all kinds of different lightings. Computer vision methods such as YOLO2 could be appropriate and not too costly computation wise.

