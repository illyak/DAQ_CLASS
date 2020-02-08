# Compare Pocket Computers:

Done nicely on wiki, a full spec comparison matrix including all those you never heard of:<br>
https://en.wikipedia.org/wiki/Comparison_of_single-board_computers
<br>

How do you do this, comparing and picking the "best" pocket computer? Depends what you want to do, of course! Here are some of the considerations relevant to this project:
- To be used as a **data acquisition engine**
- To be able to collect real data in a university and/or industrial setting
    - So for learning how to do it but also for actually doing it
- Run Jupyter Notebook
- Nominal/reasonable cost

For acquiring data from a sensor once every second, almost any cheap microcontroller will do. However, as acquisition speeds and resolutions increase, the data through-put increases and then real processing power is needed. Being able to compute or display results will require even more. Running the whole thing under Jupyter Notebook requires more yet still. 

There's also the practical side of price, availability, user base, ease of use, etc. That narrows it down quickly to the following short list which I looked at:

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
        - Atmel microcontroller core, not running embedded Linux ***disqualifies it.***
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
        - Might run hot and need cooling, depending on what is running (there's a little fan available)
        - About 2x the price of the RPi (pinches but doesn't disqualify it)

**The BeagleBone is the choice and here's why:** <br>
- Price is accessible. Boards are in stock at several suppliers.
- 100% open source project best suits the university
- The AM5729 processor is an industrial controller with impressive specs.
- BeagleBones have the same "cape" (plug-in board) board shape. Capes are cross-compatible, so far as the peripherals are common, which many of the baseline features are. 
- You can chose between a low-power Beagle and a strong processor Beagle
- The PRU processor allows real-time processing, data streaming.

