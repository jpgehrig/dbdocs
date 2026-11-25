The Oracle Database Client software is available on Oracle Technology Network website. This chapter describes the following sections:

- Downloading and Installing the Oracle Database Client Software

- Removing the Oracle Database Client Software

### Downloading and Installing the Oracle Database Client Software

The following steps describe how to install the Oracle software:

1.  Download the Instant Client for Linux on POWER Systems (64-bit) package from the Instant Client Downloads page on Oracle Technology Network at
    [`http://www.oracle.com/technetwork/index.html`](http://www.oracle.com/technetwork/index.html)
2.  Create a directory on your computer, for example, `instantclient`. Choose a directory to install the Oracle Instant Client and unzip the downloaded zip file in that directory. The unzipped file creates the `instantclient_19_3` directory.
3.  Set the `LD_LIBRARY_PATH` and the `NLS_LANG` environment variables to the full path of the `instantclient_19_3` directory. For example, if you unzipped the Instant Client zip file in the `/bin/oracle` directory, then set the `LD_LIBRARY_PATH` environment variable to `/bin/oracle/instantclient_19_3`.
    See the "[Instant Client Light Requirements](oracle-database-client-preinstallation-tasks.md)" section for information about setting the `NLS_LANG` environment variable to the required character set.

    This completes the installation of Oracle Database Client. To connect to the Oracle Database server, run the client from the Oracle Database Instant Client environment.
4.  The Object Type Translator Utility (OTT) utility may have to be modified to reflect the correct environment variable `LD_LIBRARY_PATH` as `ORACLE_HOME` may not be available.

**Note:**

If you want to use VAC compiler, then you must set the `COMPILER=VAC` value in the environment. Also, set the `VAC_VERSION` as follows:

- For Red Hat Enterprise Linux Server 7.1, set:

  `VAC_VERSION=13.1.2`

- For SUSE Linux Enterprise Server 12, set:

  `VAC_VERSION=13.1.1`

In addition to the preceding task:

- Ensure that `xlC` is in the `PATH` of your environment.

- Also, set `COMPILER_MODE = 64` if you want to build a 64-bit demo executable.

### Removing the Oracle Database Client Software

To remove the Oracle Database Client software, delete the `instantclient_19_3` directory.
