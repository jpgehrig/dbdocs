## Installing Operating System Packages

Learn how to install the latest version of your Oracle Linux and SUSE Linux Enterprise Server operating system packages listed earlier.

You must install the latest version of your operating system packages from the respective operating system vendor repository by using a package manager like `YUM` or `YaST` depending on your operating system.

Ensure that the appropriate channel or repository is enabled to include these packages.

For example:

On Oracle Linux or Red Hat Enterprise Linux, to install the latest `bc` package using `YUM`, run the following command:

    $ yum install bc

On SUSE Linux Enterprise Server, to install the latest `bc` package using `YaST`, run the following command:

    $ yast --install bc

**Parent topic:** [Operating System Requirements for x86-64 Linux Platforms](operating-system-requirements-for-x86-64-linux-platforms.md)
