# MCU 26-27

The repo for the custom MCU to replace the teensy. Based on the RP2350

## KiCad libraries and ERC

Open `MCU-2627.kicad_pro` so KiCad loads the project library tables.
`sym-lib-table` points to `Symbols/MCU_Project.kicad_sym`, which preserves
the symbol definitions used by this schematic, including standard symbols.
This keeps library comparisons independent of the standard library version
installed locally or in CI. Edit project symbols in this library and use
**Update Symbols from Library** to update the schematic afterwards.
The original downloaded symbol files remain as reference imports.

`fp-lib-table` maps `MCU_Footprints` to `footprints.pretty`. Custom footprint
assignments use this library nickname; no absolute user paths are required.

Imported pin types have been corrected: the inductor and crystal terminals
and ESD protection terminals are passive; flash clock/chip-select pins are
inputs and its quad-SPI data pins are bidirectional. The regulator's VOUT
is a power output, its supply and ground pins are power inputs, and its
inductor switch terminals are passive. See the
[RT6150A/B datasheet](https://www.richtek.com/assets/product_file/RT6150A%3DRT6150B/DS6150AB-06.pdf)
and [USBLC6-2 datasheet](https://www.st.com/resource/en/datasheet/usblc6-2.pdf).
