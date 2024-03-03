---
layout: default_blog
---

[Home](./index.html) / [Blog](./blog_index.html)


# Generating Livaja with a champion's league trophy using dreambooth.

Another 2nd place finish in the national league, maybe it was time to replace the coach. I just wanted to see my favorite player holding the champions league trophy.
replace
This project started as an idea to see wether it was possible to finetune a stable diffusion model so it could generate Marko Livaja holding the champions league trophy.

First i wanted to see what does stable diffusion know about SOCCER players, football players would be generated as american football players indicating a regional bias in the annotations. And whether it knows what the UEFA champion's league trophy looks like. Also there was the question of which baseline model should i finetune, compvis1.4, runway1.5 or the stability2.1


1 slika - photo of a soccer player 3 modela

1 slika - champion league trophy 3 modela


These results were okay enough to start my dreambooth journey. What i wanted to do was a bit different from the usual dreambooth subject/class pairing since the model doenst know what the UCL trophy looks like. Can the model learn both Marko Livaja and the UCL trophy, and how?


## Most important part of ML: The data

I went on a mission to create a dataset of ~250 images containing player holding the trophy. The usual dreambooth dataset for generating people needs ~20 instance images of the person and 10x class images. After gathering the data. I have 24 images of Marko Livaja (all wearing the same home jersey) and 242 images of various players holding the UCL trophy. 


# One weird prompt trick

First i ran some experiments with the usual dreambooth prompt pairings: "a photo of a sks soccer player" and "a photo of a soccer player", but the results were not good enough. I wanted to see if i could use the class prompt to my advantage. The new class prompt was "a soccer player holding a trophy".

1 slika -3 razlicita prompta na stability ai modelu


# Which baseline

I had to choose on of the 3 baseline models, so i ran 3 experiments with different models to see how they behave after dreambooth tuning. The results were not that different, but i like the stabilityai results the most.

1 slika - 3 razlicita baseline modela stability/compvis/runway


# How much does changing the PLR matter for the results

1 slika - 3 stability modela na razlicitin PLR


## differente schedulers ?

## SDXL refiner ? 

## does 'a photo of' part of the prompt even do anything?



_yay_

[back](./)
