---
layout: default_blog
---

[Home](./index.html) / [Blog](./blog_index.html)

# Manually setting fan speed on an ubuntu-server machine with no screen and multiple GPUs

We were unhappy with the way default nvidia drivers handled fan speeds under load. The problem to solve was how to set the fan speeds on a multi GPU ubuntu-server machine with no screen, if you have a screen you can use the nvidia-settings GUI and be happy, otherwise this should work hopefully

Using a combination of [arch linux wiki](https://wiki.archlinux.org/title/NVIDIA/Tips_and_tricks) and [cryptocurrency mining blogs](https://blockonomi.com/linux-cryptocurrency-mining/) i have arrived at a local optimum which i consider good enough. The speeds are static. # TODO: make them dynamic :), 1 idea is to have a script that emulates a fan curve.


## Cast these spells in this order:
```sh
sudo nvidia-xconfig -a --cool-bits=4 --allow-empty-initial-configuration --enable-all-gpus
```

my understanding is the --allow-empty-initial-configuration helps with the no-screen problem, and --enable-all-gpus is **essential** if you have more than one GPU, the cool-bits flags is needed for manual adjustment of fan speeds.

```sh
shutdown -r now
```

after rebooting

```sh
sudo su root
```

```sh
X :1 &
```

```sh
export DISPLAY=:1
```

```sh
nvidia-settings -a "[gpu:0]/GPUFanControlState=1" -a "[fan:0]/GPUTargetFanSpeed=75" -a "[gpu:1]/GPUFanControlState=1" -a "[fan:1]/GPUTargetFanSpeed=75" -a "[gpu:2]/GPUFanControlState=1" -a "[fan:2]/GPUTargetFanSpeed=75" -a "[gpu:3]/GPUFanControlState=1" -a "[fan:3]/GPUTargetFanSpeed=75""
```

exit root back to your user
```sh
exit
```

Pay attention to how the fans are indexed!!

wrong way to do this:
gpu:0/fan:0 gpu:1/fan:0

correct way to do this:
gpu:0/fan:0 gpu:1/fan:1

[back](./)
