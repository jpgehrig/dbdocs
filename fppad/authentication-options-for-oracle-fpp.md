## Authentication Options for Oracle Fleet Patching and Provisioning Operations

Some RHPCTL commands show authentication choices as an optional parameter.

Specifying an authentication option is not required when running an RHPCTL command on an Oracle Fleet Patching and Provisioning Client, nor when running an RHPCTL command on the Oracle Fleet Patching and Provisioning Server and operating on an Oracle Fleet Patching and Provisioning Client, because the server and client establish a trusted relationship when the client is created, and authentication is handled internally each time a transaction takes place. (The only condition for server/client communication under which an authentication option must be specified is when the server is provisioning a new Oracle Grid Infrastructure deployment—in this case, the client does not yet exist.)

**Note:**

By default, SSH uses port 22 on an Oracle FPP Server. However, in Oracle FPP 19c, you can modify the SSH port using the `./crsctl modify res ora.rhpserver -attr "USR_ORA_ENV='SSH_PORT=``new_port``'" -unsupported` command.

To operate on an `rhpclient`-less target, you must provide the Oracle Fleet Patching and Provisioning Server with information allowing it to authenticate with the `rhpclient`-less target. The options are as follows:

- Provide the `root` password (on `stdin`) for the `rhpclient`-less target

- Provide the `sudo` user name, `sudo` binary path, and the password (`stdin`) for `rhpclient`-less target

- Provide a password (either `root` or `sudouser`) non-interactively from local encrypted store (using the `-cred` authentication parameter)

- Create credentials using the `rhpctl add credentials` command and provide credentials using the `-cred` option.

- Provide a path to the identity file stored on the Oracle Fleet Patching and Provisioning Server for SSL-encrypted passwordless authentication (using the `-auth sshkey` option)

### Passwordless Authentication Details

The Oracle Fleet Patching and Provisioning Server can authenticate to `rhpclient`-less targets over SSH using a key pair. To enable this option, you must establish user equivalence between the `crsusr` on the Oracle Fleet Patching and Provisioning Server and `root` or a `sudouser` on the `rhpclient`-less target.

**Note:**

The steps to create that equivalence are platform-dependent and so not shown in detail here. For Linux, see commands `ssh-keygen` to be run on the `rhpclient`-less target and `ssh-copy-id` to be run on the Oracle Fleet Patching and Provisioning Server.

For example, assuming that you have established user equivalency between `crsusr` on the Oracle Fleet Patching and Provisioning Server and `root` on the `rhpclient`-less target, `nonRHPClient4004.example.com`, and saved the key information on the Oracle Fleet Patching and Provisioning Server at `/home/oracle/rhp/ssh-key/key -path`, then the following command will provision a copy of the specified gold image to the `rhpclient`-less target with passwordless authentication:

    $ rhpctl add workingcopy -workingcopy db12102_160607wc1 -image db12102_160607
      -targetnode nonRHPClient4004.example.com -path /u01/app/oracle/12.1/rhp/dbhome_1
      -oraclebase /u01/app/oracle -auth sshkey -arg1 user:root -arg2
       identity_file:/home/oracle/rhp/ssh-key/key

For equivalency between `crsusr` on the Oracle Fleet Patching and Provisioning Server and a privileged user (other than `root`) on the `rhpclient`-less target, the `-auth` portion of the command would be similar to the following:

    -auth sshkey -arg1 user:ssh_user -arg2 identity_file:path_to_identity_file_on_RHPS
     -arg3 sudo_location:path_to_sudo_binary_on_target

**Related Topics**

- [rhpctl add credentials](credentials-commands.md)
- [rhpctl delete credentials](credentials-commands.md)
- [rhpctl add workingcopy](workingcopy-commands.md)

**Parent topic:** [Oracle Fleet Patching and Provisioning Security Postinstallation Tasks](security-postinstallation-tasks.md)
