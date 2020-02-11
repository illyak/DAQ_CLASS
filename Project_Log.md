# DAQ_CLASS PROJECT LOG:
COMP898 Master's Project Repository and LOG

***This is the log of ideas and work on the project:***

**Jan 27, 2020**

Uploaded the project proposal. 

**Feb 3, 2020**

Sketched and uploaded a schematic with various I2C serial bus parts.

Seemingly nothing to do with IT at the moment but hang on... This is the alternative to using the gear in the lab there, I make my own. Not as nicely packaged but the DAQ concepts are all the same. This has a few advantages in portability, conceptual simplicity but also the full-cycle of building a DAQ application start to finish.

The free board layout software I tried, KiCAD: https://kicad-pcb.org/    works quite well enough to get this kind of stuff done. As an aside test, I made a little coupon board for work and sent it out today. Typical turnaround takes about a week and the blank boards come back which you then solder the parts to. 

With the parts soldered in place, an FTDI cable: https://www.ftdichip.com/Products/Cables/USBMPSSE.htm talks to all of them via the I2C serial protocol which you write from Jupyter (or MATLAB, LabVIEW, etc). I do this frequently. It works dandy.

So a finished notebook could be a temperature strip chart, reading that TMP100 sensor (U5 on the schematic) and updating a chart running in Jupyter.  Put your finger on it and the chart respond with a rising peak. 

Another one would be reading/writing text to that EEPROM (U2). It's "only" 256kb in 32768 words x 8-bits each. They come bigger, up to about 2Mb. It's enough to exercise memory allocation concepts. 

There's one that can blink LED lights, U4 is an I/O expander. That maybe should be increased to drive 7-segment displays and then numbers. The temperature read from the TMP100 sensor can be displayed. 

**Feb 4, 2020**

Thinking about the outline dimensions of the board to carry those couple schematic parts there led me to the BeagleBone Black profile which is a preloaded template in the KiCAD. The stars are aligning. There are also Arduino, Raspberry Pi and a couple other template outlines. MAking a custom outline isn't that big a deal either. But ..... I was thinking exactly about making this board as a "cape" as add-on boards on the BeagleBone are called. 

Rather than that FTDI cable, the I2C serial bus is one of many peripherals on the Beagle. You just have to hook up the right pins. 

What about Raspberry Pi...? Also a great part but more for video and flashy MAKER applications. It seems the Beagle is better for industrial, connectivity, robotics, IoT and general engineering stuff, hooking low-level hardware to high-level software. Beagle's processor is a TI part... :) Don't laugh. The company can pay for the boards.

There was another processor board I once looked at, the PYNQ FPGA from Xilinx: http://www.pynq.io/  It looked so good because it runs the Jupyter Notebook directly, no fuss. But it doesn't look like anything has happened with that, I mean, there isn't any community type action. I suspect it is just too much firepower for what one usually does for "fun" and then most all the developments with it will be company proprietary stuff. Reading sensors and logging data doesn't need that much horsepower. Also an inconvenience is that it is NOT USB bus-powered, you need a separate wall-wort, which is a pain. Basically, don't need that kind of horsepower anyway for data logging and the like.

I don't see why Jupyter Notebook wouldn't run on the Beagle. That is what I am looking into.

**Feb 6, 2020**

Inspirational chat with Prof Tim... In agreement with the Beagle idea with the plug-in cape board with some experimenter parts, like the temp sensor. Here is what I think are immediate next steps (not necessarily in order):

- Write up the formal proposal this weekend, at least to hit that milestone. Can be updated later, as needed.
- A survey comparison of the single board computers out there. 
    - Anything running embedded Linux is plenty for reading a sensor and logging data! Beagle, Raspberry, they'd all be fine. But you want to justify the choice, like due dilligence, and this reasoning goes straight into the final report anyway.
- A decision on the hardware. Here are some immediate thoughts:
    - As self-contained as possible for the sake of fool-proofing and simplicity. No special parts to get lost, nothing to hook up wrong.
    - Power budget is what you get from the USB connector under teathered operation, so less than 5V 250mA. 
    - It'll be a BeagleBone cape outline. 
    - Has to do something undeniably fun and inherently interesting.
- Check what other capes are out there so I'm not ignorantly duplicating previous effort.
- Dust off the Beagle and burn a new image on it. Play around with it. 
- Start looking at whether the Notebook can run on it or what it would take.
- Start keeping track of references, maybe as another markup file, of relevant books, websites, projects, etc.

**Feb 10 2020**

Started writing up the proposal over the weekend. Tougher task than I thought to make it sound coherent but I figure the effort is not in waste because it mostly gets recycled into the final paper. Better to chop away at it in pieces. I want to maintain that Feb 14 deadline. I presume it can be added to and modified as needed throughout the course of this project.

I looked at the Raspberry Pi...<br>
For a while I had my doubts about the BeagleBone Black as the approach to take. Everything looked better on the RPi. And their latest, the RPi-4, had even more to offer. So I eventually went back to the Beagle.org site wondering whether those guys have just been lollygagging around. Hmm... What's that Beagle AI? Just a refreshed Beagle Black? Soon discover it's essentially the Beagle X15, which was a sleeper industrial embedded computer that seemed to never have gotten anywhere, shoehorned into the standard Beagle-size board footprint. It has an industrial processor which is essentially par with the RPi, give or take. 
<br> 
The RPi is definitely better marketed, take a look at the "about us" section on their site and see how many folks are sales and marketing. Nothing wrong with that, I suppose. In the end, it is a propietary design though. 
<br>
<br>
I already decided to make a cape board for the Beagle and have been working through that. So far I have a decent board concept/purpose and all the parts picked, although that isn't completely final. It is a sensor board with enough stuff to pass through many sensoring and data logging concepts. Hours of fun...
<br>
<br>
Meanwhile, I looked around what other capes are out there, so I'm not duplicating effor. I am duplicating effort to some extent. There is quite a spread of capes available and also little add-on boards from https://www.adafruit.com/ , https://www.sparkfun.com/ , and https://www.seeedstudio.com , amoung many others. This falls under IoT, which is a hot topic these days. 

But there's nothing like customized hardware and so I'll continue down that path. There is a directly usable cape, called the PRU cape, from none other than Texas Instruments, which plugs into the Beagle and offers enough to get going, if not to handle the entire project, depending on how deep one wants to go. The PRU cape is my version of a backup or baseline and I am in parallel customizing a cape with all the relevant stuff all on one. That's a safe position in a hardware/software development project!
<br>
<br>
Next steps are to get the Notebook running on the Beagle.


