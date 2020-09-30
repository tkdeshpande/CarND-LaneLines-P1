# **Finding Lane Lines on the Road** 

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report
---

### Reflection

### 1. Pipeline:

#### 1.1. Building the pipeline:
1. Grayscaled the image
2. Applied Gaussian Blur of size **3**
3. Used Canny Edge Detection with 
   - lower_threshold = 50
   - higher_threshold = 150 
4. Region of Interest
   - lower_left  = (130, 540)
   - upper_left  = (470, 315)
   - upper_right = (490, 315)
   - lower_right = (890, 540)
5. Hough Lines
   - rho = 1
   - theta = np.pi/180
   - hough_threshold = 30
   - min_line_len = 5
   - max_line_gap = 2
6. Weighted Image Processing

*Above values are selected based on visual inspection and hence are subject to change for individuals.*

#### 1.2. Averaging and Extrapolation using draw_lines() function:
1. Calculated slope and center for each line available to the draw_lines function.
2. Classified the slope and center values between left and right side ones.
3. Calculated average values of the classified slopes and center values.
4. Identified either side line extremeties using slope, center and y(min)=315 and y(max)=540

Testing the pipeline:
- Listed all the sample images available and batch processes all to see the effect of changes in parameters.
- Also identified frames from the vidoes that were not performing well and added them to the samples for processing.


### 2. Shortcomings

1. The current approach is primarily designed for straight lane lines due to the nature of the test data. Hence if this video is tested on curved roads, it would fail.
2. Another possible limilation is that even on straight lanes, the vehicle needs to be centered in the lanes else the Region of Interest selection would fail.


### 3. Suggest possible improvements to your pipeline

1. A possible improvement would be to select a dynamic Region of Interest that would allow to detect lane lines even if the vehicle moves laterally.
2. Another possible improvement would be to have Canny threshold metric histogram values dyanamically set appropriate threshold values.
