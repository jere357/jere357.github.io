---
layout: default
---

[Research](./research.html)
# Adding additional channel features to object detection models.

 I have already spoken on what i think about deep learning research going two ways, i have pruned this model and redcued the number of parameters significantly with the LoGT loss. Now i want to propose a new method for object detection I propose that instead of using only RGB images as inputs to object detection network, I would like to construct additional channel features so that images can become something even more than just 3 channels. I believe that this idea can lay ground for some very exciting computer vision research.

![image](./assets/img/rgbd.png)

Some of "channel features" I think are worth testing out:

1.    Estimated depth RGB->RGBD (1024x1024x3 input ->1024x1024x4 input), as part of my research I've read many papers that focus on networks for monocular depth estimation such as this one http://yaksoy.github.io/highresdepth/ and I think it would be interesting to use estimated depth as a channel feature in object detection; also open for consideration is applying simple image thresholding to this depth map, the threshold can be a hyperparameter or maybe even a learnable parameter in the network somehow, that would require a slightly different approach.

2.  Applying the Fourier transform to images to construct potentially powerful channel features. As part of my research, I have also read several papers that use NeRFs. Inspired by the way Mildenhall et al. use positional encoding in chapter 5.1 in the [NeRF paper](https://arxiv.org/abs/2003.08934) I would like to try out a similar approach - but for object detection.

3.    Canny edge feature RGB->RGBC, applying the canny edge algorithm on an image and using that grayscale image as a feature, this is my least favorite feature of the 3 but I think it still has enough potential to warrant experiments.

4.    Sobel features - maybe something interesting could be achieved by applying a sobel operator to the input image - also can be a learnable parameter if it seems like something worth exploring

