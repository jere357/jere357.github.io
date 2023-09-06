---
layout: default_blog
---

[Home](./index.html) / [Blog](./blog_index.html)


# Generating Livaja with a champion's league trophy using dreambooth.

It was another 2nd place finish in the national league, i just wanted to see my favorite player holding the champions league trophy. 

This project started as an idea to see wether it was possible to finetune a stable diffusion model so it could generate a soccer player holding he champions league trophy.

First i wanted to see what does stable diffusion know about SOCCER players, football players would be generated as american football players indicating a regional bias in the annotations. And whether it knows what the UEFA champion's league trophy looks like.


## obcnmi stable diffusion rezultati
 
soccer player
soccer player holding a trophy
uefa champions league trophy

These results were a good enough starting points for my dreambooth journey.
The questions was: Can the model learn both Marko Livaja and the UCL trophy, and how?
Initial experiments with the basic dreambooth instance/class prompts such as "photo of a sks soccer player" and "photo of a soccer player" weren't good enough

## obicni dataset eskpaci

I went on a mission to create a dataset of ~250 images containing player holding the trophy. They are going to be used as class images in the dataset where the class is "a soccer player holding a UEFA champion's league trophy". The instance prompt inm this case would be "a sks soccer player with no trophy". These 2 prompts combined with the enw dataset yielded pretty good results! THen i went to see which baseline stable diffusion model i liked the most for this task, it was stabilityAI2.0 

## runwayml/stabilitai/compvis


Since this was my first time running things on stable diffusion models i wanted to see for how much of a difference things like schedulers, num_steps and varations in the prompts made.

## differente schedulers


## does 'a photo of' part of the prompt even do anything?



_yay_

[back](./)
