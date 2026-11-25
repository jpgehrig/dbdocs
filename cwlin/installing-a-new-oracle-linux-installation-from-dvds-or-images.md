## Installing Oracle Database Preinstallation RPM During an Oracle Linux Installation

Use this procedure to install a new Oracle Linux installation and to perform system configuration with the Oracle Database Preinstallation RPM:

1.  Obtain Oracle Linux by downloading disk images
    - Oracle yum

          https://yum.oracle.com/oracle-linux-isos.html

    - Oracle Software Delivery Cloud website:

          https://edelivery.oracle.com/linux

    **Note:**

    Ensure that you use the latest available update release for Oracle Linux.
2.  Start the Oracle Linux installation and respond to installation screens with values appropriate for your environment.
3.  Review the first software selection screen, which lists task-specific software options. At the bottom of the screen, there is an option to customize now or customize later. Select Customize now, and click Next.
4.  On Oracle Linux, select Servers on the left of the screen and System administration tools on the right of the screen (options may vary between releases).
    The Packages in System Tools window opens.
5.  Select the Oracle Database Preinstallation RPM package box from the package list. For example, select a package similar to the following:
    For Oracle Linux 7:

        oracle-database-preinstall-19c-1.0-1.el7.x86_64.rpm

    For Oracle Linux 8:

        oracle-database-preinstall-19c-1.0-1.el8.x86_64.rpm

    (or)

        oracle-database-preinstall-19c-1.0-1.el8.aarch64.rpm

    For Oracle Linux 9:

        oracle-database-preinstall-19c-1.0-1.el9.x86_64.rpm

    If you do not have an Oracle Database Preinstallation RPM package option that is current for your Oracle Database release, because you are using an Oracle Linux installation that is previous to your Oracle Database and Oracle Grid Infrastructure release, then install the RPM for your release manually after completing the operating system installation.
6.  Close the optional package window and click Next.
7.  Complete the other screens to finish the Oracle Linux installation.
    Oracle Linux automatically creates a standard (not role-allocated) Oracle installation owner and groups, and sets up other kernel configuration settings as required for Oracle installations.
8.  Repeat steps 2 through 6 on all other cluster member nodes.

**Parent topic:** [Automatically Configuring Oracle Linux with Oracle Database Preinstallation RPM](automatically-configuring-oracle-linux-with-oracle-preinstallation-rpm.md)
