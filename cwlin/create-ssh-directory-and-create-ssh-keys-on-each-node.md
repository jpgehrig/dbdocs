## Create SSH Directory and Create SSH Keys On Each Node

To configure SSH, you must first create RSA or DSA keys on each cluster node.

Complete the following steps on each node:

1.  Log in as the software owner (in this example, the `grid` user).
2.  To ensure that you are logged in as the `grid` user, and to verify that the user ID matches the expected user ID you have assigned to the `grid` user, enter the commands: ` `
        $ id
        $ id grid

    Ensure that Oracle user group and user and the user terminal window process you are using have group and user IDs are identical.

    For example:

        uid=54322(grid) gid=54321(oinstall) groups=54321(oinstall),54322(grid,asmadmin,asmdba)
        $ id grid uid=54322(grid) gid=54321(oinstall) groups=54321(oinstall),54322(grid,asmadmin,asmdba)
3.  If necessary, create the `.ssh` directory in the `grid` user's home directory, and set permissions on it to ensure that only the oracle user has read and write permissions:
        $ mkdir ~/.ssh
        $ chmod 700 ~/.ssh

    Note that the SSH configuration fails if the permissions are not set to 700.
4.  Enter the following command:
        $ /usr/bin/ssh-keygen -t dsa

    **Note:**

    If you have OpenSSH version 7.8 or higher installed on your system, then enter the following command to create SSH keys on each node:
        $ /usr/bin/ssh-keygen -t dsa -m PEM

    At the prompts, accept the default location for the key file (press Enter).

    Never distribute the private key to anyone not authorized to perform Oracle software installations.

    This command writes the DSA public key to the `~/.ssh/id_dsa.pub` file and the private key to the `~/.ssh/id_dsa` file.
5.  Repeat steps 1 through 4 on each node that you intend to make a member of the cluster, using the DSA key.

**Parent topic:** [Configuring SSH on Cluster Nodes](configuring-ssh-on-cluster-nodes.md)
