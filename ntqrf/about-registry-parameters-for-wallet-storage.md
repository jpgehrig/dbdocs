Parameter `WALLET_LOCATN` in file `sqlnet.ora` specifies the location of the obfuscated Oracle Wallet for use by Oracle PKI applications.

For example, the `WALLET_LOCATN` parameter for storing an Oracle Wallet in the registry in:

    \\HKEY_CURRENT_USER\SOFTWARE\ORACLE\WALLETS\SALESAPP

is located in:

    WALLET_LOCATN =  (SOURCE= (METHOD=REG) (METHOD_DATA= (KEY=SALESAPP)))

Continuing the example, the encrypted Oracle Wallet is stored in the registry in:

    \\HKEY_CURRENT_USER\SOFTWARE\ORACLE\WALLETS\SALESAPP\EWALLET.P12

and the changed Oracle Wallet stored in:

    \\HKEY_CURRENT_USER\SOFTWARE\ORACLE\WALLETS\SALESAPP\CWALLET.SSO

On Windows operating systems, if there is no value specified for parameter `WALLET_LOCATN`, then Oracle PKI applications first look for the changed wallet in registry key:

    \\HKEY_CURRENT_USER\SOFTWARE\ORACLE\WALLETS\DEFAULT

If no obfuscated wallet is found there, Oracle PKI applications look for it in the file system of the local computer at location:

    %USERPROFILE%\ORACLE\WALLETS

Regardless of location, wallets are always stored in the same format. All functionality is the same except for the location of the wallets.

- [About Oracle Wallet Manager](about-oracle-wallet-manager.md)
  Oracle Wallet Manager creates and manages Oracle Wallets.

**Parent topic:** [Storing Oracle Wallets in the Windows Registry](storing-oracle-wallets-in-windows-registry.md)
