Start and stop the daemon and force the daemon to stop a health check run.

### To start and stop the daemon:

1.  To start the daemon, use the `–d start` option as follows:
        $ ./orachk –d start

        $ ./exachk –d start

    The tools prompt you to provide required information during startup.
2.  To stop the daemon, use the `–d stop` option as follows:
        $ ./orachk –d stop

        $ ./exachk –d stop

    If a health check run is progress when you run the stop command, then the daemon indicates so and continues running.
3.  To force the daemon to stop a health check run, use the `–d stop_client` option:
        $ ./orachk –d stop_client

        $ ./exachk –d stop_client

The daemon stops the health check run and then confirms when it is done. If necessary, stop the daemon using the `–d stop` option.

**Parent topic:** [Managing the Oracle ORAchk and Oracle EXAchk Daemons](managing-daemons.md)
