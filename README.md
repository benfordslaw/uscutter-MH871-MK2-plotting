## Plotting with the USCutter MH871-MK2

### Convert SVG into HPGL using VPYPE

The USCutter’s axes are not very intuitive. The y-direction runs parallel the machine, so you must generate an SVG with a height less than the width of the machine: 34 inches. The plotter is fed in the x-direction via a spool, so your SVG can have any width. 

Download [MH871-MK2.toml](https://github.com/benfordslaw/uscutter-MH871-MK2-plotting/blob/848abf4132b205ff69012ca5817c8e2a2e542445/MH871-MK2.toml) into your project’s directory. This is a user-provided configuration file required to build the right kind of hpgl file.

In a VPYPE environment, run

`vpype --config MH871-MK2.toml read PATH/TO/SVG.svg write -d MH871-MK2 -p MH871-MK2 OUTPUT_HPGL.hpgl`

This will create an HPGL file named OUTPUT_HPGL.hpgl.

You can open and check your output .hpgl in InkScape. Pay little attention to the bounds of the A4 paper that InkScape defaults to, but do make sure that your sketch is to the right of the paper’s left edge and above the paper’s bottom edge. It works if you manually move your drawing in InkScape and save. Alternatively, you can modify the origin location's y-coordinate in the .toml file.

### Setting up the USCutter

Turn on the plotter by flipping the power switch on the left side of the machine. 

To load paper, flip all three of the anchor levers into the vertical position. This raises the rollers and allows you to slide the paper under them. Load from the back of the machine, as it will pull paper from that direction as it plots. If you are loading from a spool, make sure the plotter is parallel to the spool and nothing will interfere with the machine's ability to pull paper from it smoothly. Once your paper is perpendicular to the pen's range (it can be useful to line up one side of the paper with one of the ruler marks on the plotter), lower the rollers such that one is 1-2 inches from each edge of the paper and one is in the center of the paper. Heavier paper works best, but there is plenty of thin paper available, either on the ground or hanging behind the machine. 

Loosen the screw on the pen-holder and push the pen-holder down. Load your drawing instrument so that it touches the paper firmly and tighten the screw. If your drawing instrument is too small, wrap tape around it until it is thick enough to be held securely in the pen-holder. Release the pen-holder into the pen-up position and press ‘Test’ on the USCutter. This should plot a star in a square. Manually adjust your pen’s height in the holder if necessary. 

Unlike the AxiDraw, the USCutter’s origin is in the bottom left corner. Accordingly, slide the plotter head all the way to the right of the machine. This is going to the ‘bottom’ of the page according to its axes. When the plotter head is where you want the bottom boundary of your drawing to be, press ‘Origin.’ This will push the pen down briefly, leaving a little dot. Put a piece of tape or scrap paper under the pen when setting the origin to protect your plot if you need to. You can also pull the paper further out after setting the Origin.

### Transmitting to the USCutter

Download [CoolTerm (mac)](https://www.freeware.the-meiers.org/)

Your device may not allow you to open the application. If this happens, go to Settings > Security & Privacy, click the lock, and press ‘Open Anyway’

Connect your laptop via USB to the serial port on the USCutter before opening CoolTerm.

In the CoolTerm menu, go to Connection > Options. For Port, select the usb port connected to the USCutter. For BaudRate, choose 2400. For Flow Control, select XON only. Unselect “Software Supported Flow Control.” 

<img width="450" alt="coolterm-correct-opts" src="https://user-images.githubusercontent.com/74384808/138030927-2a5f423b-8401-492a-a059-d9ee94e1f7cf.png">

Press Connection > Connect, then Connection > Send Text/Binary File. Select your HPGL file and press OK. If there are any issues while plotting, press ‘Reset’ on the USCutter, then press ‘Cancel’ on your device. If the pen is stuck in the down position, press ‘Reset’ again on the USCutter.

If you would like to change the `Cut Speed` or `Cut Pressure`, both possible by pressing `Setup` and using the arrows as marked, do not do so while the plot is in progress. It will freeze and draw random lines. Make sure to `Test` with any new settings before plotting.
