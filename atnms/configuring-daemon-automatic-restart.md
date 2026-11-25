By default, you must manually restart the daemon if you restart the server or node on which the daemon is running.

However, if you use the automatic restart option, the daemon restarts automatically after the server or node reboot.

Only `root` can configure automatic restart.

### To configure the daemon to start automatically:

1.  To set up daemon automatic restart, use `–initsetup`:
        $ ./orachk –initsetup

        $ ./exachk –initsetup

    The tool prompts you to provide the required information during startup.

    **Note:**

    Stop the daemon before running `–initsetup`, if the daemon is already running.
2.  To query automatic restart status of the daemon, use `–initcheck`:
        $ ./orachk –initcheck

        $ ./exachk –initcheck
3.  To remove automatic restart configuration, use `–initrmsetup` :
        $ ./orachk –initrmsetup

        $ ./exachk –initrmsetup

**Parent topic:** [Managing the Oracle ORAchk and Oracle EXAchk Daemons](managing-daemons.md)
