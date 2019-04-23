# **Finding Lane Lines on the Road** 

**Finding Lane Lines on the Road**

The goal of this project:
* Make a pipeline that finds lane lines on the road


### Pipeline

1 - Resize image to a predefined value. For this pipeline I used 960 width by 540 height.
This ensures the images are scaled consistently

2 - Convert the raw image into a grey scale image

3 - Use a Gaussian Blur with a kernel of 5 to smooth out image to reduce false positives

4 - Find edges uses Canny Edge detector

5 - Create a mask to limit the area we are inspecting for lines. Having a nice mask was one
of the bigger factors in getting a good result.

6 - Perform a probabilistic Hough line function on the masked edged image.

7 - Segregate the lines into left and right lane based on the slope of the line. I considered any lines with slope greater
than 0.5 from the right lane and any line with a slope less than 0.5 from the left lane. Any other lines are rejected.

8 - Average the segregated lines to produce one line function for each lane line that we can extend to the horizon and to the bottom of the image


### Shortcomings

This pipeline is dependent on color thresholds that are typical to road markers (white and yellow). This causes problems when the road is
lighter in color as depicted in the challenge video. I am sure videos of night time drives would throw off this pipeline as well.


### Possible Improvements

Look at edge detectors less dependent on color thresholds or look at different color conversions such as HSV. Looking at things like light intensity could be interesting as most line markers are reflective.