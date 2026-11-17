---
layout:
  width: default
  title:
    visible: false
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
  tags:
    visible: true
  actions:
    visible: true
  anchors:
    visible: true
---

# Raspberry Pi 4 ReSpeaker Intelligent Speech Recognition 2 Microphone

### Raspberry Pi 4 ReSpeaker Intelligent Speech Recognition 2 Microphone

***

### Product Link

No matching current OpenELAB.io listing was found for the product version documented here.

### Introduction

The ReSpeaker 2-Mics Pi HAT is a Raspberry Pi dual microphone expansion board designed for AI and voice applications. This means you can build a more powerful and flexible voice product with integrated Amazona voice services and more.

The board is based on a low-power stereo codec developed on the WM8960. There are two microphones on either side of the board to capture sound, and it also provides three APA102 RGB LEDs, a user button, and two on-board Grove interfaces for expanding applications. In addition, either a 3.5mm audio jack or a JST 2.0 speaker output is available for audio output.

### Features

* Raspberry Pi compatible (supports Raspberry Pi Zero and Zero W, Raspberry Pi B +, Raspberry Pi 2 B and Raspberry Pi 3 B, Raspberry Pi 4 B, Raspberry Pi 3 B +)&#x20;
* 2 Microphones&#x20;
* 2 Grove interfaces&#x20;
* 1 customizable button&#x20;
* 3.5mm audio interface&#x20;
* JST2.0 audio output connector

### Specifications

### Pinout

<figure><img src="../../.gitbook/assets/image (461).png" alt=""><figcaption></figcaption></figure>

* Buttons: User-defined buttons connected to GPIO17&#x20;
* MIC\_L & MIC\_R: one microphone on the left and one on the right&#x20;
* RGB LEDs: 3 APA102 RGB LEDs connected to the Raspberry Pi's SPI interface&#x20;
* WM8960: Low-power stereo codec&#x20;
* Raspberry Pi 40-pin header: supports Raspberry Pi Zero, Raspberry Pi 1 B +, Raspberry Pi 2 B and Raspberry Pi 3 B&#x20;
* POWER: Micro USB port for powering the ReSpeaker 2-Mics Pi HAT, please power the board to provide enough current when using the speakers.&#x20;
* I2C: Grove I2C port, connects to I2C-1 GPIO12: Grove digital port, connects to GPIO12 and GPIO13&#x20;
* JST 2.0 SPEAKER OUT: For connecting to speakers, JST 2.0 connector&#x20;
* 3.5mm AUDIO JACK: for connecting headphones or speakers with a 3.5mm audio plug

### How to Use

1. System configuration and driver installation

Step 1 Insert ReSpeaker 2-Mics Pi HAT into Raspberry Pi

Insert the ReSpeaker 2-Mics Pi HAT into the Raspberry Pi, making sure the pins are aligned when inserting the Raspberry Pi.

!!!Note

{% code collapsedlinecount="10" %}
```
Do not hot-swap the ReSpeaker 2-Mics Pi HAT while it is powered up.
```
{% endcode %}

<figure><img src="https://files.seeedstudio.com/wiki/MIC_HATv1.0_for_raspberrypi/img/connection2.jpg?raw=true" alt=""><figcaption></figcaption></figure>

<figure><img src="https://files.seeedstudio.com/wiki/MIC_HATv1.0_for_raspberrypi/img/connection1.jpg?raw=true" alt=""><figcaption></figcaption></figure>

step 2. burn system, log in, change source

Since the current Pi kernel does not currently support the wm8960 codec, we need to build it manually.

1. Make sure you are running the latest Raspbian operating system (debian 9) on your Pi, you can use etcher for system burn-in!
2. You can use VNC or PUTTY to connect to the Raspberry Pi, but please configure the wifi beforehand!
3. Before installing the driver, please switch the source to Tsinghua according to the following procedure.

{% code collapsedlinecount="10" %}
```
sudo nano /etc/apt/sources.list
```
{% endcode %}

If you are commenting out the contents of the original file with #, replace it with the following：

{% code collapsedlinecount="10" %}
```
deb http://mirrors.tuna.tsinghua.edu.cn/raspbian/raspbian/ buster main non-free contrib
deb-src http://mirrors.tuna.tsinghua.edu.cn/raspbian/raspbian/ buster main non-free contrib
```
{% endcode %}

!!!Note

{% code collapsedlinecount="10" %}
```
If it is before 2019-06-20 you need to change `buster` to `Stretch` you can check when it was released by `cat /etc/rpi-issue`.
```
{% endcode %}

Step 3. Download and install the driver Run the following command

{% code collapsedlinecount="10" %}
```
sudo apt-get update
sudo apt-get upgrade
git clone https://github.com/respeaker/seeed-voicecard.git
cd seeed-voicecard #Download Sound Card Driver
sudo ./install.sh  --compat-kernel #Installing the sound card driver
reboot  #reboot
```
{% endcode %}

!!!Note

{% code collapsedlinecount="10" %}
```
If the driver installation fails you can skip to Q1 of FAQ to solve the driver installation failure problem.
```
{% endcode %}

Step 4. Check that the sound card name matches the source code seeed-voicecard.

{% code collapsedlinecount="10" %}
```
pi@raspberrypi:~/seeed-voicecard $ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ALSA [bcm2835 ALSA], device 0: bcm2835 ALSA [bcm2835 ALSA]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: ALSA [bcm2835 ALSA], device 1: bcm2835 ALSA [bcm2835 IEC958/HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: seeed2micvoicec [seeed-2mic-voicecard], device 0: bcm2835-i2s-wm8960-hifi wm8960-hifi-0 []
  Subdevices: 1/1
  Subdevice #0: subdevice #0

pi@raspberrypi:~/seeed-voicecard $ arecord -l
**** List of CAPTURE Hardware Devices ****
card 1: seeed2micvoicec [seeed-2mic-voicecard], device 0: bcm2835-i2s-wm8960-hifi wm8960-hifi-0 []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
pi@raspberrypi:~/seeed-voicecard $
```
{% endcode %}

2. Audio playback tests

Step 1. Recording Test You can record with arecord and play it back with aplay: (don't forget to plug in headphones or speakers).

{% code collapsedlinecount="10" %}
```
arecord -f cd -Dhw:1 | aplay -Dhw:1
```
{% endcode %}

It can also be tested by audacity software. After opening Audacity, select AC108 and 2 channels as inputs and bcm2835 alsa: - (hw: 0, 0) as outputs to test:

{% code collapsedlinecount="10" %}
```
$ sudo apt update
$ sudo apt install audacity
$ audacity                      // be in motion audacity
```
{% endcode %}

![](https://files.seeedstudio.com/wiki/ReSpeaker-4-Mic-Array-for-Raspberry-Pi/img/audacity.png?raw=true)

Step 2. Adjust the volume (can be skipped)

**alsamixer** is a graphical mixer program for configuring sound settings and adjusting volume, Advanced Linux Sound Architecture (ALSA).

{% code collapsedlinecount="10" %}
```
alsamixer
```
{% endcode %}

![](https://files.seeedstudio.com/wiki/MIC_HATv1.0_for_raspberrypi/img/alsamixer.png?raw=true)

!!!Note

{% code collapsedlinecount="10" %}
```
First of all, please use F6 to select seeed-2mic's sound card device.
```
{% endcode %}

The left and right arrow keys are used to select a channel or device, and the "up and down arrows" control the volume of the currently selected device. To exit the programme use ALT + Q or press Esc. More information

### Example of controlling an APA102 LED[​](https://wiki.seeedstudio.com/cn/ReSpeaker_2_Mics_Pi_HAT/#%E6%8E%A7%E5%88%B6apa102-led%E7%9A%84%E7%A4%BA%E4%BE%8B) <a href="#kong-zhi-apa102led-de-shi-li" id="kong-zhi-apa102led-de-shi-li"></a>

Each on-board APA102 LED has an additional driver chip which sets the colour of the LED and then maintains that colour until a new command is received.

![](https://files.seeedstudio.com/wiki/MIC_HATv1.0_for_raspberrypi/img/led.gif?raw=true)

Please open SPI before execution as follows.

{% code collapsedlinecount="10" %}
```
- input： `sudo raspi-config`;
- select "Interfacing Options";
- select "SPI";
- select “Yes”  
- select “OK”
- select “Finish”
```
{% endcode %}

After configuration, you can run the led example by executing the following command line

{% code collapsedlinecount="10" %}
```
cd ~/
git clone https://github.com/respeaker/mic_hat.git
sudo pip install spidev #Installation of spi drivers
cd mic_hat
python pixels.py
```
{% endcode %}

### How to use user-defined buttons[​](https://wiki.seeedstudio.com/cn/ReSpeaker_2_Mics_Pi_HAT/#%E5%A6%82%E4%BD%95%E4%BD%BF%E7%94%A8%E7%94%A8%E6%88%B7%E8%87%AA%E5%AE%9A%E4%B9%89%E6%8C%89%E9%92%AE) <a href="#ru-he-shi-yong-yong-hu-zi-ding-yi-an-niu" id="ru-he-shi-yong-yong-hu-zi-ding-yi-an-niu"></a>

There is a user-defined button on the top of the board that connects to GPIO17. We can call python and RPi.GPIO to read the state。

{% code collapsedlinecount="10" %}
```
sudo pip install rpi.gpio    // install RPi.GPIO library
nano button.py               // copy the following code in button.py
```
{% endcode %}

{% code collapsedlinecount="10" %}
```
import RPi.GPIO as GPIO
import time

BUTTON = 17

GPIO.setmode(GPIO.BCM)
GPIO.setup(BUTTON, GPIO.IN)

while True:
    state = GPIO.input(BUTTON)
    if state:
        print("off")
    else:
        print("on")
    time.sleep(1)
```
{% endcode %}

Save the code as button.py, then run it. It should display "on" when you press the button:

{% code collapsedlinecount="10" %}
```

python button.py
off
off
on
on
off
```
{% endcode %}

### FAQ

<details>

<summary>What should I do if the driver still fails to install even if I follow this wiki strictly?</summary>

If the installation of the driver fails according to the above methods, please click to download the following image (not applicable to 4 belts)

[2018-08-06-raspbian-4GB-for-respeaker](https://v2.fangcloud.com/share/7395fd138a1cab496fd4792fe5?folder_id=188000207913)

<img src="https://files.seeedstudio.com/wiki/2mics_hat/img/image_select.JPG" alt="" data-size="original">

Please perform the following steps:

* First, if you want to use the interactive functions, please enter alexa-auth or dueros-auth to request authorisation, after successful authorisation, it will generate a .avs.json file in the /home/pi directory, then you can use the interactive functions.
* Secondly, there will be a folder of routines for respeaker in /home/pi directory, so you can use the routines according to the mic you are using. But please update the routines in the respeaker directory after burning the system, you can run git pull origin master command in the respeaker directory to update the routines.

</details>

<details>

<summary><strong>#include "portaudio.h" Error when run "sudo pip install pyaudio".</strong></summary>

At the command line, enter the following command

{% code collapsedlinecount="10" %}
```
sudo apt-get install portaudio19-dev
```
{% endcode %}

</details>

<details>

<summary>Warning about installing snowboy with a warning that it is not suitable for the platform</summary>

Currently snowboy is only compatible with python2, so make sure it's python2 by installing a python virtual environment.

</details>

<details>

<summary>Sometimes there are dependency issues when sudo python file.py is used</summary>

When testing, I found that sudo executes from the system environment by default, and the dependencies used in the wiki are installed under \~/env, which can be solved with sudo \~/env/bin/python file.py.

</details>

<details>

<summary>Sound can be heard through the 3.5mm audio jack playback, but not when running ns_kws_doa_alexa_with_light.py</summary>

We have 3 players (mpv, mpg123 and gstreamer) available. mpg123 is more suitable for speech recognition and wakeup more, it is more responsive; while AudioPlayer is more suitable for gstreamer> mpv> mpg123. Gstreamer supports more audio formats and works well on raspberry pi. We can also specify the player for AudioPlayer using the environment variable PLAYER. So try the following command to enable voice \*\*\* Translated with www.DeepL.com/Translator (free version) \*\*\*。

{% code collapsedlinecount="10" %}
```

  sudo apt install mpg123
  PLAYER=mpg123 python ns_kws_doa_alexa_with_light.py

```
{% endcode %}

</details>

<details>

<summary>Calling snowboy while running voice interaction doesn't work.</summary>

Please run audacity to make sure all 4 channels are good. If there is a channel with no data, there is no reply when we say snowboy.

</details>
