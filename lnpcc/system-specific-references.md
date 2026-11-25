This appendix groups together in one place all references in this guide to system-specific information.

This appendix contains this section:

- System-Specific Information

### D.1 System-Specific Information

System-specific information is described in the appropriate Oracle system-specific documentation for your platform.

#### D.1.1 Location of Standard Header Files

The location of the standard Pro\*C/C++ header files—`sqlca.h`, `oraca.h`, and `sqlda.h`—is system specific. For other your system, see your Oracle system-specific documentation.

#### D.1.2 About Specifying Location of Included Files for the C Compiler

When you use the Pro\*C/C++ command-line option INCLUDE= to specify the location of a non-standard file to be included, you should also specify the same location for the C compiler. The way you do this is system specific. See "[Include Files](advanced-topics.md)".

#### D.1.3 ANSI C Support

Use the CODE= option to make the C code that Pro\*C/C++ generates compatible with your system's C compiler. See "[Function Prototyping](precompiler-concepts.md) ".

#### D.1.4 Struct Component Alignment

C compilers vary in the way they align struct components, usually depending on the system hardware. Use the `sqlvcp()` function to determine the padding added to the `.arr` component of a VARCHAR struct. See the section "[Find the Length of the VARCHAR Array Component](datatypes-and-host-variables.md) ".

#### D.1.5 Size of an Integer and ROWID

The size in bytes of integer datatypes and the binary external size of ROWID datatypes are system dependent. See "[INTEGER](datatypes-and-host-variables.md) " and "[ROWID](datatypes-and-host-variables.md)".

#### D.1.6 Byte Ordering

The order of bytes in a word is platform dependent. See the section "[UNSIGNED](datatypes-and-host-variables.md) ".

#### D.1.7 About Connecting to the Oracle Server

Connecting to the Oracle server using the Oracle Net drivers involves system-specific network protocols. See the section "[Interface to OCI Release 8](advanced-topics.md)" for more details.

#### D.1.8 About Linking in an XA Library

You link in your XA library in a system-dependent way. See the section "[Linking](advanced-topics.md) ", and your Oracle installation or user's guides, for more information.

#### D.1.9 Location of the Pro\*C/C++ Executable

The location of the Pro\*C/C++ Precompiler is system specific. See the section "[The Precompiler Command](precompiler-options.md)", and your installation or user's guides, for more information.

#### D.1.10 System Configuration File

Each precompiler installation has a system configuration file. This file is not shipped with the precompiler; it must be created by the system administrator. The location (directory path) which Pro\*C/C++ searches for the system configuration file is system dependent. See the section "[What Occurs During Precompilation?](precompiler-options.md) " for more information.

#### D.1.11 INCLUDE Option Syntax

The syntax for the value of the INCLUDE command-line option is system specific. See "[INCLUDE](precompiler-options.md)".

#### D.1.12 About Compiling and Linking

Compiling and linking your Pro\*C/C++ output to get an executable application is always system dependent. See the section "[Compile and Link](precompiler-concepts.md) ", and the following sections, for additional information.

#### D.1.13 User Exits

Compiling and linking Oracle Forms user exits is system specific. See [User Exits](user-exits.md).
