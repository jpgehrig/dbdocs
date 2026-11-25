Shared libraries on UNIX are similar to shared DLLs on Windows.

Object files and archive libraries are linked to generate the Oracle Database executables. Relinking is necessary after certain operations, such as installation of a patch.

On Windows, Oracle Database DLLs form part of the executable at run time and are therefore smaller. DLLs can be shared between multiple executables. Relinking by the user is not supported, but the executable images can be modified using ORASTACK.

Modifying executable images on Windows reduces the chances of running out of virtual memory when using a large SGA or when supporting thousands of connections. However, Oracle recommends doing this only under the guidance of Oracle Support Services.

**Parent topic:** [Oracle Database Differences on Windows and UNIX](oracle-database-differences-on-windows-and-unix.md)
