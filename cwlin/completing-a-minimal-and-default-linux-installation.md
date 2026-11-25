## Completing a Minimal or Default Linux Installation

You must perform either a minimal or default Linux installation.

To complete a minimal Linux installation, select one of the minimal installation options.

A minimal Linux installation option is either a custom installation where you select the Minimal option from Package Group Selection, or where you deselect all packages except for the Base pack. A minimal Linux installation lacks many RPMs required for database installation, so you must use an RPM package for your Oracle Linux release to install the required packages. The package you use depends on your Linux release, and your support status with Unbreakable Linux Network (ULN).

If you do not install the Oracle Database Preinstallation RPM, then Oracle recommends that you install your Linux operating system with the default software packages (RPMs).

A default Linux installation includes most of the required packages and helps you limit manual verification of package dependencies. Oracle recommends that you do not customize the RPMs during installation.

Refer to the official Oracle Linux documentation for more information about installing Oracle Linux:

- [Oracle Linux 7 Installation Guide](https://docs.oracle.com/en/operating-systems/oracle-linux/7/install/)
- [Oracle Linux 7: Managing Software](https://docs.oracle.com/en/operating-systems/oracle-linux/7/yum/)
- [Oracle Linux 8 Installation Guide](https://docs.oracle.com/en/operating-systems/oracle-linux/8/install/)
- [Oracle Linux 8: Managing Software](https://docs.oracle.com/en/operating-systems/oracle-linux/8/software-management/)

**Parent topic:** [Guidelines for Linux Operating System Installation](guidelines-for-linux-operating-system-installation.md)
