---
layout: post
title: Light up your life!
---

Haven't got enough colour in your life? Enjoy flash gimmicks as much as I do?
Maybe you're into gaming and need more immersion.

![beach-bias.png]({{ site.baseurl }}/images/bias-lighting/beach-bias.png)

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

When this project is complete we will have installed a Raspberry Pi controlled
bias lighting system. You will be able to configure this system to respond to 
your current HDMI feed and run some custom effects using 
[Hyperion](https://hyperion-project.org/)

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
model, you could do so to better fit your purposes. ![rpi]({{ site.baseurl }}/images/bias-lighting/rpi.png)

### Capture Card

The capture card is required to make your lighting reflect the border of the
current display, consider this component optional if you don't want this
feature. ![hdmi-capture-card]({{ site.baseurl }}/images/bias-lighting/hdmi-capture-card.png)

### PSU

Be careful when choosing your power supply; some details will determine how
many lights you can hookup & could also potentially be unsafe if you get it
wrong. Don't worry; we will cover how to be accurate with this item later on.

![psu]({{ site.baseurl }}/images/bias-lighting/psu.png)

### LED Strip

The pièce de résistance, the LED strip. Specifically from the WS281x family,
these LEDs are individually addressable; this feature is vital to make our
fancy effects. //[TODO: discuss led per cm]

![led-strip]({{ site.baseurl }}/images/bias-lighting/led-strip.png)

## The Software

The software that makes this whole thing possible is 
[Hyperion](https://hyperion-project.org/) it's a fantastic project with a great
community.

![hyperion-logo]({{ site.baseurl }}/images/bias-lighting/hyperion-logo.png)

### HyperBian

Another gracious offering from the Hyperion team is
[HyperBian](https://github.com/hyperion-project/HyperBian) this is essentially
Raspberry Pi OS List with some pre-configuration to ease the setup process.
For the more adventurous, there is, of course, Debian packages and docker images 
available from the same [Github Account](https://github.com/hyperion-project).

## The Plan

The setup process is divided into 2 parts, hardware and software setup. We will
be wiring the RPI up with the LEDs, power supply & HDMI capture card. 
The software setup will include setting up the boot drive & configuring 
Hyperion.

## Wiring the System

Assembling the system for the most part is as simple as plugging in a few 
cables. Hopefully you can work out the connections from the diagrams. I will go
into detail about connecting the RPI & LED to a common ground as this part may
be unfamiliar to novices.

![system-diagram]({{ site.baseurl }}/images/bias-lighting/system-diagram.png)

![system-installation]({{ site.baseurl }}/images/bias-lighting/system-installation.jpg)

//[TODO: other wiring images]

### Common Ground

One of the finer details to observe when plugging this project in is that the 
power supply for the RPI & the LED strip are shared. This is desirable to 
reduce the amount of plug sockets we will end up using per installation.

We won't discuss in depth why the common ground is required, just know that it
provides a common reference point that helps keep signals confined to the
return path & prevents them from interfering with each other.

This is the part where you will need some wire strippers & a soldering iron.

//[TODO: provide pictures of cable splicing & attachments, flow diagram of process?]

## Hyperion Setup

### System Image

Now that your system is all plugged in we should setup the software that is 
going to drive our LED strips. If you havent already you will need to get a 
copy of [HyperBian](https://github.com/hyperion-project/HyperBian) 
& for simplicity we will use the official 
[Raspberry Pi Imager](https://www.raspberrypi.org/software/) to create the 
bootable drive.

Once you have downloaded the required media, insert your micro SD card, open 
the RPI imager utility and use it to target the hyperbian image and your micro
SD.

![rpi-imager]({{ site.baseurl }}/images/bias-lighting/rpi-imager.png)

When you see that your image has been written successfully you can close the 
imager utility.

![rpi-imager-done]({{ site.baseurl }}/images/bias-lighting/rpi-imager-done.png)

### RPI Setup Masterclass

You could now continue to insert your SD card into your RPI boot up the system
are start to configure manually. This is fine but we are going to do some 
additional configuration to the SD card before starting up.

#### SSH

We will need to enable SSH on the system in order to make remote login 
possible. Do this simple by locating the SD card (which should be called 
somthing like 'boot') and add a file called 'ssh' in the root.

#### Wpa_supplicant

By default RPI OS use wpa_supplicant.conf to configure the wireless network. 
Again at root level in your boot drive add a file called 'wpa_supplicant.conf'
and include this code inside it:

~~~bash
TODO: wpa_supplicant example
~~~

Taking these steps should save us some time getting started and is known as 
starting the RPI in headless mode.

### Power On RPI

We're now ready to get the RPI booted up. In order to take advantage of 
starting the RPI in headless mode you must identify the IP address of the RPI
so that you can login to hyperion.

When your RPI is powering up log into your network router to see current
network devices list, observe this list until your RPI has finished booting at 
which point you should see a new device named something like 'HyperBian' along
with it's IP address. Use your browser to visit the IP address on port 8090.

### The Hyperion Interface

If you followed the previous steps correctly you should now be looking at the 
hyperion web interface.

#### General Settings

#### LED Hardware

##### LED Controller

##### LED Layout

#### Capturing Hardware

### Enabling Remote & API