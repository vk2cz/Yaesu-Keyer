[EAGLE Schematic and Board.zip](https://github.com/vk2cz/Yaesu-Keyer/files/7992164/EAGLE.Schematic.and.Board.zip)
# Yaesu FT902 PBP Iambic Keyer
Morse code iambic keyer for Yaesu FT-901 FT901D FT901DM /  FT-902 FT902D FT902DM ham radios.

## Background
The Yaesu FT901 / FT902 CW Keyer was on option on these radios back in the early 1980's, with very few radios were optioned back in the day. Of course the original CW keyer option is long obsolete,  and the original Curtis 8044 key chip was a limited run, although updated variants still available for considerable price.  The project arose out of a radio restoration project where this was pretty much the only missing option.  My intent to make this old radio relevant in 2022 mean't the keyer was needed, along with the general restoration activites of metalwork refinishing, capacitor and LED replacement.

This was my PBP tutorial, code is written for readability, and am aware it could be compressed.

## Implementation
With the proliferation of PIC's since the BS-2 in 1995, there were lots of examples of PIC implementations of iambic keyers, many using techniques and attributes that kind of worked, but inflexible with the FT902 variable CW Speed control. The 8 pin 12F683 chip was selected, readily programmed under the MicroCODE studio student license for PICBASIC PRO.
The FT901 / FT902 keyer PCB was built at 70mm by 28mm size to fit the available space, with matching pin header for the CW Option umbilical cable already waiting in the radio. Having not seen the original option board, it was presumably a similar size.

Indeed, this same keyer would readily retro-fit into almost any ham radio rig, or field telegraph.

## BOM
1 x 12F683 PIC
1 x 8 pin DIL Socket
1 x 78L05 Regulator
3 x 0.0033uF Ceramic bypass capacitors
1 x PCB  (see Gerber Zip File)
4 x 1.5k ohm 1/4w resistors
1 x BC548 NPN Transistor (any NPN with Vce>40v and Ice>70mA)
2 x 1uF / 63v Electrolytics
1 x 3mm LED (can be omitted, but visually satisfying)
1 x 0.1" header pin strip
2 x M3x8 Screws (to fit into the radio fixing posts)
1 x Firmware load (see PICBASIC PRO file)

Total budget for DIY approx AUD$7.50

## Software Flowchart

The program utilises the interupt register for the 2 digital input pins (ie not the hardware interupt).
The analog input is a A/D which reads the input volts from the FT902D front panel potentiometer on a 0 to 5v scale (0 to 255 in Byte value).
The digital 12F683 output drives a basic NPN transistor to key the transmitter. This was to isolate the 12F683 from the radios 12v relay keying voltage, and associated keying current which is over the PIC output pin capabilities.

To avoid the 12F683 stalling with lengthy pause commands, the morse dots, dashes and associated spaces are generated in DO WHILE loops, with approx 600uS pauses. This allows the interupt register to queue the next character while the keyer is still sending the current character.

While dot length and dash length weightings are not user adjustable, the code can readily be modified to suit. The code is shown as a .txt file (not pbp)

## CODE & FILES
[VK2CZ Iambic Keyer PBP.zip](https://github.com/vk2cz/Yaesu-Keyer/files/7991183/VK2CZ.Iambic.Keyer.PBP.zip)
[VK2CZ KEYER FINAL R2 spd.txt](https://github.com/vk2cz/Yaesu-Keyer/files/7991191/VK2CZ.KEYER.FINAL.R2.spd.txt)


[CW Keyer_Gerber_2021-11-19.zip](https://github.com/vk2cz/Yaesu-Keyer/files/7991212/CW.Keyer_Gerber_2021-11-19.zip)
![20220203_112542](https://user-images.githubusercontent.com/74847724/152268405-87436b60-1479-432a-ba65-1b2e80fc686d.jpg)
![20220202_150921](https://user-images.githubusercontent.com/74847724/152268411-8bd46331-8368-4c33-bc79-8351bcd334af.jpg)
![20220203_112532](https://user-images.githubusercontent.com/74847724/152268412-8a9bc3e2-21b7-4c5a-881c-d48b6cbec590.jpg)

## Hardware
There are a couple of complete kits (unassembled) available, as only one unit was needed here, extra parts were ordered to meet minimum order qty's.
