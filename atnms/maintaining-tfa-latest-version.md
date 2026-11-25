Oracle releases a new version of Oracle Trace File Analyzer approximately every three months.

Applying standard Release Update Revisions (RURs) automatically updates Oracle Trace File Analyzer. However, the Release Update Revisions (RURs) do not contain the rest of the Oracle Database support tools bundle updates. Download the latest version of Oracle Trace File Analyzer with Oracle Database support tools bundle from My Oracle Support note 1513912.1.

Upgrading is similar to first-time install. As `root`, use the `installTFA``platform` script. If Oracle Trace File Analyzer is already installed, then the installer updates the existing installation. When already installed, a cluster upgrade does not need SSH. The cluster upgrade uses the existing daemon secure socket communication between hosts.

    $ ./installTFAplatform

If you are not able to install as `root`, then install Oracle Trace File Analyzer as Oracle home owner. Use the `-extractto` and `–javahome` options:

    $ ./installTFAplatform -extractto dir -javahome jre_home

**Related Topics**

- [Installing Oracle Trace File Analyzer on Microsoft Windows](quick-start-guide.md)
- [https://support.oracle.com/rs?type=doc&amp;id=1513912.1](https://support.oracle.com/rs?type=doc&amp;amp;id=1513912.1)

**Parent topic:** [Collecting Diagnostic Data and Triaging, Diagnosing, and Resolving Issues](diagnose-troubleshoot-issues-errors.md)
