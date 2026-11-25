## Provisioning Oracle Database Homes

Use the `rhpctl add workingcopy` command to provision a working copy of a database home on a Oracle Fleet Patching and Provisioning Server, Client, or `rhpclient`-less target.

- Run the `rhpctl add workingcopy` command on a Fleet Patching and Provisioning Server, similar to the following example:
      $ rhpctl add workingcopy -image db12c -path /u01/app/dbusr/product/12.2.0/db12201
        -client client_007 -oraclebase /u01/app/dbusr/ -workingcopy wc_db122_1

  The preceding command example creates a working copy named `wc_db122_1` on all nodes of the Fleet Patching and Provisioning Client cluster named `client_007`. The gold image `db12c` is the source of the workingcopy. The directory path locations that you specify in the command must be empty.

**Related Topics**

- [rhpctl add workingcopy](workingcopy-commands.md)

**Parent topic:** [Managing Gold Images and Working Copies](managing-gold-images-and-working-copies.md)
