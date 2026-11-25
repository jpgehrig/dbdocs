## Provisioning for a Different User

If you want a different user to provision software other than the user running the command, then use the `-user` parameter of the `rhpctl add workingcopy` command.

When the provisioning is completed, all files and directories of the provisioned software are owned by the user you specified. Permissions on files on the remotely provisioned software are the same as the permissions that existed on the gold image from where you provisioned the application software.

**Parent topic:** [Provisioning Copies of Gold Images](provisioning-gold-image-copies.md)
