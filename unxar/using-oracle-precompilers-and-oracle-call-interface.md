This chapter describes how to use Oracle precompilers and the Oracle Call Interface

Topics:

- Overview of Oracle Precompilers

- Bit-Length Support for Client Applications

- Pro\*C/C++ Precompiler

- Pro\*COBOL Precompiler

- Pro\*FORTRAN Precompiler

- SQL\*Module for ADA

- OCI and OCCI

- Running Oracle JDBC/OCI Programs with a 64-Bit Driver

- Custom Make Files

- Correcting Undefined Symbols

- Multithreaded Applications

- Using Signal Handlers

- XA Functionality

### 6.1 Overview of Oracle Precompilers

Oracle precompilers are application development tools that are used to combine SQL statements for an Oracle Database with programs written in a high-level language. Oracle precompilers are compatible with ANSI SQL and are used to develop and open customized applications that run with Oracle Database or any other ANSI SQL database management system.

This section contains the following topics:

- Precompiler Configuration Files

- Relinking Precompiler Executables

- Issues Common to All Precompilers

- Static and Dynamic Linking

- Client Shared and Static Libraries

**Note:**

- `ORACLE_HOME` in this section refers to `ORACLE_HOME` that is created while installing Oracle Database Client 19c by using the Administrator Install type.

- If you have configured a read-only Oracle home, then you must copy the demo directories from ORACLE_HOME to ORACLE_BASE_HOME. Refer to [Oracle Database Installation Guide for Linux](../ladbi/running-demo-from-oracle-base-home.md) for more information.

#### 6.1.1 Precompiler Configuration Files

Configuration files for the Oracle precompilers are located in the `$ORACLE_HOME/precomp/admin` directory.

The following table lists the names of the configuration files for each precompiler.

Table 6-1 System Configuration Files for Oracle Precompilers

| Product                                                                     | Configuration File |
|:----------------------------------------------------------------------------|:-------------------|
| Pro\*C/C++                                                                  | `pcscfg.cfg`       |
| Pro\*COBOL                                                                  | `pcbcfg.cfg`       |
| Pro\*FORTRAN (IBM AIX on POWER Systems (64-Bit), HP-UX, and Oracle Solaris) | `pccfor.cfg`       |
| Object Type Translator                                                      | `ottcfg.cfg`       |
| SQL\*Module for Ada (IBM AIX on POWER Systems (64-Bit))                     | `pmscfg.cfg`       |

#### 6.1.2 Relinking Precompiler Executables

Use the `$ORACLE_HOME/precomp/lib/ins_precomp.mk` make file to relink all precompiler executables. To manually relink a particular precompiler executable, enter the following command:

    $ make -f ins_precomp.mk relink exename = executable_name

This command creates the new executable in the `$ORACLE_HOME/precomp/lib` directory, and then moves it to the `$ORACLE_HOME/bin` directory.

In the preceding example, replace `executable` with one of the product executables listed in Table 6-2.

The following table lists the executables for Oracle Precompilers:

Table 6-2 Executables for Oracle Precompilers

| Product                                                                           | Executable           |
|:----------------------------------------------------------------------------------|:---------------------|
| Pro\*FORTRAN 32-bit (Oracle Solaris, HP-UX and IBM AIX on POWER Systems (64-Bit)) | `profor`             |
| Pro\*COBOL 32-bit (Oracle Solaris, HP-UX, and IBM AIX on POWER Systems (64-Bit))  | `procob`             |
| Pro\*COBOL (Oracle Solaris, HP-UX, and IBM AIX on POWER Systems (64-Bit))         | `procob` or `rtsora` |
| Pro\*C/C++ 32 bit (HP-UX)                                                         | `proc`               |
| Pro\*FORTRAN (HP-UX)                                                              | `profor`             |
| SQL\*Module for Ada (IBM AIX on POWER Systems (64-Bit))                           | `modada`             |

#### 6.1.3 Issues Common to All Precompilers

The following issues are common to all precompilers:

- Uppercase to Lowercase Conversion

  In languages other than C, the compiler converts an uppercase function or subprogram name to lowercase. This can cause a `No such user exists` error message. If you receive this error message, then verify that the case of the function or subprogram name in the option file matches the case used in the IAPXTB table.

- Vendor Debugger Programs

  Precompilers and vendor-supplied debuggers can be incompatible. Oracle does not guarantee that a program run using a debugger performs the same way when it is run without the debugger.

- Value of `IRECLEN` and `ORECLEN` parameters

  The `IRECLEN` and `ORECLEN` parameters do not have maximum values.

#### 6.1.4 Static and Dynamic Linking

You can statically or dynamically link Oracle libraries with precompiler and OCI or OCCI applications. With static linking, the libraries and objects of the whole application are linked into a single executable program. As a result, application executables can become very large.

With dynamic linking, the executing code is partly stored in the executable program and partly stored in libraries that are linked dynamically by the application at run time. Libraries that are linked at run time are called dynamic or shared libraries. The benefits of dynamic linking are:

- Reduced disk space requirements: Multiple applications or calls to the same application can use the same dynamic libraries.

- Reduced main memory requirements: The same dynamic library image is loaded into the main memory only once, and it can be shared by multiple applications.

#### 6.1.5 Client Shared and Static Libraries

The client shared and static libraries are located in `$ORACLE_HOME/lib.` If you use the Oracle-provided `demo_``product``.mk` file to link an application, then the client shared library is linked by default.

If the shared library path environment variable setting does not include the directory that contains the client shared library, then you may see an error message similar to one of the following lines when starting an executable:

    Cannot load library libclntsh.a
    cannot open shared library: .../libclntsh.sl.10.1
    libclntsh.so.10.1: can't open file: errno=2
    can't open library: .../libclntsh.dylib.10.1
    Cannot map libclntsh.so

To avoid this error, set the shared library path environment variable to specify the appropriate directory. The following table shows sample settings for this environment variable name. If the platform supports both 32-bit and 64-bit applications, then ensure that you specify the correct directory, depending on the application that you want to run.

| Platform                                                  | Environment Variable | Sample Setting     |
|:----------------------------------------------------------|:---------------------|:-------------------|
| Oracle Solaris (32-bit and 64-bit applications) and Linux | `LD_LIBRARY_PATH`    | `$ORACLE_HOME/lib` |
| IBM AIX on POWER Systems (32-bit and 64–bit applications) | `LIBPATH`            | `$ORACLE_HOME/lib` |
| HP-UX (32-bit applications)                               | `SHLIB_PATH`         | `$ORACLE_HOME/lib` |
| HP-UX (64-bit applications)                               | `LD_LIBRARY_PATH`    | `$ORACLE_HOME/lib` |

The client shared library is created automatically during installation. If you must re-create it, then complete the following procedure:

1.  Quit all client applications that use the client shared library, including all Oracle client applications such as SQL\*Plus and Oracle Recovery Manager.

2.  Log in as the `oracle` user, and run the following command:

        $ $ORACLE_HOME/bin/genclntsh

##### Non-threaded Client Shared Library

**Note:**

The information in this section applies to HP-UX systems.

On HP-UX, you can use a non-threaded client shared library. However, you cannot use this library with any OCI application that uses or has a dependency on threads.

To use this library for applications that do not use threads, run the following command to build the OCI application for 32 and 64-bit:

    $ make -f demo_rdbms.mk build_nopthread EXE=oci02 OBJS=oci02.o

#### 6.1.6 Generating the Client Static Library

To link applications to the client static library, you must generate it first.

The client static library (`libclntst12.a`) is not generated during an Oracle Database installation. To link the applications to the client static library, you must first generate it:

1.  Switch the user to the Oracle installation owner (`oracle`).
2.  Set the `ORACLE_HOME` environment variable to specify the Oracle home directory used by the Oracle Database installation. For example:
    - Bourne, Bash, or Korn shell:

          $ ORACLE_HOME=/u01/app/oracle/product/19.0.0/dbhome_1
          $ export ORACLE_HOME

    - C shell:

          % setenv ORACLE_HOME /u01/app/oracle/product/19.0.0/dbhome_1
3.  Enter the following command:
        $ $ORACLE_HOME/bin/genclntst

### 6.2 Bit-Length Support for Client Applications

The client application type (32-bit or 64-bit) is supported on the following platforms:

- Oracle Solaris

- Linux x86-64

- IBM: Linux on System z

- IBM AIX on POWER Systems (64-Bit)

- HP-UX Itanium

The following table lists the 32-bit and 64-bit client shared libraries:

| Platform                                                 | 32-Bit Client Shared Library                                      | 64-Bit Client Shared Library                                      |
|:---------------------------------------------------------|:------------------------------------------------------------------|:------------------------------------------------------------------|
| Oracle Solaris, Linux x86-64, and IBM: Linux on System z | `$ORACLE_HOME/lib/libclntsh.so`                                   | `$ORACLE_HOME/lib/libclntsh.so`                                   |
| IBM AIX on POWER Systems (64-Bit)                        | `$ORACLE_HOME/lib/libclntsh.a`<br>`$ORACLE_HOME/lib/libclntsh.so` | `$ORACLE_HOME/lib/libclntsh.a`<br>`$ORACLE_HOME/lib/libclntsh.so` |
| HP-UX Itanium                                            | `$ORACLE_HOME/lib/libclntsh.sl`                                   | `$ORACLE_HOME/lib/libclntsh.sl`                                   |

To implement a mixed word-size installation:

1.  Run the following command to generate the 32-bit and 64-bit client shared libraries:

        $ $ORACLE_HOME/bin/genclntsh

2.  Include the paths of the required 32-bit and 64-bit client shared libraries in one of the following environment variables, depending on the platform:

    | Platform                                                        | Environment Variable |
    |:----------------------------------------------------------------|:---------------------|
    | Oracle Solaris, Linux x86-64, IBM: Linux on System z, and HP-UX | `LD_LIBRARY_PATH`    |
    | IBM AIX on POWER Systems (64-Bit)                               | `LIBPATH`            |
    | HP-UX (32-bit client applications)                              | `SHLIB_PATH`         |

#### Building 32-Bit Pro\*C and OCI Customer Applications

If the operating system supports both 32-bit and 64-bit Pro\*C and Oracle Call Interface (OCI) customer applications, then you can find more information about building 32-bit Pro\*C and OCI applications in the following files:

| For Information About. . .          | Refer to the Following Make Files. . .        |
|:------------------------------------|:----------------------------------------------|
| Building 32-bit Pro\*C applications | `$ORACLE_HOME/precomp/demo/proc/demo_proc.mk` |
| Building 32-bit OCI applications    | `$ORACLE_HOME/rdbms/demo/demo_rdbms.mk`       |

### 6.3 Pro\*C/C++ Precompiler

Before you use the Pro\*C/C++ precompiler, verify that the correct version of the operating system compiler is properly installed.

**See Also:**

- [Oracle Database Installation Guide](../install-and-upgrade.md) for information about supported compiler versions

- [Pro\*C/C++ Programmer's Guide](../lnpcc/introduction.md) for information about the Pro\*C/C++ precompiler and interface features

This section contains the following topics:

- Pro\*C/C++ Demonstration Programs

- Pro\*C/C++ User Programs

#### 6.3.1 Pro\*C/C++ Demonstration Programs

Demonstration programs are provided to show the features of the Pro\*C/C++ precompiler. There are three types of demonstration programs: C, C++, and Object programs. All demonstration programs are located in the `$ORACLE_HOME/precomp/demo/proc` directory. By default, all programs are dynamically linked with the client shared library.

To run the demonstration programs, the programs require the demonstration tables created by the `demobld.sql` script to exist in the JONES schema with a password.

The `demobld.sql` script is located in the `$ORACLE_HOME/sqlplus/demo/` directory in a read-write Oracle home and in the `$(orabasehome)/sqlplus/demo/` directory in a read-only Oracle home.

**Note:**

You must unlock the JONES account and set the password before creating the demonstrations.

Use the `demo_proc.mk` make file to create the demonstration programs. The `demo_proc.mk` file is located in the `$ORACLE_HOME/precomp/demo/proc/` directory in a read-write Oracle home and in the `$(orabasehome/precomp/demo/proc/` in a read-only Oracle home. For example, to precompile, compile, and link the `sample1` demonstration program, run the following command:

    $ make -f demo_proc.mk sample1

**Note:**

On IBM AIX on POWER Systems (64-Bit), to ensure that the demonstration programs compile correctly, include the `-r` option of the `make` command in the following examples. For example:

    $ make -r -f demo_proc.mk sample1

To create all the C demonstration programs for Pro\*C/C++, run the following command:

    $ make -f demo_proc.mk samples

To create all the C++ demonstration programs for Pro\*C/C++, run the following command:

    $ make -f demo_proc.mk cppsamples

To create all the Object demonstration programs for Pro\*C/C++, run the following command:

    $ make -f demo_proc.mk object_samples

Some demonstration programs require you to run a SQL script, located in the `$ORACLE_HOME/precomp/demo/sql` directory. If you do not run the script, then a message prompting you to run it is displayed.

To build a demonstration program and run the corresponding SQL script, include the `make` macro argument `RUNSQL=run` at the command line. For example, to create the `sample9` demonstration program and run the required `$ORACLE_HOME/precomp/demo/sql/sample9.sql` script, run the following command:

    $ make -f demo_proc.mk sample9 RUNSQL=run

To create all the Object demonstration programs and run all the required SQL scripts, run the following command:

    $ make -f demo_proc.mk object_samples RUNSQL=run

#### 6.3.2 Pro\*C/C++ User Programs

You can use the `$ORACLE_HOME/precomp/demo/proc/demo_proc.mk` make file to create user programs. This make file builds both 32-bit and 64-bit user programs. The following table shows the make files that you can use to build user programs with Pro\*C/C++:

| Platform                                                                                           | Make File      |
|:---------------------------------------------------------------------------------------------------|:---------------|
| Oracle Solaris, Linux x86-64, IBM: Linux on System z, IBM AIX on POWER Systems (64-Bit), and HP-UX | `demo_proc.mk` |

**See Also:**

The make file for more information about creating user programs

**Note:**

On IBM AIX on POWER Systems (64-Bit), to ensure that the programs compile correctly, specify the `-r` option for the `make` command used in the following examples.

To create a program by using the `demo_proc.mk` make file, run a command similar to the following:

    $ make -f demo_proc.mk target OBJS="objfile1 objfile2 ..." EXE=exename

In this example:

- `target` is the make file target that you want to use

- `objfilen` is the object file to link the program

- `exename` is the executable program

For example, to create the program `myprog` from the Pro\*C/C++ source file `myprog.pc`, run one of the following commands, depending on the source and the type of executable that you want to create:

- For C source dynamically linked with the client shared library, run the following command:

      $ make -f demo_proc.mk build OBJS=myprog.o EXE=myprog

- For C source statically linked with the client shared library, run the following command:

      $ make -f demo_proc.mk build_static OBJS=myprog.o EXE=myprog

- For C++ source dynamically linked with the client shared library, run the following command:

      $ make -f demo_proc.mk cppbuild OBJS=myprog.o EXE=myprog

- For C++ source statically linked with the client shared library, run the following command:

      $ make -f demo_proc.mk cppbuild_static OBJS=myprog.o EXE=myprog

### 6.4 Pro\*COBOL Precompiler

Table 6-3 shows the naming conventions for the Pro\*COBOL precompiler.

Table 6-3 Pro\*COBOL Naming Conventions

| Item                    | Naming Convention |
|:------------------------|:------------------|
| Executable              | `procob`          |
| Demonstration directory | `procob2`         |
| Make file               | `demo_procob.mk`  |

Pro\*COBOL supports statically linked, dynamically linked, or dynamically loadable programs. Dynamically linked programs use the client shared library. Dynamically loadable programs use the `rtsora` executable located in the `$ORACLE_HOME/bin` directory.

This section contains the following topics:

- Pro\*COBOL Environment Variables

- Pro\*COBOL Oracle Runtime System

- Pro\*COBOL Demonstration Programs

- Pro\*COBOL User Programs

- FORMAT Precompiler Option

#### 6.4.1 Pro\*COBOL Environment Variables

This section describes the environment variables required by Pro\*COBOL:

- Micro Focus Server Express COBOL Compiler

- Acucorp ACUCOBOL-GT COBOL Compiler

##### 6.4.1.1 Micro Focus Server Express COBOL Compiler

To use the Micro Focus Server Express COBOL compiler, you must set the `COBDIR` and `PATH` environment variables and the shared library path environment variable.

**See Also:**

The "Client Shared and Static Libraries" section for information about the shared library path environment variable

##### COBDIR

Set the `COBDIR` environment variable to the directory where the compiler is installed. For example, if the compiler is installed in the `/opt/lib/cobol` directory, then run the following command:

- Bourne, Bash, or Korn shell:

      $ COBDIR=/opt/lib/cobol
      $ export COBDIR

- C shell:

      % setenv COBDIR /opt/lib/cobol

##### PATH

Set the `PATH` environment variable to include the `$COBDIR/bin` directory:

- Bourne, Bash, or Korn shell:

      $ PATH=$COBDIR/bin:$PATH
      $ export PATH

- C shell:

      % setenv PATH ${COBDIR}/bin:${PATH}

##### Shared Library Path

Set the `LIBPATH`, `LD_LIBRARY_PATH`, or `SHLIB_PATH` environment variable to the directory where the compiler library is installed. For example, if the platform uses the `LD_LIBRARY_PATH` environment variable and the compiler library is installed in the `$COBDIR/coblib` directory, then run the following command:

- Bourne, Bash, or Korn shell:

      $ LD_LIBRARY_PATH=${LD_LIBRARY_PATH}:$COBDIR/coblib
      $ export LD_LIBRARY_PATH

- C shell:

      % setenv LD_LIBRARY_PATH ${LD_LIBRARY_PATH}:$COBDIR/coblib

##### 6.4.1.2 Acucorp ACUCOBOL-GT COBOL Compiler

To use the Acucorp ACUCOBOL-GT COBOL compiler, you must set the `A_TERMCAP`, `A_TERM`, `PATH`, and `LD_LIBRARY_PATH` environment variables. If the `LD_LIBRARY_PATH` environment variable setting does not include the correct directory, then an error message similar to the following is displayed when you compile or run a program:

    runcbl: error while loading shared libraries: libclntsh.so:
    cannot open shared object file: No such file or directory

##### A_TERMCAP and A_TERM

Set the `A_TERMCAP` environment variable to specify the location of the `a_termcap` file and set the `A_TERM` environment variable to specify a supported terminal from that file. For example:

- Bourne, Bash, or Korn shell:

      $ A_TERMCAP=/opt/COBOL/etc/a_termcap
      $ A_TERM=vt100
      $ export A_TERMCAP A_TERM

- C shell:

      % setenv A_TERMCAP /opt/COBOL/etc/a_termcap
      % setenv A_TERM vt100

##### PATH

Set the `PATH` environment variable to include the `/opt/COBOL/bin` directory:

- Bourne, Bash, or Korn shell:

      $ PATH=/opt/COBOL/bin:$PATH
      $ export PATH

- C shell:

      % setenv PATH opt/COBOL/bin:${PATH}

##### LD_LIBRARY_PATH

**Note:**

On IBM AIX on POWER Systems (64-Bit), the `LIBPATH` variable is the `LD_LIBRARY_PATH` variable equivalent. You must use the `LIBPATH` variable on IBM AIX on POWER Systems (64-Bit) instead of the `LD_LIBRARY_PATH` variable in the following commands.

Set the `LD_LIBRARY_PATH` environment variable to the directory where the compiler library is installed. For example, if the compiler library is installed in the `/opt/COBOL/lib` directory, then run the following command:

- Bourne, Bash, or Korn shell:

      $ LD_LIBRARY_PATH=${LD_LIBRARY_PATH}:/opt/COBOL/lib
      $ export LD_LIBRARY_PATH

- C shell:

      % setenv LD_LIBRARY_PATH ${LD_LIBRARY_PATH}:/opt/COBOL/lib

#### 6.4.2 Pro\*COBOL Oracle Runtime System

Oracle provides its own complete run-time system, called `rtsora`, to run dynamically loadable Pro\*COBOL programs. Use the `rtsora` run-time system instead of the `cobrun` run-time system to run dynamically loadable Pro\*COBOL programs. If you attempt to run a Pro\*COBOL program with `cobrun`, then an error message similar to the following is displayed:

    $ cobrun sample1.gnt
    Load error : file 'SQLADR'
    error code: 173, pc=0, call=1, seg=0
    173     Called program file not found in drive/directory

#### 6.4.3 Pro\*COBOL Demonstration Programs

Demonstration programs are provided to show the features of the Pro\*COBOL precompiler. The demonstration programs are located in the `$ORACLE_HOME/precomp/demo/procob2` directory. By default, all programs are dynamically linked with the client shared library.

To run the demonstration programs, the programs require the demonstration tables created by the `$ORACLE_HOME/sqlplus/demo/demobld.sql` script to exist in the JONES schema with a password.

**Note:**

You must unlock the JONES account and set the password before creating the demonstrations.

Use the following make file to create the demonstration programs:

    $ORACLE_HOME/precomp/demo/procob2/demo_procob.mk

To precompile, compile, and link the `sample1` demonstration program for Pro\*COBOL, run the following command:

    $ make -f demo_procob.mk sample1

To create the Pro\*COBOL demonstration programs, run the following command:

    $ make -f demo_procob.mk samples

To create and run a dynamically loadable `sample1.gnt` program to be used with the `rtsora` run-time system, run the following command:

    $ make -f demo_procob.mk sample1.gnt
    $ rtsora sample1.gnt

Some demonstration programs require you to run a SQL script, which is located in the `$ORACLE_HOME/precomp/demo/sql` directory. If you do not run the script, then a message requesting you to run it is displayed.

To build a demonstration program and run the corresponding SQL script, include the `make` macro argument `RUNSQL=run` in the command. For example, to create the `sample9` demonstration program and run the required `$ORACLE_HOME/precomp/demo/sql/sample9.sql` script, run the following command:

    $ make -f demo_procob.mk sample9 RUNSQL=run

To create the Pro\*COBOL demonstration programs and run all required SQL scripts, run the following command:

    $ make -f demo_procob.mk samples RUNSQL=run

#### 6.4.4 Pro\*COBOL User Programs

You can use the `$ORACLE_HOME/precomp/demo/procob2/demo_procob.mk` make file to create user programs. This make file builds both 32-bit and 64-bit user programs. The following table shows the make files that you can use to user programs with Pro\*COBOL:

| Platform                                                                                           | Make File        |
|:---------------------------------------------------------------------------------------------------|:-----------------|
| Oracle Solaris, Linux x86-64, IBM: Linux on System z, IBM AIX on POWER Systems (64-Bit), and HP-UX | `demo_procob.mk` |

**See Also:**

The make file for more information about creating user programs

To create a program using the `demo_procob.mk` make file, run a command similar to the following:

    $ make -f demo_procob.mk target COBS="cobfile1 cobfile2 ..." EXE=exename

In this example:

- `target` is the make file target that you want to use

- `cobfilen` is the COBOL source file for the program

- `exename` is the executable program

For example, to create the program `myprog`, run one of the following commands, depending on the source and type of executable that you want to create:

- For COBOL source, dynamically linked with the client shared library, run the following command:

      $ make -f demo_procob.mk build COBS=myprog.cob EXE=myprog

- For COBOL source, statically linked, run the following command:

      $ make -f demo_procob.mk build_static COBS=myprog.cob EXE=myprog

- For COBOL source, dynamically loadable for use with `rtsora`, run the following command:

      $ make -f demo_procob.mk myprog.gnt

#### 6.4.5 FORMAT Precompiler Option

The FORMAT precompiler option specifies the format of input lines for COBOL. If you specify the default value `ANSI`, then columns 1 to 6 contain an optional sequence number, column 7 indicates comments or continuation lines, paragraph names begin in columns 8 to 11, and statements begin in columns 12 to 72.

If you specify the value `TERMINAL`, then columns 1 to 6 are dropped, making column 7 the left most column.

### 6.5 Pro\*FORTRAN Precompiler

Before you use the Pro\*FORTRAN precompiler, verify that the correct version of the compiler is installed. This section contains the following topics:

- Pro\*FORTRAN Demonstration Programs

- Pro\*FORTRAN User Programs

**See Also:**

- [Oracle Database Installation Guide](../install-and-upgrade.md) for information about supported compiler versions

- [Pro\*FORTRAN Supplement to the Oracle Precompilers Guide](../zzfor/writing-Pro-FORTRAN-program.md) for information about the Pro\*FORTRAN precompiler and interface features

#### 6.5.1 Pro\*FORTRAN Demonstration Programs

Demonstration programs are provided to show the features of the Pro\*FORTRAN precompiler. All demonstration programs are located in the `$ORACLE_HOME/precomp/demo/profor` directory. By default, all programs are dynamically linked with the client shared library.

To run the demonstration programs, the demonstration tables created by the `$ORACLE_HOME/sqlplus/demo/demobld.sql` script must exist in the JONES schema with a password.

**Note:**

You must unlock the JONES account and set the password before creating the demonstrations.

To create the demonstration programs, use the `demo_profor.mk` make file, located in the `$ORACLE_HOME/precomp/demo/profor` directory. For example, to precompile, compile, and link the `sample1` demonstration program, run the following command:

    $ make -f demo_profor.mk sample1

To create the Pro\*FORTRAN demonstration programs, run the following command:

    $ make -f demo_profor.mk samples

Some demonstration programs require you to run a SQL script that is located in the `$ORACLE_HOME/precomp/demo/sql` directory. If you do not run the script, then a message prompting you to run it is displayed.

To build a demonstration program and run the corresponding SQL script, include the `make` macro argument `RUNSQL=run` on the command line. For example, to create the `sample11` demonstration program and run the required `$ORACLE_HOME/precomp/demo/sql/sample11.sql` script, run the following command:

    $ make -f demo_profor.mk sample11 RUNSQL=run

To create the Pro\*FORTRAN demonstration programs and run all the required SQL scripts, run the following command:

    $ make -f demo_profor.mk samples RUNSQL=run

#### 6.5.2 Pro\*FORTRAN User Programs

You can use the `$ORACLE_HOME/precomp/demo/profor/demo_profor.mk` make file to create user programs. This make file builds both 32-bit and 64-bit user programs. The following table shows the make files that you can use to build user programs with Pro\*FORTRAN:

| Platform                                                     | Make File        |
|:-------------------------------------------------------------|:-----------------|
| Oracle Solaris, IBM AIX on POWER Systems (64-Bit), and HP-UX | `demo_profor.mk` |

**See Also:**

The make file for more information about creating user programs

To create a program using the `demo_proc.mk` make file, run a command similar to the following:

    $ make -f demo_profor.mk target FORS="forfile1 forfile2 ..." EXE=exename

In this example:

- `target` is the make file target that you want to use

- `forfilen` is the FORTRAN source for the program

- `exename` is the executable program

For example, to create the program `myprog` from the Pro\*FORTRAN source file `myprog.pfo`, run one of the following commands, depending on the type of executable that you want to create:

- For an executable dynamically linked with the client shared library, run the following command:

      $ make -f demo_profor.mk build FORS=myprog.f EXE=myprog

- For an executable statically linked with the client shared library, run the following command:

      $ make -f demo_profor.mk build_static FORS=myprog.f EXE=myprog

### 6.6 SQL\*Module for ADA

**Note:**

The information in this section applies to the IBM AIX on POWER Systems (64-Bit) platform.

Before using SQL\*Module for Ada, verify that the correct version of the compiler is installed.

**See Also:**

- [Oracle Database Installation Guide](../install-and-upgrade.md) for information about required compiler versions

- [Oracle SQL\*Module for Ada Programmer's Guide](http://www.oracle.com/pls/topic/lookup?ctx=E11882-01&id=ZZMOD107) for information about SQL\*Module for Ada

This section contains the following topics:

- SQL\*Module for Ada Demonstration Programs

- SQL\*Module for Ada User Programs

#### 6.6.1 SQL\*Module for Ada Demonstration Programs

Demonstration programs are provided to show the features of SQL\*Module for Ada. All demonstration programs are located in the `$ORACLE_HOME/precomp/demo/modada` directory. By default, all programs are dynamically linked with the client shared library.

To run the `ch1_drv` demonstration program, the demonstration tables created by the `$ORACLE_HOME/sqlplus/demo/demobld.sql` script must exist in the `JONES` schema with a password.

**Note:**

You must unlock the JONES account and set the password before creating the demonstrations.

The `demcalsp` and `demohost` demonstration programs require that the sample college database exists in the `MODTEST` schema. You can use the appropriate `make` command to create the `MODTEST` schema and load the sample college database.

Run the following command to create the SQL\*Module for Ada demonstration programs, run the necessary SQL scripts to create the `MODTEST` user, and create the sample college database:

    $ make -f demo_modada.mk all RUNSQL=run

To create a single demonstration program (`demohost`) and run the necessary SQL scripts to create the `MODTEST` user, and create the sample college database, run the following command:

    $ make -f demo_modada.mk makeuser loaddb demohost RUNSQL=run

To create the SQL\*Module for Ada demonstration programs, without re-creating the sample college database, run the following command:

    $ make -f demo_modada.mk samples

To create a single demonstration program (`demohost`), without re-creating the sample college database, run the following command:

    $ make -f demo_modada.mk demohost

To run the programs, you must define an Oracle Net connect string or alias named INST1_ALIAS that is used to connect to the database where the appropriate tables exist.

#### 6.6.2 SQL\*Module for Ada User Programs

You can use the `$ORACLE_HOME/precomp/demo/modada/demo_modada.mk` make file to create user programs. To create a user program with the `demo_modada.mk` make file, run a command similar to the following:

    $ make -f demo_modada.mk ada OBJS="module1 module2 ..." \
    EXE=exename MODARGS=SQL_Module_arguments

In this example:

- `modulen` is a compiled Ada object

- `exename` is the executable program

- `SQL_Module_arguments` are the command-line arguments to be passed to the SQL\*Module

  **See Also:**

  [Oracle SQL\*Module for Ada Programmer's Guide](http://www.oracle.com/pls/topic/lookup?ctx=E11882-01&id=ZZMOD107) for information about SQL\*Module for Ada

### 6.7 OCI and OCCI

Before you use the Oracle Call Interface (OCI) or Oracle C++ Call Interface (OCCI), verify that the correct version of C or C++ is installed.

**See Also:**

- [Oracle Database Installation Guide](../install-and-upgrade.md) for information about supported compiler versions

- [Oracle Call Interface Programmer's Guide](../lnoci/introduction.md) or [Oracle C++ Call Interface Programmer's Guide](../lncpp/introduction-to-occi.md) for information about OCI and OCCI

This section contains the following topics:

- OCI and OCCI Demonstration Programs

- OCI and OCCI User Programs

#### 6.7.1 OCI and OCCI Demonstration Programs

Demonstration programs that show the features of OCI and OCCI are provided with the Oracle Database 19c Examples software. There are two types of demonstration programs: C and C++. All demonstration programs are located in the `$ORACLE_HOME/rdbms/demo` directory. By default, all programs are dynamically linked with the client shared library.

To run the demonstration programs, the programs require the demonstration tables created by the `$ORACLE_HOME/sqlplus/demo/demobld.sql `script to exist in the JONES schema with a password. Some demonstration programs require specific .sql files to be run, as mentioned in the demonstration source files. OCCI demonstration programs require occidemo.sql to be run.

**Note:**

You must unlock the JONES account and set the password before creating the demonstrations.

Use the `demo_rdbms.mk` make file, which is located in the `$ORACLE_HOME/rdbms/demo` directory, to create the demonstration programs. For example, to compile and link the `cdemo1` demonstration program, run the following command:

    $ make -f demo_rdbms.mk cdemo1

To create the C demonstration programs for OCI, run the following command:

    $ make -f demo_rdbms.mk demos

To create the C++ demonstration programs for OCCI, run the following command:

    $ make -f demo_rdbms.mk occidemos

#### 6.7.2 OCI and OCCI User Programs

You can use the `$ORACLE_HOME/rdbms/demo/demo_rdbms.mk` make file to build user programs. This make file builds either 32-bit or 64-bit user programs. The following table shows the make files that you can use to build 32-bit and 64-bit user programs with Pro\*FORTRAN:

| Platform                                                                   | Make File       |
|:---------------------------------------------------------------------------|:----------------|
| Oracle Solaris, Linux x86-64, IBM AIX on POWER Systems (64-Bit), and HP-UX | `demo_rdbms.mk` |

**See Also:**

The make file for more information about building user programs

### 6.8 Running Oracle JDBC/OCI Programs with a 64-Bit Driver

**Note:**

- The information in this section applies to Oracle Solaris, Linux x86-64, IBM: Linux on System z, IBM AIX on POWER Systems (64-Bit), and HP-UX platforms.

- You can use the instructions and make files described in this section to create JDBC/OCI user programs that use a 64-bit driver.

To run JDBC/OCI demonstration programs with a 64-bit driver:

1.  Add `$ORACLE_HOME/jdbc/lib/ojdbc5.jar` to the start of the `CLASSPATH` environment variable value for each of the following files:
        jdbc/demo/samples/jdbcoci/Makefile
        jdbc/demo/samples/generic/Inheritance/Inheritance1/Makefile
        jdbc/demo/samples/generic/Inheritance/Inheritance2/Makefile
        jdbc/demo/samples/generic/Inheritance/Inheritance3/Makefile
        jdbc/demo/samples/generic/JavaObject1/Makefile
        jdbc/demo/samples/generic/NestedCollection/Makefile
2.  Modify the JAVA and JAVAC variables in the `$ORACLE_HOME/jdbc/demo/samples/generic/Makefile` file to specify the JDK location and the `-d64` flag, as follows:
        JAVA=${ORACLE_HOME}/java/bin/java -d64
        JAVAC=${ORACLE_HOME}/java/bin/javac -d64
3.  Set the `LD_LIBRARY_PATH_64` environment variable to include the `$ORACLE_HOME/lib` directory.
    **Note:**

    On IBM AIX on POWER Systems (64-Bit), the `LIBPATH` variable is the `LD_LIBRARY_PATH_64` variable equivalent. You must use the `LIBPATH` variable on IBM AIX on POWER Systems (64-Bit) instead of the `LD_LIBRARY_PATH_64` variable.

### 6.9 Custom Make Files

Oracle recommends that you use the `demo_``product``.mk` make files provided with the software to create user programs as described in the product-specific sections of this chapter. If you modify the provided make file or if you choose to use a custom-written make file, then remember that the following restrictions apply:

- Do not modify the order of the Oracle libraries. Oracle libraries are included on the link line more than once so that all the symbols are resolved during linking.

  Except for IBM AIX on POWER Systems (64-Bit), the order of the Oracle libraries is essential on all platforms for the following reasons:

  - Oracle libraries are mutually referential. For example, functions in library A call functions in library B, and functions in library B call functions in library A.

  - The HP-UX linkers are one-pass linkers. The IBM AIX on POWER Systems (64-Bit), Linux, and Oracle Solaris linkers are two-pass linkers.

- Add the library to the beginning or to the end of the link line. Do not place user libraries between the Oracle libraries.

- If you choose to use a `make` utility such as `nmake` or GNU `make`, then you must be aware of how macro and suffix processing differs from the `make` utility provided with the operating system. Oracle make files are tested and supported with the `make` utility.

- Oracle library names and the contents of Oracle libraries are subject to change between releases. Always use the `demo_``product``.mk` make file that ships with the current release as a guide to determine the required libraries.

### 6.10 Correcting Undefined Symbols

Oracle provides the `symfind` utility to assist you in locating a library or object file where a symbol is defined. When linking a program, undefined symbols are a common error that produce an error message similar to the following:

    $ make -f demo_proc.mk sample1
    Undefined                       first referenced
     symbol                             in file
    sqlcex                              sample1.o
    sqlglm                              sample1.o
    ld: irrecoverable: Symbol referencing errors. No output written to sample1

The error occurs when the linker cannot find a definition for a referenced symbol. If this error message is displayed, then verify that the library or object file containing the definition exists on the link line and that the linker is searching the correct directories for the file.

The following example shows the output from the `symfind` utility, which is used to locate the `sqlcex` symbol:

    $ symfind sqlcex

    SymFind - Find Symbol <sqlcex> in <**>.a, .o, .so
    ------------------------------------------------------
    Command:         /u01/app/oracle/product/19.0.0/bin/symfind sqlcex
    Local Directory: /u01/app/oracle/product/19.0.0
    Output File:     (none)
    Note:            I do not traverse symbolic links
                     Use '-v' option to show any symbolic links

    Locating Archive and Object files ...
    [11645] |    467572|      44|FUNC |GLOB |0    |8      |sqlcex
    ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^ ./lib/libclntsh.sl
    [35]    |         0|      44|FUNC |GLOB |0    |5      |sqlcex
    ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^ ./lib/libsql.a

### 6.11 Multithreaded Applications

The Oracle libraries provided with this release are thread-safe, they support multithreaded applications.

**See Also:**

[Pro\*C/C++ Programmer's Guide](../lnpcc/multithreaded-applications.md) for more information on Multithreaded Applications

### 6.12 Using Signal Handlers

Oracle Database uses signals for two-task communication. Signals are installed in a user process when the process connects to the database and are removed when it disconnects.

The following table describes the signals that Oracle Database uses for two-task communication.

Table 6-4 Signals for Two-Task Communication

| Signal  | Description                                                                                                                                                                                                                                                                                                                                               |
|:--------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| SIGCLD  | The pipe driver uses SIGCLD, also referred to as SIGCHLD, when an Oracle process terminates. The operating system kernel sends a SIGCLD signal to the user process. The signal handler uses the `wait()` routine to determine if a server process died. The Oracle process does not catch SIGCLD; the user process catches it.                            |
| SIGCONT | The pipe two-task driver uses SIGCONT to send out-of-band breaks from the user process to the Oracle process.                                                                                                                                                                                                                                             |
| SIGINT  | Two-task drivers use SIGINT to detect user interrupt requests. The Oracle process does not catch SIGINT; the user process catches it.                                                                                                                                                                                                                     |
| SIGIO   | Oracle Net protocols use SIGIO to indicate incoming networking events.                                                                                                                                                                                                                                                                                    |
| SIGPIPE | The pipe driver uses SIGPIPE to detect end-of-file on the communications channel. When writing to the pipe, if no reading process exists, then a SIGPIPE signal is sent to the writing process. Both the Oracle process and the user process catch SIGPIPE. SIGCLD is similar to SIGPIPE, but it applies only to user processes, not to Oracle processes. |
| SIGTERM | The pipe driver uses SIGTERM to signal interrupts from the user to the Oracle process. This occurs when the user presses the interrupt key, Ctrl+C. The user process does not catch SIGTERM; the Oracle process catches it.                                                                                                                               |
| SIGURG  | Oracle Net TCP/IP drivers use SIGURG to send out-of-band breaks from the user process to the Oracle process.                                                                                                                                                                                                                                              |

The listed signals affect all precompiler applications. You can install one signal handler for SIGCLD (or SIGCHLD) and SIGPIPE when connected to the Oracle process. If you call the `osnsui()` routine to set it up, then you can have multiple signal handles for SIGINT. For SIGINT, use `osnsui()` and `osncui()` to register and delete signal-catching routines.

You can also install as many signal handlers as you want for other signals. If you are not connected tothe Oracle process, then you can have multiple signal handlers.

Example 6-1 shows how to set up a signal routine and a catching routine.

Example 6-1 Signal Routine and Catching Routine

    /* user side interrupt set */
    word osnsui( /*_ word *handlp, void (*astp), char * ctx, _*/)
    /*
    ** osnsui: Operating System dependent Network Set User-side Interrupt. Add an
    ** interrupt handling procedure astp. Whenever a user interrupt(such as a ^C)
    ** occurs, call astp with argument ctx. Put in *handlp handle for this
    ** handler so that it may be cleared with osncui. Note that there may be many
    ** handlers; each should be cleared using osncui. An error code is returned if
    ** an error occurs.
    */

    /* user side interrupt clear */
    word osncui( /*_ word handle _*/ );
    /*
    ** osncui: Operating System dependent Clear User-side Interrupt. Clear the
    ** specified handler. The argument is the handle obtained from osnsui. An error
    ** code is returned if an error occurs.
    */

Example 6-2 shows how to use the `osnsui()` and the `osncui()` routines in an application program.

Example 6-2 osnsui() and osncui() Routine Template

    /*
    ** User interrupt handler template.
    */
    void sig_handler()
    {
    ...
    }

    main(argc, argv)
    int arc;
    char **argv;
    {

            int handle, err;
            ...

            /* Set up the user interrupt handler */
            if (err = osnsui(&handle, sig_handler, (char *) 0))
            {
                    /* If the return value is nonzero, then an error has occurred
                       Take appropriate action for the error. */
                    ...
            }

            ...

            /* Clear the interrupt handler */
            if (err = osncui(handle))
            {
                    /* If the return value is nonzero, then an error has occurred
                       Take appropriate action for the error. */
                    ...
            }
            ...
    }

### 6.13 XA Functionality

Oracle XA is the Oracle implementation of the X/Open Distributed Transaction Processing XA interface. The XA standard specifies a bidirectional interface between resource managers that provide access to shared resources within transactions, and between a transaction service that monitors and resolves transactions.

Oracle Call Interface has the XA functionality. When building a TP-monitor XA application, ensure that the TP-monitor libraries (that define the symbols `ax_reg` and `ax_unreg`) are placed in the link line before the Oracle client shared library. This link restriction is required when using the XA dynamic registration (Oracle XA switch `xaoswd`).

Oracle Database XA calls are defined in both the client shared library (`libclntsh.a`, `libclntsh.sl`, `libclntsh.so`, or `libclntsh.dylib` depending on the platform) and the client static library (`libclntst11.a`). These libraries are located in the `$ORACLE_HOME/lib` directory.
