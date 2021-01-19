---
layout: post
title: Bias Lighting, light up your life!
---

Haven't got enough colour in your life? Enjoy flash gimmicks as much as I do?
Maybe you're into gaming and need more immersion.

![beach-bias.png]({{ site.baseurl }}/images/beach-bias.png)

If you answered yes to any of these, you're in for a treat (even if you didn't
it's going to be great).

## What is bias lighting?

By definition, bias lighting is a weak light source on the backside of a
tv or monitor that illuminates the wall or surface behind the display.
Some systems offer basic features whilst others will react to the border pixels
on your display.

Some would argue that bias lighting reduces the contrast between the display &
the surrounding environment.
If you require a rationale for installing some awesome RGB LEDs on the back of
every display you own, you could use that one.

Hopefully, by now, you are fully persuaded to join the bias bandwagon and set
up a rig of your own. There are many options you could choose to satisfy your
craving for illumination; in this post, we will follow the setup process
of just one!

## What will we achieve with this project?

//[TODO: write a brief description of what]

## Pre-requisites

It will certainly help you follow this guide if you are a little familiar with
setting up new RPI devices & have a soldering iron and some wire strippers.
It is advisable to have these things rather than channeling your inner rodent
trying to chew the insulation off of the cables.

## The Hardware

For this project you will need the following hardware:

//[TODO: include links and suggestions]

* [rpi 3b+](#Which Pi?)
* [hdmi capture card](#Capture Card)
* micro sd card
* [5v power supply](#PSU)
* [RGB LED strip (WS2812B)](#LED Strip)
* micro usb cable
* a single jumper cable

Optional extras:

* RPI case
* LED strip corner pieces


### Which Pi?

If you're unfamiliar with the specifics of choosing an RPI, you will be safest
to stick with the 3b+ model. If you are confident in your choice of another
model, you could do so to better fit your purposes.

### Capture Card

The capture card is required to make your lighting reflect the border of the
current display, consider this component optional if you don't want this
feature.

![hdmi-capture-card.png]({{ site.baseurl }}/images/hdmi-capture-card.png)

### PSU

Be careful when choosing your power supply; some details will determine how
many lights you can hookup & could also potentially be unsafe if you get it
wrong. Don't worry; we will cover how to be accurate with this item later on.

### LED Strip

The pièce de résistance, the LED strip. Specifically from the WS281x family,
these LEDs are individually addressable; this feature is vital to make our
fancy effects. //[TODO: discuss led per cm]

## The Software

The software that makes this whole thing possible is 
[Hyperion](https://hyperion-project.org/) it's a fantastic project with a great
community.

![hyperion-logo.png]({{ site.baseurl }}/images/hyperion-logo.png)

### HyperBian

Another gracious offering from the Hyperion team is
[HyperBian](https://github.com/hyperion-project/HyperBian) this is essentially
Raspberry Pi OS List with some pre-configuration to ease the setup process.
For the more adventurous, there is, of course, Debian packages and docker images 
available from the same [Github Account](https://github.com/hyperion-project).

## What are we going to do?

The setup process is divided into 2 parts, hardware and software setup. We will
be wiring the RPI up with the LEDs, power supply & HDMI capture card. 
The software setup will include setting up the boot drive & configuring 
Hyperion.