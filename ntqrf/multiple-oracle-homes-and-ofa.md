The goal of OFA is to place all Oracle Database software under one `ORACLE_HOME` directory and to spread database files across different physical drives as databases increase in size.

OFA is implemented on Windows and UNIX in the same way, and main subdirectory and file names are the same on both operating systems. Windows and UNIX differ, however, in their OFA directory tree top-level names and in the way variables are set.

On UNIX, `ORACLE_BASE` is associated with a user's environment. `ORACLE_HOME` and `ORACLE_SID` must be set in system or user login scripts. Symbolic links are supported. Although everything seems to be in one directory on the same hard drive, files may be on different hard drives if they are symbolically linked or have that directory as a mount point.

On Windows, `ORACLE_BASE` is defined in the registry (for example, in `HKEY_LOCAL_MACHINE\SOFTWARE\ORACLE\HOME0`). `ORACLE_HOME` and `ORACLE_SID` are variables defined in the registry. Symbolic links like those on UNIX are not supported.

**See Also:**

[Oracle Database Installation Guide for Microsoft Windows](../ntdbi/index.md) in the section Appendix B, "Optimal Flexible Architecture"

**Parent topic:** [Oracle Database Differences on Windows and UNIX](oracle-database-differences-on-windows-and-unix.md)
