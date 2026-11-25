This preface contains:

- Changes in Oracle Services for Microsoft Transaction Server in ODAC 12c Release 3

- Changes in Oracle Database 12c Release 1 (12.1)

### Changes in Oracle Services for Microsoft Transaction Server in ODAC 12c Release 3

The following are changes in Oracle Services for Microsoft Transaction Server Developer's Guide for ODAC 12c Release 3.

#### New Features

The following features are new in this release:

- Distributed Transactions without `Oracle.ManagedDataAccessDTC.dll`

  The `Oracle.ManagedDataAccessDTC.dll` assembly is no longer required for distributed transaction applications running in .NET Framework 4.5.2 or higher and ODP.NET, Managed Driver. Upon ODP.NET installation, `Oracle.ManagedDataAccessDTC.dll` is no longer placed into the Global Assembly Cache (GAC). For applications that use .NET Framework 4.5.1 or earlier, `Oracle.ManagedDataAccessDTC.dll` needs to be placed either in the application directory or in the GAC.

### Changes in Oracle Database 12c Release 1 (12.1)

The following are changes in Oracle Services for Microsoft Transaction Server Developer's Guide for Oracle Database 12c Release 1 (12.1).

#### New Features

The following features are new in this release:

- OraMTS Services Run as Oracle Home User

  OraMTS services now operate as a specified, lower privileged user (the Oracle Home User). A utility is provided for cases where the service must be created manually rather than by the installer. Each Oracle Home now has its own OraMTS service.

  **See Also:**

  "[Manually Creating an Oracle MTS Recovery Service](install.md)."
