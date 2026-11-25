To configure SSH, copy all the generated keys on all cluster node members into an authorized keys file that is identical on each node.

Complete the following steps:

1.  On the local node, change directories to the `.ssh` directory in the Oracle Grid Infrastructure owner's home directory (typically, either `grid` or `oracle`). Then, add the DSA key to the` authorized_keys` file using the following commands:
        $ cat id_dsa.pub >> authorized_keys
        $ ls

    In the `.ssh` directory, you should see the `id_dsa.pub` keys that you have created, and the file `authorized_keys`.
2.  On the local node, use SFTP (Secure FTP) to copy the `authorized_keys` file to the `oracle` user `.ssh` directory on a remote node. The following example is on a node called `node2`, with the Oracle Grid Infrastructure owner `grid`, where the `grid` user path is `/home/grid`:
        [grid@node1 .ssh]$ sftp authorized_keys node2:/home/grid/.ssh/

    1.  You are prompted to accept a DSA key. Enter Yes, and you see that the node you are copying to is added to the `known_hosts` file.
    2.  When prompted, provide the password for the grid user, which should be the same on all nodes in the cluster. The `authorized_keys` file is copied to the remote node.

    Your output should be similar to the following, where `xxx` represents parts of a valid IP address:
        [grid@node1 .ssh]$ sftp authorized_keys node2:/home/grid/.ssh/
        The authenticity of host 'node2 (xxx.xxx.173.152) can't be established.
        DSA key fingerprint is 7e:60:60:ae:40:40:d1:a6:f7:4e:zz:me:a7:48:ae:f6:7e.
        Are you sure you want to continue connecting (yes/no)? yes
        Warning: Permanently added 'node1,xxx.xxx.173.152' (dsa) to the list
        of known hosts
        grid@node2's password:
        authorized_keys      100%        828         7.5MB/s      00:00
3.  Using SSH, log in to the node where you copied the `authorized_keys` file. Then change to the `.ssh` directory, and using the `cat` command, add the DSA keys for the second node to the `authorized_keys` file, clicking Enter when you are prompted for a password, so that passwordless SSH is set up:
        [grid@node1 .ssh]$ ssh node2 [grid@node2 grid]$ cd .ssh [grid@node2 ssh]
        $ cat id_dsa.pub  >> authorized_keys
4.  Repeat steps 2 and 3 from each node to each other member node in the cluster.
5.  When you have added keys from each cluster node member to the `authorized_keys` file on the last node you want to have as a cluster node member, then use `sftp` to copy the `authorized_keys` file with the keys from all nodes back to each cluster node member, overwriting the existing version on the other nodes. To confirm that you have all nodes in the `authorized_keys` file, enter the command `more authorized_keys`, and determine if there is a DSA key for each member node. The file lists the type of key (`ssh-dsa`), followed by the key, and then followed by the user and server. For example:
        ssh-dsa AAAABBBB . . . = grid@node1

    The `grid` user's `/.ssh/authorized_keys` file on every node must contain the contents from all of the `/.ssh/id_dsa.pub` files that you generated on all cluster nodes.

**Parent topic:** [Configuring SSH on Cluster Nodes](configuring-ssh-on-cluster-nodes.md)
