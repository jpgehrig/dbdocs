This preface contains:

- Changes in this Release for Release 19c Version 19.1

- Changes in Oracle Database Release 18c Version 18.1

- Changes in Oracle Database 12c Release 2 (12.2.0.1)

### Changes in this Release for Release 19c Version 19.1

The following are changes in Oracle Database Enterprise User Security Administrator's Guide for Oracle Database release 19c, version 19.1.

#### New Features

The following features are new in this release:

- Enterprise Security Administrators can configure a client-side wallet also known as an external secure password store to store user name credentials when using standalone utilities.

  Doing this simplifies deployments that rely on password credentials for connecting to databases as scripts will then no longer need to embed user names and passwords. This also reduces risk because the passwords are no longer exposed, and password policies are more easily managed without changing application code or scripts whenever user names or passwords change.

  The client-side wallet can be used with the following standalone utilities:
  - Enterprise User Security Manager (EUSM)

    See [About Using a Secure External Password Store](enterprise-user-security-manager-eusm-command-summary.md) for more information about configuring the `dbuser`, `keystore`, and `ldap_user` credentials in the wallet and using the `db_alias`, `keystore_alias`, `ldap_alias`, and `wallet_location` parameters on the command-line.

  - User Migration Utility

    See [Step 0: About Using a Secure External Password Store](using-the-user-migration-utility.md) for more information about configuring the `DBADMIN` and `ENTADMIN` credentials in the wallet and using the `DBALIAS`, `ENTALIAS`, and `WALLETLOCATION` parameters on the command-line.

  - External Users Conversion Script

    See [SSL External Users Conversion Script](ssl-external-users-conversion-script.md) for more information about configuring the `dbuser` credential in the wallet and using the `-dbalias` and `-wallet_location` parameters on the command-line.

### Changes in Oracle Database Release 18c Version 18.1

The following are changes in Oracle Database Enterprise User Security Administrator's Guide for Oracle Database release 18c, version 18.1.

#### New Features

The following features are new in this release:

- Oracle Database Enterprise User Security release 18c, version 18.1 includes the following new features:

  - Enterprise User Security Manager (EUSM)

    The `eusm` command-line tool can be used to manage the Enterprise User Security (EUS) Configuration in Oracle Internet Directory (OID) directory server.

    See [Enterprise User Security Manager (EUSM) Command Reference](enterprise-user-security-manager-eusm-command-summary.md) for more information about this feature.

  - Centrally Managed Users for Microsoft Active Directory.

    This integration is the preferred option from a complexity, cost, maintenance, and development perspective for new projects that do not require some of the more complex Enterprise User Security features like trusted database links.

    See [Configuring Authentication](../dbseg/index.md) and [Configuring Authorization](../dbseg/integrating_mads_with_oracle_database.md) in Oracle Database Security Guide for more information about using centrally managed users to directly authenticate and authorize users with Microsoft Active Directory.

    See [Integrating Enterprise User Security with Microsoft Active Directory](integrating-enterprise-user-security-with-microsoft-active-directory.md) for other options to authenticate and authorize users with Microsoft Active Directory.

  - Support is added for Enterprise User Security authentication with 12C verifier generated from Oracle Internet Directory

    The 12C verifier generated from Oracle Internet Directory uses a new ZT tag, `MR-SHA512`, for multi-round Password-Based Key Derivation Function (PBKDF2) based keyed-hash message authentication code (HMAC) with SHA512 cryptographic hash functions to provide a strong password verifier. This support is added in OID bundle patch 11.1.1.9.0.

    See [Oracle® Fusion Middleware Administrator's Guide for Oracle Internet Directory](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/dbimi&id=manage_pswd_verifiers) for more information.

  - For pluggable databases, you are no longer restricted to the default wallet location. The `WALLET_LOCATION` can point to a directory location of your choice.

    See [Wallet Location for Pluggable Databases](getting-started-with-enterprise-user-security.md) for more information.

  - A new initialization parameter, `WALLET_ROOT`, is introduced to specify the path to a directory containing the wallet location.

    See [Wallet Root for Pluggable Databases](getting-started-with-enterprise-user-security.md) for more information.

### Changes in Oracle Database 12c Release 2 (12.2.0.1)

The following are changes in Oracle Database Enterprise User Security Administrator's Guide for Oracle Database 12c Release 2 (12.2.0.1).

#### New Features

The following features are new in this release:

- Enterprise User Security 12c release 2 (12.2.0.1) includes the following new features:

  - The `okcreate` command-line utility to automate creation of the service principal keytab when deploying Enterprise User Security using Kerberos authentication.

    See [Set Up Active Directory to Interoperate with Oracle Client](integrating-enterprise-user-security-with-microsoft-active-directory.md) for more information about this feature.
