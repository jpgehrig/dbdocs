## 14.3.1.3.1 Storing User Credentials in a Wallet

The following steps describe the process for adding the credentials to the wallet zip file. It is important that you store this wallet file along with the credentials in a safe location for security reasons.

1.  Unzip the cloud wallet zip file in a temporary directory.

2.  Use the service name alias in the tnsnames.ora to store credentials by running the following command:

    For example, if the service name alias is db202002041627_medium:

        ${ORACLE_HOME}/bin/orapki secretstore create_credential -wallet /tmp/cloudwallet
                   -connect_string db202002041627_medium -username username -password password

3.  Zip the cloud wallet files into a new zip file.

**Parent topic:** [Creating an Oracle Wallet Data Source](creating-oracle-wallet-data-source.md)
