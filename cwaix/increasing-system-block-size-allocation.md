Perform the following tuning configuration on AIX systems.

1.  Increase the space allocated for `ARG/ENV` list to 128. The size is specified by number of 4K blocks.
    For example:

        /usr/sbin/chdev -l sys0 -a ncargs='1024'

**Parent topic:** [Tuning AIX System Environment](tuning-aix-system-environment.md)
