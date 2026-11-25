If you are on a remote terminal, and the local system has only one visual (which is typical), then use the following syntax to set your user account `DISPLAY` environment variable:

### Remote Display

`Bourne, Korn, and Bash shells`

    $ export DISPLAY=hostname:0

`C shell`

    % setenv DISPLAY hostname:0

For example, if you are using the Bash shell and if your host name is `local_host`, then enter the following command:

    $ export DISPLAY=node1:0

### X11 Forwarding

To ensure that X11 forwarding does not cause the installation to fail, use the following procedure to create a user-level SSH client configuration file for Oracle installation owner user accounts:

1.  Using any text editor, edit or create the software installation owner's` ~/.ssh/config file`.

2.  Ensure that the `ForwardX11` attribute in the `~/.ssh/config` file is set to `no`. For example:

        Host *
            ForwardX11 no

3.  Ensure that the permissions on `~/.ssh` are secured to the Oracle installation owner user account. For example:

        $ ls -al .ssh
        total 28
        drwx------  2 grid oinstall 4096 Jun 21 2015
        drwx------ 19 grid oinstall 4096 Jun 21 2015
        -rw-r--r--  1 grid oinstall 1202 Jun 21 2015 authorized_keys
        -rwx------  1 grid oinstall  668 Jun 21 2015 id_dsa
        -rwx------  1 grid oinstall  601 Jun 21 2015 id_dsa.pub
        -rwx------  1 grid oinstall 1610 Jun 21 2015 known_hosts

**Parent topic:** [Creating Operating System Oracle Installation User Accounts](creating-operating-system-oracle-installation-user-accounts.md)
