Oracle recommends that you use the daemon process to schedule recurring health checks at regular intervals.

**Note:**

Daemon mode is supported only on the Linux and Solaris operating systems.

Configure the daemon to:

- Schedule recurring health checks at regular interval

- Send email notifications when the health check runs complete, clearly showing any differences since the last run

- Purge collection results after a pre-determined period

- Check and send email notification about stale passwords

- Store multiple profiles for automated health check runs

- Restart automatically if the server or node where it is running restarts

**Note:**

While running, the daemon answers all the prompts required by subsequent on-demand health checks.

To run on-demand health checks, do not use the daemon process started by others. Run on-demand health checks within the same directory where you have started the daemon.

If you change the system configuration such as adding or removing servers or nodes, then restart the daemon.

**Related Topics**

- [Setting and Getting Options for the Daemon](setting-getting-daemon-options.md)
- [Starting and Stopping the Daemon](starting-stopping-daemon.md)
- [Querying the Status and Next Planned Daemon Run](querying-status.md)
- [Configuring the Daemon for Automatic Restart](configuring-daemon-automatic-restart.md)

**Parent topic:** [Analyzing Risks and Complying with Best Practices](purpose-oracle-orachk-and-oracle-exachk.md)
