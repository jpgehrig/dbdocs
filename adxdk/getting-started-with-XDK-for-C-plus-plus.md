An explanation is given of how to get started with Oracle XML Developer's Kit (XDK) for C++. The C++ demo programs are on the Oracle Database Examples media.

### 26.1 Installing XDK for C++ Components

The XDK for C++ components are included with Oracle Database.

**Related Topics**

- [About Installing XDK](introduction-to-XDK.md)

**See Also:**

[Overview of XDK](introduction-to-XDK.md) for a list of the XDK for C++ components

### 26.2 Configuring the UNIX Environment for XDK for C++ Components

Topics here include component dependencies, environment variables, the runtime and compile-time environments, and the component version.

#### 26.2.1 XDK for C++ Component Dependencies on UNIX

The C++ libraries described in this section are located in `$ORACLE_HOME/lib`.

The XDK for C and C++ components are contained in the library:

    libxml19.a

In addition to the XDK for C components described in [XDK for C Component Dependencies on UNIX](getting-started-with-XDK-for-C.md), the library includes the XML class generator, which creates C++ source files based on an input document type definition (DTD) or XML Schema.

[Table 3-1](getting-started-with-XDK-for-C.md) in [XDK for C Component Dependencies on UNIX](getting-started-with-XDK-for-C.md) describes the Oracle CORE and Globalization Support libraries on which the XDK for C components (UNIX) depend. The library dependencies are the same for C and C++.

#### 26.2.2 Setting Up XDK for C++ Environment Variables on UNIX

The UNIX environment variables required for use with the XDK components are the same for C and C++.

See [Table 3-2](getting-started-with-XDK-for-C.md) in [Setting Up XDK for C Environment Variables on UNIX](getting-started-with-XDK-for-C.md).

#### 26.2.3 Testing the XDK for C++ Runtime Environment on UNIX

You can test your environment by running any of the XDK C utilities for UNIX. These utilities do not have C++ versions.

The C utilities described in [Table 3-3](getting-started-with-XDK-for-C.md) in [Testing the XDK for C Runtime Environment on UNIX](getting-started-with-XDK-for-C.md).

#### 26.2.4 Setting Up and Testing the XDK for C++ Compile-Time Environment on UNIX

How to set up and test the XDK C++ compile-time UNIX environment is described.

Both the C and C++ header files are located in `$ORACLE_HOME/xdk/include`. Table 26-1 describes the C++ header files. [Table 3-4](getting-started-with-XDK-for-C.md) in [Setting Up and Testing the XDK C Compile-Time Environment on UNIX](getting-started-with-XDK-for-C.md) describes the C header files. Your runtime environment must be set up before you can compile your C++ code.

Table 26-1 Header Files in the XDK for C++ Compile-Time Environment

| Header File  | Description                                                                                                                                                     |
|:-------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `oraxml.hpp` | Includes the Oracle9i XML ORA data types and the public ORA application programming interfaces (APIs) included in `libxml.a` (only for backward compatibility). |
| `oraxmlcg.h` | Includes the C APIs for the C++ class generator (only for backward compatibility).                                                                              |
| `oraxsd.hpp` | Includes the Oracle9i XML schema definition (XSD) validator data types and APIs (only for backward compatibility)                                               |
| `xml.hpp`    | Handles the Unified Document Object Model (DOM) APIs transparently, whether you use them through Oracle Call Interface (OCI) or standalone                      |
| `xmlotn.hpp` | Includes the common APIs, whether you compile standalone or use OCI and the Unified DOM                                                                         |
| `xmlctx.hpp` | Includes the initialization and exception-handling public APIs                                                                                                  |

##### 26.2.4.1 Testing the XDK for C++ Compile-Time Environment on UNIX

The simplest way to test your compile-time environment is to run the `make` utility on the sample programs.

The demo programs are located on the Examples media rather than the Oracle Database CD. After installing these programs, they are located in `$ORACLE_HOME/xdk/demo/cpp`.

Build and run the sample programs by executing these commands at the system prompt:

    cd $ORACLE_HOME/xdk/demo/cpp
    make

#### 26.2.5 Verifying the XDK for C++ Component Version on UNIX

How to determine which version of XDK you have is explained.

To get the version of XDK that you are using, change into `$ORACLE_HOME/lib` and run this command as the system prompt:

    strings libxml19.a | grep -i developers

### 26.3 Configuring the Windows Environment for XDK for C++ Components

Topics here include component dependencies, environment variables, testing the runtime environment, setting up and testing the compile-time environment, and Visual C/C++.

#### 26.3.1 XDK for C++ Component Dependencies on Windows

The C++ libraries described in this section are located in `%ORACLE_HOME%\bin`.

The XDK for C and C++ components are contained in this Windows library:

    libxml19.dll

[Table 3-5](getting-started-with-XDK-for-C.md) in [XDK for C Component Dependencies on Windows](getting-started-with-XDK-for-C.md) describes the Oracle Common Oracle Runtime Environment (CORE) and Globalization Support libraries on which the C components for Windows depend. The library dependencies are the same for C and C++.

#### 26.3.2 Setting Up XDK for C++ Environment Variables on Windows

The Windows environment variables required for use with the XDK are the same for C and C++.

See [Table 3-6](getting-started-with-XDK-for-C.md) in [Setting Up XDK for C Environment Variables on Windows](getting-started-with-XDK-for-C.md).

#### 26.3.3 Testing the XDK for C++ Runtime Environment on Windows

You can test your environment by running any of the XDK C utilities for UNIX. These utilities do not have C++ versions.

These utilities are described in [Table 3-7](getting-started-with-XDK-for-C.md) in [Testing the XDK for C Runtime Environment on Windows](getting-started-with-XDK-for-C.md).

#### 26.3.4 Setting Up and Testing the XDK for C++ Compile-Time Environment on Windows

How to set up and test the XDK C++ compile-time Microsoft Windows environment is described.

Table 26-1 in the section Setting Up and Testing the XDK for C++ Compile-Time Environment on UNIX describes the header files required for compilation of the C components on Windows. The relative file names are the same on both UNIX and Windows installations.

On Windows the header files are located in `%ORACLE_HOME%\xdk\include`. Your runtime environment must be set up before you can compile your code.

##### 26.3.4.1 Testing the XDK for C++ Compile-Time Environment on Windows

You can test your compile-time environment by compiling the demo programs, which are located in `%ORACLE_HOME%\xdk\demo\cpp` if you have installed the Oracle Database Examples media.

The procedure for setting the C++ compiler path is identical to the procedure described in [Setting the XDK for C Compiler Path on Windows](getting-started-with-XDK-for-C.md). The procedure for editing the `Make.bat` files is identical to the procedure described in [Editing the Make.bat Files on Windows](getting-started-with-XDK-for-C.md).

#### 26.3.5 Using the XDK for C++ Components with Visual C/C++

You can set up a project in Microsoft Visual C/C++ and use it for the demos included in XDK.

See [Using the XDK for C Components and Visual C++ in Microsoft Visual Studio](getting-started-with-XDK-for-C.md) for instructions.
