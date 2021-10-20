## Plotting with the USCutter MH871-MK2

### Convert SVG into HPGL using VPYPE

The USCutter’s axes are not very intuitive. The y-direction runs parallel the machine, so you must generate an SVG with a height less than the width of the machine: 34 inches. The plotter is fed in the x-direction via a spool, so your SVG can have any width. 

Download MH871-MK2.toml into your project’s directory. This is a user-provided configuration file required to build the right kind of hpgl file.

In a VPYPE environment, run

`vpype --config MH871-MK2.toml read PATH/TO/SVG.svg write -d MH871-MK2 -p MH871-MK2 OUTPUT_HPGL.hpgl`

This will create an HPGL file named OUTPUT_HPGL.hpgl.

You can open and check your output .hpgl in InkScape. Pay little attention to the bounds of the A4 paper that InkScape defaults to, but do make sure that your sketch is to the right of the paper’s left edge and above the paper’s bottom edge. 

### Setting up the USCutter

Turn on the plotter by flipping the power switch on the left side of the machine. 

Loosen the screw on the pen-holder and push the pen-holder down. Load your drawing instrument so that it touches the paper firmly and tighten the screw. If your drawing instrument is too small, wrap tape around it until it is thick enough to be held securely in the pen-holder. Release the pen-holder into the pen-up position and press ‘Test’ on the USCutter. This should plot a star in a square. Manually adjust your pen’s height in the holder if necessary. 

Unlike the AxiDraw, the USCutter’s origin is in the bottom left corner. Accordingly, slide the plotter head all the way to the right of the machine. This is going to the ‘bottom’ of the page according to its axes. When the plotter head is where you want the bottom boundary of your drawing to be, press ‘Origin.’ This will push the pen down briefly, leaving a little black dot. Put a piece of tape or scrap paper under the pen when setting the origin to protect your plot if you need to.

### Transmitting to the USCutter

Download CoolTerm (mac)

https://www.freeware.the-meiers.org/ 

Your device may not allow you to open the application. If this happens, go to Settings > Security & Privacy, click the lock, and press ‘Open Anyway’

Connect your laptop via USB to the serial port on the USCutter before opening CoolTerm.

In the CoolTerm menu, go to Connection > Options. For Port, select the usb port connected to the USCutter. For BaudRate, choose 2400. For Flow Control, select XON only. Unselect “Software Supported Flow Control.”

Press Connection > Connect, then Connection > Send Text/Binary File. Select your HPGL file and press OK. If there are any issues while plotting, press ‘Reset’ on the USCutter, then press ‘Cancel’ on your device. If the pen is stuck in the down position, press ‘Reset’ again on the USCutter.
![image](https://user-images.githubusercontent.com/74384808/138029770-2661b8b9-4ec9-49c2-b143-9cc2fc93d874.png)
