# Compare Pocket Computers:

*Done nicely on wiki, a full spec comparison matrix including all those you never heard of:*<br>
https://en.wikipedia.org/wiki/Comparison_of_single-board_computers
<br>
<br>
***How do you do this, comparing and picking the "best" pocket computer? Depends what you want to do, of course!*** 
<br>
<br>
Here are some of the considerations relevant to this project:
- To be used as a **data acquisition engine**
- Can be used for teaching data acquisition but also for real use in the field
- Run Jupyter Notebook
- Low level interface to I2C or SPI serial protocol
    - The intent is to build a plug-in board with an assortment of actuators and sensors for this purpose
- High level interface to standard lab bench instruments with GPIB/VISA protocol  
- Practicality: readily available for a nominal/reasonable cost and straighforward to use

For acquiring data from a sensor once every second, almost any microcontroller will do. As acquisition speeds and resolutions increase, the data through-put increases and then real processing power is needed. Being able to compute or display results will require even more. Running under Jupyter Notebook requires more yet still. One might also want to control lab bench instruments. There are also the practical considerations: price, availability, user base, minimal required accessories and cables, ease of use, etc.

A comprehensive comparison would make a project in itself, so this is somewhat subjective in the interest of time. The short list of pocket computers considered:

- ***Raspberry Pi 4***
    - Pros:
        - Very popular, low cost, most people would probably first think of using this
        - Nothing wrong, it would work too
    - Cons:
        - Needs USB 3.0 power to run tethered
        - Uses a Broadcom multimedia processor which is intended for entertainment.
            - *Entertainment is mostly what people are using it for*
        - Target audience is kids, look at the starter guide. Nothing wrong with that per se, kids of all ages.
        - It's a proprietary design. 
- ***PYNQ - Xilinx FPGA***
    - Pros:
        - Runs Jupyter right out of the box, the whole point of it
    - Cons:
        - FPGA is overkill for our purposes of setting up a data collection and instrument control framework 
            - *High-speed acquisition, ie. oscilloscopes, use FPGAs, but that would be a much bigger project* 
        - Approaching 200 bucks for a setup
        - Cable spaghetti: needs Ethnet *and* USB *and* wallwart
- ***Arduino***
    - Pros:
        - Very popular, lowest cost, doesn't need any intro
    - Cons:
        - Uses an Atmel microcontroller which is not immediately and obviously powerful enough to run Jupyter
- ***BeagleBone Black***
    - Pros:
        - Popular, been around, plenty of community
        - Runs tethered and cool on USB 2.0, ie, low power consumption, could run on battery
        - PRU processor can stream data, ie, oscilloscope-like
        - 100% open source project, both hardware and software
    - Cons:
        - Slightly more expensive than equivalent RPi
- ***BeagleBone AI***
    - Pros:
        - The processor data manual is 8063 pages. This is a real industrial controller
        - PRU co-processor can stream data, ie, oscilloscope-like
        - 100% open source project, both hardware and software
        - The "black" and the "AI" share the same cape outline
    - Cons:
        - Needs USB 3.0 to run tethered. 
        - Might run hot and need cooling, but a little fan is available
        - More money than the RPi but not prohibitively. 

**The BeagleBone is the choice and here's why:** <br>
- Price is accessible. Boards are in stock at several suppliers
- 100% open source project best suits the university
- Fully documented and all design files available. Redoing the board isn't for the faint-hearted, but possible
- There are two flavors: Can chose between a low-power Beagle (Black) and a strong processor Beagle (AI)
- The AM5729 processor in the AI version is an industrial controller with impressive specs
- The two BeagleBones have the same cape pinout and footprint. Many of the peripherals are common, which means the capes would be cross-compatible 
- The PRU processor allows real-time processing, data streaming, live control, etc.

