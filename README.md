# NICCC-LabVIEW

A LabVIEW implementation of the demoscene video *STNICCC2000 Demo* by Oxygene. Inspired by [@lunasorcery](https://twitter.com/lunasorcery)'s [matplotlib version](https://github.com/lunasorcery/niccc-matplotlib). 

View the [full video](), plus the bonus [XY graph version]().

![STNICCC2000 Demo title screen](images/niccc-labview.png?raw=true "STNICCC2000 Demo title screen")

## Implementation Details

The entire drawing algorithm is implemented within a single state machine, with a couple of helper VIs for reading bytes and words from the scene file. Information about each frame is read from the file and stored in memory, before the scene is constructed using LabVIEW's picture API. Once a frame is complete, it is written to a 2D picture control which handles z-ordering and filling of polygons.

![LabVIEW state machine](images/niccc-labview-state-machine.png?raw=true "LabVIEW state machine")

A *Slow Draw* checkbox has been added which draws the demo one polygon at a time (kinda fun to see how each frame is assembled), while the *Wireframe* checkbox draws the scene without filling the polygons.

An alternate version has been implemented which draws to an XY graph in a wireframe style. The color palette is comprised of up to 16 plots, each providing one of the 4-bit colors for the demo. Polygons with matching palette colors are drawn to the same plot, and a `NaN` value is inserted between them to prevent unwanted lines being drawn.

# Links

[Poüet](https://www.pouet.net/prod.php?which=1251) - Demo info

[ST-NICCC Competition](http://arsantica-online.com/st-niccc-competition/) - Information and download for the data file binary format
