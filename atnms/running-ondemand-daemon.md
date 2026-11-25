When running on-demand, if the daemon is running, then the daemon answers all prompts where possible including the passwords.

### To run health checks on-demand with or without the daemon:

1.  To run health checks on-demand if the daemon is running, then use:
        $ ./orachk

        $ ./exachk
2.  To avoid connecting to the daemon process, meaning the tool to interactively prompt you as required, use the `–nodaemon` option.
        $ ./orachk –nodaemon

        $ ./exachk –nodaemon

**Note:**

Daemon mode is supported only on the Linux and Solaris operating systems.

**Note:**

If you are running database pre-upgrade checks (`-u –o pre`) and if the daemon is running, then you must use the `–nodaemon` option.

**Parent topic:** [Using Oracle ORAchk and Oracle EXAchk to Manually Generate Health Check Reports](manually-generate-health-check-reports.md)
