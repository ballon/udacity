# **Finding Lane Lines on the Road** 

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

First, I've reduced image size which helped to deal with pixel noise associated with data and speed up the whole testing process.
Later in order to detect edges, I've converted them to a grayscale and leveraged canny edge edge detection methond from OpenCV. I've tuned a parameters a bit and [80, 120] seems to work well on input data.
Later I tried to use haugh transformation to find lines, but only limited that logic for a smaller trapezoid located at the bottom of the image (because that is where road is located visually most of the time). Again, I've tuned parameters a bit and went with some which worked well on most of the data provided.
In order to find the whole extent of every lane, I've extended every lane drawn up till the intersection with image bottom.
I've also added few hacks which helped to get reasonable result on challange.mp4 - I've filtered our lanes which were too close to be horizontal or vertical.


### 2. Identify potential shortcomings with your current pipeline
Algorithm can only detect straight lines, which is not always how it is in real life.
It also rely on a bunch of tuned parameters which works well for current environment, but probably won't work for other environments (e.g. city street, night driving, etc).
The output is very 'jumpy' - would be nice to have a smooth video as output.


### 3. Suggest possible improvements to your pipeline
We can deal with 'jumpy' issue described above by mixturing output for consecutive frames (they mostly should be identical).
We could also tune parameters even more to get a nice image for the input provided, but that won't solve issue fundamentally because parameteres might be different for other environments. We could also leverage ML to get lines.
