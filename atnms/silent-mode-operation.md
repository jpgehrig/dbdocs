Run health checks automatically by scheduling them with the Automated Daemon Mode operation.

**Note:**

Silent mode operation is maintained for backwards compatibility for the customers who were using it before the daemon mode was available. Silent mode is limited in the checks it runs and Oracle does not actively enhance it any further.

- Running health checks in silent mode using the `-s` option does not run any checks on the storage servers and switches.

- Running health checks in silent mode using the `-S` option excludes checks on database server that require `root` access. Also, does not run any checks on the storage servers and database servers.

To run health checks silently, configure passwordless SSH equivalency. It is not required to run remote checks, such as running against a single-instance database.

When health checks are run silently, output is similar to that described in On-Demand Mode Operation.

**Note:**

If not configured to run in silent mode operation on an Oracle Engineered System, then the tool does not perform storage server or InfiniBand switch checks.

### Including Health Checks that Require root Access

Run as `root`  or configure `sudo`  access to run health checks in silent mode and include checks that require `root` access.

To run health checks including checks that require `root` access, use the `–s`  option followed by other required options:

    $ ./orachk –s

    $ ./exachk –s

### Excluding Health Checks that Require root Access

To run health checks excluding checks that require `root` access, use the `–S`  option followed by other required options:

    $ ./orachk –S

    $ ./exachk –S

**Related Topics**

- [Using Oracle ORAchk and Oracle EXAchk to Automatically Check for Risks and System Health](automated-daemon-mode-operation.md)
- [Running Health Checks On-Demand](ondemand-mode-operation.md)

**Parent topic:** [Using Oracle ORAchk and Oracle EXAchk to Manually Generate Health Check Reports](manually-generate-health-check-reports.md)
