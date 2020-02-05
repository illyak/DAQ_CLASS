# DAQ_CLASS
COMP898 Master's Project Repository

This is the log of ideas on the project:

Feb 3, 2020

Seemingly nothing to do with IT at the moment but hang on... This is the alternative to using the gear in the lab there, I make my own. Not as nicely packaged but the DAQ concepts are all the same. This has a few advantages in portability, conceptual simplicity but also the full-cycle of building a DAQ application start to finish.

The free board layout software I tried, KiCAD: https://kicad-pcb.org/    works quite well enough to get this kind of stuff done. I made a little coupon board for work and sent it out today. Typical turnaround takes about a week and the blank boards come back which you then solder the parts to. 

With the parts soldered in place, that FTDI cable (see datasheet here attached) talks to all of them via the I2C serial protocol which you write from Jupyter (or MATLAB, LabVIEW, etc). I do this frequently. It works dandy.

So a finished notebook could be a temperature strip chart, reading that TMP100 sensor (U5 on the schematic) and updating a chart running in Jupyter.  Put your finger on it and the chart respond with a rising peak. 

Another one would be reading/writing text to that EEPROM (U2). It's "only" 256kb in 32768 words x 8-bits each. They come bigger, up to about 2Mb. It's enough to exercise memory allocation concepts. 

There's one that can blink LED lights, U4 is an I/O expander. That maybe should be increased to drive 7-segment displays and then numbers. The temperature read from the TMP100 sensor can be displayed. 

Feb 4, 2020

Thinking about the outline dimensions of the board to carry those couple schematic parts there led me to the BeagleBone Black profile which is a preloaded template in the KiCAD. How handy! There are also Arduino, Raspberry Pi and a couple other template outlines. So..... I was thinking exactly about making this board as a "cape" as add-on boards on the BeagleBone are called. The I2C serial is one of many peripherals. You just have to hook up the right pins. 

What about Raspberry Pi...? 
