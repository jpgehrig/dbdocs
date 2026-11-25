Starting with 11.2.0.1.2, Oracle Data Provider for .NET, Unmanaged Driver ships with two sets of binaries: one set for .NET Framework 2.0 and another for .NET Framework 4. ODP.NET. Managed Driver ships with one set of binaries for .NET Framework 4. ODP.NET Core has one set of binaries for .NET Core.

For example, ODP.NET 11.2.0.1.2 binaries would be the following:

- ODP.NET for .NET Framework 4

  - `Oracle.DataAccess.dll`

    - Built with .NET Framework 4

    - Assembly version number: 4.x.x.x

  - `OraOps11w.dll`

    - Used by ODP.NET for .NET Framework 2.0 and 4

- ODP.NET for .NET Framework 2.0

  - `Oracle.DataAccess.dll`

    - Built with .NET Framework 2.0

    - Assembly version number: 2.x.x.x

  - `OraOps11w.dll`

    - Used by ODP.NET for .NET Framework 2.0 and 4

The convention for ODP.NET assembly/DLL versioning is

n1.o1o2.o3o4.o5

where:

- n1 is the most significant .NET Framework version number.

- o1o2 are the first two digits of the ODP.NET product version number.

- o3o4 are the third and forth digits of the ODP.NET product version number.

- o5 is the fifth and last digit of the ODP.NET product version number.

For example, if the ODP.NET product version number is 11.2.0.2.0, the corresponding ODP.NET assembly versions are:

- .NET Framework 4 version: 4.112.2.0

- .NET Framework 2.0 version: 2.112.2.0

Note that the Oracle installer and documentation still refer to the ODP.NET product version number and not the assembly/DLL version number.

As with the .NET Framework system libraries, the first digit of the assembly version number indicates the version of the .NET Framework to use with an ODP.NET assembly.

Publisher Policy DLL is provided as before so that applications built with older versions of ODP.NET are redirected to the newer ODP.NET assembly, even though the versioning scheme has changed.

ODP.NET, Managed Driver follows a similar version model for its binaries.

ODP.NET for .NET Framework 4:

- `Oracle.ManagedDataAccess.dll`

  - Built with .NET Framework 4

  - Assembly version number: 4.x.x.x

- `Oracle.ManagedDataAccessDTC.dll`

  - Used by ODP.NET for .NET Framework 4 for distributed transactions only.

### ODP.NET, Managed Driver Versioning

Starting with ODAC 12c Release 2, the ODP.NET, Managed Driver uses assembly manifest attribute `AssemblyInformationalVersionAttribute` to uniquely identify assemblies with the same `AssemblyVersionAttribute` attribute value. This value can be accessed via .NET code, PowerShell, and other Windows applications to identify ODP.NET, Managed Driver versions uniquely.

`AssemblyInformationalVersionAttribute` is set to the same version as the actual .NET assembly version, except the fourth digit, which will no longer be 0. Instead, the version will be unique for each ODP.NET, Managed Driver release by incrementing the fourth digit for every subsequent release.

This value is accessible using .NET Framework System.Diagnostics.FileVersionInfo.ProductVersion property. The returned value can be used as a Version object or as a comparison String using comparison operators or methods. Essentially, among a collection of ODP.NET, Managed Driver assemblies that have the same assembly version, the newest ODP.NET, Managed Driver assembly will have the largest fourth digit `ProductVersion` value than an older assembly.

PowerShell Example: In this example, administrators uniquely distinguish the assemblies between ODP.NET, Managed Driver versions from an old version of ODP.NET, Managed Driver in `c:\old` and a more recent one in `c:\new`.

Script:

    $VC1 = New-Object System.Version((Get-Command C:\old\Oracle.ManagedDataAccess.dll).FileVersionInfo.ProductVersion)
    $VC2 = New-Object System.Version((Get-Command C:\new\Oracle.ManagedDataAccess.dll).FileVersionInfo.ProductVersion)
    "Compare V1 to V2: " + $VC1.CompareTo($VC2)
    "Compare V1 to V1: " + $VC1.CompareTo($VC1)
    "Compare V2 to V1: " + $VC2.CompareTo($VC1)

Output:

    Compare V1 to V2: -1
    Compare V1 to V1: 0
    Compare V2 to V1: 1

**Note:**

`ProductVersion` property comparisons will provide correct information on which version is more recent than the other only for ODP.NET, Managed Driver released from ODAC 12c Release 2 and later.
