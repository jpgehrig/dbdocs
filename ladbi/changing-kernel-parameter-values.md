## Changing Kernel Parameter Values

Use these instructions to display and change the kernel parameter values if they are different from the minimum recommended value.

Use the following commands to display the current values of the kernel parameters:

Table A-2 Commands to Display Kernel Parameter Values

| Parameter                          | Command                                                                                                            |
|:-----------------------------------|:-------------------------------------------------------------------------------------------------------------------|
| semmsl, semmns, semopm, and semmni | `# /sbin/sysctl -a | grep sem`<br>This command displays the value of the semaphore parameters in the order listed. |
| shmall, shmmax, and shmmni         | `# /sbin/sysctl -a | grep shm`<br>This command displays the details of the shared memory segment sizes.            |
| file-max                           | `# /sbin/sysctl -a | grep file-max`<br>This command displays the maximum number of file handles.                   |
| ip_local_port_range                | `# /sbin/sysctl -a | grep ip_local_port_range`<br>This command displays a range of port numbers.                   |
| rmem_default                       | `# /sbin/sysctl -a | grep rmem_default`                                                                            |
| rmem_max                           | `# /sbin/sysctl -a | grep rmem_max`                                                                                |
| wmem_default                       | `# /sbin/sysctl -a | grep wmem_default`                                                                            |
| wmem_max                           | `# /sbin/sysctl -a | grep wmem_max`                                                                                |
| aio-max-nr                         | `# /sbin/sysctl -a | grep aio-max-nr`                                                                              |

If you used the Oracle Database Preinstallation RPM to complete you preinstallation configuration tasks, then the Oracle Database Preinstallation RPM sets these kernel parameters for you. However, if you did not use the Oracle Database Preinstallation RPM or the kernel parameters are different from the minimum recommended value, then to change these kernel parameter values:

1.  Using any text editor, create or edit the `/etc/sysctl.d/97-oracle-database-sysctl.conf` file, and add or edit lines similar to:
        fs.aio-max-nr = 1048576
        fs.file-max = 6815744
        kernel.shmall = 2097152
        kernel.shmmax = 4294967295
        kernel.shmmni = 4096
        kernel.sem = 250 32000 100 128
        net.ipv4.ip_local_port_range = 9000 65500
        net.core.rmem_default = 262144
        net.core.rmem_max = 4194304
        net.core.wmem_default = 262144
        net.core.wmem_max = 1048576

    By specifying the values in the `/etc/sysctl.d/97-oracle-database-sysctl.conf `file, the values persist on system restarts.
2.  To change the current values of the kernel parameters:
        # /sbin/sysctl --system

    Review the output. If the values are incorrect, edit the `/etc/sysctl.d/97-oracle-database-sysctl.conf` file, then enter this command again.
3.  Confirm that the values are set correctly:
        # /sbin/sysctl -a
4.  Restart the computer, or run `sysctl --system` to make the changes in the `/etc/sysctl.d/97-oracle-database-sysctl.conf` file available in the active kernel memory.

Guidelines for Setting Kernel Parameter Values

- If you used the Oracle Database Preinstallation RPM, then your kernel parameter settings reside in the `/etc/sysctl.d/99-oracle-database-server-19c-preinstall-sysctl.conf` file.

- Include lines only for the kernel parameter values to change. For the semaphore parameters (kernel.sem), you must specify all four values. If any of the current values are larger than the minimum value, then specify the larger value.

- The `/etc/sysctl.conf` file has been deprecated.

- Avoid setting kernel parameter values in multiple files under `/etc/sysctl.d/`. The file with a lexically later name under `/etc/sysctl.d/` takes precedence, followed by `/etc/sysctl.conf`. Oracle recommends that you use the Oracle Database Preinstallation RPM which, among other preinstallation tasks, also sets the kernel parameter values for your database installation.

  **See Also:**

  `sysctl.conf(5)` and `sysctl.d(5)` man pages for more information

**Parent topic:** [Configuring Kernel Parameters for Linux](configuring-kernel-parameters-for-linux.md)
