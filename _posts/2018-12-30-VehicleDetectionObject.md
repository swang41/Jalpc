---
layout:     post
title:      "Self-Driving-Car: Vehicle Detection Object"
date:       2018-12-30 19:20:00 -0800
categories: [MACHINELEARNING]
---

# **Vehicle Detection Project**
---

**Vehicle Detection Project**

The goals / steps of this project are the following:

* Perform a Histogram of Oriented Gradients (HOG) feature extraction on a labeled training set of images and train a classifier neural network classifier with bagging.
* Implement a sliding-window technique and use your trained classifier to search for vehicles in images.
* Run your pipeline on a video stream (start with the test_video.mp4 and later implement on full project_video.mp4) and create a heat map of recurring detections frame by frame to reject outliers and follow detected vehicles.
* Estimate a bounding box for vehicles detected.
<hr/>

## Here I will consider the rubric points individually and describe how I addressed each point in my implementation.  

---

### Histogram of Oriented Gradients (HOG)

#### 1. Explain how (and identify where in your code) you extracted HOG features from the training images.

The code for this step is contained in the fifth and sixth code cells of the IPython notebook (with helper functions in lines #47 through #90 of the file called `extract_features.py`).  

I started by reading in all the `vehicle` and `non-vehicle` images.  Here is an example of one of each of the `vehicle` and `non-vehicle` classes:

<img src="{{ site.img_path }}/SDC/car_notcar.png" alt="Car vs Notcar" class="img_center"/>

I then explored different color spaces and different `skimage.hog()` parameters (`orientations`, `pixels_per_cell`, and `cells_per_block`).  I grabbed random images from each of the two classes and displayed them to get a feel for what the `skimage.hog()` output looks like.

Here is an example using the `YCrCb` color space and HOG parameters of `orientations=9`, `pixels_per_cell=(8, 8)` and `cells_per_block=(2, 2)`:

<img src="{{ site.img_path }}/SDC/example_hog_features.png" alt="Hog Features" class="img_center"/>

#### 2. Explain how you settled on your final choice of HOG parameters.

I tried various combinations of parameters and settle with the following `orientations=9`, `pixels_per_cell=(8, 8)` and `cells_per_block=(2, 2)` which tends to give better result in the testing time.

#### 3. Describe how (and identify where in your code) you trained a classifier using your selected HOG features (and color features if you used them).

First I principle component analysis to do the feature selection. Then I trained a bagging classifer with multilayer perceptron as its base model. The code for this step is contained in code cells through seventh to twelveth of the IPython notebook.

### Sliding Window Search

#### 1. Describe how (and identify where in your code) you implemented a sliding window search.  How did you decide what scales to search and how much to overlap windows?

I decided to perform the search only in the specified area with multiscale. The scales I used are 1.25 and 1.5. The code for this step is contained in fourteenth code cells of the IPython notebook.


#### 2. Show some examples of test images to demonstrate how your pipeline is working.  What did you do to optimize the performance of your classifier?

Ultimately I searched on two scales using YCrCb 3-channel HOG features in the feature vector, which provided a nice result.  Here are some example images:

<img src="{{ site.img_path }}/SDC/pipeline.png" alt="Pipeline" class="img_center"/>

---

### Video Implementation

#### 1. Provide a link to your final video output.  Your pipeline should perform reasonably well on the entire project video (somewhat wobbly or unstable bounding boxes are ok as long as you are identifying the vehicles most of the time with minimal false positives.)
Here's a result.
<p align="center">
<iframe width="560" height="315" src="https://www.youtube.com/embed/fzRYC2RM4KY" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</p>
#### 2. Describe how (and identify where in your code) you implemented some kind of filter for false positives and some method for combining overlapping bounding boxes.

I recorded the positions of positive detections in each frame of the video.  From the positive detections I created a heatmap and then thresholded that map to identify vehicle positions.  I then used `scipy.ndimage.measurements.label()` to identify individual blobs in the heatmap.  I then assumed each blob corresponded to a vehicle.  I constructed bounding boxes to cover the area of each blob detected. The code for this step is contained in the code cells thirteenth and fifteenth of IPython notebook.

Here's an example result showing the heatmap from a series of frames of video, the result of `scipy.ndimage.measurements.label()` and the bounding boxes then overlaid on the last frame of video:

#### Here are five frames and their corresponding heatmaps and the output of `scipy.ndimage.measurements.label()` on the integrated heatmap from all five frames:

<img src="{{ site.img_path }}/SDC/merge.png" alt="Merge" class="img_center"/>

#### Here the resulting bounding boxes are drawn onto the last frame in the series:
<img src="{{ site.img_path }}/SDC/result_merge.png" alt="Result" class="img_center"/>


---

### Discussion

#### 1. Briefly discuss any problems / issues you faced in your implementation of this project.  Where will your pipeline likely fail?  What could you do to make it more robust?

In the very begining I have use hog and color features, but while I was using color features the model tended to give more false positive prediction. I guess this might be caused by the the color features both spatial and histogram aren't robust to various size and direction. In the end, I chose to keep only hog features for simplicity and apply PCA to select 500 features out of 5000+ features. Along the way of dealing with false positive, I also higher the probablity to make model less likely to predict car.

My pipeline will be likely fail when the input image with different scale or image with objects which has similar shape as car. In order to make it more rubust, substitubing the sliding windows scheme with more advance scheme like region of interest pooling and extracting features with pretrain deep learning model.
