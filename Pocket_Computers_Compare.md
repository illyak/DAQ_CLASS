# Compare Pocket Computers:

*Already nicely done on wiki, a full spec comparison matrix including all those you never heard of:*<br>
https://en.wikipedia.org/wiki/Comparison_of_single-board_computers
<br>
<br>
***How do you do this, comparing and picking the "best" pocket computer? Depends what you want to do, of course!*** 
<br>
<br>
Here are some of the considerations relevant to this project:
- To be used as a **data acquisition engine**
- To be used for teaching data acquisition concepts but also for real use in the field
- Runs Jupyter Notebook
- Accessible peripherals for low level interfaces to I2C, SPI, etc., components
    - Accepts plug-in boards with an assortment of actuators, sensors and converters
- Capable of USB or Ethernet interface to standard lab bench instruments with GPIB/VISA protocol  
- Practicality: readily available for a nominal/reasonable cost and straighforward to use

For acquiring data from a sensor once every second, almost any microcontroller will do. As acquisition speeds and resolutions increase, the data through-put increases and then real processing power is needed. Being able to compute or display results will require even more. Running under Jupyter Notebook requires more yet still. One might also want to control lab bench instruments. There are also the practical considerations: price, availability, user base, minimal required accessories and cables, ease of use, etc.

A comprehensive performance comparison would make a project in itself, so this is necessarily somewhat subjective in the interest of time. The short list of pocket computers considered:

- ***Raspberry Pi 4***
    - Pros:
        - Very popular, low cost, most people would probably first think of using this
        - A tough call, nothing wrong, it would work too
    - Cons:
        - Needs USB 3.0 power to run tethered
        - Uses a Broadcom multimedia processor which is intended for entertainment.
            - *Doesn't mean it is lacking performance though*
        - Target audience is school kids, look at the starter guide
            - Nothing wrong with that per se, it still is very capable
        - It is a proprietary design 
- ***PYNQ - Xilinx FPGA***
    - Pros:
        - Runs Jupyter right out of the box, the whole point of this board
    - Cons:
        - FPGA is overkill for our purposes of setting up a data collection and instrument control framework 
            - *High-speed acquisition, ie. oscilloscopes, use FPGAs, but that would be a much bigger project* 
        - Approaching 200 bucks for a setup
        - Cable spaghetti: needs Ethernet *and* USB *and* wallwart for debug
- ***Arduino***
    - Pros:
        - Very popular, lowest cost, doesn't need any intro
    - Cons:
        - Uses an Atmel microcontroller, not obviously adequate to run Jupyter, doubtful
- ***BeagleBone Black***
    - Pros:
        - Popular, been around, plenty of community
        - Runs tethered and cool on USB 2.0, ie, low power consumption, could run on battery
        - Real-time PRU co-processor can stream data, ie, oscilloscope-style
        - 100% open source project, both hardware and software
    - Cons:
        - No fatal flaws, slightly more expensive than equivalent RPi
- ***BeagleBone AI***
    - Pros:
        - Uses a bonafide industrial controller with huge featureset
        - 100% open source project, both hardware and software
        - The "black" and the "AI" share the same cape pinout
            - The AI is a superset of the Black
    - Cons:
        - Needs USB 3.0 to run tethered. 
        - Might run hot and need cooling, but a little fan is available
        - Rounding the 100 bucks threshold
<br>

## The BeagleBone is the choice and here's why: <br>
- Price is accessible. Boards are in stock at normal parts suppliers (Digi-Key, Mouser, Newark)
- 100% open source project best suits the university and modern data transparency concepts
- Fully documented and all design files available. Redoing the board isn't for the faint-hearted, but possible
- Two flavors: Chose between a low-power Beagle (Black) and a strong processor Beagle (AI)
- The AM5729 processor on the AI version is an industrial controller with seemingly inexhaustable specs
    - The software paradigm will change before the hardware possibilities are fully exploited
- Both Beagles have the same cape pinout. Many of the peripherals are common, which means the capes are cross-compatible 
- The PRU co-processor is intended for real-time processing, data streaming, live control, etc
    - Can program in ASSEMBY with a 45-count RISC instruction set, full gamut from highest to lowest level programming.

