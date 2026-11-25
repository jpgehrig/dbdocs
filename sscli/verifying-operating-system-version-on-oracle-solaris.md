To check your software to see if they meet minimum version requirements for installation, perform the following steps:

1.  To determine which version of Oracle Solaris is installed:
        $ uname -r

        5.11

    In this example, the version shown is Oracle Solaris 11 (5.11). If necessary, refer to your operating system documentation for information about upgrading the operating system.
2.   To determine the release level:
        $ cat /etc/release

        Oracle Solaris 11.4 SPARC

    In this example, the release level shown is Oracle Solaris 11.4 SPARC.
3.  To determine detailed information about the operating system version such as update level, SRU, and build:
    1.  On Oracle Solaris 11
            $ pkg list entire

            NAME (PUBLISHER) VERSION IFO
            entire (solaris) 0.5.11-0.175.3.1.0.5.0 i--

**Parent topic:** [Checking the Software Requirements for Oracle Solaris](checking-the-software-requirements-for-oracle-solaris.md)
