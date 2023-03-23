---
layout: default
---

[Home](./)
# Hobby projects

In this document, I showcase several projects that I made in my free time, 2 of them were parts of huggingface sprints which are awesome events i suggest you to check them out

## World of Warcraft fishing bot

This was a project I made for fun, I wanted to make a world of warcraft fishing bot using computer vision. The version that used openCV for detecting the fishing bobber didn't work very reliably. So I created a small dataset of 150ish (probably way too many) labeled pictures and trained the yolov3 network to detect it. The results were much better than standard computer vision algorithms for object detection.

* [youtube demo](https://youtu.be/iax2S7DT20w)
* [github repo](https://github.com/jere357/fishermansfriend)

## Projected GAN for painting generation
This project was done for the huggan huggingface event. I used the wikiart dataset and trained the projected GAN on it, I also trained/transfer learned a couple of models to my academic painter friends' paintings that all contained small houses, since she had around ~20 paintings with small houses i was interested in whether that was enough for a GAN to actually learn how to generate such houses since they are all of similair shape. I was also interested in seeing how transfer learning behaved when working with GANs. These results were cool when they came out but models like DALLE2 and stable diffusion are just something else man

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

