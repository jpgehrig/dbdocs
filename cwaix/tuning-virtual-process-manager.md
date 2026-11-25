Oracle recommends that you use the `vpm_xvcpus` command to tune virtual processor.

When you enable CPU folding with only one CUP, your system may reboot and face performance problems.

1.  Check if CPU folding is enabled:
        schedo -L| grep "vpm_xvcpus" |cut -d " " -f 17

    The above command returns 0 if CPU folding is enabled.
2.  Set value of the `vpm_xvcpus` parameter to at least 2:
        schedo -o vpm_xvcpus=2

**Parent topic:** [Tuning AIX System Environment](tuning-aix-system-environment.md)
