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

**Feb 10, 2020**

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
<br>
But there's nothing like customized hardware and so I'll continue down that path. There is a directly usable cape, called the PRU cape, from none other than Texas Instruments, which plugs into the Beagle and offers enough to get going, if not to handle the entire project, depending on how deep one wants to go. The PRU cape is my version of a backup or baseline and I am in parallel customizing a cape with all the relevant stuff all on one. That's a safe position in a hardware/software development project!
<br>
<br>
Todo:
- Continue distilling the hardware situation
- Need to get the Notebook running on the Beagle

**Feb 12, 2020**

Worked on the details of the cape schematic last night and started wondering whether I got some rabbit-holes here. I found some very slick parts, like the Bosch BME680 environmental sensor which measures VOC gas (air quality), barometric pressure, humidity, and temperature. Trouble is, from reading the datasheet, it doesn't look like simple register read/writes to get the data. Digging further into the docs, they say there is an API. That might be a little more envolved then I want to or need to be. TBD... 
<br>
In the interest of fair dislosure, I work for TI. So the Beagle, which uses a TI processor, might be getting some preferential treatment. Still, I think the fact that it is an off-the-shelf processor and the Beagles are all 100% open source, I think, is the better way to go.
<br>
I was mulling through the part datasheet how the I2C peripheral is routed out to which header pin. Hooha, is that thing complicated! As if the hundreds of pins wasn't enough, each pin has over a dozen port functions which have to be assigned to be brought out to the actual working pin. All that stuff usually gets set in a "driver", nobody would ever worry about it. But where does that driver come from? Someone has to write it. Sooner or later, you have to map out the pins and get the right connection to be able to interface hardware with software.   

**Feb 13, 2020**

This evening I looked at the Beagle, thinking the hardware side can probably standby while I sort out the Beagle and whether Jupyter will run. That KiCAD is actually surprisingly easy to use and the few times I ever even needed to go into the documentation, what I wanted was there, easily clarified and I could get on with it. Meanwhile I got a board sample back for work which looks like what was intended, so that whole process is closed loop.   
<br>
So I got the latest Debian image and loaded it on the Beagle. I was running "headless" tethered to a main debugging PC via a USB cable. I poked around the Cloud9 IDE debugger, all well and all very nice. I got an LED to blink! And there was much rejoicing. That's as far as I got for the evening. Not sure I have some settings right for being able to download stuff to the Beagle from Git via the controlling PC and I'll look into that next. Probably should be able to give the Beagle a definitive thumbs up or down this weekend, whether I can get Jupyter to run on it. 
<br>
<br>
**Got plans for the weekend...?** Should be pretty good weekend because:
- Beagle AI -> ordered and coming tomorrow
- PocketBeagle -> ordered and coming Friday
- LP5036 EVM -> ordered and coming Friday. That's the color LED driver chip and with a couple wires I can jumper into the Beagle I2C serial bus lines to control. Other such kits are available.    

**Feb 17, 2020**

Good news:
<br>
Got Jupyter loading and server working on both the BBAI and the BBB... The AI gets fairly warm running its stuff so a little fan is probably not a bad idea. Or maybe the BBB will do for my purposes, it runs cool. I had a "headless" Linux image loaded on the BBB, so I was able to SSH and see that the Jupyter server was running but wasn't able to do anything, mainly because I'm not so versed in Linux commands and don't know what I'm doing... 
<br>
On the hardware side, all the parts I picked can be assigned unique addresses on the same I2C bus. Not sure if that's dumb luck or if  it's the intent of the spec. 
<br>
Next: I'll load the normal desktop version on the BBB. Then I'll load PyVISA to see whether I can run a Notebook to take a reading from a bench instrument, like a volt meter. <br>
Also need to figure out how to use GIT from the BBB. 

**Feb 22, 2020**

Not so fast... 
<br>
I loaded the normal desktop Linux image version of the BBB, thinking I'd get crackin' writing some Notebooks...
<br>
Jupyter does "run" on the BBB, but we should rather say "crawl". I was able to get the on-board LED to blink from the Notebook, but it is unusably clunky and I think that is the way it is, not sure anything can be done about it to speed it up. This is apparently a processor limitation, it's choking. Maybe that's why there's no chit-chat on the web about Jupyter running on the BBB. Aha!
<br>
<br>
Current thinking: 
- What I thought was a lack of adequate memory issue is generally a non-issue. You can boot and run any of them off an SD card. The SD card is basically an SSD. With some secret Linux commands, the drive can be partitioned to full usage of the 16GB or even the 128GB cards I happen to have.
- I have ***not*** yet fully verified the py-VISA library to interface with bench instruments. I can import it and run without errors, it sees there is something there but then I am lacking a (Windows only!) driver to open the channel to communicate. All I have is a handheld meter with a serial over USB and it's lacking a driver. I don't have any better instruments at home with either real USB or Ethernet. I'll take it to work to test. 
- The BBB would have been nice because it is the most stable and practical. But it looks disqualified for lack of horsepower and we have to go with the BBAI. The BBAI is so new that the documentation is half-baked. 
- A complication is that I am not certain the BBAI has the I2C bus peripheral brought out to the header. Most of the sensors use I2C serial bus. That would mean I'd have to redo the device tree. 
- The device tree makes perfect sense to me, the question is whether I get lost in crappy documentation. A simple microcontroller can have its port pins redefined on the fly. With a complicatd processors, you have the device tree file to define the port pin functions at startup as part of the boot file. Then in an FPGA, you don't even have set port pin options, you have to define all that pin functionality and need tools like HDL to help with that.

**Next step:** I'll proceed with the BBAI.

**Feb 23, 2020**

Added a little matchbox fan to the BBAI so it can run cooler and presumably not throttle down the clock. I booted from SD card, did the memory partition expansion to 128GB and installed Jupyter. Did the blinking LED trick. Yes sir, it generally runs much smoother than the Black, almost like a regular desktop. Perhaps we are approaching the point where a lean-running welterweight processor punches as hard as a super heavyweight loaded down with full Windows handicap. Trying to run Jupyter and the Cloud9 IDE at the same time, on the other hand, left it hanging. So you have to do only one large thing at a time. Fair enough. The Jupyter part seems to be running decently though and that is encouraging. I imagine that simple sensor reads and updates to simple plots should work fine. That is the intent here, a type of sandbox. You can move on to compile the optimized algorithms and run them on the BBAI too but that's a totally different project. <br>
<br>
Then I checked what Python packages were loaded as part of the general Linux install. A nice buffet spread: Numpy was there, also the I2C library (goodie!) but not Matplotlib which I tried to load with a straight PIP command but it bawked because of some missing dependancy. That's another project for another day. I don't think Miniconda runs on ARM core processors to make all this handling one-stop-shopping. Maybe it did once but not anything recent I can find. Don't need all that much and will add some other day. <br>
<br>
Next, they constantly tell you to update all the various OS components which I tried but it hung on the kernel updates. Had to force reboot twice. Not sure how critical all those updates really are, I might not have the absolute latest, but I'm not way off either and it seems to work fine without the updates. This just goes to show how half-baked this BBAI actually is though. I start and proceed according to their directions... and it doesn't work! <br>
<br>
I notice that noone else appears to be running Jupyter on the BBAI, so this is the latest and greatest, man. Nothing fatal about it yet either, just various gottchas which I think happen regardless of what platform, even with hardware.<br>
<br>
Was able to find and look at a device tree file but do not have the serial cable to see whether it is the one which it is actually booting with. It says the I2C is brought out to the the pin and that is brought out to the header, according to the schematic. Looks good on paper. It is probably easier to just try it and see what happens, than to follow the trail of breadcrumbs with that serial debugger. Gonna try and make that happen this week because if I2C is brought out and works, we would be in very good shape.<br>

**Some next moves:**
- Test the I2C on the BBAI. I'll need to breadboard something.
- Finalize the basic setup and document it.
- See if I can duplicate an SD card setup.
- Start using GIT for everything. Not so much revision control, it's better sharing and best crash-proofing. 
- Install Matplotlib, maybe Pandas. 

**Feb 25, 2020**

Was using the Linux I2C-Tools library to check what is even brought out to the pins. Confusion here! The schematic says I2C-4 and I2C-5 are on the header pins. The Linux i2cdetect command says i2c-0 and i2c-3 are turned on. The 8000-page manual says there are 5 I2C controllers labeled i= 1,2,3,4,5 and no zero. Somebody is mislabeled and I can only hope the confusion resolves in my favor. The Linux might be counting from zero and so that its i2c-3 is actually the hardware i2c-4. and the the Linux i2c-0 is actually the hardware i2c-1 which is reserved for the PMIC power supply chip, I can see on the schematic. I might get lucky. I am hoping to avoid that device tree stuff because that could burn a lot of time. But, then again, the whole point here is learning. <br>
<br>
Writing this entry today from the Beagle AI too... Ha!





