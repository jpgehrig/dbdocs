## Checking Kernel and Package Requirements for Linux

Verify your kernel and packages to see if they meet minimum requirements for installation.

1.  To determine the distribution and version of Linux installed, enter one of the following commands:
        # cat /etc/oracle-release
        # cat /etc/redhat-release
        # cat /etc/os-release
        # lsb_release -id
2.  To determine if the required kernel errata is installed, enter the following command:
        # uname -r

    The following is an example of the output this command displays on an Oracle Linux 7 system:

        4.14.35-1902.0.18.el7uek.x86_6

    Review the required errata level for your distribution. If the errata level is previous to the required minimum errata update, then obtain and install the latest kernel update from your Linux distributor.
3.  To determine whether the required packages are installed, enter commands similar to the following:
    `# rpm -q ``package_name`

    Alternatively, if you require specific system architecture information, then enter the following command:

    `# rpm -qa --queryformat "%{NAME}-%{VERSION}-%{RELEASE} (%{ARCH})\n" | grep ``package_name`

    You can also combine a query for multiple packages, and review the output for the correct versions. For example:

        # rpm -q binutils compat-libstdc++ gcc glibc libaio libgcc libstdc++ \
        make sysstat unixodbc

    If a package is not installed, then install it from your Linux distribution media or download the required package version from your Linux distributor's website.

**Parent topic:** [Configuring Operating Systems for Oracle Database on Linux](configuring-operating-systems-for-oracle-database-on-linux.md)
