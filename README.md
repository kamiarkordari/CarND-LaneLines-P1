# **Udacity Self-Driving Car Engineer Nanodegree - Finding Lane Lines on the Road**
[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)

<img src="examples/laneLines_thirdPass.jpg" width="480" alt="Combined Image" />

Overview
---
When we drive, we use our eyes to decide where to go.  The lines on the road that show us where the lanes are act as our constant reference for where to steer the vehicle.  Naturally, one of the first things we would like to do in developing a self-driving car is to automatically detect lane lines using an algorithm.

In this project we detect lane lines on the road from images and videos taken by a camera on the car.

We use Python and OpenCV. The file containing the project code is P1.ipynb, which is a Jupyter Notebook. This Notebook is exported as an HTML file to P1.html for easier viewing of the results.  

The requirements of the project are detailed here: [project rubric](https://review.udacity.com/#!/rubrics/322/view)


Pipeline
---
In order to detect lane lines on an image or frame of a video stream, we apply the following pipeline to the image or video frame:
1. Convert image to grayscale
2. Apply Gaussian Blur smoothing to reduce noise for the edge detection step
3. Apply Canny Edge Detection
4. Apply region of interest to mask the lines out of this region
4. Apply Hough transform to detect lines
5. Draw lines by following these steps:
-- Separate lines into right and left based on being negative or positive
-- Filter out lines with unreasonable slope values by comparing to some thresholds
-- Calculate a weighted average of slopes
-- Fit a line to left and right points
6. Overlay left and right lines onto the original image


Shortcomings
---
The performance of the lane finding algorithms may degrade in these situations:
- Low color contrast between road and lines, e.g. due to rain
- low lighting e.g. at sunset
- Curved roads
- When there is no lanes on the road, e.g. on dirt road
- When lanes are temporarily not straight, e.g. when merging with another road
- When road goes on a hill or vertical curvature
- When other cars cover the lanes


Improvements
---
We can use these methods to make our algorithm generalize better for a wider range of circumstances:
- Non-linear fit for the curved lanes
- Use parameter filtering to make changes from one frame to another smooth
- Impose a maximum change in parameters (e.g. slope of a line) from one frame to another. e.g. a parameter cannot change more than 10% from one frame to another


License
---
This project is copyright is under MIT License.
