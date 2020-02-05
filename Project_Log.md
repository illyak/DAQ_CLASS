# DAQ_CLASS PROJECT LOG:
COMP898 Master's Project Repository and LOG

*This is the log of ideas on the project:*

Jan 27, 2020

Uploaded the project proposal. 

Feb 3, 2020

Sketched and uploaded a schematic with various I2C serial bus parts.

Seemingly nothing to do with IT at the moment but hang on... This is the alternative to using the gear in the lab there, I make my own. Not as nicely packaged but the DAQ concepts are all the same. This has a few advantages in portability, conceptual simplicity but also the full-cycle of building a DAQ application start to finish.

The free board layout software I tried, KiCAD: https://kicad-pcb.org/    works quite well enough to get this kind of stuff done. I made a little coupon board for work and sent it out today. Typical turnaround takes about a week and the blank boards come back which you then solder the parts to. 

With the parts soldered in place, that FTDI cable (see datasheet here attached) talks to all of them via the I2C serial protocol which you write from Jupyter (or MATLAB, LabVIEW, etc). I do this frequently. It works dandy.

So a finished notebook could be a temperature strip chart, reading that TMP100 sensor (U5 on the schematic) and updating a chart running in Jupyter.  Put your finger on it and the chart respond with a rising peak. 

Another one would be reading/writing text to that EEPROM (U2). It's "only" 256kb in 32768 words x 8-bits each. They come bigger, up to about 2Mb. It's enough to exercise memory allocation concepts. 

There's one that can blink LED lights, U4 is an I/O expander. That maybe should be increased to drive 7-segment displays and then numbers. The temperature read from the TMP100 sensor can be displayed. 

Feb 4, 2020

Thinking about the outline dimensions of the board to carry those couple schematic parts there led me to the BeagleBone Black profile which is a preloaded template in the KiCAD. How handy! There are also Arduino, Raspberry Pi and a couple other template outlines. So..... I was thinking exactly about making this board as a "cape" as add-on boards on the BeagleBone are called. T

Rather than that FTDI cable, the I2C serial bus is one of many peripherals on the Beagle. You just have to hook up the right pins. 

What about Raspberry Pi...? Also a great part but more for video and flashy MAKER applications. It seems the Beagle is better for industrial, connectivity, robotics, IoT and general engineering stuff, hooking low-level hardware to high-level software. Beagle's processor is a TI part... :) Don't laugh. The company can pay for the boards.

**I don't see why Jupyter Notebook wouldn't run on the Beagle.** 

There was another processor I once looked at, the PYNQ FPGA from Xilinx: http://www.pynq.io/  But it doesn't look like anything has happened with that, and/or it's too far out for these purposes. Reading sensors and logging data doesn't need that much horsepower. Xilinx documentation is known to be awful in the industry. Like, we need a decent bicycle, not a Porsche.
