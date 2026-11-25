## 4 Configuring Operating Systems for Oracle Grid Infrastructure on Linux

Complete operating system configuration requirements and checks for Linux operating systems before you start installation.

- [Guidelines for Linux Operating System Installation](guidelines-for-linux-operating-system-installation.md)
  Operating system guidelines to be aware of before proceeding with an Oracle installation.
- [Reviewing Operating System and Software Upgrade Best Practices](reviewing-operating-system-and-software-upgrade-best-practices.md)
  These topics provide general planning guidelines and platform-specific information about upgrades and migration.
- [Reviewing Operating System Security Common Practices](reviewing-operating-system-security-common-practices.md)
  Secure operating systems are an important basis for general system security.
- [About Installation Fixup Scripts](about-installation-fixup-scripts.md)
  Oracle Universal Installer detects when the minimum requirements for an installation are not met, and creates shell scripts, called fixup scripts, to finish incomplete system configuration steps.
- [About Operating System Requirements](about-operating-system-requirements.md)
  Depending on the products that you intend to install, verify that you have the required operating system kernel and packages installed.
- [Using Oracle RPM Checker on IBM: Linux on System z](using-oracle-rpm-checker-on-zlinux.md)
  Use the Oracle RPM Checker utility to verify that you have the required Red Hat Enterprise Linux or SUSE packages installed on the operating system before you start the Oracle Database or Oracle Grid Infrastructure installation.
- [Operating System Requirements for x86-64 Linux Platforms](operating-system-requirements-for-x86-64-linux-platforms.md)
  The Linux distributions and packages listed in this section are supported for this release on x86-64.
- [Operating System Requirements for IBM: Linux on System z](operating-system-requirements-for-zlinux.md)
  The Linux distributions and packages listed in this section are supported for this release on IBM: Linux on System z.
- [Operating System Requirements for Linux for Arm (aarch64)](operating-system-reqs-arm.md)
  The Linux distribution and packages listed in this section are supported for this release on Linux for Arm (aarch64).
- [Additional Drivers and Software Packages for Linux](additional-drivers-and-software-packages-for-linux.md)
  Information about optional drivers and software packages.
- [Checking Kernel and Package Requirements for Linux](checking-kernel-and-package-requirements-for-linux.md)
  Verify your kernel and packages to see if they meet minimum requirements for installation.
- [Setting Clock Source for VMs on Linux x86-64](setting-clock-source-for-vm-on-linux.md)
  Oracle recommends that you set the clock source to `tsc` for better performance in virtual environments (VM) on Linux x86-64.
- [Installing the cvuqdisk RPM for Linux](installing-the-cvuqdisk-rpm-for-linux.md)
  If you do not use an Oracle Database Preinstallation RPM, and you want to use the Cluster Verification Utility, then you must install the `cvuqdisk` RPM.
- [Reviewing HugePages Memory Allocation](reviewing-hugespages-memory-allocation.md)
  Review this information if your operating system has HugePages enabled.
- [Setting and Disabling Transparent HugePages on UEK Kernels](setting-thp-uek.md)
  Learn when to set Transparent HugePages and when to disable Transparent HugePages depending on your UEK kernel version.
- [Enabling the Name Service Cache Daemon](enabling-the-name-service-cache-daemon.md)
  To allow Oracle Clusterware to better tolerate network failures with NAS devices or NFS mounts, enable the Name Service Cache Daemon (`nscd`).
- [Using Automatic SSH Configuration During Installation](using-automatic-ssh-configuration-during-installation.md)
  To install Oracle software, configure secure shell (SSH) connectivity between all cluster member nodes.
- [Verifying the Disk I/O Scheduler on Linux 8 and Later Systems](setting-the-disk-io-scheduler-on-linux-8.md)
  Disk I/O schedulers reorder, delay, or merge requests for disk I/O to achieve better throughput and lower latency.
- [Verifying the Disk I/O Scheduler on Linux 7 Systems](setting-the-disk-io-scheduler-on-linux.md)
  Disk I/O schedulers reorder, delay, or merge requests for disk I/O to achieve better throughput and lower latency.
- [Setting Network Time Protocol for Cluster Time Synchronization](setting-network-time-protocol-for-cluster-time-synchronization.md)
  Use either the Oracle Cluster Time Synchronization or network time protocol (NTP) option for time synchronization.
