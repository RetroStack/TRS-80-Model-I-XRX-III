# TRS-80 Model 1 XRX-III Mod

This project faithfully reimplements the small brown mod board often seen attached to the keyboard of an TRS-80 Model 1. It corrects a software bug in earlier versions of the Level II ROMs, a bug later fixed in version 1.3. The design replicates the original mod's functionality using a 1-to-1 PCB design, including components, interfaces, and even traces.

Since this mod is no longer required for the latest ROM version, there's no need to create it. If you have an older computer, simply update the ROMs, and this mod becomes unnecessary. This repository serves more as a historical record and recreation of the board rather than for implementation.

For more details about this mod, visit: http://www.trs-80.org/xrx-modification/

The entire project is available under the MIT license.

## Project Details

![Overview](/Latest/TRS80_Model_I_XRX_III_Overview.png)

### Latest Files

In the "Latest" folder, you'll find the most up-to-date design files, including:
- 3D views of the board
- The full schematics

### Implementation

This board has been implemented using KiCAD 7. The KiCAD project files are included in this repository.

![Front](/Latest/TRS80_Model_I_XRX_III_3D_Front.png)
![Back](/Latest/TRS80_Model_I_XRX_III_3D_Back.png)

### Schematic Details

The mod monitors when the cassette-interface-in flip-flop on the main board resets. Upon this event, it performs two actions:
1) it removes the clear from the 12-bit counter on the mod board, and
2) it sets a flip-flop to prevent the signal from the OpAmps from reaching the mainboard flip-flop for the cassette data-in.

The counter, utilizing a clock from the video circuitry, counts until 43.3ms have elapsed, after which it resets the mod flip-flop and reopens the cassette data-in port. This process helps to avoid noise being accidentally picked up by the software, which was listening too early (a bug in early system ROM versions).

The board employs two NOR gates for the flip-flop and uses the other two NOR gates to gate the CASSIN signal and then to invert its value (since the gating also inverts the data, restoring the original state of CASSIN). 

Another noteworthy aspect is the use of the two diodes and the pull-up resistor, configured to function like an AND gate. Opting for diodes and a resistor was likely a more cost-effective solution than adding another IC.

### RetroStack Libraries

To work with this KiCAD project, you'll need the RetroStack libraries for KiCAD. Please [follow this link](https://www.github.com/RetroStack/KiCAD-Libraries) to access and install these libraries.

## Main TRS-80 Model 1 Repository

For additional resources related to the TRS-80 Model 1, be sure to check out the [central page for the TRS-80 Model 1](https://www.github.com/RetroStack/TRS-80-Model-I) on [RetroStack](https://www.github.com/RetroStack).

## Support this Project

RetroStack is dedicated to learning about older computer systems and creating documentation and videos about them. We are also resurrecting older computer systems by reimplementing them and making replacement parts available for free. If you're interested in supporting this project, consider visiting our [Patreon page](https://www.patreon.com/RetroStack). Your support is greatly appreciated!

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
