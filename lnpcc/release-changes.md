This preface lists changes in Pro\*C/C++ Programmer's Guide.

### Changes in Pro\*C/C++ Release 18c, Version 18.1

#### New Features

The following feature is new in this release:

- Support for Oracle Connection Manager in Traffic Director Mode

  Oracle Connection Manager in Traffic Director Mode is a proxy that is placed between supported database clients and database instances for improved high availability, connection multiplexing, and load balancing.

  See [About Using Oracle Connection Manager in Traffic Director Mode](performance-tuning.md) for more information.

### Changes in Pro\*C/C++ 12c Release 2 (12.2)

#### New Features

The following features are new in this release:

- Pro\*C/C++ now supports identifier lengths of 128 bytes. In previous releases, the identifier length limit was 30 bytes.

- Pro\*C/C++ now supports Oracle Instant Client - Basic Light version.

- Pro\*C/C++ now introduces a new command line option “trim_password”, to prevent authentication issues caused by password strings that contain trailing blank space.

- High Availability features such as Transaction Guard are implemented in the OCI layer. For more information, see the Call Interface Programmer’s Guide.
