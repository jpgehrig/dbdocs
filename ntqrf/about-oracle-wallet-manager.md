Oracle Wallet Manager creates and manages Oracle Wallets.

If you want to use the Windows registry for Oracle Wallets, then you must select the Use Windows System Registry check box. If Windows System Registry is selected, then the tool shows a list of existing keys when it opens a wallet or saves a new wallet. The list appears in:

    \\HKEY_CURRENT_USER\SOFTWARE\ORACLE\WALLETS

You can select one of the existing locations or enter the name for a new location (registry key). If you enter a new key called `key1`, for example, then the tool creates the following registry key:

    \\HKEY_CURRENT_USER\SOFTWARE\ORACLE\WALLETS\KEY1

The encrypted wallet is stored in:

    \\HKEY_CURRENT_USER\SOFTWARE\ORACLE\WALLETS\KEY1\EWALLET.P12

The obfuscated wallet is stored in:

    \\HKEY_CURRENT_USER\SOFTWARE\ORACLE\WALLETS\KEY1\CWALLET.SSO

If you do not select the Use Windows System Registry check box, then the tool displays all the available drives and directories on the local computer. You can select one of the existing directories or enter a new directory. The tool stores the encrypted or the obfuscated wallet in the selected directory or creates the directory if it does not exist.

- [About Sharing Wallets and sqlnet.ora Files Among Multiple Databases](about-sharing-wallets-and-sqlnet.ora-files-among-multiple-databases.md)
  Multiple nonreplicated databases cannot share wallets.

**See Also:**

[Oracle Database Enterprise User Security Administrator's Guide](../dbimi/using-oracle-wallet-manager.md) for more information about using Oracle Wallet Manager

**Parent topic:** [About Registry Parameters for Wallet Storage](about-registry-parameters-for-wallet-storage.md)
