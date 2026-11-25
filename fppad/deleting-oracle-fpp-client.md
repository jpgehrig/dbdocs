## Deleting a Fleet Patching and Provisioning Client

Use the following procedure to delete a Fleet Patching and Provisioning Client.

1.  Before deleting the Fleet Patching and Provisioning Client, you must first delete the working copies and users on the Fleet Patching and Provisioning Server, as follows:
    1.  Query the list of working copies that have been provisioned on the Fleet Patching and Provisioning Client cluster.
        Run the following command:

            $ rhpctl query workingcopy -client client_name
    2.  Delete each of the working copies listed in the output of the preceding command.
        Run the following command for each working copy and specify the name of the working copy you want to delete:

            $ rhpctl delete workingcopy -workingcopy working_copy_name
    3.  Query the list of users from the Fleet Patching and Provisioning Client cluster.
        Run the following command:

            $ rhpctl query user -client client_name
    4.  Delete the users listed in the output of the preceding command, as follows:
        Run the following command and specify the name of the user you want to delete and the name of the client:

            $ rhpctl delete user -user user_name —client client_name
2.  On the Fleet Patching and Provisioning Client cluster, delete the client, as follows:
    1.  Stop the Fleet Patching and Provisioning Client daemon.
        Run the following command:

            $ srvctl stop rhpclient
    2.  Delete the Fleet Patching and Provisioning Client configuration.
        Run the following command:

            $ srvctl remove rhpclient
3.  Delete the client site configuration on the Fleet Patching and Provisioning Server cluster.
    Run the following command and specify the name of the client:

        $ rhpctl delete client -client client_name

**Parent topic:** [Configuring Oracle Fleet Patching and Provisioning Clients](configuring-oracle-fpp-clients.md)
