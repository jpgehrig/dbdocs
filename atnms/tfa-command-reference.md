The Trace File Analyzer control utility, TFACTL, is the command-line interface for Oracle Trace File Analyzer.

TFACTL provides a command-line and shell interface to Oracle Trace File Analyzer commands for:

- Administration

- Summary and analysis

- Diagnostic collection

The `tfactl` commands that you can run depends on your access level.

- You need `root` access or `sudo` access to `tfactl` to run administration commands.

- Run a subset of commands as:

  - An Oracle Database home owner or Oracle Grid Infrastructure home owner

  - A member of `OS DBA` or `ASM` groups

  You gain access to summary, analysis, and diagnostic collection functionality by running the commands as an Oracle Database home owner or Oracle Grid Infrastructure home owner.

To grant other users access to `tfactl`:

    tfactl access

To use `tfactl` as a command-line tool:

    tfactl command [options]

To use `tfactl` as a shell interface:

    tfactl

Once the shell starts enter commands as needed.

    $ tfactl

    tfactl>

Append the `-help` option to any of the `tfactl` commands to obtain command-specific help.

    $ tfactl command -help

- [Installing Oracle Trace File Analyzer](install-tfa-platform.md)
  Understand the options that you can supply to the Oracle Trace File Analyzer installer script to customize the installation.
- [Running Administration Commands](running-administration-commands.md)
  You need `root` access to `tfactl`, or `sudo` access to run all administration commands.
- [Running Summary and Analysis Commands](running-summary-and-analysis-commands.md)
  Use these commands to view the summary of deployment and status of Oracle Trace File Analyzer, and changes and events detected by Oracle Trace File Analyzer.
- [Running Diagnostic Collection Commands](running-diagnostic-collection-commands.md)
  Run the diagnostic collection commands to collect diagnostic data.

**Parent topic:** [Appendixes](appendixes.md)
