# **Finding Lane Lines on the Road** 

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./test_images_output/orig.png "test_imgs"
[image2]: ./test_images_output/gray.png "gray_imgs"
[image3]: ./test_images_output/soft.png "soft_imgs"
[image4]: ./test_images_output/canny.png "canny_imgs"
[image5]: ./test_images_output/clip.png "clip_imgs"
[image6]: ./test_images_output/clip2.png "clip2_imgs"
[image7]: ./test_images_output/out.png "out_imgs"

---

### Reflection
### Here is all my test images 
![alt text][image1]
### 1. Pipeline description, explaining how i modified the draw_lines() function.

My pipeline consisted of 5 steps. 

## I. I converted the images to grayscale
![alt text][image2]
## II. I applied gaussian filter to smooth the sharp edges
![alt text][image3]
## III. I applied the canny algorithm to detect the edges of the image
![alt text][image4]
## IV. I applied a clipping mask to select only the area of interest that is includes the lane lines
![alt text][image5]
![alt text][image6]

then i applied hough_lines function to extract the lines from the output image of canny 
but the result is alot of lines disonected 

# In order to draw a single line on the left and right lanes, I modified the draw_lines() function 
to connect and average only 2 lane lines
i sperate the 2 lane line by slope into 2 categories 
negative slope which represent the left lane
positive slope which represent the right lane
a weighted average is applied by the length of every line to get the average line (slope and intercept)

## V. i compined the detected lane lines to the original image
![alt text][image7]

### 2. Identify potential shortcomings with your current pipeline

One potential shortcoming would be what would happen when 
the colour of the line is not clear due to the shades of trees 

### 3. Suggest possible improvements to your pipeline

A possible improvement would be to apply a coulor transformation
