Oracle recommends that you use the `vmo` command to tune virtual memory.

**Note:**

- The `lru_file_repage` parameter does not apply to IBM AIX 7.1 and later updates to IBM AIX 7.1.
- The tunable parameters `strict_maxclient` and `strict_maxperm`are deprecated in IBM AIX 7.2 and later updates to IBM AIX 7.2.

Table 3-5 Recommended Values for Virtual Memory Manager

| Parameter         | Value |
|:------------------|:------|
| `minperm%`        | 3     |
| `maxperm%`        | 90    |
| `maxclient% = 90` | 90    |

For example:

    vmo -p -o minperm%=3
    vmo -p -o maxperm%=90
    vmo -p -o maxclient%=90

You must restart the system for these changes to take effect.

**Parent topic:** [Tuning AIX System Environment](tuning-aix-system-environment.md)
