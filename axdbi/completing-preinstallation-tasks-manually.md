You can complete the preinstallation configuration tasks manually.

Oracle recommends that you use Oracle Universal Installer and Cluster Verification Utility fixup scripts to complete minimal configuration settings. If you cannot use fixup scripts, then complete minimum system settings manually.

- [Configuring Shell Limits and System Configuration Parameters for IBM AIX](configuring-shell-limits-and-system-configuration-parameters-for-ibm-aix.md)
  These topics explain how to configure shell limits and system configuration parameters manually if you cannot complete them using the fixup scripts.
- [Checking Asynchronous Input Output Processes](checking-asynchronous-input-output-processes.md)
  On IBM AIX 6 and IBM AIX 7, the Asynchronous Input Output (AIO) device drivers are enabled by default. For both IBM AIX 6 and IBM AIX 7, increase the number of aioserver processes from the default value. The recommended value for aio_maxreqs is 64k (65536). Confirm this value for both IBM AIX 6 and IBM AIX 7.
- [Setting UDP and TCP Kernel Parameters Manually](setting-udp-and-tcp-kernel-parameters-manually.md)
  If you do not use a Fixup script or CVU to set ephemeral ports, then use NDD to ensure that the kernel TCP/IP ephemeral port range is broad enough to provide enough ephemeral ports for the anticipated server workload.
