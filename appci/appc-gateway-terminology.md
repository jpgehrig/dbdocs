The following topic contains a list of terms and definitions pertaining to the gateway and its components and function.

For a list of other terms and definitions associated with the gateway, refer to Chapter 1 of the [Oracle Database Gateway for APPC User's Guide](../appug/oracle-database-gateway-appc-introduction.md).

### Gateway Initialization File

This file is known as `init``sid.``ora` and it contains parameters that govern the operation of the gateway. If you are using the SNA protocol, refer to [Gateway Initialization Parameters for SNA Protocol](appc-gateway-initialization-parameters-sna.md) for more information. Refer to [Gateway Initialization Parameters for TCP/IP Communication Protocol](appc-gateway-initialization-parameters-tcp-ip.md) if your protocol is TCP/IP.

### Gateway Remote Procedure

The Oracle Database Gateway for APPC provides prebuilt remote procedures. In general, the following three remote procedures are used:

- `PGAINIT`, which initializes transactions

- `PGAXFER`, which transfers data

- `PGATERM`, which terminates transactions

Refer to "[RPC Functions](appc-gateway-introduction.md)" in this guide and to Appendix B, "Gateway RPC Interface" in the [Oracle Database Gateway for APPC User's Guide](../appug/oracle-database-gateway-appc-rpc-interface.md) for more information about gateway remote procedures.

### dg4pwd

`dg4pwd` is a utility which encrypts passwords that are normally stored in the gateway initialization file. Passwords are stored in an encrypted form in the password file, making the information more secure. Refer to "[Passwords in the Gateway Initialization File](appc-gateway-security-requirements.md)" for detailed information about how the `dg4pwd` utility works.

### tg4tcpmap tool

This gateway mapping tool is applicable only when the gateway is using TCP/IP support for IMS Connect. Its function is to map the Side Profile Name to TCP/IP and IMS Connect attributes into the `PGA_TCP_IMSC` table.

### PGA (Procedural Gateway Administration)

PGA is a general reference within this guide to all or most components constituting the Oracle Database Gateway for APPC. This term is used when references to a specific product or component are too narrow.

### PGDL (Procedural Gateway Definition Language)

PGDL is the collection of statements used to define transactions and data to the PGAU.

### PL/SQL Stored Procedure Specification (PL/SQL package)

This is a precompiled PL/SQL procedure that is stored in Oracle database.

### UTL_RAW PL/SQL Package (the UTL_RAW Functions)

This component of the gateway represents a series of data conversion functions for PL/SQL RAW variables and remote host data. The types of conversions performed depend on the language of the remote host data. Refer to Appendix D of the [Oracle Database Gateway for APPC User's Guide](../appug/data-type-conversion-oracle-database-gateway-appc.md) for more information.

### UTL_PG PL/SQL Package (the UTL_PG Functions)

This component of the gateway represents a series of COBOL numeric data conversion functions. Refer to `NUMBER_TO_RAW` and `RAW_TO_NUMBER` argument values in Appendix C of the [Oracle Database Gateway for APPC User's Guide](../appug/oracle-database-gateway-appc-utl_pg-interface.md) for supported numeric data type conversions.
