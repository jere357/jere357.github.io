---
layout: default_blog
---

[Home](./) / [Blog](./blog_index.html)
# Hobby projects

In this document, I showcase several projects that I made in my free time, 2 of them were parts of huggingface sprints which are awesome events i suggest you to check them out


## World of Warcraft fishing bot

This was a project I made for fun, I wanted to make a world of warcraft fishing bot using computer vision. The version that used openCV for detecting the fishing bobber didn't work very reliably. So I created a small dataset of 150ish (probably way too many) labeled pictures and trained the yolov3 network to detect it. The results were much better than standard computer vision algorithms for object detection.

* [youtube demo](https://youtu.be/iax2S7DT20w)
* [github repo](https://github.com/jere357/fishermansfriend)

## Dreambooth finetuning to see my favorite soccer player holding the champion's league trophy
At one point in the future i will write an elaborate blogpost about this project, for now enjoy this short recap. I gathered around 250 images of soccer players holding the champions league trophy and 25 images of Livaja. Things didn't work good when i was using the standard dreambooth instance/class prompt pairs like: "a photo of a soccer player" and "a photo of a sks soccer player". But when i changed them to "a photo of a soccer player holding a trophy" and "a photo of a sks player" the results were looking much better. Can i call myself a prompt engineer now? Shoutout to Donik from IPG@fer

![impr](/assets/img/livaja.jpg){:width="50%"}

## Projected GAN for painting generation
This project was done for the huggan huggingface event. I used the wikiart dataset and trained the projected GAN on it, I also trained/transfer learned a couple of models to my academic painter friends' paintings that all contained small houses, since she had around ~20 paintings with small houses i was interested in whether that was enough for a GAN to actually learn how to generate such houses since they are all of similair shape. I was also interested in seeing how transfer learning behaved when working with GANs. I have taken some models trained on e.g. abstract expressionism images and and the fine-tuned it to Hana's houses. The results very neat but this event lasted only 2 weeks i think so i didn't have time to experiment further / formulate some kind of loss to measure the impact of this transfer learning.

These results were cool when they came out but models like DALLE2 and stable diffusion are just something else man

![impr](/assets/img/impressionism.png){:width="50%"}

*Some cherry picked results from the impressionism model*

![hhae](/assets/img/AE_HH.png){:width="50%" :style="padding-left:25%"}

*Results from the abstract expressionism model that was transfer learned to paint Hana's houses*


By the way! this huggingface space was displayed alongside some of Hana's work at a gallery in Labin, Croatia :D
The outputs from the original Projected GAN were 256x256, that was too small to be displayed on a projector, so i upscaled them with ESRGAN to look prettier on a big screen, it worked out nice.

![check it outtt](/assets/img/hanagalerija.jpg){:width="50%"}

It was also present at her first solo exhibition, a big day for her, congrats! I forgot to take pictures, but for that one we chose to display a video of a walk through the GAN input space by adding slight noise to the input vector and displaying a slightly different house every second, (Lipschitz continuity, very cool) it was cool how on a scale of 5-10 seconds the house was pretty much the same, but if you come back after a few minutes it could be an entirely different house

* [huggingface space demo](https://huggingface.co/spaces/huggan/projected_gan_art)
* [Instagram link where you can see some of her work](https://www.instagram.com/hanaqhanak)

## Hosting a minecraft server on oboslete hardware that was collecting dust at our department
My colleague and me had a brilliant idea of hosting a minecraft server on some old PCs we had at our lab. They were some 10+ years old PCs with some old intel quad core processors and 8 GB of DDR2/800 MHz RAM. we slapped arch on that bad boy and hosted the server. We have added the minecraft server startup service to systemd; all of this was very easy thanks to the good people at the AUR. Because this old PC we just connected to our intranet wasn't visible from the outside we both started developing our proxy solutions with nginx. I will gladly send you the IP if you want to join :)
* [Arch user repository](https://aur.archlinux.org/)


## Fine-tuning english GPT-2 for rap lyric generation
This project was done during for the huggingface jax flax community week workshop. I scraped genius.com using their API to create the dataset
we used. Model training was done on a v3 TPU on google cloud which was provided to us as a part of the workshop. The results were ok it was
interesting to see how it captured the usual theme of the rapper’s songs (e.g. Tupac vs Lauyrn Hill). These results were cool at the time, but GPT4 and chatGPT are just too good (have that much <b>more parameters</b>?)

* [huggingface space demo](https://huggingface.co/spaces/Cropinky/gpt2-rap-songs)

