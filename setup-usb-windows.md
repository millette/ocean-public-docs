---
layout: page
title: Setup an Ocean over USB on Windows
group: navigation
---
This aim of this guide is to help you set up a new Ocean in less than five minutes, using USB on Windows.  After working through this guide, your Ocean will be connected to your WiFi network, and you should be able to access it via `ssh`.

<h3>Under construction</h3>

## Prerequisites for Windows

We recommend ZOC for connecting to an Ocean over USB.  [Download ZOC here](http://www.emtec.com/zoc/)

We will assume you are using ZOC for the rest of this guide.

However, `PuTTY` is another available option.  PuTTY can be downloaded [from this site](http://www.putty.org/).


## 1. Power on the Ocean and connect the USB

{% include setup/power.md %}

## 2. Start ZOC and connect to the Ocean

When you launch the ZOC application, the Quick Connection wizard will pop open.  

![]({{ site.baseurl }}/assets/images/StartupWizard.PNG)

In this window, in the “Connect to:” field, type "serial".

Next, change “Connection type” in the dropdown menu to “Serial/Direct” and click on the “Configuration” button next to it.

![Selecting the serial/direct option and click "Configuration"]({{ site.baseurl }}/assets/images/SelectingSerialDirect.PNG)

The *Configure Serial/Direct Options* window will pop up.  Select the checkbox “Override session profile defaults”.

![Final config settings]({{ site.baseurl }}/assets/images/ConfigurationPopup.PNG)

More options should appear.  Find the “Scan...” button, and click it.  The following dialog should pop up.

![COM entries without Ocean plugged in]({{ site.baseurl }}/assets/images/SerialScanBeforeOcean.PNG)

Take a note of the list of available entries in "Ports" table, but then press "Cancel" to go back to the *Configure Serial/Direct Options* window.

Next, *Plug in the Ocean into your computer's USB port*.

Next, press “Scan...” again.  The same dialog as before should pop up.  

![Note the new COM entry that shows up]({{ site.baseurl }}/assets/images/SerialScanAfter.PNG)

Select the new COM option that shows up, and press "OK".

Back on the *Configure Serial/Direct Options* window, select 115200 for baudrate, and turn RTS and DTR dropdown menus to both off, like this:

![Final config settings]({{ site.baseurl }}/assets/images/FinalConfigSetting.PNG)

Press OK to close the window, and then press “Connect" on the *Quick Connection* window.  You should now see the following:

![Final config settings]({{ site.baseurl }}/assets/images/Connected.PNG)



## 3. Start the Ocean login prompt

Type `bypass` into the ZOC console, and you will see the following:

![Final config settings]({{ site.baseurl }}/assets/images/ConsoleConnected.PNG)

Two things will happen after this. The power button light will change color, from white to blue. Also, You should see standard linux login prompt.

    $ bypass
    ev s1

    Debian GNU/Linux 8 FineRock ttyS2

    FineRock login:

Note that every Ocean device has a unique name assigned to it. FineRock is the name of the test device we used to create this document. Your device will have a different name.

## 4. Login to your Ocean

{% include setup/login.md %}

## 5. Follow the steps in the setup program

{% include setup/setup-program.md %}

## 6. Exit setup mode

{% include setup/exit.md %}


## OSX: `screen` won't start

Verify that your computer can detect the Ocean.  On your terminal, type the following:

    ls /dev/tty.usbmodem*

If your Ocean is powered on, you have a USB connection between the Ocean and your computer, and the USB cable is working correctly, you should see something like the following:

    /dev/tty.usbmodem1411

NOTE: if you have more than one Ocean, or more than one UBS modem device, attached to your computer, then you will obviously see more than one listing!


# Next steps

- [Use `ssh` to connect to your Ocean]({{ site.baseurl }}/connect-with-ssh).