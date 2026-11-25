## Windows Authentication No Longer Uses NTLM by Default

For Microsoft Windows installations with `AUTHENTICATION_SERVICES=NTS`, in this Oracle Database release, the `SQLNET.NO_NTLM` parameter setting in the `sqlnet.ora` file defaults to `TRUE`, which can cause ORA-12638 errors.

Date: August 2023

In previous releases, the default for `AUTHENTICATION_SERVICES=NTS` was `FALSE`. `SQLNET.NO_NTLM` controls whether NTLM can be used with NTS authentication. A `TRUE` setting means that NTLM cannot be used in NTS authentication. Because NTLM does not normally provide mutual authentication and is hence less secure, a `TRUE` setting for `SQLNET.NO_NTLM` makes the database and client more secure.

The `SQLNET.NO_NTLM` parameter is used on both the server and the client. If you have upgraded a Microsoft Windows installation of Oracle Database, or upgraded a client in which `SQLNET.NO_NTLM` had not been set, then its default will be `TRUE`. In that case, when you have `SQLNET.AUTHENTICATION_SERVICES=NTS` in your `sqlnet.ora`, clients can encounter the error `ORA-12638: Credential retrieval failed`.

If you prefer to use NTLM authentication for certain clients, then set this parameter as required in client-side `sqlnet.ora` files:

    SQLNET.NO_NTLM=FALSE

You must include this setting on both the server and client, and this setting should be the same on both. Ideally, you should ensure that `SQLNET.NO_NTLM` is set to `TRUE`. However, if there is an authentication failure in `extproc`, a virtual account, or a local account on Windows, set the client `SQLNET.NO_NTLM` to `FALSE`, and then retry the login. If you change `SQLNET.NO_NTLM` on the server, then you must restart the database.

**Related Topics**

- [Upgrade Your Database Now - ORA-12638 on Windows only from Oracle 19.10.0 onwards](https://mikedietrichde.com/2021/03/10/ora-12638-on-windows-only-from-oracle-19-10-0-onwards/)
- [Windows : While Connect to Database Getting ORA-12638 After Applying Jan 2021 WINDBBP 19.10.0.0.210119 On Windows 64/32 Bit Database Client (Doc ID 2757734.1)](https://support.oracle.com/rs?type=doc&id=2757734.1)

**Parent topic:** [Required Postinstallation Tasks](required-postinstallation-tasks.md)
