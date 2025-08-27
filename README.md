# Macintosh IIsi power supply riser board replica

This is a replica of the daughterboard found in the Apple/Sony Macintosh IIsi APS-06 power supply. The part number printed on the original board is AP41S. This PCB often suffers from severe corrosion damage due to electrolytic capacitor leakage, so this project aims to provide you with a way to replace it with a brand new PCB.

<img src="assembled.jpg?raw=true" width="400">

To aid with reverse engineering, all of the components were removed from the board and inspected out of circuit. I used pictures of the bare board ([top](barepcb_top.jpg?raw=true), [bottom](barepcb_bottom.jpg?raw=true)) to draw a replica design. The [Bomarc schematics](https://www.macdat.net/files/pdf/apple/schematics/bomarc/mac_iisi.pdf) were a huge help with part identification and understanding the circuit. However, those schematics did have a few mistakes, which I have corrected in my schematics and BOM. My replica design has been successfully used to build a brand new board with all new components except for the two obsolete ICs.

## Schematics

[Here is a link to the schematics in PDF format](iisi-riser-board.pdf?raw=true).

## Build Notes

[Here is an image that shows the names that I arbitrarily gave each component, along with their values](placement.png?raw=true). It may help if you decide to build one yourself.

The trimpot is used to adjust the voltage. If you build one yourself, it may be prudent to test the power supply with a dummy load connected and get the trimpot adjusted properly before trying to use it in an actual Mac IIsi.

## BOM

[Here is the bill of materials in CSV format](iisi-riser-board.csv). All of the parts with the exception of the two obsolete Mitsubishi/Renesas ICs can be purchased brand new from Digi-Key. Note that you need to purchase ten of the leadframe pins for the edge connector.

## Gerbers

[Here is a link to the gerbers](gerbers/) if you want to have boards made yourself. I ordered them as 30.5x36mm, single layer, 0.8 mm thickness, HASL, and solder mask and silkscreen only on one side.

## Purchasing

For convenience, I plan on building some of these up for sale to recoup my costs on this project. I also will save some bare PCBs you can purchase if you just want to move all of your components over from your original corrosion-damaged PCB. Stay tuned for more info on how I will sell these.

## KiCad Design Notes

- The trace widths were very strange on this board, so I just used polygon copper fills to redraw them all. I also manually tweaked each pad's size to bring everything close to the original design.
- The board fails some DRC checks which I have added as exclusions.
- The three GND-to-GND 0-ohm resistors cause three "Unconnected Items" warnings in the DRC. These can be safely ignored.

## Differences from Bomarc reverse-engineered schematics

- The resistor labeled as 8200 ohms in Bomarc's schematic is really 8.2 ohms.
- The chip marked as `44` is really a Mitsubishi/Renesas M51944BML, not a transistor. It's a voltage detector/reset IC.
- The diode marked as `=B` is a Schottky diode; I opted to use the onsemi SB05-05C, which is also marked as `B`.
- I have identified all of the ceramic capacitor values using an LCR meter.
- Pin 9 of the edge connector has been correctly labeled as GND.

