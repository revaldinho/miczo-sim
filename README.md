# miczo-sim

This is a BASIC Logic Simulator which was included as a type-in listing in the first edition of the book Digital Logic Testing and Simulation, by Alexander Miczo.[1] The original edition of the book is long since out of print and although a second edition is available, the later one was created in 2005 and has probably dropped the BASIC listing.

The original program was created for a MicroSoft BASIC but needs some tweaks to run on other BASICs, e.g. the code assumes some features such as

 * allowing arrays of up to 10 elements to be undeclared
 * allowing READ statements expecting numeric data to accept empty DATA fields
 * allowing comments beginning with an apostrophe to appear immediately after any other valid statement

Amstrad CPC BASIC has all of these features, and the program has been tested by running on the [JavaCPC](https://sourceforge.net/projects/javacpc/) emulator.

A [short extract of the original text](https://github.com/revaldinho/miczo-sim/blob/main/src-orig/MicroSimulator.pdf) is included describing the simulator, the program listing and a number of suggested execises which invite extension and improvement of the simulator. 

Both PDF and original BASIC source code in ASCII format are provided in the [src-orig/](https://github.com/revaldinho/miczo-sim/blob/main/src-orig) directory.

Alternative src-xyz/ directories are intended for extended versions, and possibly versions customized for specific BASIC dialects and micro-computer hosts.

[1] Digital Logic Testing and Simulation, Alexander Miczo, Harper Collins, New York 1986
