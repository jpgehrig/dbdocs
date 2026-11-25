## Running a Zero-Downtime Upgrade Using Oracle GoldenGate for Replication

Run a zero-downtime upgrade using Oracle GoldenGate for replication.

1.  Prepare the Fleet Patching and Provisioning Server.

    Create gold images of the Oracle GoldenGate software in the image library of the Fleet Patching and Provisioning Server.
    **Note:**

    You can download the Oracle GoldenGate software for your platform from Oracle eDelivery. The Oracle GoldenGate 12.3 installable kit contains the required software for both Oracle Database 11g and Oracle Database 12c databases.
    If you download the Oracle GoldenGate software, then extract the software home and perform a software only installation on the Fleet Patching and Provisioning Server.

    Create gold images of the Oracle GoldenGate software for both databases, as follows:
        $ rhpctl import image -image 112ggimage -path path -imagetype ORACLEGGSOFTWARE
        $ rhpctl import image -image 12ggimage -path path -imagetype ORACLEGGSOFTWARE

    In both of the preceding commands, `path` refers to the location of the Oracle GoldenGate software home on the Fleet Patching and Provisioning Server for each release of the database.

2.  Prepare the Oracle FPP Client or `rhpclient`-less target database.

    Provision working copies of the Oracle GoldenGate software to the cluster hosting the database, as follows:
        $ rhpctl add workingcopy -workingcopy GG_Wcopy_11g -image 112ggimage -user
          user_name -node 12102_cluster_node -path path {-root | -sudouser user_name
          -sudopath sudo_bin_path}
        $ rhpctl add workingcopy -workingcopy GG_Wcopy_12c -image 12ggimage -user
          user_name -node 12102_cluster_node -path path {-root | -sudouser user_name
          -sudopath sudo_bin_path}

    If the database is hosted on the Oracle Fleet Patching and Provisioning Server, itself, then neither the `-targetnode` nor `-client` parameters are required.
    **Note:**

    Working copy names must be unique, therefore you must use a different working copy name on subsequent Oracle FPP Clients and `rhpclient`-less targets. You can create unique working copy names by including the name of the Oracle FPP Client or `rhpclient`-less target name in the working copy name.

3.  Provision a working copy of the Oracle Database 12c software home to the Oracle FPP Client or `rhpclient`-less target.

**Note:**

You can do this preparation ahead of the maintenance window without disrupting any operations on the server.

- You can run the upgrade command on the Oracle Fleet Patching and Provisioning Server to upgrade a database hosted on the server, an Oracle Database 12c release 1 (12.1.0.2) `rhpclient`-less target, or a database hosted on an Oracle Fleet Patching and Provisioning Client 12c release 2 (12.2.0.1) or later releases. You can also run the command on an Oracle Fleet Patching and Provisioning Client 18c or later to upgrade a database hosted on the Oracle FPP Client, itself.
  Use the upgrade command similar to the following:
      $ rhpctl zdtupgrade database -dbname sierra -destwc DB_Wcopy_121 -ggsrcwc
        GG_Wcopy_11g -ggdstwc GG_Wcopy_12c -targetnode 12102_cluster_node -root

  In the preceding command, `12102_cluster_node` refers to the Oracle Grid Infrastructure 12c release 1 (12.1.0.2) cluster hosting the database you want to upgrade.

**Related Topics**

- [rhpctl import image](image-commands.md)
- [rhpctl add workingcopy](workingcopy-commands.md)
- [rhpctl zdtupgrade database](database-commands.md)

**Parent topic:** [Zero-Downtime Upgrade](zero-downtime-upgrade.md)
