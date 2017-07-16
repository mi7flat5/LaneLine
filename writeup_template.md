# **Finding Lane Lines on the Road** 

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
Find lanes on a road in an image, and generalize the process to work for video
### Reflection

The first step in my image processing pipeline is to isolate the lane line. 
To do this I used some thresholding functions to isolate only yellow and 
white parts of the image. This process yeilds binary images, 
so I created a depth 3 image with each layer being the same binary image. 
This was done so that the pipeline can work as though it were working with 
the origional color image. 
the next step is the create a grayscale image. The image is already only 
black and white but I ran it through this function to process the image 
into an image that the next step is expecting. 
I then run the image through gaussean blur, which helps smooth the image 
before canny edge detection. 
The next step is to create an image from the gradients in the blurred image. 
Next I create a mask that will allow the line creation step to ignore parts 
of the image that are not in a region of interest. 
Then I create an array of lines and 
iterate through it and seperate 
right and left lane lines. I then find the minimum 
and maximum extents of each line, and move the extentst 
along a vector direction that will increase the length of the line. 
Then I add these lines to an empty image. 
The final step is to add the line image to the origional image.  


### 2. Potential shortcomings with current pipeline


The biggest shortcoming to my approach is that in some parts of the videos it can be a little jittery. 
Another shortcoming is that occasionally it will pick up extranous artifacts and make a strange line. This doesnt happen often or for long but it does happen occasionally. 



### 3. Possible improvements to pipeline

In order to address the jittery issue, I think a good approach would be to cache left and right lines somehow. Then I could compare new lines against the slope of previous lines and if it is to far outside 
a given tolerance I could just use the line from the previous frame. I could also keep a running average of the lines and comapere new lines against that. 
in order to address the extraneous artifact problem. I could create a tighter mask. perhaps a mask that masks out the middle of the triangle also and only searches a small line region to the left and right. This would take a lot of fine tunning and I'm not sure it would be terribly effective in a real time situation. 
I think the best approach would be to ignore lines that are greater than or less than a certain angle tollerance. 

### 4. Final thoughts
I'm relatively happy with how this turned out. 
I would like the yellow line video to perform a little better. 
If I optimize the pipeline to work with
that video the challenge suffers. 
As I have it now the challenge video works well and the 
yellow line video has a couple imperfections. 
Ideally I'd have more logic controlling the masking and parameter choices, 
but I think this is perhaps overkill for the current project. 
I'd like to keep learning. 
This was tremendous fun for me. 