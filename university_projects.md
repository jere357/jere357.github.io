---
layout: default
---
[Home](./)

# University projects w/ deep learning

In this document, I showcase several deep learning projects that I completed during my time as a university student. These projects cover a variety of applications in natural language processing, computer vision, and generative modeling.


## Method for People Counting From Image Sequence
My BSc thesis. I located people in a single image using the tinyface detector (it was clearly the best of all methods we observed (at that time)) and then devel-
oped an algorithm that created trajectories and followed/counted people from frame to frame in a video. Thanks to Nikola Banić for his guidance while i was working on this.

[Youtube demo I uploaded in communication with Nikola](https://www.youtube.com/watch?v=XzzDttREG-o)

## Music genre classification from lyrics

We had a dataset composed of 250k song lyrics and their respective genres. The part I worked on was creating a tfidf weighted fasttext vector
from the top 10 ranked words in the song, and then finding the best classification algorithm. To no one’s surprise, it was XGBoost

* [Project report](https://www.fer.unizg.hr/_download/repository/TAR-2019-ProjectReports.pdf#section*.15)

## Pix2pixGAN for generating facial expressions
We trained a pix2pix GAN. The dataset had neutral facial expression image, an image with some emotion,
and the corresponding emotion vector, the results were surprisingly good. Network inputs were: face image with neutral expression + emotion
encoded in a vector output: face image with drawn emotion

* [Project report (in Croatian)](https://drive.google.com/file/d/1R-Hhop7eXfG4Eu4uMDlqt0fVyCT2dNHp/view)
* [dataset](https://paperswithcode.com/dataset/ck)


## Retinal fluid segmentation using 2D U-net
This was done as my graduate project, the dataset I had was the same one used in the Retouch Challenge. Experimented with different/new
loss functions and observed how the end result changes with respect to the loss function with interesting results

[dataset](https://retouch.grand-challenge.org/)

## Using ESRGAN for achieving superresolution

A seminar on  GANs and how they could be used for superresolution in images, and various difficulties the traditional approach had in achieving
superresolution. I'm a big fan of how GANs work for superresolution.
