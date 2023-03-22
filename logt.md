---
layout: default
---

[Home](./index.html) / [Research](./research.html)

# Line Over Ground Truth loss

For the past 6 months, I have worked on shelf detection as my task on this project. In our case, the main goal of shelf detection in their pipeline is to determine the ordinal number of the shelf on which the product is placed on (most bottom shelf (first), middle shelf (second), ...). We have tried to apply some traditional computer vision methods to this problem but none of them proved to be robust enough to be used in an "in-the-wild" environment such as a store. Exact and precise localization of the shelf bounding boxes wasn't necessary.

![](./assets/img/mapbad.png)
*Image where mAP says these predictions are bad (beacuse of it being based on IoU) but in our very specific case of shelf detection/numeration the predicted bounding boxes work just fine.*

I have proposed a new LoGT evaluation metric [you can check out the source code here](https://github.com/jere357/yolov5-RGBD/blob/master/val_jere.py#L526). LoGT represents the predicted bounding box as a line that is going through the middle of that bbox. If that line crosses the ground truth bounding box I declare the loss to be 0 otherwise, it's 1. Keep in mind this is purely an evaluation metric and training is still done using CIoU (me and my colleague tried to formulate our training loss but cIoU was simply better than anything we came up with :) ). This being a very simple 1-class object detection problem where even the simplest yolov network configuration achieves great results but requires a "large" amount of parameters. Using my previously proposed metric I managed to prune the memory footprint from 1.4m parameters (yolov5n, the smallest config you can find on the ultralytics yolov5 github repo) to a tiny yolov5femto/yolov5pico models of 30k/150k parameters, with the same FPN based architecture but significantly fewer filters in every convolutional layer, achieving nearly the same results on their in-house shelf detection dataset.

[LoGT_matrix source code](https://github.com/jere357/yolov5-RGBD/blob/master/val_jere.py#L526)
I will try to explain this code here 

#TODO: actually explain it

I will try my best to explain how i imagined LoGT loss on an example. It is similair to IoU in the sense that it being 0 is not satisfactory and it being 1 is excellent. So far it is only discrete, it could be continuous in the future but I'm not sure how much it matters since i only use it as an evaluation metric. Let's say you have G ground truth bounding boxes and P predictions. We construct a LoGT matrix where each row is a predicted bounding box, and each column is a ground truth bounding box. The matrix shape is PxG. Element (i,j) of that matrix is the LoGT metric between that prediction and the ground truth. 

The First thing to do is deconstruct the prediction bounding boxes into lines, this could be something else but i decided to [KISS](https://en.wikipedia.org/wiki/KISS_principle) (so far, I felt there was no need to complicate things on a simple task such as shelf detection).

```python
P = bboxes_to_lines(predictions) # represent predicted bboxes as a single line going through the middle of that box
LoGT_matrix = numpy.zeros(P,G) # [PxG] skeleton
for i, line in enumerate(P):
    for j, ground_truth in enumerate(G):
        if line passes through ground_truth:
            LoGT[j,i] = 1
        else:
            LoGT[j,i] = 0 # it already is 0 but leaves room for future code when maybe i don't want it to be discrete

```
Consider an example like this: green are the ground truth bounding boxes, and red are your predicitons. They are indexed with numbers so it's more intuitive to follow the rows and columns.
![pusi kurac](./assets/img/logt_demo1.png)
For this ground truth and output i want the LoGT matrix to look like this:

**The Cauchy-Schwarz Inequality**
$$\left( \sum_{k=1}^n a_k b_k \right)^2 \leq \left( \sum_{k=1}^n a_k^2 \right) \left( \sum_{k=1}^n b_k^2 \right)$$

| 1 | 0 | 0 |
| 0 | 1 | 0 |
| 0 | 0 | 1 |


