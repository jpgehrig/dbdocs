## Postinstallation Configuration Using the ConfigToolAllCommands Script

You can create and run a response file configuration after installing Oracle software.

The `configToolAllCommands` script requires users to create a second response file, of a different format than the one used for installing the product. Starting with Oracle Database 12c Release 2 (12.2), the `configToolAllCommands` script is deprecated and may be desupported in a future release.

Starting with Oracle Database 18c Release, use the `executeConfigTools` script to complete the postinstall configuration.

- [About the Postinstallation Configuration File](about-the-postinstallation-configuration-file.md)
  The configuration assistants are started with a script called `configToolAllCommands`.
- [Creating a Password Response File](creating-a-password-response-file.md)
  Use these steps to create a password response file for use with the `configToolAllCommands` script..
- [Running Postinstallation Configuration Using a Script and Response Files](running-postinstallation-configuration-using-a-script-and-response-files.md)
  You can run the postinstallation configuration assistants with the `configToolAllCommands` script.

**See Also:**

"[Postinstallation Configuration Using Response File Created During Installation](postinstallation-configuration-using-response-file-created-during-installation.md)" for an alternate method of postinstallation configuration of Oracle software using the same response file created at the time of installation.

**Parent topic:** [Installing and Configuring Oracle Grid Infrastructure Using Response Files](installing-and-configuring-oracle-grid-infrastructure-using-response-files.md)
