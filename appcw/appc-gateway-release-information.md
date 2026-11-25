The following topics provide information about this release of the Oracle Database Gateway for APPC:

- Product Set

- Changes and Enhancements

- Known Restrictions

### Product Set

The following product components are included in the product installation media:

- Oracle Database Gateway for APPC, 12c Release 2 (12.2)

- Oracle Net, 12c Release 2 (12.2)

### Changes and Enhancements

The following sections describe the changes and enhancements unique to the 11g release of the gateway:

- Gateway Password Encryption Tool

- Partial IPv6 Support

#### Gateway Password Encryption Tool

The Gateway Password Encryption tool (`g4drpwd`) has been replaced by a generic feature that is now part of Heterogeneous Services. Refer to Chapter 15, "Security Considerations" in Oracle Database Gateway Installation and Configuration Guide for Microsoft Windows for details.

#### Partial IPv6 Support

There is full IPv6 support between Oracle databases and the gateway but IPv6 is not yet supported between the gateway and IMS Connect.

### Known Restrictions

The following sections list the known restrictions for the Oracle Database Gateway for APPC and PGAU.

#### Known Restrictions for the Gateway

The following restrictions are known to exist in this release of the Oracle Database Gateway for APPC.

##### Multibyte Character Sets Are Not Supported for Numeric Data and Clauses

The Oracle Database Gateway for APPC has supported multibyte character set data for COBOL `PIC G` datatypes since version 3.4. However, the non-numeric character data (such as \$, (,), +, -,.) that is allowed in `DISPLAY` datatypes and `PIC 9` edit masks must still be specified in EBCDIC. The non-numeric character data is not subject to MBCS translation.

##### CICS Transactions Do Not Allow PF Key Emulation

When performing a CICS transaction using the Oracle Database Gateway for APPC, you cannot emulate CICS PF keys.

##### APPC PIP Data Is Not Supported

You cannot define and transmit APPC `PIP` data in this release of the Oracle Database Gateway for APPC.

##### Floating Point Data Type Conversion Is Not Supported

Oracle Database Gateway for APPC does not support floating point data type conversion.

##### Transaction Programs Are Responsible for All Data Compression and Decompression

The Oracle Database Gateway for APPC does not provide exits for compression and decompression facilities. All data exchanged between the gateway and the transaction must be in uncompressed format.

##### IBM VS COBOL II Compiler Desupported

The IBM VS COBOL II compiler has been desupported. However, the string "`IBMVSCOBOLII`" is still used as the value of the compiler name parameter to represent any COBOL compiler you choose to use. The value `IBMVSCOBOLII` should still be used and does not create a dependency on any specific version of the compiler.

#### Known Restrictions for PGAU

##### Restrictions with PGAU COBOL COPY REPLACE

When COBOL input to the PGAU `DEFINE DATA` statement contains a `COPY` `REPLACE` clause, only the first replacement is made.
