This preface contains:

- Changes in Oracle Providers for ASP.NET in ODAC 12c Release 4

- Changes in Oracle Providers for ASP.NET Release 11.2.0.2

- Changes in Oracle Providers for ASP.NET Release 11.2.0.1.2

### Changes in Oracle Providers for ASP.NET in ODAC 12c Release 4

The following are changes in Oracle Providers for ASP.NET for ODAC 12c Release 4.

#### New Features

The following features are new in this release:

- NuGet

  Oracle Providers for ASP.NET are available in a NuGet package. This capability simplifies distributing these providers to developers and end users.

- Windows Installer

  Oracle Providers for ASP.NET are now available as part of an ODAC Microsoft Windows Installer (MSI) package.

- ODP.NET, Managed Driver Support

  Oracle Providers for ASP.NET for .NET Framework 4 and higher depend on ODP.NET, Managed Driver (`Oracle.ManagedDataAccess.dll`), rather than ODP.NET, Unmanaged Driver (`Oracle.DataAccess.dll`) as in previous releases. The providers' DLL version is 4.121.2.1, which distinguishes it from its predecessor version 4.121.2.0, which in ODAC 12c Release 3 depended on unmanaged ODP.NET. In addition, Oracle Providers for ASP.NET for .NET Framework 4 and higher is now a platform independent assembly, enabling platform-independent applications to simply use the same .NET assembly, regardless of the platform.

  Oracle Providers for ASP.NET for .NET Framework 2.0 is platform dependent and depends on ODP.NET, Unmanaged Driver. Its version number remains the same as 2.121.2.0.

### Changes in Oracle Providers for ASP.NET Release 11.2.0.2

The following are changes in Oracle Providers for ASP.NET for Release 11.2.0.2.

#### New Features

The following feature is new in this release:

- 64-bit Oracle Providers for ASP.NET XCopy for Windows x64

  Now available for Windows x64 systems, Oracle Providers for ASP.NET XCopy provides system administrators with a smaller client install size than the standard client, and is easier to configure. XCopy simplifies embedding the ASP.NET providers in customized deployment packages.

  **See Also:**

  XCopy under "[Oracle Providers for ASP.NET Installation](IntroInstallation.md)."

### Changes in Oracle Providers for ASP.NET Release 11.2.0.1.2

The following are changes in Oracle Providers for ASP.NET for Release 11.2.0.1.2.

#### New Features

The following feature is new in this release:

- ASP.NET 4 Support

  Oracle Providers for ASP.NET 4 supports ASP.NET 4.
