Depending on your environment, you can reduce the default setting of the PARALLEL_MIN_SERVERS parameter.

In Oracle Database 12c, the default for PARALLEL_MIN_SERVERS changed from `0` to a value that was provided based on your hardware platform. This change was made to provide sufficient minimal support for parallel execution. If you find that the new default setting is too high, then adjust the setting for your requirements. The default for `PARALLEL_MAX_SERVERS` has not changed. If the default in your old environment is unchanged, then you do not need to take further action.

**See Also:**

[Oracle Database Reference](../refrn/PARALLEL_MIN_SERVERS.md) for information about `PARALLEL_MIN_SERVERS`

**Parent topic:** [Required Tasks to Complete After Upgrading Oracle Database](required-tasks-to-complete-after-upgrade.md)
