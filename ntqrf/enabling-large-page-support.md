To take advantage of large pages, the amount of physical memory must be greater than the amount of System Global Area (SGA) specified in the parameter file.

Large pages might not be allocated always during instance startup. Large pages are supported in 2 modes:

- Regular mode: All of the SGA is attempted to be allocated in large pages. If the required amount of large pages are not available, then the instance does not come up.

- Mixed mode: All of the SGA is attempted to be allocated in large pages. If no more large pages are available, then the subsequent allocations are done using regular pages. So the SGA allocation can be a mixed set of large pages and regular pages.

  The mixed mode also supports a time parameter (in `msecs`). If a large page allocation took more time than the msecs specified by this time parameter, then subsequent allocations are made using regular pages. This parameter is helpful when the database startup time might be too long due to the entire SGA being allocated using large pages.

**Note:**

In regular mode, large page usage locks the entire SGA into physical memory. Physical memory is not released during a shrink operation. In mixed mode, only the large pages from the SGA are locked in physical memory, not released during a shrink operation and regular pages remain pageable.

**See Also:**

Your operating system documentation for restrictions on allocating large pages

To enable large page support:

1.  Go to the directory `ORACLE_HOME``\bin\oracle.key`.
2.  Open the `oracle.key` in a text editor and record the value found. It is set by Oracle Universal Installer. The default is:
        SOFTWARE\ORACLE\KEY_HOMENAME
3.  Start Registry Editor at the command prompt:
        C:\> regedit

    **Note:**

    Although Registry Editor lets you view and modify registry keys and parameter values, you usually are not required to do so. In fact, you can render your system useless if you make incorrect changes. Therefore, only advanced users must edit the registry. Back up your system before making any changes in the registry.

    `oracle.key` file must not be modified or removed. Oracle binaries open it to determine the location in the registry where their variables are stored.
4.  Go to the `HKEY_LOCAL_MACHINE` file.
    Locate the key corresponding to the value found in the `oracle.key` file. In the default case, for example, locate:

        HKEY_LOCAL_MACHINE\SOFTWARE\ORACLE\KEY_HOMENAME
5.  Create one of the following, depending on where you want to enable large page support:
    - `ORA_LPENABLE` to enable large page support on all instances. Its value decides the mode of large pages for all Oracle database instances on the computer.

    - `ORA_``SID``_LPENABLE` to enable large page support on a specific instance. Its value decides the mode of large pages for the specific database instance.

      Set the value of the above registry entry to `1` for regular mode and `2` for mixed mode.

      The time parameter for mixed mode is optional. To specify this time parameter which is instance specific, create `ORA_``SID``_LPMAXTIME` and set the value to the desired number of millisecs.

      When this time parameter is specified for an instance and the large pages allocation takes more than the specified millisecs, then the rest of the SGA is allocated using regular pages.
6.  Exit Registry Editor.

By default, Oracle allocates the minimum available large page size when using large pages. The minimum available large page size, 16 MB, is obtained by using the `GetLargePageMinumum` function.

**Note:**

Do not set the initialization parameter `lock_sga` when large pages are enabled. Large page usage locks the entire SGA into physical memory. When used with the parameter `lock_sga`, database startup fails with an error because the operating system automatically locks. That is, it prevents memory from being paged to disk when large pages are requested. Physical memory is not released during a shrink operation.

**Parent topic:** [Overview of Large Page Support](overview-of-large-page-support.md)
