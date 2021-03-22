# NanoSwinSIDb-Piggyback
Have a faulty 6581/8580 SID chip and need a replacement? The Nano SwinSIDb is a great (though I will admit, not best) choice, but it has one fatal flaw: lack of paddle support. Using this revision on the original Nano SwinSIDb design, you can "piggyback" your original SID chip with a faulty audio circuit and use some of it's secondary functions to add back in support for reading analog paddle inputs, external audio input, and random number generator while synthesizing music using the tried-and-true Nano SwinSIDb circuit.

![Group of Nano SwinSIDb Piggybacks](/images/group.jpg)

## Building
The majority of the components are small SMD parts, but almost all of them can be hand-soldered with a steady hand. The only component that must be soldered using solder paste and a rework station is the active clock chip in a 3.2mm x 2.5mm package. Ensure you double check that no pads are bridged before soldering on the last part, the DIP-28 socket for the SID, because it will cover up a part of the board.

The same jumpers are provided as the original nano SwinSIDb for filter type (MOS6581/MOS8580) and output level (high/low). The jumpers are on by default to use a MOS6581 filter and have high output. You can cut them using an exacto knife to change the settings.

I use PCBWay to manufacture my boards, and all of the necessary files are provided that will be compatible with their services.

<p float="left">
<img src="/images/top.jpg" width="32%" alt="Top of Nano SwinSIDb Piggyback" />
<img src="/images/bottom.jpg" width="32%" alt="Bottom of Nano SwinSIDb Piggyback" />
<img src="/images/sid.jpg" width="32%" alt="Nano SwinSIDb Piggyback with MOS6581 on Top" />
</p>

## Programming Firmware
A standard 6-Pin AVR ICSP header is provided on this board layout unlike the original Nano SwinSIDb. You shouldn't have to solder on a male pin header to program the board. Instead, I use a simple 6-pin cable from my programmer with a male end on it and hold it in place while flashing the chip.

Use the command `make flash` within the firmware directory to flash the copy of the SwinSID firmware with the ['Lazy' fix by Code Killer](http://www.forum64.de/index.php?thread/56605-nano-swinsid-upgrades-paddles-etc/&pageNo=2). Follow this by `make fuse` to ensure that the chip is configured correctly. The makefile utilizes avrdude with an Arduino ISP programmer on port `/dev/ttyACM0` _(linux environment)_. If this configuration doesn't work for you, either modify the Makefile or use your own flash programming environment to flash the provided firmware hex file or any other SwinSID compatible firmware.

## Additional Information
More information about building and programming your own board can be found at [tolaemon.com/nss](http://www.tolaemon.com/nss/). Most of the same principles should apply just with a few different parts. If you'd like to purchase one of these pre-built, I may have some available on my website, [dcdalrymple.com/NanoSwinSIDb-Piggyback/](https://dcdalrymple.com/NanoSwinSIDb-Piggyback/).

## Resources
- [SwinSID Analog Controller Hack](https://ilesj.wordpress.com/2014/07/24/swinsid-analog-controller-hack/)
- [nano SwinSIDb Tutorial](http://www.tolaemon.com/nss/)
