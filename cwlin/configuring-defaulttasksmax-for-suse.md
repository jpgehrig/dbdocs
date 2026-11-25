## Configuring Default Thread Limits Value for SUSE Linux

If you are on SUSE Linux Enterprise Server 12 SP2 or later, or SUSE Linux Enterprise Server 15 or later, then set the DefaultTasksMax parameter value to `65535`.

Increase the default thread limits, DefaultTasksMax value from `512` to `65535` to avoid running into service failures.

1.  View the contents of `/etc/systemd/system.conf `to know the current `DefaultTasksMax` value. Alternatively, run the following command:
        $ systemctl show --property DefaultTasksMax
2.  If your DefaultTasksMax value is not `65535`, then uncomment the line in `/etc/systemd/system.conf` and set the value to `65535`.
3.  To enable the new settings, reboot your system or run the following command:
        $ systemctl daemon-reload

**Parent topic:** [Completing Preinstallation Tasks Manually](completing-preinstallation-tasks-manually.md)
