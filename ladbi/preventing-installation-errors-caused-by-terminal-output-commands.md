## Preventing Installation Errors Caused by Terminal Output Commands

During an Oracle Grid Infrastructure installation, OUI uses SSH to run commands and copy files to the other nodes. During the installation, hidden files on the system (for example, `.bashrc` or `.cshrc`) can cause `makefile` and other installation errors if they contain terminal output commands.

To avoid this problem, you must modify hidden files in each Oracle installation owner user home directory to suppress all output on `STDOUT` or `STDERR` (for example, `stty`, `xtitle`, and other such commands) as in the following examples:

Bourne, Bash, or Korn shell:

    if [ -t 0 ]; then
       stty intr ^C
    fi

C shell:

    test -t 0
    if ($status == 0) then
       stty intr ^C
    endif

**Note:**

If the remote shell can load hidden files that contain `stty` commands, then OUI indicates an error and stops the installation.

**Parent topic:** [Creating Operating System Oracle Installation User Accounts](creating-operating-system-oracle-installation-user-accounts.md)
