Usually, health checks run at scheduled intervals. However, Oracle recommends that you run health checks on-demand when needed.

Examples of when you must run health checks on-demand:

- Pre- or post-upgrades

- Machine relocations from one subnet to another

- Hardware failure or repair

- Problem troubleshooting

- In addition to go-live testing

To start on-demand health check runs, log in to the system as an appropriate user, and then run an appropriate tool. Specify the options to direct the type of run that you want.

    $ ./orachk

    $ ./exachk

**Note:**

To avoid problems while running the tool from terminal sessions on a network attached workstation or laptop, consider running the tool using VNC. If there is a network interruption, then the tool continues to process to completion. If the tool fails to run, then re-run the tool. The tool does not resume from the point of failure.

Output varies depending on your environment and options used:

- The tool starts discovering your environment

- If you have configured passwordless SSH equivalency, then the tool does not prompt you for passwords

- If you have not configured passwordless SSH for a particular component at the required access level, then the tool prompts you for password

- If the daemon is running, then the commands are sent to the daemon process that answers all prompts, such as selecting the database and providing passwords

- If the daemon is not running, then the tool prompts you for required information, such as which database you want to run against, the required passwords, and so on

- The tool investigates the status of the discovered components

  **Note:**

  If you are prompted for passwords, then the Expect utility runs when available. In this way, the passwords are gathered at the beginning, and the Expect utility supplies the passwords when needed at the root password prompts. The Expect utility being supplying the passwords enables the tool to continue without the need for further input. If you do not use the Expect utility, then closely monitor the run and enter the passwords interactively as prompted.

  Without the Expect utility installed, you must enter passwords many times depending on the size of your environment. Therefore, Oracle recommends that you use the Expect utility.

  While running pre- or post-upgrade checks, Oracle ORAchk and Oracle EXAchk automatically detect databases that are registered with Oracle Clusterware and presents the list of databases to check.

  Run the pre-upgrade checks during the upgrade planning phase. Oracle ORAchk and Oracle EXAchk prompt you for the version to which you are planning to upgrade:
      $ ./orachk –u –o pre

      $ ./exachk –u –o pre

  After upgrading, run the post-upgrade checks:
      $ ./orachk –u –o post

      $ ./exachk –u –o post

- The tool starts collecting information across all the relevant components, including the remote nodes.

- The tool runs the health checks against the collected data and displays the results.

- After completing the health check run, the tool points to the location of the detailed HTML report and the `.zip`  file that contains more output.

**Related Topics**

- [Running On-Demand With or Without the Daemon](running-ondemand-daemon.md)
- [Sending Results by Email](sending-results-by-email.md)
- [Expect - Expect - Home Page](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/atnms&id=expect_utility_download)

**Parent topic:** [Using Oracle ORAchk and Oracle EXAchk to Manually Generate Health Check Reports](manually-generate-health-check-reports.md)
