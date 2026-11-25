This section explains how to install Oracle Trace File Analyzer on different operating systems.

- Oracle Trace File Analyzer
  Oracle Trace File Analyzer helps you collect and analyze diagnostic data.
- Supported Environments
  You can use Oracle Trace File Analyzer with all supported versions of Oracle Database and Oracle Grid Infrastructure.
- Installing Oracle Trace File Analyzer on Linux or UNIX as root User in Daemon Mode
  To obtain the fullest capabilities of Oracle Trace File Analyzer, install it as `root`.
- Installing Oracle Trace File Analyzer on Linux or UNIX as Non-root User in Non-Daemon Mode
  If you are unable to install as `root`, then install Oracle Trace File Analyzer as the Oracle home owner.
- Installing Oracle Trace File Analyzer on Microsoft Windows
- Installing Oracle Trace File Analyzer on Microsoft Windows in Non-Daemon Mode
- Oracle Trace File Analyzer Key Directories
  Based on your installation type, the `ora_home` and the `bin` directories can differ.
- Oracle Trace File Analyzer Command Interfaces
  The `tfactl` tool functions as command-line interface, shell interface, and menu interface.
- Masking Sensitive Data
  Masking sensitive data is an optional feature that you can configure Oracle Trace File Analyzer to mask sensitive data in log files.
- Securing Access to Oracle Trace File Analyzer
  Running `tfactl` commands is restricted to authorized users.
- Uninstalling Oracle Trace File Analyzer

**Parent topic:** [Collecting Diagnostic Data and Triaging, Diagnosing, and Resolving Issues](diagnose-troubleshoot-issues-errors.md)

### 13.1 Oracle Trace File Analyzer

Oracle Trace File Analyzer helps you collect and analyze diagnostic data.

As a DBA, you are expected to do more work with fewer resources all the time. You are under pressure to keep the mission-critical applications up and running. When something goes wrong, everyone looks to you to understand what went wrong and how to fix it.

It is not always easy. You have to run the right tools at the right time. If you're using Oracle Grid Infrastructure, then you also have to collect diagnostic data from all the database nodes. Collecting this data can require you to use tools that you rarely use. Needless to say, each tool has its own syntax.

The amount of data you collect can be huge. Only a fraction of the data that you collect is useful, but how can you know which part is relevant? You must collect it all, quickly, before the data is overwritten. In the meantime, you have still got a problem that costs your company time and money.

Oracle Trace File Analyzer enables you to collect diagnostic data. Collecting diagnostic data is a crucial step to resolving problems that occur with your Oracle Database.

Oracle Trace File Analyzer monitors your logs for significant problems that potentially impact your service. Oracle Trace File Analyzer also automatically collects relevant diagnostics when it detects any potential problems.

Oracle Trace File Analyzer can identify the relevant information in log files. It trims log files to just the parts that are necessary to resolve an issue. Oracle Trace File Analyzer also collects data across cluster nodes and consolidates everything in one place.

Using important database diagnostic tools is easy with Oracle Trace File Analyzer. Oracle Trace File Analyzer hides the complexity by providing a single interface and syntax for them all.

**Related Topics**

- [Introduction to Oracle Trace File Analyzer](introduction-oracle-trace-file-analyzer.md)

**Parent topic:** Getting Started with Oracle Trace File Analyzer

### 13.2 Supported Environments

You can use Oracle Trace File Analyzer with all supported versions of Oracle Database and Oracle Grid Infrastructure.

Oracle Trace File Analyzer works on the following operating systems:

- Linux OEL

- Linux RedHat

- Linux SuSE

- Linux Itanium

- zLinux

- Oracle Solaris SPARC

- Oracle Solaris x86-64

- AIX

- HPUX Itanium

- HPUX PA-RISC

- Microsoft Windows 64-bit

Oracle Trace File Analyzer is supported on the operating system versions supported by Oracle Database. Use a Java Runtime Edition of version 1.8.

Oracle Trace File Analyzer is shipped with Oracle Gird Infrastructure since versions 11.2.0.4 and 12.1.0.2. However, this install does not include many of the Oracle Database tools. Oracle releases new versions of Oracle Trace File Analyzer several times a year. These new releases include new features and bug fixes.

Ensure that you get the latest Oracle Trace File Analyzer with Oracle Database support tools bundle from My Oracle Support note 1513912.1.

**Related Topics**

- [https://support.oracle.com/rs?type=doc&amp;id=1513912.1](https://support.oracle.com/rs?type=doc&amp;amp;id=1513912.1)

**Parent topic:** Getting Started with Oracle Trace File Analyzer

### 13.3 Installing Oracle Trace File Analyzer on Linux or UNIX as root User in Daemon Mode

To obtain the fullest capabilities of Oracle Trace File Analyzer, install it as `root`.

Oracle Trace File Analyzer maintains Access Control Lists (ACLs) to determine which users are allowed access. By default, the `GRID_HOME` owner and `ORACLE_HOME` owner have access to their respective diagnostics. No other users can perform diagnostic collections.

If Oracle Trace File Analyzer is already installed, then reinstalling performs an upgrade to the existing location. If Oracle Trace File Analyzer is not already installed, then the recommended location is `/opt/oracle.tfa`.

To install as `root`:

1.  Download appropriate Oracle Trace File Analyzer zipped file, copy the downloaded file to the required machine, and then unzip.
2.  Run the `installTFA` command:
        $ ./installTFA-platform

The installation prompts you to do a local or cluster install.

Cluster install requires passwordless SSH user equivalency for `root` to all cluster nodes. If not already configured, then the installation optionally sets up passwordless SSH user equivalency and then removes at the end.

If you do not wish to use passwordless SSH, then you install on each host using a local install. Run the `tfactl syncnodes` command to generate and deploy relevant SSL certificates.

The Cluster Ready Services (CRS) do not manage Oracle Trace File Analyzer because Oracle Trace File Analyzer must be available if CRS goes down.

The installation configures Oracle Trace File Analyzer for auto-start. The implementation of auto-start is platform-dependent. Linux uses` init`, or an `init` replacement, such as `upstart` or `systemd`. Microsoft Windows uses a Windows service.

Installing Oracle Trace File Analyzer as root on Linux or Solaris on non-engineered systems automatically sets up and runs the Oracle ORAchk daemon.

The daemon restarts at 1 am every day to discover any environment changes. The daemon runs a full local Oracle ORAchk check at 2 am every day, and a partial run of the most impactful checks every 6 hours through the `oratier1` profile.

The daemon automatically purges any collections older than 2 weeks.

You can change the daemon settings after enabling auto start. To remove auto start any time, run `tfactl run orachk -autostop`.

**Related Topics**

- [Installing Oracle Trace File Analyzer](install-tfa-platform.md)
- Securing Access to Oracle Trace File Analyzer

**Parent topic:** Getting Started with Oracle Trace File Analyzer

### 13.4 Installing Oracle Trace File Analyzer on Linux or UNIX as Non-root User in Non-Daemon Mode

If you are unable to install as `root`, then install Oracle Trace File Analyzer as the Oracle home owner.

Oracle Trace File Analyzer has reduced capabilities in this installation mode.

You cannot complete the following tasks:

- Automate diagnostic collections

- Collect diagnostics from remote hosts

- Collect files that are not readable by the Oracle home owner, for example, `/var/log/messages`, or certain Oracle Grid Infrastructure logs

To install as the Oracle home owner, use the `–extractto` option. Using the `–extractto` option tells Oracle Trace File Analyzer where to install to. Also, use the `–javahome` option to indicate which JRE to use. Use the JRE already available in the Oracle home, unless you have a later version available.

    ./installTFA-platform -extractto install_dir -javahome jre_home

**Related Topics**

- [Installing Oracle Trace File Analyzer](install-tfa-platform.md)

**Parent topic:** Getting Started with Oracle Trace File Analyzer

### 13.5 Installing Oracle Trace File Analyzer on Microsoft Windows

**Note:**

.NET Framework version 4.0.30319 or later is required to install Oracle Trace File Analyzer. If you experience installation errors, then ensure that you have the correct .NET Framework version installed.

1.  Download appropriate Oracle Trace File Analyzer zipped file, copy the downloaded file to one of the required machines, and then unzip.
2.  Open a command prompt as administrator and then run the installation script by specifying a Perl home.
    For example:

        install.bat -perlhome D:\oracle\product\12.2.0\dbhome_1\perl

The installer prompts you to do a local or cluster install. If you select cluster install, then the installer installs Oracle Trace File Analyzer on local and remote cluster nodes.

Alternatively, you can perform a local install on each host. Run the `tfactl syncnodes` command to generate and deploy relevant SSL certificates.

**Related Topics**

- [Determine which .NET Framework versions are installed](https://docs.microsoft.com/en-us/dotnet/framework/migration-guide/how-to-determine-which-versions-are-installed)

**Parent topic:** Getting Started with Oracle Trace File Analyzer

### 13.6 Installing Oracle Trace File Analyzer on Microsoft Windows in Non-Daemon Mode

If you do not want Oracle Trace File Analyzer to run automatically as a windows service, then install it in non-daemon mode. Oracle Trace File Analyzer has reduced capabilities in this installation mode.

You cannot complete the following tasks:

- Automate diagnostic collections

- Collect diagnostics from remote hosts

- Collect files that are not readable by the Oracle home owner

1.  Download appropriate Oracle Trace File Analyzer zipped file, copy the downloaded file to one of the required machines, and then unzip.
2.  Open a command prompt as administrator and then run the installation script.
        tfa_home\bin\tfactl.bat -setupnd

**Parent topic:** Getting Started with Oracle Trace File Analyzer

### 13.7 Oracle Trace File Analyzer Key Directories

Based on your installation type, the `ora_home` and the `bin` directories can differ.

If you have installed Oracle Trace File Analyzer with Oracle Grid Infrastructure, then `TFA_HOME` will be `GRID_HOME/tfa/``hostname``/tfa_home`.

Table 13-1 Key Oracle Trace File Analyzer Directories

| Directory                                      | Description                                                                                                                                                   |
|:-----------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `tfa/bin`                                      | Contains the command-line interface `tfactl`<br>If Oracle Grid Infrastructure is installed, then `tfactl` is also installed in the `GRID_HOME/bin` directory. |
| `tfa/repository`                               | Directory where Oracle Trace File Analyzer stores diagnostic collections.                                                                                     |
| `tfa/``node``/tfa_home/database`               | Contains Berkeley database that stores data about the system.                                                                                                 |
| `tfa/``node``/tfa_home/diag`                   | Tools for troubleshooting Oracle Trace File Analyzer.                                                                                                         |
| `tfa/``node``/tfa_home/diagnostics_to_collect` | Place files here to include them in the next collection, then have them deleted afterwards.                                                                   |
| `tfa/``node``/tfa_home/log`                    | Contains logs about Oracle Trace File Analyzer operation.                                                                                                     |
| `tfa/``node``/tfa_home/resources`              | Contains resource files, for example, the log masking control file.                                                                                           |
| `tfa/``node``/tfa_home/output`                 | Contains extra metadata about the environment.                                                                                                                |

**Parent topic:** Getting Started with Oracle Trace File Analyzer

### 13.8 Oracle Trace File Analyzer Command Interfaces

The `tfactl` tool functions as command-line interface, shell interface, and menu interface.

Table 13-2 Oracle Trace File Interfaces

| Interface       | Command              | How to use                                                                           |
|:----------------|:---------------------|:-------------------------------------------------------------------------------------|
| Command-line    | `$ tfactl ``command` | Specify all command options at the command line.                                     |
| Shell interface | `$ tfactl`           | Set and change the context and then run commands from within the shell.              |
| Menu Interface  | `$ tfactl ``menu`    | Select the menu navigation options and then choose the command that you want to run. |

**Parent topic:** Getting Started with Oracle Trace File Analyzer

### 13.9 Masking Sensitive Data

Masking sensitive data is an optional feature that you can configure Oracle Trace File Analyzer to mask sensitive data in log files.

Oracle Trace File Analyzer masks information such as host names or IP addresses and replaces sensitive data consistently throughout all files. Replacing consistently means that the information is still relevant and useful for the purposes of diagnosis without sharing any sensitive data.

#### To configure masking:

1.  Create a file called `mask_strings.xml` in the directory `tfa_home/resources`.
2.  Define a `mask_strings` element then within that a `mask_string` element, with `original` and `replacement` for each string you wish to replace:
    For example:
        <mask_strings>
             <mask_string>
                  <original>WidgetNode1</original>
                  <replacement>Node1</replacement>
             </mask_string>
             <mask_string>
                  <original>192.168.5.1</original>
                  <replacement>Node1-IP</replacement>
             </mask_string>
             <mask_string>
                  <original>WidgetNode2</original>
                  <replacement>Node2</replacement>
             </mask_string>
             <mask_string>
                  <original>192.168.5.2</original>
                  <replacement>Node2-IP</replacement>
             </mask_string>
        </mask_strings>

    Oracle Trace File Analyzer automatically locates the `mask_strings.xml` files, and starts replacing the sensitive data in the diagnostics it collects.

**Parent topic:** Getting Started with Oracle Trace File Analyzer

### 13.10 Securing Access to Oracle Trace File Analyzer

Running `tfactl` commands is restricted to authorized users.

`tfactl` provides a command-line interface and shell to do the following:

- Run diagnostics and collect all relevant log data from a time of your choosing

- Trim log files around the time, collecting only what is necessary for diagnosis

- Collect and package all trimmed diagnostics from any desired nodes in the cluster and consolidate everything in one package on a single node

Authorized non-root users can run a subset of the `tfactl` commands. All other `tfactl` commands require `root` access. Users who are not authorized cannot run any `tfactl` command.

By default, the following users are authorized to access a subset of `tfactl` commands:

- Oracle Grid Infrastructure home owner

- Oracle Database home owners

User access is applicable only if Oracle Trace File Analyzer is installed as `root` on Linux and UNIX. User access is not applicable if Oracle Trace File Analyzer is installed as non-root, or on Microsoft Windows.

#### To provision user access to tfactl:

- To list the users who have access to `tfactl`:

      tfactl access lsusers

- To add a user to access `tfactl`:

      tfactl access add –user user [-local]

  By default, access commands apply to cluster-wide unless `–local` is used to restrict to local node.

- To remove a user from accessing `tfactl`:

      tfactl access remove –user user [-local]

- To remove all users from accessing `tfactl`:

      tfactl access removeall [-local]

- To reset user access to default:

      tfactl access reset

- To enable user access:

      tfactl access enable

- To disable user access:

      tfactl access disable

**Related Topics**

- [tfactl access](running-administration-commands.md)

**Parent topic:** Getting Started with Oracle Trace File Analyzer

### 13.11 Uninstalling Oracle Trace File Analyzer

1.  To uninstall Oracle Trace File Analyzer, run the `uninstall` command as `root`, or install user.
        $ tfactl uninstall

**Parent topic:** Getting Started with Oracle Trace File Analyzer
