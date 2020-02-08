# Compare Pocket Computers:

Done nicely on wiki, a full spec comparison matrix:<br>
https://en.wikipedia.org/wiki/Comparison_of_single-board_computers
<br>

How do you do this, comparing and picking the "best" pocket computer? Depends what you want to use it for. We want to use it for **data acquisition.** We want to be able to collect real data in a university and/or industrial setting. We want to run Python Jupyter Notebook.  

If you acquire data from a sensor once every second, almost any cheap microcontroller can keep up. However, as acquisition speeds and resolutions increase, the data through-put increases and then you start to need real processing power. Being able to compute or display results will require even more. 

There's also the practical side of price, availability, user base, ease of use, etc. That narrows it down quickly. 

I looked at:

- ***Raspberry Pi 4***
    - Pros:
        - Very popular
        - Best cost/performance
        - Widely available
        - No fatal flaws, would work too
    - Cons:
        - Needs USB 3.0 to run tethered.
        - Uses a Broadcom multimedia processor which makes it better for 
        - Target audience is kids. Nothing wrong about that per se. It's meant for kids of all ages.
        - It's a proprietary design. Maybe that's not the best way in a university setting.
- ***Arduino***
    - Pros:
        - Very popular
        - Lowest cost
        - Easiest way to add "smarts" to a project
    - Cons:
        - Atmel microcontroller core, not running embedded Linux disqualifies it.
- ***BeagleBone Black***
    - Pros:
        - Popular enough
        - Runs tethered on USB 2.0, ie, low power consumption
        - PRU processor can stream data
        - 100% open source project, both hardware and software
    - Cons:
        - Slightly more expensive than equivalent RPi
        - 
- ***BeagleBone AI***
    - Pros:
        - Quite a rocket
        - PRU processor can stream data
        - 100% open source project, both hardware and software
    - Cons:
        - Needs USB 3.0 to run tethered. 
        - About 2x the price of the RPi, but still not inaccessible.

    - Beagle is 100% open source design. You don't get a Raspberry schematic, let alone the PCB design files. Of course, designing your own computer board isn't for the faint-hearted. 
    - The new BeagleBone AI is a rocket at the expense of needing USB 3.0 to run tethered. 
    - The older BeagleBone Black runs cool tethered on a USB 2.0.  
    - The BeagleBone Black or AI can use the same "cape" plug-in board and are compatible, so far as the peripherals are common, which many of the baseline features are. 
