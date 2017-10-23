# plink86_decode
Fork from https://github.com/roguevm/roguevm-tools.
PLINK86 is a DOS overlay manager used in games such as Wonderland or the Spellcasting series.
Its purpose is to allow for larger programs by dynamically switching between one or more
overlay files, containing program code, text and other binary data.

Any given executable linked via PLINK86 contains a header describing attributes such as the
individual segment's location in the overlay file, the overall segment length and where in
memory the segment should be loaded.
Thus far, I have only found single-overlay configurations.

## Work in progress
* All segments are discovered, retrieved and relocated correctly, but jump table references
to addresses within each segment still need to be fixed up.
* Clean-up, removal of RTLink-specific code and renaming of all refernces to RTLink.

See original README.md below.

# roguevm-tools
RogueVM tools repository

## rtlink_decode
Is a tool written to process games using the RTLink/Plus overlay manager and produce
a flat executable suitable for disassembling with tools such as IDA. It includes
a Makefile, but I've only really tested compiling it with Visual Studio.
The project requires an installation of ScummVM in order to use some of it's classes.

The tool currently detects and handles two different versions of RTLink/Plus..
one version that supports having an external overlay file containing segments,
and another where all the segments are inside the executable. The tool also can
detect, but not yet handle, a third form where an external rtlinkst.com file is
used.

Please remember that produced executables aren't intended to be runnable, and will
only be useful for simplifying disassembly. Also, if you do debug a game using
RTLink/Plus, any of the dynamic segments may shift in and out of memory at any
time, so generally breakpoints can only be placed in the low segments, or in
the thunk methods that are used to pass control to dynamic segments.
