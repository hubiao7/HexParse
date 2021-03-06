Hex Parser and AVR8 Simulator
=============================

Hex Parser
----------
This Hex Parse is design according the Intel Hex format.
We will need a IDE simulator to run a program code in order to generate a hex file. Then we can save the data byte using the HexParse program. The data bytes
will save into a flash memory, which is an large array in the program. The AVR8 simulator will use the data inside flash memory to simulate instruction.
This Hex Parser can still work if there is 20 bit addressing mode (record type 02) or 32 bit addressing mode (record type 04) in a single Hex file.


AVR8 Simulator
--------------
A simulator library for AVR8 microcontroller. It only supports non-XMEGA instructions sets. The library does not support the MCU in-built peripherals, though it can be easily extended. This effort might be pursued in the future.

How to Clone
------------
The following instructions assume that you use ```Git Bash```.
```
git clone https://github.com/Bennyaw/HexParse.git
git submodule init
git submodule update
```

How to Update AvrSimulator
--------------------------
If ```AvrSimulator``` has new updates, the repository can be updated by issuing the command in the ```AVrSimulator``` folder,
```
cd AvrSimulator             # If not already in the folder
git pull origin master      # Pull the simulator updates from the source
ceedling clobber            # Do cleaning
ceedling                    # Build the AvrSimulator
```

Requirements
------------
software: ruby, mingw64/32, git; package: ceedling,
IDE simulator: Atmel Studio 7.0


Running The Simulator
---------------------
We included a small front-end simulation demo program which loads any AVR8 program in Intel Hex file format. The front-end simulator has very simplistic interface just for demonstration. At the moment the user cannot view the disassembled instruction yet (this project might be supported in the future). Only the machine instructions and registers are dumped.

To build the, type:
```
ceedling release
```
Although the libraries are OS-agnostic, but the small front-end simulation demo program is not. It can run only in Windows DOS box. To run the program, go to the project base directory and issue:
```
build\release\simulate.exe <filename>
```
where the ```filename``` is the filename of the Intel hex file to run.

The ATMEL bubblesort project can be found in ```data/example/BubbleSort/```. The assembled program can be found in ```data/example/BubbleSort/Bubblesort/Debug/```. To simulate it, type:
```
build\release\simulate.exe data\example\BubbleSort\BubbleSort\Debug\BubbleSort.hex
```
The original code of the bubble sort program is from [here](http://www.microchip.com//wwwAppNotes/AppNotes.aspx?appnote=en591174).
