# **Udacity Self-Driving Car Engineer Nanodegree - Finding Lane Lines on the Road**
[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)

<img src="examples/laneLines_thirdPass.jpg" width="480" alt="Combined Image" />

Overview
---

When we drive, we use our eyes to decide where to go.  The lines on the road that show us where the lanes are act as our constant reference for where to steer the vehicle.  Naturally, one of the first things we would like to do in developing a self-driving car is to automatically detect lane lines using an algorithm.

In this project we detect lane lines on the road from images and videos taken by a camera on the car. We use Python and OpenCV.  

This repo contains the code written to complete the first project on Udacity Self-Driving Car Nanodegree.

To file containing project code is P1.ipynb.

To meet specifications in the project, take a look at the requirements in the [project rubric](https://review.udacity.com/#!/rubrics/322/view)


Pipeline
---

Start with an image or frame of a video stream.
1. Convert image to grayscale
2. Apply Gaussian Blur smoothing to reduce noise for the edge detection step
3. Apply Canny Edge Detection
4. Apply region of interest to mask the lines out of this region
4. Apply Hough transform to detect lines
5. Draw Lines:
- Separate lines into right and left line based on being negative or positive. In order to find a single line for the left or right lanes, we filter out the unreasonable results.
- Filter out lines based on slope value
- Calculate a weighted average of slopes
- Fit a line to left and right points
6. Overlay left and right lines onto the original image


Shortcomings
---
Performance will degrade in these situations:
- Low contrast between road and lines colors, e.g. due to rain
- When it is dark e.g. at sunset
- Curved roads
- When no lanes in the road, e.g. on dirt road
- Hills or vertical curvature
- When other cars cover the lanes

Improvements
---
We can use methods that generalize better for a wider range of circumstances. These includes:
- non-linear fit for the curved lanes
- Use parameter filtering to make changes from one frame to another smooth.
- Impose a maximum change in parameters from one frame to another. e.g. a parameter cannot change more than 10% from one frame to another.

License
---
This project is copyright is under MIT License.
