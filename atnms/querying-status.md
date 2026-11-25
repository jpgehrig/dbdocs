Query the status and next automatic run schedule of the running daemon.

    -d status|info|nextautorun

- `-d status`: Checks if the daemon is running.

- `-d info`: Displays information about the running daemon.

- `-d nextautorun [-id ``ID``]`: Displays the next automatic run time.

### To query the status and next planned daemon run:

1.  To check if the daemon is running, use `–d status`:
        $ ./orachk –d status

        $ ./exachk –d status

    If the daemon is running, then the daemon confirms and displays the PID.
2.  To query more detailed information about the daemon, use `–d info`:
        $ ./orachk –d info

        $ ./exachk –d info

    The daemon responds with the following information:

    - Node on which the daemon is installed

    - Version

    - Install location

    - Time when the daemon was started
3.  To query the next scheduled health check run, use `–d nextautorun`:
        $ ./orachk –d nextautorun

        $ ./exachk –d nextautorun

    The daemon responds with details of schedule.

    If you have configured multiple daemon option profiles, then the output shows whichever is scheduled to run next.

    If you have configured multiple daemon option profiles, then query the next scheduled health check run of a specific profile using `–id ``ID`` -d nextautorun`:
        $ ./orachk –d ID –d nextautorun

        $ ./exachk –d ID –d nextautorun

    The daemon responds with details of the schedule for the daemon options profile ID you have specified.

**Parent topic:** [Managing the Oracle ORAchk and Oracle EXAchk Daemons](managing-daemons.md)
