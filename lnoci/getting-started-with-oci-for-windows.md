How to get started with OCI for Windows.

This appendix describes only the features of OCI that apply to the Windows 2003, Windows 2000, and Windows XP operating systems. Windows NT is no longer supported.

This chapter contains these topics:

- What Is Included in the OCI Package for Windows?

- Oracle Directory Structure for Windows

- Sample OCI Programs for Windows

- About Compiling OCI Applications for Windows

- About Linking OCI Applications for Windows

- About Running OCI Applications for Windows

- Oracle XA Library

- About Using the Object Type Translator for Windows

### D.1 What Is Included in the OCI Package for Windows?

The OCI for Windows package includes the additional libraries required for linking your OCI programs.

The Oracle Call Interface for Windows package includes:

- Oracle Call Interface (OCI)

- Required Support Files (RSFs)

- Oracle Universal Installer

- Header files for compiling OCI applications

- Library files for linking OCI applications

- Sample programs for demonstrating how to build OCI applications

**See Also:**

[About Oracle Instant Client](instant-client.md) for a simplified OCI installation option

### D.2 Oracle Directory Structure for Windows

OCI is included in the default Oracle Database installation.

When you install Oracle Database, Oracle Universal Installer creates the OCI files in the `oci`, `bin`, and `precomp` directories under the `ORACLE_BASE\ORACLE_HOME` directory. These files include the library files needed to link and run OCI applications, and link with other Oracle for Microsoft Windows products, such as Oracle Forms.

The `ORACLE_BASE\ORACLE_HOME` directory contains the following directories described in Table D-1 that are relevant to OCI.

Table D-1 ORACLE_HOME Directories and Contents

| Directory Name              | Contents                                                      |
|:----------------------------|:--------------------------------------------------------------|
| `\bin`                      | Executable and help files                                     |
| `\oci`                      | Oracle Call Interface directory for Windows files             |
| `\oci\include`              | Header files, such as `oci.h` and `ociap.h`                   |
| `\oci\samples`              | Sample programs                                               |
| `\precomp\admin\ottcfg.cfg` | Object Type Translator utility and default configuration file |

### D.3 Sample OCI Programs for Windows

Where sample program files and corresponding project files are copied when you install OCI.

When OCI is installed, a set of sample programs and their corresponding project files are copied to the `ORACLE_BASE\ORACLE_HOME``\oci\samples` subdirectory. Oracle recommends that you build and run these sample programs to verify that OCI has been successfully installed and to familiarize yourself with the steps involved in developing OCI applications.

To build a sample, run a batch file`(make.bat)`at the command prompt. For example, to build the `cdemo1.c` sample, enter the following command in the directory `samples`:

    C:> make cdemo1

After you finish using these sample programs, you can delete them if you choose.

The `ociucb.c` program should be compiled using `ociucb.bat`. This batch file creates a DLL and places it in the `ORACLE_BASE\ORACLE_HOME``\bin` directory. To load user callback functions, set the environment registry variable `ORA_OCI_UCBPKG` to `OCIUCB`.

### D.4 About Compiling OCI Applications for Windows

When you compile an OCI application, you must include the appropriate OCI header files.

The header files are located in the `\ORACLE_BASE\ORACLE_HOME``\oci\include` directory.

For Microsoft Visual C++, specify `\ORACLE_BASE\ORACLE_HOME\oci\lib\msvc` in the libraries section of the Option dialog box. For the Borland compiler, specify `\ORACLE_BASE\ORACLE_HOME\oci\lib\bc`.

For example, if you are using Microsoft Visual C++ 8.0, you must put in the appropriate path, `\oracle\db_1\oci\include`, in the Directories page of the Options dialog in the Tools menu.

**Note:**

The only Microsoft Visual C++ releases supported for the current OCI release are 7.1 or later.

**See Also:**

Your compiler's documentation for specific information about compiling your application and special compiler options

### D.5 About Linking OCI Applications for Windows

The OCI calls are implemented in dynamic-link libraries (DLLs) that Oracle provides.

The DLLs are located in the `ORACLE_BASE\ORACLE_HOME``\bin` directory and are part of the Required Support Files (RSFs).

Oracle only provides the `oci.lib` import library for use with the Microsoft compiler. Borland compiler is also supported by Oracle for use with OCI. Oracle recommends that applications must always link with `oci.lib` to avoid relinking or compilation with every release.

When using `oci.lib` with the Microsoft compiler, you do not have to indicate any special link options.

This section includes the following topics:

- oci.lib

- Client DLL Loading When Using Load Library()

#### D.5.1 oci.lib

Why you need applications linked with oci.lib.

Oracle recommends that applications be linked with `oci.lib`, which takes care of loading the correct versions of the Oracle DLLs.

#### D.5.2 Client DLL Loading When Using Load Library()

How directories are searched when using the LoadLibrary.

The following directories are searched in this order by the `LoadLibrary()` function for client DLL loading:

- Directory from which the application is loaded or the directory where `oci.dll` is located

- Current directory

- Windows:

  - The 32-bit Windows system directory `(system32)`. Use the `GetWindowsDirectory()` function of the Windows API to obtain the path of this directory.

  - The 16-bit Windows directory `(system)`. There is no Win32 function that obtains the path of this directory, but it is searched.

- Directories that are listed in the `PATH` environment variable

### D.6 About Running OCI Applications for Windows

What’s needed to tun an OCI applications for Windows.

To run an OCI application, ensure that the entire corresponding set of Required Support Files (RSFs) is installed on the computer that is running your OCI application.

### D.7 Oracle XA Library

The XA application programming interface (API) is typically used to enable an Oracle Database to interact with a transaction processing (TP) monitor, such as:

- Oracle Tuxedo

- IBM Transarc Encina

- IBM CICS

You can also use TP monitor statements in your client programs. The use of the XA API is supported from OCI.

The Oracle XA Library is automatically installed as part of Oracle Database Enterprise Edition. Table D-2 lists the components created in your Oracle home directory. The `oci.lib` import library contains the XA exports.

Table D-2 Oracle XA Components

| Component | Location                                |
|:----------|:----------------------------------------|
| `xa.h`    | `ORACLE_BASE\ORACLE_HOME``\oci\include` |

This section includes the following topics:

- About Compiling and Linking an OCI Program with the Oracle XA Library

- About Using XA Dynamic Registration

- XA and TP Monitor Information

#### D.7.1 About Compiling and Linking an OCI Program with the Oracle XA Library

How to compile and link an OCI program with the Oracle XA Library.

To compile and link an OCI program with the Oracle XA Library:

1.  Compile `program``.c` by using Microsoft Visual C++ or the Borland compiler, making sure to include`ORACLE_BASE\ORACLE_HOME``\rdbms\xa` in your path.

2.  Link `program``.obj` with the libraries shown in Table D-3:

    Table D-3 Link Libraries

    | Library       | Location                                                                               |
    |:--------------|:---------------------------------------------------------------------------------------|
    | `oraxa12.lib` | `ORACLE_BASE\ORACLE_HOME``\rdbms\xa`                                                   |
    | `oci.lib`     | `ORACLE_BASE\ORACLE_HOME``\oci\lib\msvc` or,<br>`ORACLE_BASE\ORACLE_HOME``\oci\lib\bc` |

3.  Run `program``.exe`.

#### D.7.2 About Using XA Dynamic Registration

The database supports the use of XA dynamic registration.

XA dynamic registration improves the performance of applications interacting with XA-compliant TP monitors. For TP monitors to use XA dynamic registration with an Oracle Database on Windows, you must add either an environmental variable or a registry variable to the Windows systems on which your TP monitor is running. See either of the following sections for instructions:

- Adding an Environmental Variable for the Current Session

- About Adding a Registry Variable for All Sessions

- Adding a Registry Variable:

##### D.7.2.1 Adding an Environmental Variable for the Current Session

Adding an environmental variable at the command prompt affects only the current session.

##### To Add an Environmental Variable:

From the computer where your TP monitor is installed, enter the following at the command prompt:

    C:\> set ORA_XA_REG_DLL = vendor.dll

In this example, `vendor``.dll` is the TP monitor DLL provided by your vendor.

##### D.7.2.2 About Adding a Registry Variable for All Sessions

Adding a registry variable affects all sessions on your Windows system.

This is useful for computers where only one TP monitor is running.

##### D.7.2.3 Adding a Registry Variable:

To add a registry variable for the TP monitor provided by your vendor, follow these steps.

1.  Go to the computer where your TP monitor is installed.
2.  Enter the following at the command prompt:
        C:\> regedt32

    The Registry Editor window appears.
3.  Go to `HKEY_LOCAL_MACHINE\SOFTWARE\ORACLE\HOME``ID`.
4.  Select the Add Value in the Edit menu. The Add Value dialog box appears.
5.  Enter `ORA_XA_REG_DLL` in the Value Name text box.
6.  Select `REG_EXPAND_SZ` from the Datatype list.
7.  Click OK. The String Editor dialog box appears.
8.  Enter `vendor``.dll` in the String field, where `vendor``.dll` is the TP monitor DLL provided by your vendor.
9.  Click OK. The Registry Editor adds the parameter.
10. Select Exit from the Registry menu.
    The registry exits.

#### D.7.3 XA and TP Monitor Information

See the Distributed TP: The XA Specification and other specific TP monitor and XA information.

Distributed TP: The XA Specification (C193) published by the Open Group at the web site: [Distributed TP: The XA Specification](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/lnoci&id=xa_specification)

**See Also:**

- [Oracle Database Development Guide](../adfns/xa.md), the topic about developing applications with Oracle XA, for more information about the Oracle XA Library and using XA dynamic registration

### D.8 About Using the Object Type Translator for Windows

To take advantage of objects, run the Object Type Translator (OTT) against the database to generate a header file that includes the C structs.

For example, if a `PERSON` type has been created in the database, OTT can generate a C struct with elements corresponding to the attributes of `PERSON`. In addition, a null indicator struct is created that represents null information for an instance of the C struct.

The intype file tells OTT which object types should be translated. This file also controls the naming of the generated structs.

**Note:**

The INTYPE File Assistant is not available, starting with Oracle Database 10g Release 1.

Note that the `CASE` specification inside the intype files, such as `CASE=LOWER`, applies only to C identifiers that are not specifically listed, either through a `TYPE` or `TRANSLATE` statement in the intype file. It is important to provide the type name with the appropriate cases, such as TYPE `Person` and Type `PeRsOn`, in the intype file.

OTT on Windows can be invoked from the command line. A configuration file can also be named on the command line. For Windows, the configuration file is `ottcfg.cfg,` located in `ORACLE_BASE\ORACLE_HOME``\precomp\admin`.
