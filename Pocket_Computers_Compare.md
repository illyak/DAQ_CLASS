# Compare Pocket Computers:

How do you do this, comparing and picking the "best" pocket computer? Depends what you want to use it for.

The object here is data acquisition. We want to be able to do real work in a university or industrial setting. 

So here is a list of criteria
I looked at Raspberry Pi, which is essentially the competing single board computer. It had me seriously wondering but then I revisited the Beagle.org page and saw/realized there is a new one: BeagleBone AI. Key advantages of the Beagle system:
BeagleBone Black (= BBB, it's what I showed you) is lighter and less power hungry. There's no free lunch, MIPS cost Watts.
- If BBB isn't good enough, there is BeagleBone AI. 
- A cape I do would be pin compatible (!!) to the extent they share the peripheral features.
- Beagle is open source. Raspberry is proprietary. There is no Raspberry schematic. 
- Raspberry has a great beginner's guide. Nicely done, but for kids, which is the target audience. Kids of all ages, nothing wrong with that.
- BBB and BBAI have a PRU, real-time processor.
- The BBAI has an AM5729 processor which is just ridiculous. The datasheet is > 4k pages...
- Tradeoff the MIPS vs Watts. No free lunch, powerful processors need to be supplied with more power.  

- Beagle is 100% open source design. You don't get a Raspberry schematic, let alone the PCB design files. Of course, doing your own board isn't for the faint-hearted. 
- The new BeagleBone AI is a rocket at the expense of needing USB 3.0 to run tethered. 
- The older BeagleBone Black runs cool tethered on a USB 2.0.  
- The BeagleBone Black or AI can use the same "cape" plug-in board and are compatible, so far as the peripherals are common, which many of the standard issue ones are. 
