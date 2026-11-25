Use this table to set parameters manually if you cannot use the fixup scripts. Verify that the kernel parameters are set to values greater than or equal to the minimum values shown in the following table.

Table A-1 Minimum HP-UX Itanium Kernel Parameter Settings

| Parameter             | Minimum Value      |
|:----------------------|:-------------------|
| executable_stack      | 0                  |
| ksi_alloc_max         | 32768              |
| max_thread_proc       | 1024               |
| maxdsiz               | 1073741824 (1 GB)  |
| maxdsiz_64bit         | 2147483648 (2 GB)  |
| maxfiles              | 1024               |
| maxfiles_lim          | 63488              |
| maxssiz               | 134217728 (128 MB) |
| maxssiz_64bit         | 1073741824 (1 GB)  |
| maxuprc               | 3686               |
| msgmni                | 4096               |
| msgtql                | 4096               |
| ncsize                | 35840              |
| nflocks               | 4096               |
| ninode                | 34816              |
| nkthread              | 7184               |
| nproc                 | 4096               |
| semmni                | 4096               |
| semmns                | 8192               |
| semmnu                | 4092               |
| semvmx                | 32767              |
| shmmax                | 1073741824         |
| shmmni                | 4096               |
| shmseg                | 512                |
| tcp_largest_anon_port | 65500              |
| udp_largest_anon_port | 65500              |

### Guidelines for Setting Kernel Parameter Values

- If the current value for any parameter is higher than the value listed in this table, then do not change the value of that parameter.

- Do not specify values for the following parameters as they are obsolete on HP-UX 11.31:
  - msgmap

  - msgseg

- If you do not use HFS, then retain the default ninode value.

**Parent topic:** [Configuring Kernel Parameters on HP-UX Itanium Systems](configuring-kernel-parameters-on-hp-ux-itanium-systems.md)
