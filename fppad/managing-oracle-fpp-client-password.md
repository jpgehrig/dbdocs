## Managing the Fleet Patching and Provisioning Client Password

The Oracle Fleet Patching and Provisioning (Oracle FPP) Client uses a password stored internally to authenticate itself with the RHP server.

You cannot query the Oracle FPP Client password, however, if for some reason, you are required to reset this password, then you can do so, as follows, on the RHP server cluster:

1.  Run the following command on the Fleet Patching and Provisioning Server cluster to generate a new password and store it in the client credential:
        $ rhpctl modify client -client client_name -password
2.  Run the following command on the Fleet Patching and Provisioning Server cluster to generate a credential file:
        $ rhpctl export client -client client_name -clientdata file_path

    For example, to generate a credential file for a Fleet Patching and Provisioning Client named `mjk9394`:

        $ rhpctl export client -client mjk9394 -clientdata /tmp/mjk9394.xml
3.  Continuing with the preceding example, transport the generated credential file securely to the Fleet Patching and Provisioning Client cluster and then run the following command on any node in the Fleet Patching and Provisioning Client cluster:
        $ srvctl modify rhpclient -clientdata path_to_mjk9394.xml
4.  Restart the Fleet Patching and Provisioning Client daemon by running the following commands on the Fleet Patching and Provisioning Client cluster:
        $ srvctl stop rhpclient
        $ srvctl start rhpclient

**Parent topic:** [Oracle Fleet Patching and Provisioning Security Postinstallation Tasks](security-postinstallation-tasks.md)
