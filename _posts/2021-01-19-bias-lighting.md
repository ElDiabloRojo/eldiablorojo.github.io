---
layout: post
title: Bias Lighting, light up your life!
---

Haven't got enough colour in your life? Enjoy flash gimmicks as much as I do?
Maybe you're into gaming and need more immersion, if you answered yes to any of
these you're in for a treat (even if you didn't it's going to be great).

![beach-bias.png]({{ site.baseurl }}/images/beach-bias.png)

## What is bias lighting?

By definition Bias Lighting is a weak light source on the backside of a 
tv or monitor that illuminates the wall or suface behind the display.

Some would argue that bias lighting reduces the contrast between the display &
the surrounding environment.
If you require a rationale for installing some awesome RGB LEDs on the back of
every display you own, you could use that one.

Hopefully by now you are fully persuaded to join the bias bandwagon and setup a
rig of your own. There are many options you could choose to satisfy your 
craving for illumination however in this post we will follow the setup process
of just one!

## Pre-requisites

It will certainly help you follow this guide if you are a little familiar with
setting up new rpi devices & have a solder iron and some wire strippers.
It is advisable to have these things rather than chanelling your inner rodent 
trying to chew the insulation off of the cables. 

## The Hardware

For this project you will need the following hardware:

* [rpi 3b+](#Which Pi?)
* [hdmi capture card](#Capture Card)
* micro sd card
* [5v power supply](#PSU)
* [RGB LED strip (WS2812B)](#LED Strip)
* micro usb cable
* a single jumper cable

Optional extras:

* rpi case
* LED strip corner pieces


### Which Pi?

If you're unfamiliar with the specifics of choosing a rpi you will be 
safest to stick with the 3b+ model, however if you are confident in you choice
of another model you could do so to better fit your purposes.

### Capture Card

The capture card is required to make your lighting reflect the border of the 
current display, consider this component optional if you don't want this
feature.

![hdmi-capture-card.png]({{ site.baseurl }}/images/hdmi-capture-card.png)

### PSU

Be careful when choosing your power supply there are some details that will
determine how many lights you can hookup & could also potentially be unsafe if 
you get it wrong. Don't worry, we will cover how to be accurate with this item 
later on.

### LED Strip

The pièce de résistance, the LED strip. Specifically from the WS281x family,
these LEDs are individually addressable, this feature is vital to make our 
fancy effects.

## The Software

The software that makes this whole thing possible is the wonderful:
[hyperion-project](https://hyperion-project.org/) it's a fantastic project with 
a great community.

![hyperion-logo.png]({{ site.baseurl }}/images/hyperion-logo.png)

### HyperBian

Another gracious offering from the hyperion team is
[HyperBian](https://github.com/hyperion-project/HyperBian) this is essentially
Raspberry Pi OS List with some pre-configuration to ease the setup process.
For the more adventurous there is of course debian packages and docker images 
available from the same [Github Account](https://github.com/hyperion-project).

## What are we going to do?

The setup process is divided into 2 parts, hardware and software setup. For the 
hardware setup we will be wiring the Pi up with the LEDs, power supply & HDMI 
capture card. The software setup will consist of setting up the boot drive for
the Pi & configuring hyperion.