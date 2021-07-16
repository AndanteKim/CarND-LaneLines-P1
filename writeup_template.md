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
[image2]: ./examples/canny.png	"Canny"
[image3]: ./examples/hough.png "Hough Lines"
[image4]: ./examples/result.png "Result"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I converted the grayscaled images to gaussian noise kernel. Second, I converted the grayscaled and gaussian images to the canny algorithm to detect edges in the images. Third, I set four-sided vertices like a polygon(trapezoid) to configure detection range within the edges. If the pixels of images are out of range of the polygon, then they are set to black color(i.e. zero value). Fourth, I set parameters of hough lines (i.e. rho, theta, threshold, minimum line length, and maximum line gap) to detect lanes for each image. Then, the images will show red lines when it detects white or yellow lanes based on the parameters. Fifth, I combined the original images with the red lines filtered from hough_lines function through weighted_img(weighted image) function. Eventually, we would see the ideal images detecting lanes as red lines.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by adding some red lines at the end of y coordinates of images.
Before modifying draw_lines() function, the detecting red lines is somewhat short as below.

If you'd like to include images to show how the pipeline works, here is how to include an image:

![alt text][image1]
![alt_text][image2]
![alt_text][image3]
![alt_text][image4]

### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when there is changing image sizes. If the sizes are different for each pictures, the detection function could not find some edges. Then, hough lines draw red lines wrongly.

Another shortcoming could be when there are poor quality of images. For example, if there exists any poor quality of images, the detection function would not work. This is because it cannot find a feature clearly or could find a feature wrongly.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to make my own detection algorithm which has flexible range of detection depending on the size of images.

Another potential improvement could be to create an algorithm when there occur special cases such as poor quality of images. For example, I need to analyze why my current algorithm cannot detect some special cases. Then, I create an improved algorithm and test images over and over again until the algorithm detects lanes for each image well.
