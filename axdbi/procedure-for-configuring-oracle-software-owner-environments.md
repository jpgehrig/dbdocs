Configure each Oracle installation owner user account environment.

1.  Start an X terminal session (`xterm`) on the server where you are running the installation.
2.   Enter the following command to ensure that X Window applications can display on this system, where hostname is the fully qualified name of the local host from which you are accessing the server:
        $ xhost + hostname
3.  If you are not logged in as the software owner user, then switch to the software owner user you are configuring. For example, with the user `grid`:
        $ su - grid

    On systems where you cannot run `su` commands, use `sudo` instead:
        $ sudo -u grid -s
4.  To determine the default shell for the user, enter the following command:
        $ echo $SHELL
5.  Open the user's shell startup file in any text editor:
    - Bash shell (`bash`):

          $ vi .bash_profile

    - Bourne shell (`sh`) or Korn shell (`ksh`):

          $ vi .profile

    - C shell (`csh` or `tcsh`):

          % vi .login
6.  Enter or edit the following line, specifying a value of `022` for the default file mode creation mask:
        umask 022
7.  If the` ORACLE_SID`, `ORACLE_HOME`, or `ORACLE_BASE` environment variables are set in the file, then remove these lines from the file.
8.  Save the file, and exit from the text editor.
9.  To run the shell startup script, enter one of the following commands:
    - Bash shell:

          $ . ./.bash_profile

    - Bourne, Bash, or Korn shell:

          $ . ./.profile

    - C shell:

          % source ./.login
10. Use the following command to check the PATH environment variable:
        $ echo $PATH

    Remove any Oracle environment variables.
11.  If you are not installing the software on the local system, then enter a command similar to the following to direct X applications to display on the local system:
    - Bourne, Bash, or Korn shell:

          $ export DISPLAY=local_host:0.0

    <!-- -->

    - C shell:

          % setenv DISPLAY local_host:0.0

    In this example, `local_host` is the host name or IP address of the system (your workstation, or another client) on which you want to display the installer.
12.  If the `/tmp` directory has less than 5 GB of free space, then identify a file system with at least 5 GB of free space and set the `TMP` and `TMPDIR` environment variables to specify a temporary directory on this file system:
    **Note:**

    You cannot use a shared file system as the location of the temporary file directory (typically `/tmp`) for Oracle RAC installations. If you place `/tmp` on a shared file system, then the installation fails.

    1.  Use the `df -h` command to identify a suitable file system with sufficient free space.
    2.  If necessary, enter commands similar to the following to create a temporary directory on the file system that you identified, and set the appropriate permissions on the directory:
            $ sudo - s
            # mkdir /mount_point/tmp
            # chmod 775 /mount_point/tmp
            # exit
    3.  Enter commands similar to the following to set the `TMP` and `TMPDIR` environment variables:
        Bourne, Bash, or Korn shell:

            $ TMP=/mount_point/tmp
            $ TMPDIR=/mount_point/tmp
            $ export TMP TMPDIR

        C shell:

            % setenv TMP /mount_point/tmp
            % setenv TMPDIR /mount_point/tmp
13. To verify that the environment has been set correctly, enter the following commands:
        $ umask
        $ env | more

    Verify that the `umask` command displays a value of `22`, `022`, or `0022` and that the environment variables you set in this section have the correct values.

**Parent topic:** [Creating Operating System Oracle Installation User Accounts](creating-operating-system-oracle-installation-user-accounts.md)
