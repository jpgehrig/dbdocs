These topics explain how to configure kernel parameters manually for Oracle Solaris if you cannot complete them using the fixup scripts.

- [Minimum Parameter Settings for Installation](minimum-parameter-settings-for-installation.md)
  Use this table to set parameters manually if you cannot use the fixup scripts.
- [Checking Shared Memory Resource Controls](checking-shared-memory-resource-controls.md)
  Use the `prctl` command to make runtime interrogations of and modifications to the resource controls associated with an active process, task, or project on the system.
- [Configuring Additional Shared Memory Identifiers Limit](configuring-additional-shared-memory-identifiers-limit.md)
  Starting with 18c, on Oracle Solaris systems, Oracle Database uses a new method of sharing memory among a group of processes, also known as Managed Global Areas (MGA). The operating system memory allocation mechanism for this new method is Optimized Shared Memory (OSM).
- [Displaying and Changing Kernel Parameter Values](displaying-and-changing-kernel-parameter-values.md)
  Use these procedures to display the current value specified for resource controls and to change them if necessary:
- [Setting UDP and TCP Kernel Parameters Manually](setting-udp-and-tcp-kernel-parameters-manually.md)
  If you do not use a Fixup script or CVU to set ephemeral ports, then set TCP/IP ephemeral port range parameters to provide enough ephemeral ports for the anticipated server workload.

**Parent topic:** [Completing Preinstallation Tasks Manually](completing-preinstallation-tasks-manually.md)
