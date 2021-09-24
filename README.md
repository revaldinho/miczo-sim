# miczo-sim

This is a BASIC Logic Simulator which was included as a type-in listing in the first edition of the book Digital Logic Testing and Simulation, by Alexander Miczo.[1] The original edition of the book is long since out of print and although a second edition is available, the later one was created in 2005 and has probably dropped the BASIC listing.

The original program was created for a MicroSoft BASIC but needs some tweaks to run on other BASICs, e.g. the code assumes some features such as

 * allowing arrays of up to 10 elements to be undeclared
 * allowing READ statements expecting numeric data to accept empty DATA fields
 * allowing comments beginning with an apostrophe to appear immediately after any other valid statement

Amstrad CPC BASIC has all of these features, and the program has been tested by running on the [JavaCPC](https://sourceforge.net/projects/javacpc/) emulator.

A [short extract of the original text](https://github.com/revaldinho/miczo-sim/blob/main/src-orig/MicroSimulator.pdf) is included describing the simulator, the program listing and a number of suggested execises which invite extension and improvement of the simulator. 

Both PDF and original BASIC source code in ASCII format are provided in the [src-orig/](https://github.com/revaldinho/miczo-sim/blob/main/src-orig) directory.

The src-generic/ directory contains a modified version of the program which has so far been tested on

 * Locomotive (CPC) BASIC
 * Brandy BASIC
 * Chipmunk BASIC

The main changes compared with the original for BASIC compatibility are

 * explicit declaration of all arrays
 * revision of the DATA statements to use all numeric values including 0 or -1 fields for end-of-data or invalid entries (see updated DATA description below)
 * replacement of comments starting with an apostrophe by full REM keywords and preceding statement separating colons where necessary
 * addition of explicit GOTO keyword in ELSE <line_no> redirections

## Functional Changes

As well as the minor language tweaks, the code is modified to store logic values in a single byte rather than the original two byte format. This reduces the amount of space needed for storage of the logic values both in the main array and the event queue. More importantly though, the BASIC statements for manipulating the logic values are now simplified to use BASIC bit-wise operations, and there is actually a small run time speed improvement. 

The new logic encoding is

 * 0 = ‘0’ = Logic zero
 * 1 = ‘Z’ = Tristate (high impedance)
 * 2 = ‘X’ = Unknown
 * 3 = ‘1’ = Logic one

Of the BASICs tested, all are able to do the bit-wise AND and OR operations.  However not all BASICs perform the same bit-wise NOT operation. CPC BASIC for example will happily compute &55 as NOT &AA. However, chipmunk BASIC computes &00  as NOT &55, and indeed this is the same result given for a NOT operation on any non-zero number.  The NOT operation instead has to be computed arithmetically as (&03 - value), and then any &01 (‘Z’) results are corrected to &02 (‘X’).

## DATA Statements

The original DATA statements are described in the PDF of the Logic Simulation chapter. The differences introduced by the new code are as follows.

### Netlist description

All unused input fields for logic and fanout gate entries should be filled with 0s explicitly

### Stimulus description

The End of Field token is changed from the string “*” to numeric -1



[1] Digital Logic Testing and Simulation, Alexander Miczo, Harper Collins, New York 1986
