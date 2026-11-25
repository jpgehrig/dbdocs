If you have public and private network interface cards (NICs) on a single Windows computer and they are not in the correct order, then you might experience problems with any configuration (Oracle Enterprise Manager, for example) that uses `gethostname`.

If the private NIC is seen first by Windows, then a `gethostname` call returns the host name of the private interconnect. Whichever tool is calling `gethostname` has configuration or connectivity problems stemming from this nonpublic network information.

You can determine the current order of your NICs, and change it if necessary, as follows:

1.  From the Start menu, select Control Panel.
2.  Select Network and Internet, and then select Network and Sharing Center.
3.  Change the network adapter settings, depending on your operating system:
    - For Windows Server 2008, select Manage adapter settings.

    - For Windows Server 2008 R2, select Change adapter settings.
4.  Click Organize, then Layout, and then select Menu bar.
5.  From the Advanced menu, click Advanced Settings. The Advanced Settings window opens.
6.  From the Connections window in the Adapters and Binding tab, select the network adapter that you want.
7.  Move this network adapter to the top or the bottom of the list by using the up and down arrow buttons.
8.  Click OK.

**Parent topic:** [Tuning Windows to Optimize Oracle Database](tuning-windows-to-optimize-oracle-database.md)
