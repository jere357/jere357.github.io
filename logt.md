---
layout: default
---

[Home](./index.html) / [Research](./research.html)

# Line Over Ground Truth loss

For the past 6 months, I have worked on shelf detection as my task on this project. In our case, the main goal of shelf detection in their pipeline is to determine the ordinal number of the shelf on which the product is placed on (most bottom shelf (first), middle shelf (second), ...). We have tried to apply some traditional computer vision methods to this problem but none of them proved to be robust enough to be used in an "in-the-wild" environment such as a store. Exact and precise localization of the shelf bounding boxes wasn't necessary.

![](./assets/img/mapbad.png)
*Image where mAP says these predictions are bad (beacuse of it being based on IoU) but in our very specific case of shelf detection/numeration the predicted bounding boxes work just fine.*

I have proposed a new LoGT evaluation metric [you can check out the source code here](https://github.com/jere357/yolov5-RGBD/blob/39ad3cfa5782b5c1aba1cda3b47b7ae2ac9d1b2d/val_jere.py#L524). LoGT represents the predicted bounding box as a line that is going through the middle of that bbox. If that line crosses the ground truth bounding box I declare the loss to be 0 otherwise, it's 1. Keep in mind this is purely an evaluation metric and training is still done using CIoU (me and my colleague tried to formulate our training loss but cIoU was simply better than anything we came up with :) ). This being a very simple 1-class object detection problem where even the simplest yolov network configuration achieves great results but requires a "large" amount of parameters. Using my previously proposed metric I managed to prune the memory footprint from 1.4m parameters (yolov5n, the smallest config you can find on the ultralytics yolov5 github repo) to a tiny yolov5femto/yolov5pico models of 30k/150k parameters, with the same FPN based architecture but significantly fewer filters in every convolutional layer, achieving nearly the same results on their in-house shelf detection dataset.

[LoGT_matrix source code](https://github.com/jere357/yolov5-RGBD/blob/39ad3cfa5782b5c1aba1cda3b47b7ae2ac9d1b2d/val_jere.py#L524)
I will try to explain this code here 

#TODO: actually explain it
