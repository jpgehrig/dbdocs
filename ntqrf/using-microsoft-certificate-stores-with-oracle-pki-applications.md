Wallet Resource Locator (WRL) specifies that parameter `WALLET_LOCATN` in file `sqlnet.ora` identifies a particular PKI.

You can choose between using Oracle Wallet or Microsoft Certificate Stores by setting parameter `WALLET_LOCATN` in `sqlnet.ora`. To use credentials from Microsoft Certificate Stores, set parameter`WALLET_LOCATN` in `sqlnet.ora` to:

    WALLET_LOCATN = (SOURCE = (METHOD=MCS))

The Oracle application uses Oracle's TCP/IP with SSL protocol (TCPS) to connect to Oracle Server. The SSL protocol uses X.509 certificates and trust points from the user's Microsoft Certificate Store for SSL authentication.

**Parent topic:** [About Windows Public Key Infrastructure](about-windows-public-key-infrastructure.md)
