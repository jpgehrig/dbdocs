Check your software to see if they meet the minimum version, filesets, and Authorized Problem Analysis Reports (APARs) requirements for installation:

1.  To determine the distribution and version of IBM AIX installed:
        # oslevel -s

    If the operating system version is lower than what is required, then upgrade your operating system accordingly to the currently supported or later version and level.
    IBM AIX maintenance packages are available from the following website:
    [https://www.ibm.com](https://www.ibm.com/)
2.  To determine if the required filesets are installed and committed enter a command similar to the following:
        # lslpp -l bos.adt.base bos.adt.lib bos.adt.libm bos.perf.perfstat \
        bos.perf.libperfstat bos.perf.proctools
3.  To determine the supported kernel mode:
        # getconf KERNEL_BITMODE

    - The expected output of this command is 64. If you do not see the expected output, then you cannot install the software on this system.

    - Oracle Database supports 64-bit kernel and does not provide support for 32-bit kernel applications.
4.  To determine if an APAR is installed:
        # /usr/sbin/instfix -i -k "IV16716 IV20880 IV21128 IV28319"

    If an APAR is not installed, then download it from the following website and install it:
    [https://www.ibm.com](https://www.ibm.com/)
5.  If you require a CSD for WebSphere MQ, then refer to the following website for download and installation information:
    [https://www.ibm.com](https://www.ibm.com/)

**Parent topic:** [Configuring Operating Systems for Oracle Database on IBM AIX on POWER Systems (64-Bit)](configuring-operating-systems-for-oracle-database-on-ibm-aix-on-power-systems-64-bit.md)
