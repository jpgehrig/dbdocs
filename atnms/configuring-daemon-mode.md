Use the daemon to configure automatic health check runs at scheduled intervals.

**Note:**

Daemon mode is supported only on the Linux and Solaris operating systems.

**Note:**

If you have an Oracle Engineered System, then in addition to the following usage steps, follow the system-specific instructions.

1.  Set the daemon properties.
    At a minimum, set `AUTORUN_SCHEDULE` and `NOTIFICATION_EMAIL`.

    For example, to set the tool to run at 3 AM every Sunday and email the results to `some.body@example.com`, run the following command:

        $ ./orachk –set “AUTORUN_SCHEDULE=3 * * 0 ;NOTIFICATION_EMAIL=some.body@example.com”

        $ ./exachk –set “AUTORUN_SCHEDULE=3 * * 0 ;NOTIFICATION_EMAIL=some.body@example.com”
2.  Configure the health check daemon.
3.  Start the daemon as `root` (recommended) or as the Oracle Database or Oracle Grid Infrastructure home owner.
        # ./orachk –d start

        # ./exachk –d start
4.  Answer the questions prompted during startup.

**Parent topic:** [Oracle ORAchk and Oracle EXAchk Command-Line Options](orachk-and-exachk-command-line-options.md)
