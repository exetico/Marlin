## Firmware for Ender 5 Plus with BIGTREETECH SKR 1.4 Turbo

**The following fork are created with the following configuration**:
- Ender 5 Plus
- BIGTREETECH SKR 1.4 Turbo with **TMC2208**-drivers
  - Please note that your should set the drivers to UART (Check the [video](https://www.youtube.com/watch?v=vS8RM2RPe-s))
- **Stock screen** (Read: **Not** TFT35, as many users use)
  - [New firmware](https://github.com/exetico/Marlin/blob/2.0.6.1-BTT-SKR-V1.4-Turbo-Ender5Plus_StockScreen/CR-XABL_Screens_V2Rev2.7z) to the screen
- Mainboard mount plate (Mounted [In center](https://www.thingiverse.com/thing:4543939) or [edge mounted](https://www.thingiverse.com/thing:4051503))
<br>

## You'll need to....
1) Print the adapter-brachet
2) Replace motherboard, and fix the wirering - We'll recommend [this video](https://www.youtube.com/watch?v=vS8RM2RPe-s)
  - **Remember** to do the wirering as shown in the "**Stock screen-wirering**"-section! 
4) Update the [firmware](https://github.com/exetico/Marlin/blob/2.0.6.1-BTT-SKR-V1.4-Turbo-Ender5Plus_StockScreen/CR-XABL_Screens_V2Rev2.7z) of the stock-screen
  - Remember to format the card as FAT32 with 4K clusters (MicroSD - **not** SDHC)
5) Build the firmware to the motherboard with PlatformIO
6) Copy the `firmware.bin` to your printer (It's located in `.pio\build\LPC1769`, after you've builded it)

<br>

### Stock screen-wirering

Please note that the blue cable in the screen, are not in use. We just added is, as a spare one.

<span align="center">
	<img src="docs/wires_in-screen.jpg" width="30%">
  <img src="docs/screen-pins_in_board.png" width="30%">
  <img src="docs/wireeing.png" width="30%">
	<br>
	<p>The BL Touch are added in the Z_MIN and SERVO-ports. Please see the YouTube-video for more details about that.</p>
</span>

### Screen Firmware
1) Download the [firmware](https://github.com/exetico/Marlin/blob/2.0.6.1-BTT-SKR-V1.4-Turbo-Ender5Plus_StockScreen/CR-XABL_Screens_V2Rev2.7z) 
2) Unpack it
3) Format a MicroSD-card to FAT32 with **4K cluster-size**
4) Copy the `DWIN_SET`-folder to the SD-card
5) Place the MicroSD-card in the stock screen, and power it on. Wait for it to be finish, and turn it back off. It will sat "END !" in the first line, after it's done.

<span align="center">
	<img src="docs/firmware-flash.png" width="30%">
</span>


<br>

We're used a good amount of sources, to guide us through the process and hints
- [YouTube Video with Board-swap](https://www.youtube.com/watch?v=vS8RM2RPe-s)
- [Source for Screen Firmware](https://github.com/InsanityAutomation/Marlin/blob/CrealityDwin2.0_Bleeding/CR-XABL_Screens_V2Rev2.7z)
- [Notes about using the stock screen with SRK - It's 1.3! So just for extra information](https://www.deviousweb.com/2020/05/08/ender-5-plus-skr1-3-and-factory-screen/)
- [Great guide with LOTS of good tips, content and pictures](https://github.com/GadgetAngel/SKR-V1.4-Turbo-Stepper-Driver-Jumper-Configuration-Manual/tree/master/CURRENT-Manual)

Due to changes in Marlin, we couldn't get the newest repo to work as we wanted.
<br>
<hr>
<br>

# Marlin 3D Printer Firmware

![GitHub](https://img.shields.io/github/license/marlinfirmware/marlin.svg)
![GitHub contributors](https://img.shields.io/github/contributors/marlinfirmware/marlin.svg)
![GitHub Release Date](https://img.shields.io/github/release-date/marlinfirmware/marlin.svg)
[![Build Status](https://github.com/MarlinFirmware/Marlin/workflows/CI/badge.svg?branch=bugfix-2.0.x)](https://github.com/MarlinFirmware/Marlin/actions)

<img align="right" width=175 src="buildroot/share/pixmaps/logo/marlin-250.png" />

Additional documentation can be found at the [Marlin Home Page](https://marlinfw.org/).
Please test this firmware and let us know if it misbehaves in any way. Volunteers are standing by!

## Marlin 2.0

Marlin 2.0 takes this popular RepRap firmware to the next level by adding support for much faster 32-bit and ARM-based boards while improving support for 8-bit AVR boards. Read about Marlin's decision to use a "Hardware Abstraction Layer" below.

Download earlier versions of Marlin on the [Releases page](https://github.com/MarlinFirmware/Marlin/releases).

## Building Marlin 2.0

To build Marlin 2.0 you'll need [Arduino IDE 1.8.8 or newer](https://www.arduino.cc/en/main/software) or [PlatformIO](http://docs.platformio.org/en/latest/ide.html#platformio-ide). Detailed build and install instructions are posted at:

  - [Installing Marlin (Arduino)](http://marlinfw.org/docs/basics/install_arduino.html)
  - [Installing Marlin (VSCode)](http://marlinfw.org/docs/basics/install_platformio_vscode.html).

### Supported Platforms

  Platform|MCU|Example Boards
  --------|---|-------
  [Arduino AVR](https://www.arduino.cc/)|ATmega|RAMPS, Melzi, RAMBo
  [Teensy++ 2.0](http://www.microchip.com/wwwproducts/en/AT90USB1286)|AT90USB1286|Printrboard
  [Arduino Due](https://www.arduino.cc/en/Guide/ArduinoDue)|SAM3X8E|RAMPS-FD, RADDS, RAMPS4DUE
  [LPC1768](http://www.nxp.com/products/microcontrollers-and-processors/arm-based-processors-and-mcus/lpc-cortex-m-mcus/lpc1700-cortex-m3/512kb-flash-64kb-sram-ethernet-usb-lqfp100-package:LPC1768FBD100)|ARM® Cortex-M3|MKS SBASE, Re-ARM, Selena Compact
  [LPC1769](https://www.nxp.com/products/processors-and-microcontrollers/arm-microcontrollers/general-purpose-mcus/lpc1700-cortex-m3/512kb-flash-64kb-sram-ethernet-usb-lqfp100-package:LPC1769FBD100)|ARM® Cortex-M3|Smoothieboard, Azteeg X5 mini, TH3D EZBoard
  [STM32F103](https://www.st.com/en/microcontrollers-microprocessors/stm32f103.html)|ARM® Cortex-M3|Malyan M200, GTM32 Pro, MKS Robin, BTT SKR Mini
  [STM32F401](https://www.st.com/en/microcontrollers-microprocessors/stm32f401.html)|ARM® Cortex-M4|ARMED, Rumba32, SKR Pro, Lerdge, FYSETC S6
  [STM32F7x6](https://www.st.com/en/microcontrollers-microprocessors/stm32f7x6.html)|ARM® Cortex-M7|The Borg, RemRam V1
  [SAMD51P20A](https://www.adafruit.com/product/4064)|ARM® Cortex-M4|Adafruit Grand Central M4
  [Teensy 3.5](https://www.pjrc.com/store/teensy35.html)|ARM® Cortex-M4|
  [Teensy 3.6](https://www.pjrc.com/store/teensy36.html)|ARM® Cortex-M4|

## Submitting Changes

- Submit **Bug Fixes** as Pull Requests to the ([bugfix-2.0.x](https://github.com/MarlinFirmware/Marlin/tree/bugfix-2.0.x)) branch.
- Follow the [Coding Standards](http://marlinfw.org/docs/development/coding_standards.html) to gain points with the maintainers.
- Please submit your questions and concerns to the [Issue Queue](https://github.com/MarlinFirmware/Marlin/issues).

## Marlin Support

For best results getting help with configuration and troubleshooting, please use the following resources:

- [Marlin Documentation](http://marlinfw.org) - Official Marlin documentation
- [Marlin Discord](https://discord.gg/n5NJ59y) - Discuss issues with Marlin users and developers
- Facebook Group ["Marlin Firmware"](https://www.facebook.com/groups/1049718498464482/)
- RepRap.org [Marlin Forum](http://forums.reprap.org/list.php?415)
- [Tom's 3D Forums](https://forum.toms3d.org/)
- Facebook Group ["Marlin Firmware for 3D Printers"](https://www.facebook.com/groups/3Dtechtalk/)
- [Marlin Configuration](https://www.youtube.com/results?search_query=marlin+configuration) on YouTube

## Credits

The current Marlin dev team consists of:

 - Scott Lahteine [[@thinkyhead](https://github.com/thinkyhead)] - USA &nbsp; [Donate](http://www.thinkyhead.com/donate-to-marlin)
 - Roxanne Neufeld [[@Roxy-3D](https://github.com/Roxy-3D)] - USA
 - Chris Pepper [[@p3p](https://github.com/p3p)] - UK
 - Bob Kuhn [[@Bob-the-Kuhn](https://github.com/Bob-the-Kuhn)] - USA
 - Erik van der Zalm [[@ErikZalm](https://github.com/ErikZalm)] - Netherlands &nbsp; [![Flattr Erik](https://api.flattr.com/button/flattr-badge-large.png)](https://flattr.com/submit/auto?user_id=ErikZalm&url=https://github.com/MarlinFirmware/Marlin&title=Marlin&language=&tags=github&category=software)

## License

Marlin is published under the [GPL license](/LICENSE) because we believe in open development. The GPL comes with both rights and obligations. Whether you use Marlin firmware as the driver for your open or closed-source product, you must keep Marlin open, and you must provide your compatible Marlin source code to end users upon request. The most straightforward way to comply with the Marlin license is to make a fork of Marlin on Github, perform your modifications, and direct users to your modified fork.

While we can't prevent the use of this code in products (3D printers, CNC, etc.) that are closed source or crippled by a patent, we would prefer that you choose another firmware or, better yet, make your own.
