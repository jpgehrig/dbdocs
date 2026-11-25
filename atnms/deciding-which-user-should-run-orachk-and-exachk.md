Run health checks as `root`. Also, run health checks as the Oracle Database home owner or the Oracle Grid Infrastructure home owner.

Most health checks do not require `root` access. However, you need `root` privileges to run a subset of health checks.

To run `root` privilege checks, Oracle ORAchk uses the script `root_orachk.sh` and Oracle EXAchk uses the script `root_exachk.sh`.

By default, the `root_orachk.sh` and `root_exachk.sh` scripts are created in the `$HOME` directory used by Oracle ORAchk and Oracle EXAchk. Change the directory by setting the environment variable `RAT_ROOT_SH_DIR`.

Specify a location for sudo remote access as follows:

    export RAT_ROOT_SH_DIR=/mylocation

Add an entry in the /etc/sudoers as follows:

    oracle ALL=(root) NOPASSWD:/mylocation/root_orachk.sh

For security reasons, create the `root` scripts outside of the standard temporary directory in a custom directory.

### To decide which user to run Oracle ORAchk and Oracle EXAchk:

1.  Specify the custom directory using the `RAT_ROOT_SH_DIR`  environment variable.
        export RAT_ROOT_SH_DIR=/orahome/oradb/
2.  Specify a location for `sudo`  remote access.
        export RAT_ROOT_SH_DIR=/mylocation
3.  Add an entry in the `/etc/sudoers`  file.
        oracle ALL=(root) NOPASSWD:/mylocation/root_orachk.sh

    **Note:**

    Specify full paths for the entries in the `/etc/sudoers`  file. Do not use environment variables.
4.  (recommended) Run Oracle ORAchk and Oracle EXAchk as `root`.
    Use `root` user credentials to run Oracle ORAchk and Oracle EXAchk.

    The Oracle ORAchk and Oracle EXAchk processes that run as `root`, perform user lookups for the users who own the Oracle Database home and Oracle Grid Infrastructure home. If `root` access is not required, then the Oracle ORAchk and Oracle EXAchk processes use the `su` command to run health checks as the applicable Oracle Database home user or Oracle Grid Infrastructure home user. Accounts with lower privileges cannot have elevated access to run health checks that require `root` access.

    Running health checks as `root` has advantages in role-separated environments or environments with more restrictive security.
5.  Run Oracle ORAchk and Oracle EXAchk as Oracle Database home owner or Oracle Grid Infrastructure home owner:
    Use Oracle Database home owner or Oracle Grid Infrastructure home owner credentials to run Oracle ORAchk and Oracle EXAchk.

    The user who runs Oracle ORAchk and Oracle EXAchk must have elevated access as `root` to run health checks that need `root` access.

    Running health checks as Oracle Database home owner or Oracle Grid Infrastructure home owner requires multiple runs in role-separated environments. More restrictive security requirements do not permit elevated access.

    There are several other options:

    - Skip the checks that require `root` access.

    - Specify the `root`  user ID and password when prompted.

    - Configure `sudo`.

      If you are using `sudo`, then add an entry for the `root` script, located in `$HOME` in the `/etc/sudoers` file that corresponds to the user who is running the health checks.

      To determine what `$HOME` is set to, run the `echo $HOME`  command.

      For example:
          user ALL=(root) NOPASSWD:/root/root_orachk.sh

          user ALL=(root) NOPASSWD:/root/root_exachk.sh

    - Pre-configure passwordless SSH connectivity.

**Parent topic:** [Configuring Oracle ORAchk and Oracle EXAchk](config-orachk-and-exachk.md)
