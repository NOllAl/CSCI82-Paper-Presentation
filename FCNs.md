FCNs
========================================================
author: Karma Tarap & Alexander Noll
date: 26-10-2017
autosize: true

Problem
========================================================

Standard convolutional neural networks (CNNs) are good at **global classification**:

![](FCNs-figure/CNN.png)


Problem
========================================================

What if we are interested in asking the question: where is the hotdog?

![](FCNs-figure/FCN-Motivation.png)

Problem
========================================================

So we have a local classification problem:

+ For each point of an image a class is supposed to be predicted
+ Numerous applications: e.g self-driving-cars (will be shown in code) use it for [drivable surface classification](https://www.youtube.com/watch?v=qWl9idsCuLQ)

<!--html_preserve--><iframe src="https://www.youtube.com/embed/qWl9idsCuLQ" width="630" height="472.5" frameborder="0" allowfullscreen=""></iframe><!--/html_preserve-->

Other approaches
========================================================
Sliding windows
![](FCNs-figure/sliding-windows.png)

Fully Convolutional Neural Networks
========================================================

End-to-end learning (i.e. no manual intervention, like in sliding windows) approach to image segmentation problem

+ They are a series of convolutional layers and pooling-layers decreasing the size of the output
+ Followed by a series of **deconvolutional layers** or **transposed convolutional layers** or **upsampling layers** that increase the output size
+ Skip layers are very important for performance
+ Transfer learning for pre-training weights

Convolutional layers
========================================================

Convolutional layers use the **spatial symmetry** of the problem to reduce the number of weights. They do this using the concept of **weight sharing**: a hot-dog in the upper right is the same as a hot-dog in the lower left corner.

Important parameters:

+ Kernel size: how big of a region should share the same weights
+ Stride: how many steps at a time should the filter take

Pooling layers
========================================================

Summarize patch of an image by taking the maximum or mean (or whatever)

Important parameters:

+ Kernel size: how big of a region should the summary function be applied to
+ Strinde. how many steps at a time should the filter take

Dimensionality problem
========================================================

Both convolutional layers and pooling layers reduce the image dimension. This is desired in a classification setting, but not in a segmentation setting: the output dimension should be equal to the input dimension.

Solution
========================================================

Use **upsamling** or **transposed convolutional** or **deconvolutional** layers:

Skip connections
========================================================

Used to transfer information from **early layers** directely into layers close to output layer via elementwise addition.

![](FCNs-figure/skip-cons.png)

Architecture
========================================================

Results: PASCAL VOC
========================================================

+ 1112 images (see below)
+ SIFT Flow: 

![](FCNs-figure/pascal.png)
![](FCNs-figure/pascal-res.png)

Results: VOC, NYUDv2 and SIFT Flow
========================================================

![](FCNs-figure/Voc-NYDU2.png)
![](FCNs-figure/SiftFlow.png)
