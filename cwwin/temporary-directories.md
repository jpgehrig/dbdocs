## Temporary Directories

To install properly across all nodes, OUI uses the temporary folders defined within Microsoft Windows.

The TEMP and TMP environment variables should point to the same local directory on all nodes in the cluster.

By default, these settings are defined as `%USERPROFILE%\Local Settings\Temp` and `%USERPROFILE%\Local Settings\Tmp` in the Environment Settings of My Computer. It is recommended to explicitly redefine these as `%WINDIR%\temp` and `%WINDIR%\tmp`.

For example, if Windows is installed on the C drive, then the temporary directories would be defined as `C:\Windows\temp` or `C:\Windows\tmp` for all nodes.

**Parent topic:** [About the Directories Used During Installation of Oracle Grid Infrastructure](about-the-directories-used-during-installation-of-oracle-grid-infrastructure.md)
