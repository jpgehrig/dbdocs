Enterprise User Security Manager (EUSM) is a command-line tool you can use to manage the Enterprise User Security (EUS) Configuration in the Oracle Internet Directory (OID) directory server.

The EUSM command-line tool sends data to and retrieves data from the Oracle Internet Directory (OID) directory server. You can use Oracle Enterprise Manager to administer enterprise users, enterprise domains, and enterprise roles stored in OID as described in [Oracle Enterprise Manager](configuration-and-administration-tools-overview.md). However, this becomes a cumbersome process if the entries are very large and the process cannot be automated. Hence, the use of this command-line tool becomes a requirement.

The file path of the EUSM command is:

    $ORACLE_HOME/bin

EUSM is a user friendly command-line tool. Entering `eusm` on the shell and pressing `Enter` or `Return`, prints all the commands that are supported. Also entering `eusm help <``command``>` or just `eusm <``command``>` and pressing `Enter` or `Return` prints the signature of a particular command supported by EUSM. Note that you must enter `eusm` in all lowercase characters.

Both EUSM commands and command-line options are not case sensitive.

Password credentials for the users: dbuser and ldap_user, and for the keystore can be stored in a client-side Oracle wallet in the external secure password store by providing information regarding the `<alias, username, ``password``>` for each one. See About Using a Secure External Password Store, where this is described in more detail. Examples for each of the EUSM commands show this usage.

This chapter contains descriptions of the EUSM commands listed by their group. Each description contains the following parts:

| Section     | Description                                                                                                                                                |
|:------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------|
| Term        | Describes the function of each term.                                                                                                                       |
| Syntax      | Shows how to enter the command and provides a brief description of the basic uses of the command.                                                          |
| Options     | Describes the function of each clause and option appearing in the syntax.                                                                                  |
| Usage Notes | Provides additional information on uses of the command and on how the command works.                                                                       |
| Examples    | Gives examples of the command using SSL port connectivity and not using SSL port connectivity to OID and using an Oracle wallet to store user credentials. |

This chapter includes the following topics:

- About Using a Secure External Password Store

- About SSL Port Connectivity through EUSM to OID

- Enterprise User Security Manager (EUSM) Command Summary

### 7.1 About Using a Secure External Password Store

If you want to use a secure external password store, then configure the Oracle wallet as described in the information that follows; otherwise, passwords can be provided interactively and you can skip this section.

Before you run the Enterprise User Security Manager (EUSM), configure a client-side Oracle wallet as a secure external password store so that your applications can use password credentials stored in the wallet to connect to databases. Storing database password credentials in a client-side Oracle wallet eliminates the need to embed passwords in application code, batch jobs, or scripts. This reduces the risk of exposing passwords in the clear in scripts and application code, and allows you to more easily manage password policies for user accounts without changing application code or scripts whenever passwords change.

See [Configuring a Client to Use the External Password Store](../dbseg/configuring-authentication.md) for steps to configure a client to use the external password store by using the `mkstore` command-line utility.

**Note:**

The external password store of the wallet is separate from the area where public key infrastructure (PKI) credentials are stored. Consequently, you cannot use Oracle Wallet Manager to manage credentials in the external password store of the wallet. Instead, use the command-line utility `mkstore` to manage these credentials.

Using the `mkstore CreateCredential` command, configure the following user credentials by providing information for `<alias, username, ``password``>`, in which you will be prompted to enter the password for each user.

- `dbalias``, dbuser, ``password`

- `ldap_alias``, ldap_user, ``password`

- `keystore_alias``, keystore, ``passowrd`

Configuring these user credentials allows you to use the following parameters on the EUSM command line:

- `dbalias=<db-password-alias> `

- `ldap_alias=<OID-user-password-alias>`

- `keystore_alias=<keystore-password-alias>`

EUSM command examples use the following wallet credential information for users: `dbuser`, `ldap_user`, and `keystore` that was provided for the alias name, user name, and password. The wallet location is specified as shown.

- `dbadmin1`, `sysman`, `password`

- `ldabadmin1`, `ldapman`, `password`

- `keystore1`, `keystore`, `password`

- `wallet_location=``/oracle/product/db_1/wallets`

EUSM command-line examples use the following entries on the command-line:

- `dbalias=dbadmin1`

- `ldap_alias=ldabadmin1`

- `keystore_alias=keystore1`

- `wallet_location=``/oracle/product/db_1/wallets`

After configuring the client-side wallet, enable auto-login for Oracle Wallets to allow the administrator running EUSM commands to access and perform these services without having to supply the necessary credentials.

**See Also:**

- [Managing the Secure External Password Store for Password Credentials](../dbseg/configuring-authentication.md) for more information about creating a client-side password store wallet to store alias, user name, and password credentials for users

- [About Using Auto Login for Oracle Wallets](using-oracle-wallet-manager.md) for information about enabling auto login for Oracle wallets that enables PKI-based access to services without requiring human intervention to supply the necessary user name passwords required to run EUSM

### 7.2 About SSL Port Connectivity through EUSM to OID

To enhance security, use the SSL Port connectivity option (`ldap_ssl_port=<OID ssl port>`) when connecting from Enterprise User Security Manager (EUSM) to Oracle Internet Directory (OID) directory server.

Using the SSL Port connectivity option (`ldap_ssl_port=<OID ssl port>`) assumes the environment where the OID directory server is set up supports the SSL port.

The following are additional parameters that must be given to EUSM to connect to the SSL port of the OID server:

- The `ldap_ssl_port` option takes the ssl port of the directory server (OID) as input from the EUSM command line.

- The `keystore=<path to PKCS12 format of keystore>` file path parameter takes the path to the PKCS12 format of the keystore (for example, `ewallet.p12` file) as input from the command line and the password is taken from the Oracle client-side wallet when the wallet is configured as a secure external password store or is taken interactively with the option `–K prompt for keystore password`.

#### Prerequisites

Prerequisites include the following:

- The client must have a keystore in PKCS12 format for example, ewallet.p12 file. This keystore file consists of a client private key certificate.

- The inputs for the passwords of keystore should also be given by the client.

- The client must have Java 2 SDK, v1.4 or any updated version that supports the current EUSM API.

### 7.3 Enterprise User Security Manager (EUSM) Command Summary

Enterprise User Security Manager (EUSM) commands are listed by group with links to its command page.

| Group of Commands                                                 | Command                        | Description                                                                       |
|:------------------------------------------------------------------|:-------------------------------|:----------------------------------------------------------------------------------|
| Manage Enterprise Domains                                         | listDomains                    | Lists the domains in the realm.                                                   |
| Manage Enterprise Domains                                         | createDomain                   | Creates a domain in the realm.                                                    |
| Manage Enterprise Domains                                         | deleteDomain                   | Deletes a domain from the realm.                                                  |
| Manage Enterprise Domains                                         | listDomainInfo                 | Lists the domain information.                                                     |
| Manage Domain Administrators                                      | addDomainAdmin                 | Adds a domain administrator.                                                      |
| Manage Domain Administrators                                      | listDomainAdmins               | Lists the domain administrators. The domain is taken as one of the inputs.        |
| Manage Domain Administrators                                      | removeDomainAdmin              | Removes a domain administrator                                                    |
| Manage Databases in an Existing Domain                            | addDatabase                    | Adds a database to the domain.                                                    |
| Manage Databases in an Existing Domain                            | removeDatabase                 | Removes a database from the domain.                                               |
| Manage Database Administrators                                    | addDBAdmin                     | Adds a database administrator.                                                    |
| Manage Database Administrators                                    | removeDBAdmin                  | Removes a database administrator.                                                 |
| Manage Database Administrators                                    | listDBAdmins                   | Lists the database administrators.                                                |
| Manage Database Administrators                                    | listDBInfo                     | Lists the database information.                                                   |
| Manage user-schema mappings                                       | createMapping                  | Creates the user and shared schema mapping.                                       |
| Manage user-schema mappings                                       | deleteMapping                  | Deletes a mapping.                                                                |
| Manage user-schema mappings                                       | listMappings                   | Lists the user and shared schema mappings.                                        |
| Enable or Disable Current User Database Links Usage in the Domain | setCulinkStatus                | Enables or disables the current user database-link usage in the domain.           |
| Setting Authentication Types                                      | setAuthTypes                   | Sets authentication types to be accepted for the users in the domain.             |
| Manage Enterprise Roles/Global Roles                              | createRole                     | Creates an enterprise role.                                                       |
| Manage Enterprise Roles/Global Roles                              | deleteRole                     | Deletes an enterprise role.                                                       |
| Manage Enterprise Roles/Global Roles                              | addGlobalRole                  | Adds a global role or administrative role to an enterprise role.                  |
| Manage Enterprise Roles/Global Roles                              | removeGlobalRole               | Removes a global role or administrative role from an enterprise role.             |
| Manage Enterprise Roles/Global Roles                              | grantRole                      | Grants an enterprise role.                                                        |
| Manage Enterprise Roles/Global Roles                              | revokeRole                     | Revokes an enterprise role.                                                       |
| Manage Enterprise Roles/Global Roles                              | listEnterpriseRoles            | Lists the enterprise roles.                                                       |
| Manage Enterprise Roles/Global Roles                              | listEnterpriseRolesOfUser      | Lists the enterprise roles of a user.                                             |
| Manage Enterprise Roles/Global Roles                              | listEnterpriseRoleInfo         | Lists enterprise role information.                                                |
| Manage Enterprise Roles/Global Roles                              | listGlobalRolesInDB            | Lists the global roles in the database.                                           |
| Manage Enterprise Roles/Global Roles                              | listSharedSchemasInDB          | Lists the shared schemas in the database.                                         |
| Manage Proxy Authentication                                       | createProxyPerm                | Creates a proxy permission object.                                                |
| Manage Proxy Authentication                                       | deleteProxyPerm                | Deletes a proxy permission object.                                                |
| Manage Proxy Authentication                                       | addTargetUser                  | Adds a target database user to the proxy permission object.                       |
| Manage Proxy Authentication                                       | removeTargetUser               | Removes a target database user from the proxy permission object.                  |
| Manage Proxy Authentication                                       | grantProxyPerm                 | Maps an enterprise user to the database user through the proxy permission object. |
| Manage Proxy Authentication                                       | revokeProxyPerm                | Revokes a proxy permission object.                                                |
| Manage Proxy Authentication                                       | listProxyPermissions           | Lists the proxy permissions. Input is the domain name.                            |
| Manage Proxy Authentication                                       | listProxyPermissionsOfUser     | Lists the proxy permissions for the user. Input is user distinguished name.       |
| Manage Proxy Authentication                                       | listProxyPermissionInfo        | Lists the proxy permission information.                                           |
| Manage Proxy Authentication                                       | listTargetUsersInDB            | Lists the target users in the database.                                           |
| Manage Database-OID Authentication Method                         | setDBOIDAuth                   | Sets the database-OID authentication method.                                      |
| Manage Database-OID Authentication Method                         | listDBOIDAuth                  | Lists the database-OID authentication method.                                     |
| Manage the list of the Password Accessible Domains                | addToPwdAccessibleDomains      | Adds a domain to the password accessible domains group in the realm.              |
| Manage the list of the Password Accessible Domains                | removeFromPwdAccessibleDomains | Removes a domain from the password accessible domains group in the realm.         |
| Manage the list of the Password Accessible Domains                | listPwdAccessibleDomains       | Lists the password accessible domains in the realm.                               |
| Display Realm Properties                                          | listRealmCommonAttr            | Lists the realm common attributes.                                                |
| App Context Namespace                                             | createAppCtxNamespace          | Adds a new namespace.                                                             |
| App Context Namespace                                             | listAppCtxNamespaces           | Lists the namespaces.                                                             |
| App Context Namespace                                             | deleteAppCtxNamespace          | Deletes a namespace.                                                              |
| App Context Attribute                                             | createAppCtxAttribute          | Adds a new attribute.                                                             |
| App Context Attribute                                             | listAppCtxAttributes           | Lists the attributes.                                                             |
| App Context Attribute                                             | deleteAppCtxAttribute          | Deletes an attribute.                                                             |
| App Context Attribute Value                                       | createAppCtxAttributeValue     | Adds a new attribute value.                                                       |
| App Context Attribute Value                                       | listAppCtxAttributeValues      | Lists the attribute values.                                                       |
| App Context Attribute Value                                       | deleteAppCtxAttributeValue     | Deletes an attribute value.                                                       |
| Manage App Context Users                                          | createAppCtxUsers              | Adds a new user for an attribute value.                                           |
| Manage App Context Users                                          | listAppCtxUsers                | Lists all users for an attribute value.                                           |
| Manage App Context Users                                          | deleteAppCtxUsers              | Deletes a user from an attribute value.                                           |
| Help                                                              | help \<command name\>          | Displays help for a command.                                                      |

#### Examples of EUSM Commands Use Options

Examples for EUSM commands use some of the following options and values, where values are used for example purposes only:

- proxy_permission=PROXY01

- domain_name=test_domain

- domain_name=OracleDefaultDomain — an enterprise domain

- realm_dn=dc=yy, dc=company,dc=com

- user_dn=cn=test_user,cn=Users,dc=yy,dc=company,dc=com

- database_name=dbtest1

- map_type=ENTRY — can be either ENTRY or SUBTREE

- map_dn=cn=test_user,cn=Users,dc=yy,dc=company,dc=com

- mapping_name=MAPPING01

- schema=test_user

- status=ENABLED — can be either ENABLED or DISABLED

- auth_type=SSL

- enterprise_role=ent_connect — enterprise role

- enterprise_role=ent_resource — global role

- global_role=global_resource

- global_role=global_connect

- dbuser=system — a privileged user

- db_alias=dbadmin1 — alias for dbuser credentials stored in an Oracle wallet

- dbconnect_string=zzzz10-yy.yy.company.com:1531:dbtest1

- target_user=PROXY_TEST

- namespace=ns1

- attribute_name=attr1

- attribute_value=val1

- ldap_host=xxxxx.zz.company.com — name of the OID server

- ldap_SSL_port=3131 — OID SSL (SASL) port used for OID connections; ports 3132 to 3141 or 13131 to 13141 can also be used

- keystore=/etc/myapp/keyStore — path to PKCS12 format of keystore; keystore location is administrator defined

- keystore_alias=keystore1 — alias for keystore credentials stored in an Oracle wallet

- ldap port =3060 — nonSSL (SASL) port used for OID connections; ports 3061 to 3070 or 13060 to 13070 can also be used

- ldap_user_dn=cn=orcladmin — OID administrator name

- ldap_alias=ldapadmin1 — alias for ldap_user credentials stored in an Oracle wallet

- wallet_location=/oracle/product/db_1/wallets — the wallet or secure external password store location

#### 7.3.1 createDomain

Creates a domain in the realm.

##### Syntax

    createDomain
         domain_name=<domain name>
         realm_dn=<DN of the realm>
         ldap_host=<OID host>
         ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>
         keystore=<path to keystore>
         keystore_alias=<keystore password alias>
         ldap_user_dn=<DN of OID user>
         ldap_alias=<OID user password alias>
         wallet_location=<wallet location>

##### Options

Each option must be prefixed with a space. Multiple options can be concatenated and prefixed with single space.

| Option                                                        | Description                                                                         |
|:--------------------------------------------------------------|:------------------------------------------------------------------------------------|
| `domain_name=<domain name>`                                   | Name of the domain.                                                                 |
| `realm_dn=<DN of the realm>`                                  | DN of the realm.                                                                    |
| `ldap_host=<OID host>`                                        | OID host.                                                                           |
| `ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>` | OID non ssl port or OID ssl port.                                                   |
| `keystore=<path to keystore>`                                 | Path to the keystore.                                                               |
| `keystore_alias=<keystore password alias>`                    | Keystore password taken from the Oracle wallet.                                     |
| `ldap_user_dn=<DN of OID user>`                               | DN of OID user which is used for authenticating and executing a command in the OID. |
| `ldap_alias=<OID user password alias> `                       | OID user password taken from the Oracle wallet.                                     |
| `wallet_location=<wallet location>`                           | Path to Oracle wallet when using the wallet.                                        |

##### Usage Notes

None.

##### Examples

Examples include creating a domain in the realm with and without SSL port connectivity to OID.

Example 7-1 Creating a Domain in the Realm with SSL Port Conectivity to OID and Using Passwords Stored in the Oracle Wallet

    eusm createDomain domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_ssl_port=3131 keystore=/etc/myapp/keyStore keystore_alias=keystore1 ldap_user_dn=cn=orcladmin ldap_alias=ldabadmin1 wallet_location=/oracle/product/db_1/wallets

Example 7-2 Creating a Domain in the Realm with SSL Port Conectivity to OID

    eusm createDomain domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_ssl_port=3131 keystore=/etc/myapp/keyStore ldap_user_dn=cn=orcladmin

Example 7-3 Creating a Domain in the Realm with non-SSL Port Conectivity to OID

    eusm createDomain domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3060 ldap_user_dn=cn=orcladmin

#### 7.3.2 deleteDomain

Deletes a domain from the realm.

##### Syntax

    deleteDomain
         domain_name=<domain name>
         realm_dn=<DN of the realm>
         ldap_host=<OID host>
         ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>
         keystore=<path to keystore>
         keystore_alias=<keystore password alias>
         ldap_user_dn=<DN of OID user>
         ldap_alias=<OID user password alias>
         wallet_location=<wallet location>

##### Options

Each option must be prefixed with a space. Multiple options can be concatenated and prefixed with single space.

| Option                                                        | Description                                                                         |
|:--------------------------------------------------------------|:------------------------------------------------------------------------------------|
| `domain_name=<domain name>`                                   | Name of the domain.                                                                 |
| `realm_dn=<DN of the realm> `                                 | DN of the realm.                                                                    |
| `ldap_host=<OID host>`                                        | OID host.                                                                           |
| `ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>` | OID non ssl port or OID ssl port.                                                   |
| `keystore=<path to keystore>`                                 | Path to the keystore.                                                               |
| `keystore_alias=<keystore password alias>`                    | Keystore password taken from the Oracle wallet.                                     |
| `ldap_port=<OID non ssl port> `                               | OID non ssl port.                                                                   |
| `ldap_user_dn=<DN of OID user>`                               | DN of OID user which is used for authenticating and executing a command in the OID. |
| `ldap_alias=<OID user password alias>`                        | OID user password taken from the Oracle wallet.                                     |
| `wallet_location=<wallet location>`                           | Path to Oracle wallet when using the wallet.                                        |

##### Usage Notes

None.

##### Examples

Examples include deleting a domain in the realm with and without SSL port connectivity to OID.

Example 7-4 Deleting a Domain from the Realm with SSL Port Conectivity to OID and Using Passwords Stored in the Oracle Wallet

    eusm deleteDomain domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_ssl_port=3131 keystore=/etc/myapp/keyStore keystore_alias=keystore1 ldap_user_dn=cn=orcladmin ldap_alias=ldabadmin1 wallet_location=/oracle/product/db_1/wallets

Example 7-5 Deleting a Domain from the Realm with SSL Port Conectivity to OID

    eusm deleteDomain domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_ssl_port=3131 keystore=/etc/myapp/keyStore ldap_user_dn=cn=orcladmin

Example 7-6 Deleting a Domain from the Realm with non-SSL Port Conectivity to OID

    eusm deleteDomain domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3060 ldap_user_dn=cn=orcladmin

#### 7.3.3 listDomains

Lists the domains in the realm.

##### Syntax

    listDomains
         realm_dn=<DN of the realm>
         ldap_host=<OID host>
         ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>
         keystore=<path to keystore>
         keystore_alias=<keystore password alias>
         ldap_user_dn=<DN of OID user>
         ldap_alias=<OID user password alias>
         wallet_location=<wallet location>

##### Options

Each option must be prefixed with a space. Multiple options can be concatenated and prefixed with single space.

| Option                                                        | Description                                                                         |
|:--------------------------------------------------------------|:------------------------------------------------------------------------------------|
| `realm_dn=<DN of the realm> `                                 | DN of the realm.                                                                    |
| `ldap_host=<OID host>`                                        | OID host.                                                                           |
| `ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>` | OID non ssl port or OID ssl port.                                                   |
| `keystore=<path to keystore>`                                 | Path to the keystore.                                                               |
| `keystore_alias=<keystore password alias>`                    | Keystore password taken from the Oracle wallet.                                     |
| `ldap_user_dn=<DN of OID user>`                               | DN of OID user which is used for authenticating and executing a command in the OID. |
| `ldap_alias=<OID user password alias>`                        | OID user password taken from the Oracle wallet.                                     |
| `wallet_location=<wallet location>`                           | Path to Oracle wallet when using the wallet.                                        |

##### Usage Notes

None.

##### Examples

Examples include listing the domains in the realm with and without SSL port connectivity to OID.

Example 7-7 Lists the domains in the realm with SSL Port Conectivity to OID and Using Passwords Stored in the Oracle Wallet

    eusm listDomains realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_ssl_port=3131 keystore=/etc/myapp/keyStore keystore_alias=keystore1 ldap_user_dn=cn=orcladmin ldap_alias=ldabadmin1 wallet_location=/oracle/product/db_1/wallets

Example 7-8 Lists the domains in the realm with SSL Port Conectivity to OID

    eusm listDomains realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_ssl_port=3131 keystore=/etc/myapp/keyStore ldap_user_dn=cn=orcladmin

Example 7-9 Lists the domains in the realm with non-SSL Port Conectivity to OID

    eusm listDomains realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3060 ldap_user_dn=cn=orcladmin

#### 7.3.4 listDomainInfo

List domain information.

##### Syntax

    listDomainInfo
         domain_name=<domain name>
         realm_dn=<DN of the realm>
         ldap_host=<OID host>
         ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>
         keystore=<path to keystore>
         keystore_alias=<keystore password alias>
         ldap_user_dn=<DN of OID user>
         ldap_alias=<OID user password alias>
         wallet_location=<wallet location>

##### Options

Each option must be prefixed with a space. Multiple options can be concatenated and prefixed with single space.

| Option                                                        | Description                                                                         |
|:--------------------------------------------------------------|:------------------------------------------------------------------------------------|
| `domain_name=<domain name>`                                   | Name of the domain.                                                                 |
| `realm_dn=<DN of the realm> `                                 | DN of the realm.                                                                    |
| `ldap_host=<OID host>`                                        | OID host.                                                                           |
| `ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>` | OID non ssl port or OID ssl port.                                                   |
| `keystore=<path to keystore>`                                 | Path to the keystore.                                                               |
| `keystore_alias=<keystore password alias>`                    | Keystore password taken from the Oracle wallet.                                     |
| `ldap_user_dn=<DN of OID user>`                               | DN of OID user which is used for authenticating and executing a command in the OID. |
| `ldap_alias=<OID user password alias>`                        | OID user password taken from the Oracle wallet.                                     |
| `wallet_location=<wallet location>`                           | Path to Oracle wallet when using the wallet.                                        |

##### Usage Notes

None.

##### Examples

Examples include listing the domain information with and without SSL port connectivity to OID.

Example 7-10 Listing the Domain Information with SSL Port Conectivity to OID and Using Passwords Stored in the Oracle Wallet

    eusm listDomainInfo domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_ssl_port=3131 keystore=/etc/myapp/keyStore keystore_alias=keystore1 ldap_user_dn=cn=orcladmin ldap_alias=ldabadmin1 wallet_location=/oracle/product/db_1/wallets

Example 7-11 Listing the Domain Information with SSL Port Conectivity to OID

    eusm listDomainInfo domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_ssl_port=3131 keystore=/etc/myapp/keyStore ldap_user_dn=cn=orcladmin

Example 7-12 Listing the Domain Information with non-SSL Port Conectivity to OID

    eusm listDomainInfo domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3060 ldap_user_dn=cn=orcladmin

#### 7.3.5 addDomainAdmin

Adds a domain administrator.

##### Syntax

    addDomainAdmin
         domain_name=<domain name>
         realm_dn=<DN of the realm>
         user_dn=<user DN>
         ldap_host=<OID host>
         ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>
         keystore=<path to keystore>
         keystore_alias=<keystore password alias>
         ldap_user_dn=<DN of OID user>
         ldap_alias=<OID user password alias>
         wallet_location=<wallet location>

##### Options

Each option must be prefixed with a space. Multiple options can be concatenated and prefixed with single space.

| Option                                                        | Description                                                                                            |
|:--------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------|
| `domain_name=<domain name>`                                   | Name of the domain.                                                                                    |
| `realm_dn=<DN of the realm> `                                 | DN of the realm.                                                                                       |
| `user_dn=<user DN>`                                           | DN of the user. For example, the user to be added as database administrator in the command addDBAdmin. |
| `ldap_host=<OID host>`                                        | OID host.                                                                                              |
| `ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>` | OID non ssl port or OID ssl port.                                                                      |
| `keystore=<path to keystore>`                                 | Path to the keystore.                                                                                  |
| `keystore_alias=<keystore password alias>`                    | Keystore password taken from the Oracle wallet.                                                        |
| `ldap_user_dn=<DN of OID user>`                               | DN of OID user which is used for authenticating and executing a command in the OID.                    |
| `ldap_alias=<OID user password alias>`                        | OID user password taken from the Oracle wallet.                                                        |
| `wallet_location=<wallet location>`                           | Path to Oracle wallet when using the wallet.                                                           |

##### Usage Notes

None.

##### Examples

Examples include adding a domain administrator with and without SSL port connectivity to OID.

Example 7-13 Adding a Domain Administrator with SSL Port Conectivity to OID and Using Passwords Stored in the Oracle Wallet

    eusm addDomainAdmin domain_name=test_domain user_dn=cn=test_user,cn=Users,dc=yy,dc=company,dc=com realm_dn=dc=yy, dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_ssl_port=3131 keystore=/etc/myapp/keyStore keystore_alias=keystore1 ldap_user_dn=cn=orcladmin ldap_alias=ldabadmin1 wallet_location=/oracle/product/db_1/wallets

Example 7-14 Adding a Domain Administrator with SSL Port Conectivity to OID

    eusm addDomainAdmin domain_name=test_domain user_dn=cn=test_user,cn=Users,dc=yy,dc=company,dc=com realm_dn=dc=yy, dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_ssl_port=3131 keystore=/etc/myapp/keyStore ldap_user_dn=cn=orcladmin

Example 7-15 Adding a Domain Administrator with non-SSL Port Conectivity to OID

    eusm addDomainAdmin domain_name=test_domain user_dn=cn=test_user,cn=Users,dc=yy,dc=company,dc=com realm_dn=dc=yy, dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3060 ldap_user_dn=cn=orcladmin

#### 7.3.6 removeDomainAdmin

Removes a domain administrator.

##### Syntax

    removeDomainAdmin
         domain_name=<domain name>
         realm_dn=<DN of the realm>
         user_dn=<user DN>
         ldap_host=<OID host>
         ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>
         keystore=<path to keystore>
         keystore_alias=<keystore password alias>
         ldap_user_dn=<DN of OID user>
         ldap_alias=<OID user password alias>
         wallet_location=<wallet location>

##### Options

Each option must be prefixed with a space. Multiple options can be concatenated and prefixed with single space.

| Option                                                        | Description                                                                                                 |
|:--------------------------------------------------------------|:------------------------------------------------------------------------------------------------------------|
| `domain_name=<domain name>`                                   | Name of the domain.                                                                                         |
| `realm_dn=<DN of the realm> `                                 | DN of the realm.                                                                                            |
| `user_dn=<user DN>`                                           | DN of the user. For example, the user to be removed as database administrator in the command removeDBAdmin. |
| `ldap_host=<OID host>`                                        | OID host.                                                                                                   |
| `ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>` | OID non ssl port or OID ssl port.                                                                           |
| `keystore=<path to keystore>`                                 | Path to the keystore.                                                                                       |
| `keystore_alias=<keystore password alias>`                    | Keystore password taken from the Oracle wallet.                                                             |
| `ldap_user_dn=<DN of OID user>`                               | DN of OID user which is used for authenticating and executing a command in the OID.                         |
| `ldap_alias=<OID user password alias>`                        | OID user password taken from the Oracle wallet.                                                             |
| `wallet_location=<wallet location>`                           | Path to Oracle wallet when using the wallet.                                                                |

##### Usage Notes

None.

##### Examples

Examples include removing a domain administrator with and without SSL port connectivity to OID.

Example 7-16 Removing a Domain Administrator with SSL Port Conectivity to OID and Using Passwords Stored in the Oracle Wallet

    eusm removeDomainAdmin domain_name=test_domain user_dn=cn=test_user,cn=Users,dc=yy,dc=company,dc=com realm_dn=dc=yy, dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_ssl_port=3131 keystore=/etc/myapp/keyStore keystore_alias=keystore1 ldap_user_dn=cn=orcladmin ldap_alias=ldabadmin1 wallet_location=/oracle/product/db_1/wallets

Example 7-17 Removing a Domain Administrator with SSL Port Conectivity to OID

    eusm removeDomainAdmin domain_name=test_domain user_dn=cn=test_user,cn=Users,dc=yy,dc=company,dc=com realm_dn=dc=yy, dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_ssl_port=3131 keystore=/etc/myapp/keyStore ldap_user_dn=cn=orcladmin

Example 7-18 Removing a Domain Administrator with non-SSL Port Conectivity to OID

    eusm removeDomainAdmin domain_name=test_domain user_dn=cn=test_user,cn=Users,dc=yy,dc=company,dc=com realm_dn=dc=yy, dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3060 ldap_user_dn=cn=orcladmin

#### 7.3.7 listDomainAdmins

Lists the domain administrators. The domain is taken as one of the inputs.

##### Syntax

    listDomainAdmins
         domain_name=<domain name>
         realm_dn=<DN of the realm>
         ldap_host=<OID host>
         ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>
         keystore=<path to keystore>
         keystore_alias=<keystore password alias>
         ldap_user_dn=<DN of OID user>
         ldap_alias=<OID user password alias>
         wallet_location=<wallet location>

##### Options

Each option must be prefixed with a space. Multiple options can be concatenated and prefixed with single space.

| Option                                                        | Description                                                                         |
|:--------------------------------------------------------------|:------------------------------------------------------------------------------------|
| `domain_name=<domain name>`                                   | Name of the domain.                                                                 |
| `realm_dn=<DN of the realm> `                                 | DN of the realm.                                                                    |
| `ldap_host=<OID host>`                                        | OID host.                                                                           |
| `ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>` | OID non ssl port or OID ssl port.                                                   |
| `keystore=<path to keystore>`                                 | Path to the keystore.                                                               |
| `keystore_alias=<keystore password alias>`                    | Keystore password taken from the Oracle wallet.                                     |
| `ldap_user_dn=<DN of OID user>`                               | DN of OID user which is used for authenticating and executing a command in the OID. |
| `ldap_alias=<OID user password alias>`                        | OID user password taken from the Oracle wallet.                                     |
| `wallet_location=<wallet location>`                           | Path to Oracle wallet when using the wallet.                                        |

##### Usage Notes

None.

##### Examples

Examples include listing domain administrators with and without SSL port connectivity to OID.

Example 7-19 Listing the Domain Administrators with SSL Port Conectivity to OID and Using Passwords Stored in the Oracle Wallet

    eusm listDomainAdmins domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_ssl_port=3131 keystore=/etc/myapp/keyStore keystore_alias=keystore1 ldap_user_dn=cn=orcladmin ldap_alias=ldabadmin1 wallet_location=/oracle/product/db_1/wallets

Example 7-20 Listing the Domain Administrators with SSL Port Conectivity to OID

    eusm listDomainAdmins domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_ssl_port=3131 keystore=/etc/myapp/keyStore ldap_user_dn=cn=orcladmin

Example 7-21 Listing the Domain Administrators with non-SSL Port Conectivity to OID

    eusm listDomainAdmins domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3060 ldap_user_dn=cn=orcladmin

#### 7.3.8 addDatabase

Adds a database to the domain.

##### Syntax

    addDatabase
         domain_name=<domain name>
         realm_dn=<DN of the realm>
         database_name=<Database name>
         ldap_host=<OID host>
         ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>
         keystore=<path to keystore>
         keystore_alias=<keystore password alias>
         ldap_user_dn=<DN of OID user>
         ldap_alias=<OID user password alias>
         wallet_location=<wallet location>

##### Options

Each option must be prefixed with a space. Multiple options can be concatenated and prefixed with single space.

| Option                                                        | Description                                                                         |
|:--------------------------------------------------------------|:------------------------------------------------------------------------------------|
| `domain_name=<domain name>`                                   | Name of the domain.                                                                 |
| `realm_dn=<DN of the realm> `                                 | DN of the realm.                                                                    |
| `database_name=<Database name>`                               | Database name.                                                                      |
| `ldap_host=<OID host>`                                        | OID host.                                                                           |
| `ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>` | OID non ssl port or OID ssl port.                                                   |
| `keystore=<path to keystore>`                                 | Path to the keystore.                                                               |
| `keystore_alias=<keystore password alias>`                    | Keystore password taken from the Oracle wallet.                                     |
| `ldap_user_dn=<DN of OID user>`                               | DN of OID user which is used for authenticating and executing a command in the OID. |
| `ldap_alias=<OID user password alias>`                        | OID user password taken from the Oracle wallet.                                     |
| `wallet_location=<wallet location>`                           | Path to Oracle wallet when using the wallet.                                        |

##### Usage Notes

None.

##### Examples

Examples include adding a database to the domain with and without SSL port connectivity to OID.

Example 7-22 Adding a Database to the Domain with SSL Port Conectivity to OID and Using Passwords Stored in the Oracle Wallet

    eusm addDatabase domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com database_name=dbtest1 ldap_host=xxxxx.zz.company.com ldap_ssl_port=3131 keystore=/etc/myapp/keyStore keystore_alias=keystore1 ldap_user_dn=cn=orcladmin ldap_alias=ldabadmin1 wallet_location=/oracle/product/db_1/wallets

Example 7-23 Adding a Database to the Domain with SSL Port Conectivity to OID

    eusm addDatabase domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com database_name=dbtest1 ldap_host=xxxxx.zz.company.com ldap_ssl_port=3131 keystore=/etc/myapp/keyStore ldap_user_dn=cn=orcladmin

Example 7-24 Adding a Database to the Domain with non-SSL Port Conectivity to OID

    eusm addDatabase domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com database_name=dbtest1 ldap_host=xxxxx.zz.company.com ldap_port=3060 ldap_user_dn=cn=orcladmin

#### 7.3.9 removeDatabase

Removes a database from the domain.

##### Syntax

    removeDatabase
         domain_name=<domain name>
         realm_dn=<DN of the realm>
         database_name=<Database name>
         ldap_host=<OID host>
         ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>
         keystore=<path to keystore>
         keystore_alias=<keystore password alias>
         ldap_user_dn=<DN of OID user>
         ldap_alias=<OID user password alias>
         wallet_location=<wallet location>

##### Options

Each option must be prefixed with a space. Multiple options can be concatenated and prefixed with single space.

| Option                                                        | Description                                                                          |
|:--------------------------------------------------------------|:-------------------------------------------------------------------------------------|
| `domain_name=<domain name>`                                   | Name of the domain.                                                                  |
| `realm_dn=<DN of the realm> `                                 | DN of the realm.                                                                     |
| `database_name=<Database name>`                               | Database name.                                                                       |
| `ldap_host=<OID host>`                                        | OID host.                                                                            |
| `ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>` | OID non ssl port or OID ssl port.                                                    |
| `keystore=<path to keystore>`                                 | Path to the keystore.                                                                |
| `keystore_alias=<keystore password alias>`                    | Keystore password from the Oracle wallet.                                            |
| `ldap_user_dn=<DN of OID user>`                               | DN of OID user which is used for authenticating and  executing a command in the OID. |
| `ldap_alias=<OID user password alias>`                        | OID user password taken from the Oracle wallet.                                      |
| `wallet_location=<wallet location>`                           | Path to Oracle wallet when using the wallet.                                         |

##### Usage Notes

None.

##### Examples

Examples include removing a database from the domain with and without SSL port connectivity to OID.

Example 7-25 Removing a Database from the Domain with SSL Port Conectivity to OID and Using Passwords Stored in the Oracle Wallet

    eusm removeDatabase domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com database_name=dbtest1 ldap_host=xxxxx.zz.company.com ldap_ssl_port=3131 keystore=/etc/myapp/keyStore keystore_alias=keystore1 ldap_user_dn=cn=orcladmin ldap_alias=ldabadmin1 wallet_location=/oracle/product/db_1/wallets

Example 7-26 Removing a Database from the Domain with SSL Port Conectivity to OID

    eusm removeDatabase domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com database_name=dbtest1 ldap_host=xxxxx.zz.company.com ldap_ssl_port=3131 keystore=/etc/myapp/keyStore ldap_user_dn=cn=orcladmin

Example 7-27 Removing a Database from the Domain with non-SSL Port Conectivity to OID

    eusm removeDatabase domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com database_name=dbtest1 ldap_host=xxxxx.zz.company.com ldap_port=3060 ldap_user_dn=cn=orcladmin

#### 7.3.10 addDBAdmin

Adds a database administrator.

##### Syntax

    addDBAdmin
         realm_dn=<DN of the realm>
         database_name=<Database name>
         user_dn=<Distinguished name of the user>
         ldap_host=<OID host>
         ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>
         keystore=<path to keystore>
         keystore_alias=<keystore password alias>
         ldap_user_dn=<DN of OID user>
         ldap_alias=<OID user password alias>
         wallet_location=<wallet location>

##### Options

Each option must be prefixed with a space. Multiple options can be concatenated and prefixed with single space.

| Option                                                        | Description                                                                                            |
|:--------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------|
| `realm_dn=<DN of the realm> `                                 | DN of the realm.                                                                                       |
| `database_name=<Database name>`                               | Database name.                                                                                         |
| `user_dn=<user DN>`                                           | DN of the user. For example, the user to be added as database administrator in the command addDBAdmin. |
| `ldap_host=<OID host>`                                        | OID host.                                                                                              |
| `ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>` | OID non ssl port or OID ssl port.                                                                      |
| `keystore=<path to keystore>`                                 | Path to the keystore.                                                                                  |
| `keystore_alias=<keystore password alias>`                    | Keystore password taken from the Oracle wallet.                                                        |
| `ldap_user_dn=<DN of OID user>`                               | DN of OID user which is used for authenticating and  executing a command in the OID.                   |
| `ldap_alias=<OID user password alias> `                       | OID user password taken from the Oracle wallet.                                                        |
| `wallet_location=<wallet location>`                           | Path to Oracle wallet when using the wallet.                                                           |

##### Usage Notes

None.

##### Examples

Examples include adding a database administrator with and without SSL port connectivity to OID.

Example 7-28 Adding a Database Administrator with SSL Port Conectivity to OID and Using Passwords Stored in the Oracle Wallet

    eusm addDBAdmin realm_dn=dc=yy,dc=company,dc=com database_name=dbtest1 user_dn=cn=test_user,cn=Users,dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_ssl_port=3131 keystore=/etc/myapp/keyStore keystore_alias=keystore1 ldap_user_dn=cn=orcladmin ldap_alias=ldabadmin1 wallet_location=/oracle/product/db_1/wallets

Example 7-29 Adding a Database Administrator with SSL Port Conectivity to OID

    eusm addDBAdmin realm_dn=dc=yy,dc=company,dc=com database_name=dbtest1 user_dn=cn=test_user,cn=Users,dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_ssl_port=3131 keystore=/etc/myapp/keyStore ldap_user_dn=cn=orcladmin

Example 7-30 Adding a Database Administrator with non-SSL Port Conectivity to OID

    eusm addDBAdmin realm_dn=dc=yy,dc=company,dc=com database_name=dbtest1 user_dn=cn=test_user,cn=Users,dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3060 ldap_user_dn=cn=orcladmin

#### 7.3.11 listDBAdmins

Lists the database administrators.

##### Syntax

    listDBAdmins
         realm_dn=<DN of the realm>
         database_name=<Database name>
         ldap_host=<OID host>
         ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>
         keystore=<path to keystore>
         keystore_alias=<keystore password alias>
         ldap_user_dn=<DN of OID user>
         ldap_alias=<OID user password alias>
         wallet_location=<wallet location>

##### Options

Each option must be prefixed with a space. Multiple options can be concatenated and prefixed with single space.

| Option                                                        | Description                                                                         |
|:--------------------------------------------------------------|:------------------------------------------------------------------------------------|
| `realm_dn=<DN of the realm> `                                 | DN of the realm.                                                                    |
| `database_name=<Database name>`                               | Database name.                                                                      |
| `ldap_host=<OID host>`                                        | OID host.                                                                           |
| `ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>` | OID non ssl port or OID ssl port.                                                   |
| `keystore=<path to keystore>`                                 | Path to the keystore.                                                               |
| `keystore_alias=<keystore password alias>`                    | Keystore password taken from the Oracle wallet.                                     |
| `ldap_user_dn=<DN of OID user>`                               | DN of OID user which is used for authenticating and executing a command in the OID. |
| `ldap_alias=<OID user password alias>`                        | OID user password taken from the Oracle wallet.                                     |
| `wallet_location=<wallet location>`                           | Path to Oracle wallet when using the wallet.                                        |

##### Usage Notes

None.

##### Examples

Examples include listing the database administrators with and without SSL port connectivity to OID.

Example 7-31 Listing the Database Administrators with SSL Port Conectivity to OID and Using Passwords Stored in the Oracle Wallet

    eusm listDBAdmins realm_dn=dc=yy,dc=company,dc=com database_name=dbtest1 ldap_host=xxxxx.zz.company.com ldap_ssl_port=3131 keystore=/etc/myapp/keyStore keystore_alias=keystore1 ldap_user_dn=cn=orcladmin ldap_alias=ldabadmin1 wallet_location=/oracle/product/db_1/wallets

Example 7-32 Listing the Database Administrators with SSL Port Conectivity to OID

    eusm listDBAdmins realm_dn=dc=yy,dc=company,dc=com database_name=dbtest1 ldap_host=xxxxx.zz.company.com ldap_ssl_port=3131 keystore=/etc/myapp/keyStore ldap_user_dn=cn=orcladmin

Example 7-33 Listing the Database Administrators with non-SSL Port Conectivity to OID

    eusm listDBAdmins realm_dn=dc=yy,dc=company,dc=com database_name=dbtest1 ldap_host=xxxxx.zz.company.com ldap_port=3060 ldap_user_dn=cn=orcladmin

#### 7.3.12 listDBInfo

Lists the database information.

##### Syntax

    listDBInfo
         realm_dn=<DN of the realm>
         database_name=<Database name>
         ldap_host=<OID host>
         ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>
         keystore=<path to keystore>
         keystore_alias=<keystore password alias>
         ldap_user_dn=<DN of OID user>
         ldap_alias=<OID user password alias>
         wallet_location=<wallet location>

##### Options

Each option must be prefixed with a space. Multiple options can be concatenated and prefixed with single space.

| Option                                                        | Description                                                                         |
|:--------------------------------------------------------------|:------------------------------------------------------------------------------------|
| `realm_dn=<DN of the realm> `                                 | DN of the realm.                                                                    |
| `database_name=<Database name>`                               | Database name.                                                                      |
| `ldap_host=<OID host>`                                        | OID host.                                                                           |
| `ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>` | OID non ssl port or OID ssl port.                                                   |
| `keystore=<path to keystore>`                                 | Path to the keystore.                                                               |
| `keystore_alias=<keystore password alias>`                    | Keystore password taken from the Oracle wallet.                                     |
| `ldap_user_dn=<DN of OID user>`                               | DN of OID user which is used for authenticating and executing a command in the OID. |
| `ldap_alias=<OID user password alias>`                        | OID user password taken from the Oracle wallet.                                     |
| `wallet_location=<wallet location>`                           | Path to Oracle wallet when using the wallet.                                        |

##### Usage Notes

None.

##### Examples

Examples include listing the database information with and without SSL port connectivity to OID.

Example 7-34 Lists the Database Information with SSL Port Conectivity to OID and Using Passwords Stored in the Oracle Wallet

    eusm listDBInfo realm_dn=dc=yy,dc=company,dc=com database_name=dbtest1 ldap_host=xxxxx.zz.company.com ldap_ssl_port=3131 keystore=/etc/myapp/keyStore keystore_alias=keystore1 ldap_user_dn=cn=orcladmin ldap_alias=ldabadmin1 wallet_location=/oracle/product/db_1/wallets

Example 7-35 Lists the Database Information with SSL Port Conectivity to OID

    eusm listDBInfo realm_dn=dc=yy,dc=company,dc=com database_name=dbtest1 ldap_host=xxxxx.zz.company.com ldap_ssl_port=3131 keystore=/etc/myapp/keyStore ldap_user_dn=cn=orcladmin

Example 7-36 Lists the Database Information with non-SSL Port Conectivity to OID

    eusm listDBInfo realm_dn=dc=yy,dc=company,dc=com database_name=dbtest1 ldap_host=xxxxx.zz.company.com ldap_port=3060 ldap_user_dn=cn=orcladmin

#### 7.3.13 removeDBAdmin

Removes a database administrator.

##### Syntax

    removeDBAdmin
         realm_dn=<DN of the realm>
         database_name=<Database name>
         user_dn=<Distinguished name of the user>
         ldap_host=<OID host>
         ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>
         keystore=<path to keystore>
         keystore_alias=<keystore password alias>
         ldap_user_dn=<DN of OID user>
         ldap_alias=<OID user password alias>
         wallet_location=<wallet location>

##### Options

Each option must be prefixed with a space. Multiple options can be concatenated and prefixed with single space.

| Option                                                        | Description                                                                                            |
|:--------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------|
| `realm_dn=<DN of the realm> `                                 | DN of the realm.                                                                                       |
| `database_name=<Database name>`                               | Database name.                                                                                         |
| `user_dn=<user DN>`                                           | DN of the user. For example, the user to be added as database administrator in the command addDBAdmin. |
| `ldap_host=<OID host>`                                        | OID host.                                                                                              |
| `ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>` | OID non ssl port or OID ssl port.                                                                      |
| `keystore=<path to keystore>`                                 | Path to the keystore.                                                                                  |
| `keystore_alias=<keystore password alias>`                    | Keystore password taken from the Oracle wallet.                                                        |
| `ldap_user_dn=<DN of OID user>`                               | DN of OID user which is used for authenticating and executing a command in the OID.                    |
| `ldap_alias=<OID user password alias>`                        | OID user password taken from the Oracle wallet.                                                        |
| `wallet_location=<wallet location>`                           | Path to Oracle wallet when using the wallet.                                                           |

##### Usage Notes

None.

##### Examples

Examples include removing a database administrator with and without SSL port connectivity to OID.

Example 7-37 Removing a Database Administrator with SSL Port Conectivity to OID and Using Passwords Stored in the Oracle Wallet

    eusm removeDBAdmin realm_dn=dc=yy,dc=company,dc=com database_name=dbtest1 user_dn=cn=test_user,cn=Users,dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_ssl_port=3131 keystore=/etc/myapp/keyStore keystore_alias=keystore1 ldap_user_dn=cn=orcladmin ldap_alias=ldabadmin1 wallet_location=/oracle/product/db_1/wallets

Example 7-38 Removing a Database Administrator with SSL Port Conectivity to OID

    eusm removeDBAdmin realm_dn=dc=yy,dc=company,dc=com database_name=dbtest1 user_dn=cn=test_user,cn=Users,dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_ssl_port=3131 keystore=/etc/myapp/keyStore ldap_user_dn=cn=orcladmin

Example 7-39 Removing a Database Administrator with non-SSL Port Conectivity to OID

    eusm removeDBAdmin realm_dn=dc=yy,dc=company,dc=com database_name=dbtest1 user_dn=cn=test_user,cn=Users,dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3060 ldap_user_dn=cn=orcladmin

#### 7.3.14 createMapping

Creates the user and shared schema mapping.

##### Syntax

    createMapping
        [domain_name=<domain name>]
        [database_name=<database name>]
         realm_dn=<DN of the realm>
         map_type=<mapping type ENTRY/SUBTREE>
         map_dn=<DN which is being mapped to schema>
         schema=<database schema>
         ldap_host=<OID host>
         ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>
         keystore=<path to keystore>
         keystore_alias=<keystore password alias>
         ldap_user_dn=<DN of OID user>
         ldap_alias=<OID user password alias>
         wallet_location=<wallet location>

##### Options

Each option must be prefixed with a space. Multiple options can be concatenated and prefixed with single space.

| Option                                                        | Description                                                                         |
|:--------------------------------------------------------------|:------------------------------------------------------------------------------------|
| `[domain_name=<domain name>]`                                 | Name of the domain.                                                                 |
| `[database_name=<database name>]`                             | Database name.                                                                      |
| `realm_dn=<DN of the realm>`                                  | DN of the realm.                                                                    |
| `map_type=<mapping type ENTRY/SUBTREE>`                       | Type of mapping ENTRY/SUBTREE.                                                      |
| `map_dn=<DN which is being mapped to schema> `                | DN that is being mapped to the schema.                                              |
| `schema=<database schema>`                                    | Database schema.                                                                    |
| `ldap_host=<OID host>`                                        | OID host.                                                                           |
| `ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>` | OID non ssl port or OID ssl port.                                                   |
| `keystore=<path to keystore>`                                 | Path to the keystore.                                                               |
| `keystore_alias=<keystore password alias>`                    | Keystore password taken from the Oracle wallet.                                     |
| `ldap_user_dn=<DN of OID user>`                               | DN of OID user which is used for authenticating and executing a command in the OID. |
| `ldap_alias=<OID user password alias>`                        | OID user password taken from the Oracle wallet.                                     |
| `wallet_location=<wallet location>`                           | Path to Oracle wallet when using the wallet.                                        |

##### Usage Notes

None.

##### Examples

Examples include creating the user or shared schema mapping with and without SSL port connectivity to OID.

Example 7-40 Creating the User or Shared Schema Mapping with SSL Port Conectivity to OID and Using Passwords Stored in the Oracle Wallet

    eusm createMapping database_name=dbtest1 realm_dn=dc=yy,dc=company,dc=com map_type=ENTRY map_dn=cn=test_user,cn=Users,dc=yy,dc=company,dc=com schema=test_user ldap_host=xxxxx.zz.company.com ldap_ssl_port=3131 keystore=/etc/myapp/keyStore keystore_alias=keystore1 ldap_user_dn=cn=orcladmin ldap_alias=ldabadmin1 wallet_location=/oracle/product/db_1/wallets

Example 7-41 Creating the User or Shared Schema Mapping with SSL Port Conectivity to OID

    eusm createMapping database_name=dbtest1 realm_dn=dc=yy,dc=company,dc=com map_type=ENTRY map_dn=cn=test_user,cn=Users,dc=yy,dc=company,dc=com schema=test_user ldap_host=xxxxx.zz.company.com ldap_ssl_port=3131 keystore=/etc/myapp/keyStore ldap_user_dn=cn=orcladmin

Example 7-42 Creating the User or Shared Schema Mapping with non-SSL Port Conectivity to OID

    eusm createMapping database_name=dbtest1 realm_dn=dc=yy,dc=company,dc=com map_type=ENTRY map_dn=cn=test_user,cn=Users,dc=yy,dc=company,dc=com schema=test_user ldap_host=xxxxx.zz.company.com ldap_port=3060 ldap_user_dn=cn=orcladmin

#### 7.3.15 deleteMapping

Deletes a mapping.

##### Syntax

    deleteMapping
        [domain_name=<domain name>]
        [database_name=<database name>]
         realm_dn=<DN of the realm>
         mapping_name=<Name of mapping>
         ldap_host=<OID host>
         ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>
         keystore=<path to keystore>
         keystore_alias=<keystore password alias>
         ldap_user_dn=<DN of OID user>
         ldap_alias=<OID user password alias>
         wallet_location=<wallet location>

##### Options

Each option must be prefixed with a space. Multiple options can be concatenated and prefixed with single space.

| Option                                                        | Description                                                                         |
|:--------------------------------------------------------------|:------------------------------------------------------------------------------------|
| `[domain_name=<domain name>]`                                 | Name of the domain.                                                                 |
| `[database_name=<database name>]`                             | Database name.                                                                      |
| `realm_dn=<DN of the realm>`                                  | DN of the realm.                                                                    |
| `mapping_name=<Name of mapping>`                              | Name of the mapping.                                                                |
| `ldap_host=<OID host>`                                        | OID host.                                                                           |
| `ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>` | OID non ssl port or OID ssl port.                                                   |
| `keystore=<path to keystore>`                                 | Path to the keystore.                                                               |
| `keystore_alias=<keystore password alias>`                    | Keystore password taken from the Oracle wallet.                                     |
| `ldap_user_dn=<DN of OID user>`                               | DN of OID user which is used for authenticating and executing a command in the OID. |
| `ldap_alias=<OID user password alias>`                        | OID user password taken from the Oracle wallet.                                     |
| `wallet_location=<wallet location>`                           | Path to Oracle wallet when using the wallet.                                        |

##### Usage Notes

None.

##### Examples

Examples include deleting the user or shared schema mapping with and without SSL port connectivity to OID.

Example 7-43 Deleting the User or Shared Schema Mapping with SSL Port Conectivity to OID and Using Passwords Stored in the Oracle Wallet

    eusm deleteMapping database_name=dbtest1 realm_dn=dc=yy,dc=company,dc=com mapping_name=MAPPING01 ldap_host=xxxxx.zz.company.com ldap_ssl_port=3131 keystore=/etc/myapp/keyStore keystore_alias=keystore1 ldap_user_dn=cn=orcladmin ldap_alias=ldabadmin1 wallet_location=/oracle/product/db_1/wallets

Example 7-44 Deleting the User or Shared Schema Mapping with SSL Port Conectivity to OID

    eusm deleteMapping database_name=dbtest1 realm_dn=dc=yy,dc=company,dc=com mapping_name=MAPPING01 ldap_host=xxxxx.zz.company.com ldap_ssl_port=3131 keystore=/etc/myapp/keyStore ldap_user_dn=cn=orcladmin

Example 7-45 Deleting the User or Shared Schema Mapping with non-SSL Port Conectivity to OID

    eusm deleteMapping database_name=dbtest1 realm_dn=dc=yy,dc=company,dc=com mapping_name=MAPPING01 ldap_host=xxxxx.zz.company.com ldap_port=3060 ldap_user_dn=cn=orcladmin

#### 7.3.16 listMappings

Lists the user and shared schema mappings.

##### Prerequisites

(Optional) List the prerequisites for executing the command in the following list:

- Prerequisite \#1

- Prerequisite \#2

##### Syntax

    listMappings
        [domain_name=<domain name>]
        [database_name=<database name>]
         realm_dn=<DN of the realm>
         ldap_host=<OID host>
         ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>
         keystore=<path to keystore>
         keystore_alias=<keystore password alias>
         ldap_user_dn=<DN of OID user>
         ldap_alias=<OID user password alias>
         wallet_location=<wallet location>

##### Options

Each option must be prefixed with a space. Multiple options can be concatenated and prefixed with single space.

| Option                                                        | Description                                                                         |
|:--------------------------------------------------------------|:------------------------------------------------------------------------------------|
| `[domain_name=<domain name>]`                                 | Name of the domain.                                                                 |
| `[database_name=<database name>]`                             | Database name.                                                                      |
| `realm_dn=<DN of the realm>`                                  | DN of the realm.                                                                    |
| `ldap_host=<OID host>`                                        | OID host.                                                                           |
| `ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>` | OID non ssl port or OID ssl port.                                                   |
| `keystore=<path to keystore>`                                 | Path to the keystore.                                                               |
| `keystore_alias=<keystore password alias>`                    | Keystore password taken from the Oracle wallet.                                     |
| `ldap_user_dn=<DN of OID user>`                               | DN of OID user which is used for authenticating and executing a command in the OID. |
| `ldap_alias=<OID user password alias>`                        | OID user password taken from the Oracle wallet.                                     |
| `wallet_location=<wallet location>`                           | Path to Oracle wallet when using the wallet.                                        |

##### Usage Notes

None.

##### Examples

Examples include listing the user or shared schema mappings with and without SSL port connectivity to OID.

Example 7-46 Listing the User or Shared Schema Mappings with SSL Port Conectivity to OID and Using Passwords Stored in the Oracle Wallet

    eusm listMappings database_name=dbtest1 realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_ssl_port=3131 keystore=/etc/myapp/keyStore keystore_alias=keystore1 ldap_user_dn=cn=orcladmin ldap_alias=ldabadmin1 wallet_location=/oracle/product/db_1/wallets

Example 7-47 Listing the User or Shared Schema Mappings with SSL Port Conectivity to OID

    eusm listMappings database_name=dbtest1 realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_ssl_port=3131 keystore=/etc/myapp/keyStore ldap_user_dn=cn=orcladmin

Example 7-48 Listing the User or Shared Schema Mappings with non-SSL Port Conectivity to OID

    eusm listMappings database_name=dbtest1 realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3060 ldap_user_dn=cn=orcladmin

#### 7.3.17 setCulinkStatus

Enables or disables the current user database-link usage in the domain.

##### Syntax

    setCulinkStatus
         domain_name=<domain name>
         realm_dn=<DN of the realm>
         status=<ENABLED/DISABLED>
         ldap_host=<OID host>
         ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>
         keystore=<path to keystore>
         keystore_alias=<keystore password alias>
         ldap_user_dn=<DN of OID user>
         ldap_alias=<OID user password alias>
         wallet_location=<wallet location>

##### Options

Each option must be prefixed with a space. Multiple options can be concatenated and prefixed with single space.

| Option                                                        | Description                                                                         |
|:--------------------------------------------------------------|:------------------------------------------------------------------------------------|
| `domain_name=<domain name>`                                   | Name of the domain.                                                                 |
| `realm_dn=<DN of the realm> `                                 | DN of the realm.                                                                    |
| `status=<ENABLED/DISABLED> `                                  | Whether the status is enabled or disabled.                                          |
| `ldap_host=<OID host>`                                        | OID host.                                                                           |
| `ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>` | OID non ssl port or OID ssl port.                                                   |
| `keystore=<path to keystore>`                                 | Path to the keystore.                                                               |
| `keystore_alias=<keystore password alias>`                    | Keystore password taken from the Oracle wallet.                                     |
| `ldap_user_dn=<DN of OID user>`                               | DN of OID user which is used for authenticating and executing a command in the OID. |
| `ldap_alias=<OID user password alias>`                        | OID user password taken from the Oracle wallet.                                     |
| `wallet_location=<wallet location>`                           | Path to Oracle wallet when using the wallet.                                        |

##### Usage Notes

None.

##### Examples

Examples include enabling the current user database-link usage in the domain with and without SSL port connectivity to OID.

Example 7-49 Enabling the Current User Database-link Usage in the Domain with SSL Port Conectivity to OID and Using Passwords Stored in the Oracle Wallet

    eusm setCulinkStatus domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com status=ENABLED ldap_host=xxxxx.zz.company.com ldap_ssl_port=3131 keystore=/etc/myapp/keyStore keystore_alias=keystore1 ldap_user_dn=cn=orcladmin ldap_alias=ldabadmin1 wallet_location=/oracle/product/db_1/wallets

Example 7-50 Enabling the Current User Database-link Usage in the Domain with SSL Port Conectivity to OID

    eusm setCulinkStatus domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com status=ENABLED ldap_host=xxxxx.zz.company.com ldap_ssl_port=3131 keystore=/etc/myapp/keyStore ldap_user_dn=cn=orcladmin

Example 7-51 Enabling the Current User Database-link Usage in the Domain with non-SSL Port Conectivity to OID

    eusm setCulinkStatus domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com status=ENABLED ldap_host=xxxxx.zz.company.com ldap_port=3060 ldap_user_dn=cn=orcladmin

#### 7.3.18 setAuthTypes

Sets the authentication types to be accepted for the users in the domain

##### Syntax

    setAuthTypes
         domain_name=<domain name>
         realm_dn=<DN of the realm>
         auth_types=<Allowed User-DB authentication>
         ldap_host=<OID host>
         ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>
         keystore=<path to keystore>
         keystore_alias=<keystore password alias>
         ldap_user_dn=<DN of OID user>
         ldap_alias=<OID user password alias>
         wallet_location=<wallet location>

##### Options

Each option must be prefixed with a space. Multiple options can be concatenated and prefixed with single space.

| Option                                                        | Description                                                                         |
|:--------------------------------------------------------------|:------------------------------------------------------------------------------------|
| `domain_name=<domain name>`                                   | Name of the domain.                                                                 |
| `realm_dn=<DN of the realm>`                                  | DN of the realm.                                                                    |
| `auth_types=<Allowed User-DB authentication>`                 | Allowed user-database authentication types                                          |
| `ldap_host=<OID host>`                                        | OID host.                                                                           |
| `ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>` | OID non ssl port or OID ssl port.                                                   |
| `keystore=<path to keystore>`                                 | Path to the keystore.                                                               |
| `keystore_alias=<keystore password alias>`                    | Keystore password taken from the Oracle wallet.                                     |
| `ldap_user_dn=<DN of OID user>`                               | DN of OID user which is used for authenticating and executing a command in the OID. |
| `ldap_alias=<OID user password alias>`                        | OID user password taken from the Oracle wallet.                                     |
| `wallet_location=<wallet location>`                           | Path to Oracle wallet when using the wallet.                                        |

##### Usage Notes

None.

##### Examples

Examples include setting the authentication type accepted for user in the domain with and without SSL port connectivity to OID.

Example 7-52 Setting the Authentication Types Accepted for the Users in the Domain with SSL Port Conectivity to OID and Using Passwords Stored in the Oracle Wallet

    eusm setAuthTypes domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com auth_type=SSL ldap_host=xxxxx.zz.company.com ldap_ssl_port=3131 keystore=/etc/myapp/keyStore keystore_alias=keystore1 ldap_user_dn=cn=orcladmin ldap_alias=ldabadmin1 wallet_location=/oracle/product/db_1/wallets

Example 7-53 Setting the Authentication Types Accepted for the Users in the Domain with SSL Port Conectivity to OID

    eusm setAuthTypes domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com auth_type=SSL ldap_host=xxxxx.zz.company.com ldap_ssl_port=3131 keystore=/etc/myapp/keyStore ldap_user_dn=cn=orcladmin

Example 7-54 Setting the Authentication Types Accepted for the Users in the Domain with non-SSL Port Conectivity to OID

    eusm setAuthTypes domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com auth_type=SSL ldap_host=xxxxx.zz.company.com ldap_port=3060 ldap_user_dn=cn=orcladmin

#### 7.3.19 createRole

Creates an enterprise role.

##### Syntax

    createRole
         enterprise_role=<Enterprise role name>
         domain_name=<domain name>
         realm_dn=<DN of the realm>
         ldap_host=<OID host>
         ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>
         keystore=<path to keystore>
         keystore_alias=<keystore password alias>
         ldap_user_dn=<DN of OID user>
         ldap_alias=<OID user password alias>
         wallet_location=<wallet location>

##### Options

Each option must be prefixed with a space. Multiple options can be concatenated and prefixed with single space.

| Option                                                        | Description                                                                          |
|:--------------------------------------------------------------|:-------------------------------------------------------------------------------------|
| `enterprise_role=<Enterprise role name>`                      | Name of the enterprise role.                                                         |
| `domain_name=<domain name>`                                   | Name of the domain.                                                                  |
| `realm_dn=<DN of the realm> `                                 | DN of the realm.                                                                     |
| `ldap_host=<OID host>`                                        | OID host.                                                                            |
| `ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>` | OID non ssl port or OID ssl port.                                                    |
| `keystore=<path to keystore>`                                 | Path to the keystore.                                                                |
| `keystore_alias=<keystore password alias>`                    | Keystore password taken from the Oracle wallet.                                      |
| `ldap_user_dn=<DN of OID user>`                               | DN of OID user which is used for authenticating and  executing a command in the OID. |
| `ldap_alias=<OID user password alias>`                        | OID user password taken from the Oracle wallet.                                      |
| `wallet_location=<wallet location>`                           | Path to Oracle wallet when using the wallet.                                         |

##### Usage Notes

Enterprise roles are access privileges assigned to enterprise users. Enterprise roles are a set of Oracle role-based authorizations across one or more databases in an enterprise domain. Enterprise roles are stored in the directory and contain one or more global roles.

A global role is a role managed in a directory, but its privileges are contained within a single database. A global role is created in a database using SQL\*Plus. For example:

    SQL> create role global_connect identified globally;
    SQL> create role global_resource identified globally;
    SQL> grant connect to global_connect;
    SQL> grant resource to global_resource;

##### Examples

Examples include creating an enterprise role in an enterprise domain in the realm with and without SSL port connectivity to OID.

Example 7-55 Creating a Role with SSL Port Conectivity to OID and Using Passwords Stored in the Oracle Wallet

    eusm createRole enterprise_role=ent_connect domain_name=OracleDefaultDomain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_ssl_port=3131 keystore=/etc/myapp/keyStore keystore_alias=keystore1 ldap_user_dn=cn=orcladmin ldap_alias=ldabadmin1 wallet_location=/oracle/product/db_1/wallets

Example 7-56 Creating a Role with SSL Port Conectivity to OID

    eusm createRole enterprise_role=ent_connect domain_name=OracleDefaultDomain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_ssl_port=3131 keystore=/etc/myapp/keyStore ldap_user_dn=cn=orcladmin

Example 7-57 Creating a Role with non-SSL Port Conectivity to OID

    eusm createRole enterprise_role=ent_connect domain_name=OracleDefaultDomain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3060 ldap_user_dn=cn=orcladmin

#### 7.3.20 deleteRole

Deletes an enterprise role.

##### Syntax

    deleteRole
         enterprise_role=<Enterprise role name>
         domain_name=<domain name>
         realm_dn=<DN of the realm>
         ldap_host=<OID host>
         ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>
         keystore=<path to keystore>
         keystore_alias=<keystore password alias>
         ldap_user_dn=<DN of OID user>
         ldap_alias=<OID user password alias>
         wallet_location=<wallet location>

##### Options

Each option must be prefixed with a space. Multiple options can be concatenated and prefixed with single space.

| Option                                                        | Description                                                                         |
|:--------------------------------------------------------------|:------------------------------------------------------------------------------------|
| `enterprise_role=<Enterprise role name>`                      | Name of the enterprise role.                                                        |
| `domain_name=<domain name>`                                   | Name of the domain.                                                                 |
| `realm_dn=<DN of the realm> `                                 | DN of the realm.                                                                    |
| `ldap_host=<OID host>`                                        | OID host.                                                                           |
| `ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>` | OID non ssl port or OID ssl port.                                                   |
| `keystore=<path to keystore>`                                 | Path to the keystore.                                                               |
| `keystore_alias=<keystore password alias>`                    | Keystore password taken from the Oracle wallet.                                     |
| `ldap_user_dn=<DN of OID user>`                               | DN of OID user which is used for authenticating and executing a command in the OID. |
| `ldap_alias=<OID user password alias>`                        | OID user password taken from the Oracle wallet.                                     |
| `wallet_location=<wallet location>`                           | Path to Oracle wallet when using the wallet.                                        |

##### Usage Notes

Enterprise roles are access privileges assigned to enterprise users. Enterprise roles are a set of Oracle role-based authorizations across one or more databases in an enterprise domain. Enterprise roles are stored in the directory and contain one or more global roles.

A global role is a role managed in a directory, but its privileges are contained within a single database. A global role is created in a database using SQL\*Plus. For example:

    SQL> create role global_connect identified globally;
    SQL> create role global_resource identified globally;
    SQL> grant connect to global_connect;
    SQL> grant resource to global_resource;

##### Examples

Examples include deleting an enterprise role in an enterprise domain in the realm with and without SSL port connectivity to OID.

Example 7-58 Deleting a Role with SSL Port Conectivity to OID and Using Passwords Stored in the Oracle Wallet

    eusm deleteRole enterprise_role=ent_connect domain_name=OracleDefaultDomain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_ssl_port=3131 keystore=/etc/myapp/keyStore keystore_alias=keystore1 ldap_user_dn=cn=orcladmin ldap_alias=ldabadmin1 wallet_location=/oracle/product/db_1/wallets

Example 7-59 Deleting a Role with SSL Port Conectivity to OID

    eusm deleteRole enterprise_role=ent_connect domain_name=OracleDefaultDomain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_ssl_port=3131 keystore=/etc/myapp/keyStore ldap_user_dn=cn=orcladmin

Example 7-60 Deleting a Role with non-SSL Port Conectivity to OID

    eusm deleteRole enterprise_role=ent_connect domain_name=OracleDefaultDomain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3060 ldap_user_dn=cn=orcladmin

#### 7.3.21 addGlobalRole

Adds a global role or an administrative role to an enterprise role.

##### Syntax

    addGlobalRole
         enterprise_role=<Enterprise role name>
         domain_name=<domain name>
         realm_dn=<DN of the realm>
         database_name=<Database name>
         global_role=<Global role name>
         dbuser=<Database user name to connect>
         db_alias=<Database username password alias>
         dbconnect_string=<Database connect string>
         ldap_host=<OID host>
         ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>
         keystore=<path to keystore>
         keystore_alias=<keystore password alias>
         ldap_user_dn=<DN of OID user>
         ldap_alias=<OID user password alias>
         wallet_location=<wallet location>

##### Options

Each option must be prefixed with a space. Multiple options can be concatenated and prefixed with single space.

| Option                                                        | Description                                                                         |
|:--------------------------------------------------------------|:------------------------------------------------------------------------------------|
| `enterprise_role=<Enterprise role name>`                      | Name of the enterprise role.                                                        |
| `domain_name=<domain name>`                                   | Name of the domain.                                                                 |
| `realm_dn=<DN of the realm> `                                 | DN of the realm.                                                                    |
| `database_name=<Database name>`                               | Database name.                                                                      |
| `global_role=<Global role name>`                              | Global role or administrative role name.                                            |
| `dbuser=<Database user name to connect>`                      | The database user name to connect.                                                  |
| `db_alias=<Database username password alias>`                 | Database user password taken from the Oracle wallet.                                |
| `dbconnect_string=<Database connect string>`                  | Database connect string                                                             |
| `ldap_host=<OID host>`                                        | OID host.                                                                           |
| `ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>` | OID non ssl port or OID ssl port.                                                   |
| `keystore=<path to keystore>`                                 | Path to the keystore.                                                               |
| `keystore_alias=<keystore password alias>`                    | Keystore password taken from the Oracle wallet.                                     |
| `ldap_user_dn=<DN of OID user>`                               | DN of OID user which is used for authenticating and executing a command in the OID. |
| `ldap_alias=<OID user password alias>`                        | OID user password taken from the Oracle wallet.                                     |
| `wallet_location=<wallet location>`                           | Path to Oracle wallet when using the wallet.                                        |

##### Usage Notes

Enterprise roles are access privileges assigned to enterprise users. Enterprise roles are a set of Oracle role-based authorizations across one or more databases in an enterprise domain. Enterprise roles are stored in the directory and contain one or more global roles.

A global role and an administrative role are roles managed in a directory, but their privileges are contained within a single database. A global role and an administrative role are created in a database using SQL\*Plus. A `global_role` for administrative role can be either `SYSDBA`, `SYSOPER`, `SYSBACKUP`, `SYSKM`, or `SYSDG`. For example:

    SQL> create role global_connect identified globally;
    SQL> create role global_resource identified globally;
    SQL> grant connect to global_connect;
    SQL> grant resource to global_resource;

##### Examples

Examples include adding a global role and an administrative role in an enterprise domain in the realm for a database user with and without SSL port connectivity to OID.

Example 7-61 Adding a Global Role with SSL Port Conectivity to OID and Using Passwords Stored in the Oracle Wallet

    eusm addGlobalRole enterprise_role=ent_resource domain_name=OracleDefaultDomain realm_dn=dc=yy,dc=company,dc=com database_name=dbtest1 global_role=global_resource dbuser=system db_alias=dbadmin1 dbconnect_string=zzzz10-yy.yy.company.com:1531:dbtest1  ldap_host=xxxxx.zz.company.com ldap_ssl_port=3131 keystore=/etc/myapp/keyStore keystore_alias=keystore1 ldap_user_dn=cn=orcladmin ldap_alias=ldabadmin1 wallet_location=/oracle/product/db_1/wallets

Example 7-62 Adding an Administrative Role with SSL Port Conectivity to OID and Using Passwords Stored in the Oracle Wallet

    eusm addGlobalRole enterprise_role=ent_resource domain_name=OracleDefaultDomain realm_dn=dc=yy,dc=company,dc=com database_name=dbtest1 global_role=SYSDBA dbuser=system db_alias=dbadmin1 dbconnect_string=zzzz10-yy.yy.company.com:1531:dbtest1 ldap_host=xxxxx.zz.company.com ldap_ssl_port=3131 keystore=/etc/myapp/keyStore keystore_alias=keystore1 ldap_user_dn=cn=orcladmin ldap_alias=ldabadmin1 wallet_location=/oracle/product/db_1/wallets

Example 7-63 Adding a Global Role with SSL Port Conectivity to OID

    eusm addGlobalRole enterprise_role=ent_resource domain_name=OracleDefaultDomain realm_dn=dc=yy,dc=company,dc=com database_name=dbtest1 global_role=global_resource dbuser=system dbconnect_string=zzzz10-yy.yy.company.com:1531:dbtest1 ldap_host=xxxxx.zz.company.com ldap_ssl_port=3131 keystore=/etc/myapp/keyStore ldap_user_dn=cn=orcladmin

Example 7-64 Adding an Administrative Role with SSL Port Conectivity to OID

    eusm addGlobalRole enterprise_role=ent_resource domain_name=OracleDefaultDomain realm_dn=dc=yy,dc=company,dc=com database_name=dbtest1 global_role=SYSDBA dbuser=system dbconnect_string=zzzz10-yy.yy.company.com:1531:dbtest1 ldap_host=xxxxx.zz.company.com ldap_ssl_port=3131 keystore=/etc/myapp/keyStore ldap_user_dn=cn=orcladmin

Example 7-65 Adding a Global Role with non-SSL Port Conectivity to OID

    eusm addGlobalRole enterprise_role=ent_resource domain_name=OracleDefaultDomain realm_dn=dc=yy,dc=company,dc=com database_name=dbtest1 global_role=global_resource dbuser=system dbconnect_string=zzzz10-yy.yy.company.com:1531:dbtest1 ldap_host=xxxxx.zz.company.com ldap_port=3060 ldap_user_dn=cn=orcladmin

Example 7-66 Adding an Administrative Role with non-SSL Port Conectivity to OID

    eusm addGlobalRole enterprise_role=ent_resource domain_name=OracleDefaultDomain realm_dn=dc=yy,dc=company,dc=com database_name=dbtest1 global_role=SYSDBA dbuser=system dbconnect_string=zzzz10-yy.yy.company.com:1531:dbtest1 ldap_host=xxxxx.zz.company.com ldap_port=3060 ldap_user_dn=cn=orcladmin

#### 7.3.22 removeGlobalRole

Removes a global role or an administrative role from an enterprise role.

##### Syntax

    removeGlobalRole
         enterprise_role=<Enterprise role name>
         domain_name=<domain name>
         realm_dn=<DN of the realm>
         database_name=<Database name>
         global_role=<Global role name >
         dbuser=<Database user name to connect>
         db_alias=<Database username password alias>
         dbconnect_string=<Database connect string>
         ldap_host=<OID host>
         ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>
         keystore=<path to keystore>
         keystore_alias=<keystore password alias>
         ldap_user_dn=<DN of OID user>
         ldap_alias=<OID user password alias>
         wallet_location=<wallet location>

##### Options

Each option must be prefixed with a space. Multiple options can be concatenated and prefixed with single space.

| Option                                                        | Description                                                                         |
|:--------------------------------------------------------------|:------------------------------------------------------------------------------------|
| `enterprise_role=<Enterprise role name>`                      | Name of the enterprise role.                                                        |
| `domain_name=<domain name>`                                   | Name of the domain.                                                                 |
| `realm_dn=<DN of the realm> `                                 | DN of the realm.                                                                    |
| `database_name=<Database name>`                               | Database name.                                                                      |
| `global_role=<Global role name>`                              | Global role or administrative role name.                                            |
| `dbuser=<Database user name to connect>`                      | The database user name to connect.                                                  |
| `db_alias=<Database username password alias>`                 | Database user password taken from the Oracle wallet.                                |
| `dbconnect_string=<Database connect string>`                  | Database connect string                                                             |
| `ldap_host=<OID host>`                                        | OID host.                                                                           |
| `ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>` | OID non ssl port or OID ssl port.                                                   |
| `keystore=<path to keystore>`                                 | Path to the keystore.                                                               |
| `keystore_alias=<keystore password alias>`                    | Keystore password taken from the Oracle wallet.                                     |
| `ldap_user_dn=<DN of OID user>`                               | DN of OID user which is used for authenticating and executing a command in the OID. |
| `ldap_alias=<OID user password alias>`                        | OID user password taken from the Oracle wallet.                                     |
| `wallet_location=<wallet location>`                           | Path to Oracle wallet when using the wallet.                                        |

##### Usage Notes

Enterprise roles are access privileges assigned to enterprise users. Enterprise roles are a set of Oracle role-based authorizations across one or more databases in an enterprise domain. Enterprise roles are stored in the directory and contain one or more global roles.

A global role and an administrative role are roles managed in a directory, but their privileges are contained within a single database. A global role and an administrative role are created in a database using SQL\*Plus. A `global_role` for administrative role can be either `SYSDBA`, `SYSOPER`, `SYSBACKUP`, `SYSKM`, or `SYSDG`. For example:

    SQL> create role global_connect identified globally;
    SQL> create role global_resource identified globally;
    SQL> grant connect to global_connect;
    SQL> grant resource to global_resource;

##### Examples

Examples include removing a global role and an administrative role in an enterprise domain in the realm from a database user with and without SSL port connectivity to OID.

Example 7-67 Removing a Global Role with SSL Port Conectivity to OID and Using Passwords Stored in the Oracle Wallet

    eusm removeGlobalRole enterprise_role=ent_resource domain_name=OracleDefaultDomain realm_dn=dc=yy,dc=company,dc=com database_name=dbtest1 global_role=global_connect dbuser=system db_alias=dbadmin1 dbconnect_string=zzzz10-yy.yy.company.com:1531:dbtest1 ldap_host=xxxxx.zz.company.com ldap_ssl_port=3131 keystore=/etc/myapp/keyStore keystore_alias=keystore1 ldap_user_dn=cn=orcladmin ldap_alias=ldabadmin1 wallet_location=/oracle/product/db_1/wallets

Example 7-68 Removing an Administrative Role with SSL Port Conectivity to OID and Using Passwords Stored in the Oracle Wallet

    eusm removeGlobalRole enterprise_role=ent_resource domain_name=OracleDefaultDomain realm_dn=dc=yy,dc=company,dc=com database_name=dbtest1 global_role=SYSDBA dbuser=system db_alias=dbadmin1 dbconnect_string=zzzz10-yy.yy.company.com:1531:dbtest1 ldap_host=xxxxx.zz.company.com ldap_ssl_port=3131 keystore=/etc/myapp/keyStore keystore_alias=keystore1 ldap_user_dn=cn=orcladmin ldap_alias=ldabadmin1 wallet_location=/oracle/product/db_1/wallets

Example 7-69 Removing a Global Role with SSL Port Conectivity to OID

    eusm removeGlobalRole enterprise_role=ent_resource domain_name=OracleDefaultDomain realm_dn=dc=yy,dc=company,dc=com database_name=dbtest1 global_role=global_connect dbuser=system dbconnect_string=zzzz10-yy.yy.company.com:1531:dbtest1 ldap_host=xxxxx.zz.company.com ldap_ssl_port=3131 keystore=/etc/myapp/keyStore ldap_user_dn=cn=orcladmin

Example 7-70 Removing an Administrative Role with SSL Port Conectivity to OID

    eusm removeGlobalRole enterprise_role=ent_resource domain_name=OracleDefaultDomain realm_dn=dc=yy,dc=company,dc=com database_name=dbtest1 global_role=SYSDBA dbuser=system dbconnect_string=zzzz10-yy.yy.company.com:1531:dbtest1 ldap_host=xxxxx.zz.company.com ldap_ssl_port=3131 keystore=/etc/myapp/keyStore ldap_user_dn=cn=orcladmin

Example 7-71 Removing a Global Role with non-SSL Port Conectivity to OID

    eusm removeGlobalRole enterprise_role=ent_resource domain_name=OracleDefaultDomain realm_dn=dc=yy,dc=company,dc=com database_name=dbtest1 global_role=global_connect dbuser=system dbconnect_string=zzzz10-yy.yy.company.com:1531:dbtest1 ldap_host=xxxxx.zz.company.com ldap_port=3060 ldap_user_dn=cn=orcladmin

Example 7-72 Removing an Administrative Role with non-SSL Port Conectivity to OID

    eusm removeGlobalRole enterprise_role=ent_resource domain_name=OracleDefaultDomain realm_dn=dc=yy,dc=company,dc=com database_name=dbtest1 global_role=SYSDBA dbuser=system dbconnect_string=zzzz10-yy.yy.company.com:1531:dbtest1 ldap_host=xxxxx.zz.company.com ldap_port=3060 ldap_user_dn=cn=orcladmin

#### 7.3.23 grantRole

Grants an enterprise role.

##### Syntax

    grantRole
         enterprise_role=<Enterprise role name>
         domain_name=<domain name>
         realm_dn=<DN of the realm>
         [user_dn=<Distinguished name of user>]
         [group_dn=<Distinguished name of group>]
         ldap_host=<OID host>
         ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>
         keystore=<path to keystore>
         keystore_alias=<keystore password alias>
         ldap_user_dn=<DN of OID user>
         ldap_alias=<OID user password alias>
         wallet_location=<wallet location>

##### Options

Each option must be prefixed with a space. Multiple options can be concatenated and prefixed with single space.

| Option                                                        | Description                                                                         |
|:--------------------------------------------------------------|:------------------------------------------------------------------------------------|
| `enterprise_role=<Enterprise role name>`                      | Name of the enterprise role.                                                        |
| `domain_name=<domain name>`                                   | Name of the domain.                                                                 |
| `realm_dn=<DN of the realm> `                                 | DN of the realm.                                                                    |
| `[user_dn=<Distinguished name of user>]`                      | DN of the user.                                                                     |
| `[group_dn=<Distinguished name of group>]`                    | DN of the group.                                                                    |
| `ldap_host=<OID host>`                                        | OID host.                                                                           |
| `ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>` | OID non ssl port or OID ssl port.                                                   |
| `keystore=<path to keystore>`                                 | Path to the keystore.                                                               |
| `keystore_alias=<keystore password alias>`                    | Keystore password taken from the Oracle wallet.                                     |
| `ldap_user_dn=<DN of OID user>`                               | DN of OID user which is used for authenticating and executing a command in the OID. |
| `ldap_alias=<OID user password alias>`                        | OID user password taken from the Oracle wallet.                                     |
| `wallet_location=<wallet location>`                           | Path to Oracle wallet when using the wallet.                                        |

##### Usage Notes

Enterprise roles are access privileges assigned to enterprise users. Enterprise roles are a set of Oracle role-based authorizations across one or more databases in an enterprise domain. Enterprise roles are stored in the directory and contain one or more global roles.

A global role is a role managed in a directory, but its privileges are contained within a single database. A global role is created in a database using SQL\*Plus. For example:

    SQL> create role global_connect identified globally;
    SQL> create role global_resource identified globally;
    SQL> grant connect to global_connect;
    SQL> grant resource to global_resource;

##### Examples

Examples include granting an enterprise role in an enterprise domain in the realm to a user with and without SSL port connectivity to OID.

Example 7-73 Granting a Role to a User with SSL Port Conectivity to OID and Using Passwords Stored in the Oracle Wallet

    eusm grantRole enterprise_role=ent_connect domain_name=OracleDefaultDomain realm_dn=dc=yy,dc=company,dc=com user_dn=cn=test_user,cn=Users,dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_ssl_port=3131 keystore=/etc/myapp/keyStore keystore_alias=keystore1 ldap_user_dn=cn=orcladmin ldap_alias=ldabadmin1 wallet_location=/oracle/product/db_1/wallets

Example 7-74 Granting a Role to a User with SSL Port Conectivity to OID

    eusm grantRole enterprise_role=ent_connect domain_name=OracleDefaultDomain realm_dn=dc=yy,dc=company,dc=com user_dn=cn=test_user,cn=Users,dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_ssl_port=3131 keystore=/etc/myapp/keyStore ldap_user_dn=cn=orcladmin

Example 7-75 Granting a Role to a User with non-SSL Port Conectivity to OID

    eusm grantRole enterprise_role=ent_connect domain_name=OracleDefaultDomain realm_dn=dc=yy,dc=company,dc=com user_dn=cn=test_user,cn=Users,dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3060 ldap_user_dn=cn=orcladmin

#### 7.3.24 revokeRole

Revokes an enterprise role.

##### Syntax

    revokeRole
         enterprise_role=<Enterprise role name>
         domain_name=<domain name>
         realm_dn=<DN of the realm>
         [user_dn=<Distinguished name of user>]
         [group_dn=<Distinguished name of group>]
         ldap_host=<OID host>
         ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>
         keystore=<path to keystore>
         keystore_alias=<keystore password alias>
         ldap_user_dn=<DN of OID user>
         ldap_alias=<OID user password alias>
         wallet_location=<wallet location>

##### Options

Each option must be prefixed with a space. Multiple options can be concatenated and prefixed with single space.

| Option                                                        | Description                                                                         |
|:--------------------------------------------------------------|:------------------------------------------------------------------------------------|
| `enterprise_role=<Enterprise role name>`                      | Name of the enterprise role.                                                        |
| `domain_name=<domain name>`                                   | Name of the domain.                                                                 |
| `realm_dn=<DN of the realm> `                                 | DN of the realm.                                                                    |
| `[user_dn=<Distinguished name of user>]`                      | DN of the user.                                                                     |
| `[group_dn=<Distinguished name of group>]`                    | DN of the group.                                                                    |
| `ldap_host=<OID host>`                                        | OID host.                                                                           |
| `ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>` | OID non ssl port or OID ssl port.                                                   |
| `keystore=<path to keystore>`                                 | Path to the keystore.                                                               |
| `keystore_alias=<keystore password alias>`                    | Keystore password taken from the Oracle wallet.                                     |
| `ldap_user_dn=<DN of OID user>`                               | DN of OID user which is used for authenticating and executing a command in the OID. |
| `ldap_alias=<OID user password alias>`                        | OID user password taken from the Oracle wallet.                                     |
| `wallet_location=<wallet location>`                           | Path to Oracle wallet when using the wallet.                                        |

##### Usage Notes

Enterprise roles are access privileges assigned to enterprise users. Enterprise roles are a set of Oracle role-based authorizations across one or more databases in an enterprise domain. Enterprise roles are stored in the directory and contain one or more global roles.

A global role is a role managed in a directory, but its privileges are contained within a single database. A global role is created in a database using SQL\*Plus. For example:

    SQL> create role global_connect identified globally;
    SQL> create role global_resource identified globally;
    SQL> grant connect to global_connect;
    SQL> grant resource to global_resource;

##### Examples

Examples include revoking an enterprise role in an enterprise domain in the realm from a user with and without SSL port connectivity to OID.

Example 7-76 Revoking a Role from a User with SSL Port Conectivity to OID and Using Passwords Stored in the Oracle Wallet

    eusm revokeRole enterprise_role=ent_connect domain_name=OracleDefaultDomain realm_dn=dc=yy,dc=company,dc=com user_dn=cn=test_user,cn=Users,dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_ssl_port=3131 keystore=/etc/myapp/keyStore keystore_alias=keystore1 ldap_user_dn=cn=orcladmin ldap_alias=ldabadmin1 wallet_location=/oracle/product/db_1/wallets

Example 7-77 Revoking a Role from a User with SSL Port Conectivity to OID

    eusm revokeRole enterprise_role=ent_connect domain_name=OracleDefaultDomain realm_dn=dc=yy,dc=company,dc=com user_dn=cn=test_user,cn=Users,dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_ssl_port=3131 keystore=/etc/myapp/keyStore ldap_user_dn=cn=orcladmin

Example 7-78 Revoking a Role from a User with non-SSL Port Conectivity to OID

    eusm revokeRole enterprise_role=ent_connect domain_name=OracleDefaultDomain realm_dn=dc=yy,dc=company,dc=com user_dn=cn=test_user,cn=Users,dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3060 ldap_user_dn=cn=orcladmin

#### 7.3.25 listEnterpriseRoles

Lists the enterprise roles.

##### Syntax

     listEnterpriseRoles
         domain_name=<domain name>
         realm_dn=<DN of the realm>
         ldap_host=<OID host>
         ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>
         keystore=<path to keystore>
         keystore_alias=<keystore password alias>
         ldap_user_dn=<DN of OID user>
         ldap_alias=<OID user password alias>
         wallet_location=<wallet location>

##### Options

Each option must be prefixed with a space. Multiple options can be concatenated and prefixed with single space.

| Option                                                        | Description                                                                         |
|:--------------------------------------------------------------|:------------------------------------------------------------------------------------|
| `domain_name=<domain name>`                                   | Name of the domain.                                                                 |
| `realm_dn=<DN of the realm> `                                 | DN of the realm.                                                                    |
| `ldap_host=<OID host>`                                        | OID host.                                                                           |
| `ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>` | OID non ssl port or OID ssl port.                                                   |
| `keystore=<path to keystore>`                                 | Path to the keystore.                                                               |
| `keystore_alias=<keystore password alias>`                    | Keystore password taken from the Oracle wallet.                                     |
| `ldap_user_dn=<DN of OID user>`                               | DN of OID user which is used for authenticating and executing a command in the OID. |
| `ldap_alias=<OID user password alias>`                        | OID user password taken from the Oracle wallet.                                     |
| `wallet_location=<wallet location>`                           | Path to Oracle wallet when using the wallet.                                        |

##### Usage Notes

Enterprise roles are access privileges assigned to enterprise users. Enterprise roles are a set of Oracle role-based authorizations across one or more databases in an enterprise domain. Enterprise roles are stored in the directory and contain one or more global roles.

A global role is a role managed in a directory, but its privileges are contained within a single database. A global role is created in a database using SQL\*Plus. For example:

    SQL> create role global_connect identified globally;
    SQL> create role global_resource identified globally;
    SQL> grant connect to global_connect;
    SQL> grant resource to global_resource;

##### Examples

Examples include listing enterprise roles in an enterprise domain in the realm with and without SSL port connectivity to OID.

Example 7-79 List the Enterprisre Roles with SSL Port Conectivity to OID and Use Passwords Stored in the Oracle Wallet

    eusm listEnterpriseRoles domain_name=OracleDefaultDomain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_ssl_port=3131 keystore=/etc/myapp/keyStore keystore_alias=keystore1 ldap_user_dn=cn=orcladmin ldap_alias=ldabadmin1 wallet_location=/oracle/product/db_1/wallets

Example 7-80 List the Enterprisre Roles with SSL Port Conectivity to OID

    eusm listEnterpriseRoles domain_name=OracleDefaultDomain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_ssl_port=3131 keystore=/etc/myapp/keyStore ldap_user_dn=cn=orcladmin

Example 7-81 List the Enterprisre Roles with non-SSL Port Conectivity to OID

    eusm listEnterpriseRoles domain_name=OracleDefaultDomain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3060 ldap_user_dn=cn=orcladmin

#### 7.3.26 listEnterpriseRolesOfUser

Lists the enterprise roles of a user.

##### Syntax

    listEnterpriseRolesOfUser
         user_dn=<Distinguished name of user>
         realm_dn=<DN of the realm>
         ldap_host=<OID host>
         ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>
         keystore=<path to keystore>
         keystore_alias=<keystore password alias>
         ldap_user_dn=<DN of OID user>
         ldap_alias=<OID user password alias>
         wallet_location=<wallet location>

##### Options

Each option must be prefixed with a space. Multiple options can be concatenated and prefixed with single space.

| Option                                                        | Description                                                                         |
|:--------------------------------------------------------------|:------------------------------------------------------------------------------------|
| `user_dn=<Distinguished name of user>`                        | DN of the user.                                                                     |
| `realm_dn=<DN of the realm> `                                 | DN of the realm.                                                                    |
| `ldap_host=<OID host>`                                        | OID host.                                                                           |
| `ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>` | OID non ssl port or OID ssl port.                                                   |
| `keystore=<path to keystore>`                                 | Path to the keystore.                                                               |
| `keystore_alias=<keystore password alias>`                    | Keystore password taken from the Oracle wallet.                                     |
| `ldap_user_dn=<DN of OID user>`                               | DN of OID user which is used for authenticating and executing a command in the OID. |
| `ldap_alias=<OID user password alias>`                        | OID user password taken from the Oracle wallet.                                     |
| `wallet_location=<wallet location>`                           | Path to Oracle wallet when using the wallet.                                        |

##### Usage Notes

Enterprise roles are access privileges assigned to enterprise users. Enterprise roles are a set of Oracle role-based authorizations across one or more databases in an enterprise domain. Enterprise roles are stored in the directory and contain one or more global roles.

A global role is a role managed in a directory, but its privileges are contained within a single database. A global role is created in a database using SQL\*Plus. For example:

    SQL> create role global_connect identified globally;
    SQL> create role global_resource identified globally;
    SQL> grant connect to global_connect;
    SQL> grant resource to global_resource;

##### Examples

Examples include listing the enterprise roles of a user in the realm with and without SSL port connectivity to OID.

Example 7-82 List the Enterprise Roles of a User with SSL Port Conectivity to OID and Use Passwords Stored in the Oracle Wallet

    eusm listEnterpriseRolesOfUser user_dn=cn=test_user,cn=Users,dc=yy,dc=company,dc=com realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_ssl_port=3131 keystore=/etc/myapp/keyStore keystore_alias=keystore1 ldap_user_dn=cn=orcladmin ldap_alias=ldabadmin1 wallet_location=/oracle/product/db_1/wallets

Example 7-83 List the Enterprise Roles of a User with SSL Port Conectivity to OID

    eusm listEnterpriseRolesOfUser user_dn=cn=test_user,cn=Users,dc=yy,dc=company,dc=com realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_ssl_port=3131 keystore=/etc/myapp/keyStore ldap_user_dn=cn=orcladmin

Example 7-84 List the Enterprise Roles of a User with non-SSL Port Conectivity to OID

    eusm listEnterpriseRolesOfUser user_dn=cn=test_user,cn=Users,dc=yy,dc=company,dc=com realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3060 ldap_user_dn=cn=orcladmin

#### 7.3.27 listEnterpriseRoleInfo

Lists the enterprise role information.

##### Syntax

    listEnterpriseRoleInfo
         enterprise_role=<Enterprise role name>
         domain_name=<domain name>
         realm_dn=<DN of the realm>
         ldap_host=<OID host>
         ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>
         keystore=<path to keystore>
         keystore_alias=<keystore password alias>
         ldap_user_dn=<DN of OID user>
         ldap_alias=<OID user password alias>
         wallet_location=<wallet location>

##### Options

Each option must be prefixed with a space. Multiple options can be concatenated and prefixed with single space.

| Option                                                        | Description                                                                         |
|:--------------------------------------------------------------|:------------------------------------------------------------------------------------|
| `enterprise_role=<Enterprise role name>`                      | Name of the enterprise role.                                                        |
| `domain_name=<domain name>`                                   | Name of the domain.                                                                 |
| `realm_dn=<DN of the realm> `                                 | DN of the realm.                                                                    |
| `ldap_host=<OID host>`                                        | OID host.                                                                           |
| `ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>` | OID non ssl port or OID ssl port.                                                   |
| `keystore=<path to keystore>`                                 | Path to the keystore.                                                               |
| `keystore_alias=<keystore password alias>`                    | Keystore password taken from the Oracle wallet.                                     |
| `ldap_user_dn=<DN of OID user>`                               | DN of OID user which is used for authenticating and executing a command in the OID. |
| `ldap_alias=<OID user password alias> `                       | OID user password taken from the Oracle wallet.                                     |
| `wallet_location=<wallet location>`                           | Path to Oracle wallet when using the wallet.                                        |

##### Usage Notes

Enterprise roles are access privileges assigned to enterprise users. Enterprise roles are a set of Oracle role-based authorizations across one or more databases in an enterprise domain. Enterprise roles are stored in the directory and contain one or more global roles.

A global role is a role managed in a directory, but its privileges are contained within a single database. A global role is created in a database using SQL\*Plus. For example:

    SQL> create role global_connect identified globally;
    SQL> create role global_resource identified globally;
    SQL> grant connect to global_connect;
    SQL> grant resource to global_resource;

##### Examples

Examples include listing the enterprise role information in an enterprise domain in the realm with and without SSL port connectivity to OID.

Example 7-85 List the Enterprise Role Information with SSL Port Conectivity to OID and Use Passwords Stored in the Oracle Wallet

    eusm listEnterpriseRoleInfo enterprise_role=ent_connect domain_name=OracleDefaultDomain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_ssl_port=3131 keystore=/etc/myapp/keyStore keystore_alias=keystore1 ldap_user_dn=cn=orcladmin ldap_alias=ldabadmin1 wallet_location=/oracle/product/db_1/wallets

Example 7-86 List the Enterprise Role Information with SSL Port Conectivity to OID

    eusm listEnterpriseRoleInfo enterprise_role=ent_connect domain_name=OracleDefaultDomain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_ssl_port=3131 keystore=/etc/myapp/keyStore ldap_user_dn=cn=orcladmin

Example 7-87 List the Enterprise Role Information with non-SSL Port Conectivity to OID

    eusm listEnterpriseRoleInfo enterprise_role=ent_connect domain_name=OracleDefaultDomain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3060 ldap_user_dn=cn=orcladmin

#### 7.3.28 listGlobalRolesInDB

Lists the global roles in the database.

##### Syntax

    listGlobalRolesInDB
         dbuser=<Database user name to connect>
         db_alias=<Database username password alias>
         dbconnect_string=<Database connect string>
         wallet_location=<wallet location>

##### Options

Each option must be prefixed with a space. Multiple options can be concatenated and prefixed with single space.

| Option                                        | Description                                                 |
|:----------------------------------------------|:------------------------------------------------------------|
| `dbuser=<Database user name to connect>`      | The database user name to connect.                          |
| `db_alias=<Database username password alias>` | Password of the database user taken from the Oracle wallet. |
| `dbconnect_string=<Database connect string>`  | Database connect string                                     |
| `wallet_location=<wallet location>`           | Path to Oracle wallet when using the wallet.                |

##### Usage Notes

Enterprise roles are access privileges assigned to enterprise users. Enterprise roles are a set of Oracle role-based authorizations across one or more databases in an enterprise domain. Enterprise roles are stored in the directory and contain one or more global roles.

A global role is a role managed in a directory, but its privileges are contained within a single database. A global role is created in a database using SQL\*Plus. For example:

    SQL> create role global_connect identified globally;
    SQL> create role global_resource identified globally;
    SQL> grant connect to global_connect;
    SQL> grant resource to global_resource;

##### Examples

Listing the global roles for a database user.

Example 7-88 Listing the Global Roles in the Database and Using Passwords Stored in the Oracle Wallet

    eusm listGlobalRolesInDB dbuser=system db_alias=dbadmin1 dbconnect_string=zzzz10-yy.yy.company.com:1531:dbtest1 wallet_location=/oracle/product/db_1/wallets

Example 7-89 Listing the Global Roles in the Database

    eusm listGlobalRolesInDB dbuser=system dbconnect_string=zzzz10-yy.yy.company.com:1531:dbtest1

#### 7.3.29 listSharedSchemasInDB

Lists the shared schemas in the database.

##### Syntax

    listSharedSchemasInDB
         dbuser=<Database user name to connect>
         db_alias=<Database username password alias>
         dbconnect_string=<Database connect string>
         wallet_location=<wallet location>

##### Options

Each option must be prefixed with a space. Multiple options can be concatenated and prefixed with single space.

| Option                                        | Description                                                 |
|:----------------------------------------------|:------------------------------------------------------------|
| `dbuser=<Database username to connect>`       | The database user name to connect.                          |
| `db_alias=<Database username password alias>` | Password of the database user taken from the Oracle wallet. |
| `dbconnect_string=<Database connect string>`  | Database connect string                                     |
| `wallet_location=<wallet location>`           | Path to Oracle wallet when using the wallet.                |

##### Usage Notes

None.

##### Examples

Listing the shared schemas for a database user.

Example 7-90 List the Shared Schemas in the Database and Use Passwords Stored in the Oracle Wallet

    eusm listSharedSchemasInDB dbuser=system db_alias=dbadmin1 dbconnect_string=zzzz10-yy.yy.company.com:1531:dbtest1 wallet_location=/oracle/product/db_1/wallets

Example 7-91 List the Shared Schemas in the Database

    eusm listSharedSchemasInDB dbuser=system dbconnect_string=zzzz10-yy.yy.company.com:1531:dbtest1

#### 7.3.30 createProxyPerm

Creates a proxy permission object.

##### Syntax

    createProxyPerm
         proxy_permission=<proxy permission name>
         domain_name=<domain name>
         realm_dn=<DN of the realm>
         ldap_host=<OID host>
         ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>
         keystore=<path to keystore>
         keystore_alias=<keystore password alias>
         ldap_user_dn=<DN of OID user>
         ldap_alias=<OID user password alias>
         wallet_location=<wallet location>

##### Options

Each option must be prefixed with a space. Multiple options can be concatenated and prefixed with single space.

| Option                                                        | Description                                                                         |
|:--------------------------------------------------------------|:------------------------------------------------------------------------------------|
| `proxy_permission=<proxy permission name>`                    | Name of the proxy permission.                                                       |
| `domain_name=<domain name>`                                   | Name of the domain.                                                                 |
| `realm_dn=<DN of the realm> `                                 | DN of the realm.                                                                    |
| `ldap_host=<OID host>`                                        | OID host.                                                                           |
| `ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>` | OID non ssl port or OID ssl port.                                                   |
| `keystore=<path to keystore>`                                 | Path to the keystore.                                                               |
| `keystore_alias=<keystore password alias>`                    | Keystore password taken from the Oracle wallet.                                     |
| `ldap_user_dn=<DN of OID user>`                               | DN of OID user which is used for authenticating and executing a command in the OID. |
| `ldap_alias=<OID user password alias>`                        | OID user password taken from the Oracle wallet.                                     |
| `wallet_location=<wallet location>`                           | Path to Oracle wallet when using the wallet.                                        |

##### Usage Notes

Proxy Authentication is a process typically employed in an environment with a middle tier such as a firewall, wherein the end user authenticates to the middle tier, which then authenticates to the directory on the user's behalf—as its proxy. The middle tier logs into the directory as a proxy user. A proxy user can switch identities and, once logged into the directory, switch to the end user's identity. It can perform operations on the end user's behalf, using the authorization appropriate to that particular end user.

To create the proxy permission, you must first create the proxy user in the database.

    SQL> create user proxy_test identified by proxy_test;
    SQL> alter user proxy_test grant connect through enterprise users;

##### Examples

Examples include creating a proxy permission object in an enterprise domain in the realm with and without SSL port connectivity to OID.

Example 7-92 Create the Proxy Permission Object PROXY01 with SSL Port Conectivity to OID and Use Passwords Stored in the Oracle Wallet

    eusm createProxyPerm proxy_permission=PROXY01 domain_name=OracleDefaultDomain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3131 keystore=/etc/myapp/keyStore keystore_alias=keystore1 ldap_user_dn=cn=orcladmin ldap_alias=ldabadmin1 wallet_location=/oracle/product/db_1/wallets

Example 7-93 Create the Proxy Permission Object PROXY01 with SSL Port Conectivity to OID

    eusm createProxyPerm proxy_permission=PROXY01 domain_name=OracleDefaultDomain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3131 keystore=/etc/myapp/keyStore -K ldap_user_dn=cn=orcladmin

Example 7-94 Create the Proxy Permission Object PROXY01 with non-SSL Port Conectivity to OID

    eusm createProxyPerm proxy_permission=PROXY01 domain_name=OracleDefaultDomain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3060 ldap_user_dn=cn=orcladmin

#### 7.3.31 deleteProxyPerm

Deletes a proxy permission object.

##### Syntax

    deleteProxyPerm
         proxy_permission=<proxy permission name>
         domain_name=<domain name>
         realm_dn=<DN of the realm>
         ldap_host=<OID host>
         ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>
         keystore=<path to keystore>
         keystore_alias=<keystore password alias>
         ldap_user_dn=<DN of OID user>
         ldap_alias=<OID user password alias>
         wallet_location=<wallet location>

##### Options

Each option must be prefixed with a space. Multiple options can be concatenated and prefixed with single space.

| Option                                                        | Description                                                                         |
|:--------------------------------------------------------------|:------------------------------------------------------------------------------------|
| `proxy_permission=<proxy permission name>`                    | Name of the proxy permission.                                                       |
| `domain_name=<domain name>`                                   | Name of the domain.                                                                 |
| `realm_dn=<DN of the realm> `                                 | DN of the realm.                                                                    |
| `ldap_host=<OID host>`                                        | OID host.                                                                           |
| `ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>` | OID non ssl port or OID ssl port.                                                   |
| `keystore=<path to keystore>`                                 | Path to the keystore.                                                               |
| `keystore_alias=<keystore password alias>`                    | Keystore password taken from the Oracle wallet.                                     |
| `ldap_user_dn=<DN of OID user>`                               | DN of OID user which is used for authenticating and executing a command in the OID. |
| `ldap_alias=<OID user password alias>`                        | OID user password taken from the Oracle wallet.                                     |
| `wallet_location=<wallet location>`                           | Path to Oracle wallet when using the wallet.                                        |

##### Usage Notes

Proxy Authentication is a process typically employed in an environment with a middle tier such as a firewall, wherein the end user authenticates to the middle tier, which then authenticates to the directory on the user's behalf—as its proxy. The middle tier logs into the directory as a proxy user. A proxy user can switch identities and, once logged into the directory, switch to the end user's identity. It can perform operations on the end user's behalf, using the authorization appropriate to that particular end user.

##### Examples

Examples include deleting a proxy permission object in an enterprise domain in the realm with and without SSL port connectivity to OID.

Example 7-95 Deleting the Proxy Permission PROXY01 with SSL Port Conectivity to OID and Using Passwords Stored in the Oracle Wallet

    eusm deleteProxyPerm proxy_permission=PROXY01 domain_name=OracleDefaultDomain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3131 keystore=/etc/myapp/keyStore keystore_alias=keystore1 ldap_user_dn=cn=orcladmin ldap_alias=ldabadmin1 wallet_location=/oracle/product/db_1/wallets

Example 7-96 Deleting the Proxy Permission PROXY01 with SSL Port Conectivity to OID

    eusm deleteProxyPerm proxy_permission=PROXY01 domain_name=OracleDefaultDomain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3131 keystore=/etc/myapp/keyStore ldap_user_dn=cn=orcladmin

Example 7-97 Deleting the Proxy Permission PROXY01 with non-SSL Port Conectivity to OID

    eusm deleteProxyPerm proxy_permission=PROXY01 domain_name=OracleDefaultDomain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3060 ldap_user_dn=cn=orcladmin

#### 7.3.32 addTargetUser

Adds a target database user to the proxy permission object.

##### Syntax

     addTargetUser
         proxy_permission=<proxy permission name>
         domain_name=<domain name>
         realm_dn=<DN of the realm>
         database_name=<Database name>
         target_user=<Target user in database>
         dbuser=<Database user name to connect>
         db_alias=<Database username password alias>
         dbconnect_string=<Database connect string>
         ldap_host=<OID host>
         ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>
         keystore=<path to keystore>
         keystore_alias=<keystore password alias>
         ldap_user_dn=<DN of OID user>
         ldap_alias=<OID user password alias>
         wallet_location=<wallet location>

##### Options

Each option must be prefixed with a space. Multiple options can be concatenated and prefixed with single space.

| Option                                                        | Description                                                                         |
|:--------------------------------------------------------------|:------------------------------------------------------------------------------------|
| `proxy_permission=<proxy permission name>`                    | Name of the proxy permission.                                                       |
| `domain_name=<domain name>`                                   | Name of the domain.                                                                 |
| `realm_dn=<DN of the realm> `                                 | DN of the realm.                                                                    |
| `database_name=<Database name>`                               | Database name.                                                                      |
| `target_user=<Target user in database>`                       | Target user in the database.                                                        |
| `dbuser=<Database user name to connect>`                      | The database user name to connect.                                                  |
| `db_alias=<Database username password alias>`                 | Password of the database user taken from the Oracle wallet.                         |
| `dbconnect_string=<Database connect string>`                  | Database connect string                                                             |
| `ldap_host=<OID host>`                                        | OID host.                                                                           |
| `ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>` | OID non ssl port or OID ssl port.                                                   |
| `keystore=<path to keystore>`                                 | Path to the keystore.                                                               |
| `keystore_alias=<keystore password alias>`                    | Keystore password taken from the Oracle wallet.                                     |
| `ldap_user_dn=<DN of OID user>`                               | DN of OID user which is used for authenticating and executing a command in the OID. |
| `ldap_alias=<OID user password alias>`                        | OID user password taken from the Oracle wallet.                                     |
| `wallet_location=<wallet location>`                           | Path to Oracle wallet when using the wallet.                                        |

##### Usage Notes

Proxy Authentication is a process typically employed in an environment with a middle tier such as a firewall, wherein the end user authenticates to the middle tier, which then authenticates to the directory on the user's behalf—as its proxy. The middle tier logs into the directory as a proxy user. A proxy user can switch identities and, once logged into the directory, switch to the end user's identity. It can perform operations on the end user's behalf, using the authorization appropriate to that particular end user.

##### Examples

Examples include adding a target database user to the proxy permission object in an enterprise domain in the realm with and without SSL port connectivity to OID.

Example 7-98 Add the Target Database User to the Proxy Permission Object with SSL Port Conectivity to OID and Using Passwords Stored in the Oracle Wallet

    eusm addTargetUser proxy_permission=PROXY01 domain_name=OracleDefaultDomain realm_dn=dc=yy,dc=company,dc=com database_name=dbtest1 target_user=PROXY_TEST dbuser=system db_alias=dbadmin1 dbconnect_string=zzzz10-yy.yy.company.com:1531:dbtest1 ldap_host=xxxxx.zz.company.com ldap_port=3131 keystore=/etc/myapp/keyStore keystore_alias=keystore1 ldap_user_dn=cn=orcladmin ldap_alias=ldabadmin1 wallet_location=/oracle/product/db_1/wallets

Example 7-99 Add the Target Database User to the Proxy Permission Object with SSL Port Conectivity to OID

    eusm addTargetUser proxy_permission=PROXY01 domain_name=OracleDefaultDomain realm_dn=dc=yy,dc=company,dc=com database_name=dbtest1 target_user=PROXY_TEST dbuser=system dbconnect_string=zzzz10-yy.yy.company.com:1531:dbtest1 ldap_host=xxxxx.zz.company.com ldap_port=3131 keystore=/etc/myapp/keyStore ldap_user_dn=cn=orcladmin

Example 7-100 Add the Target Database User to the Proxy Permission Object with non-SSL Port Conectivity to OID

    eusm addTargetUser proxy_permission=PROXY01 domain_name=OracleDefaultDomain realm_dn=dc=yy,dc=company,dc=com database_name=dbtest1 target_user=PROXY_TEST dbuser=system dbconnect_string=zzzz10-yy.yy.company.com:1531:dbtest1 ldap_host=xxxxx.zz.company.com ldap_port=3060 ldap_user_dn=cn=orcladmin

#### 7.3.33 removeTargetUser

Removes a target database user from the proxy permission object.

##### Syntax

    removeTargetUser
         proxy_permission=<proxy permission name>
         domain_name=<domain name>
         realm_dn=<DN of the realm>
         database_name=<Database name>
         target_user=<Target user in database>
         dbuser=<Database user name to connect>
         db_alias=<Database username password alias>
         dbconnect_string=<Database connect string>
         ldap_host=<OID host>
         ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>
         keystore=<path to keystore>
         keystore_alias=<keystore password alias>
         ldap_user_dn=<DN of OID user>
         ldap_alias=<OID user password alias>
         wallet_location=<wallet location>

##### Options

Each option must be prefixed with a space. Multiple options can be concatenated and prefixed with single space.

| Option                                                        | Description                                                                         |
|:--------------------------------------------------------------|:------------------------------------------------------------------------------------|
| `proxy_permission=<proxy permission name>`                    | Name of the proxy permission.                                                       |
| `domain_name=<domain name>`                                   | Name of the domain.                                                                 |
| `realm_dn=<DN of the realm> `                                 | DN of the realm.                                                                    |
| `database_name=<Database name>`                               | Database name.                                                                      |
| `target_user=<Target user in database>`                       | Target user in the database.                                                        |
| `dbuser=<Database username to connect>`                       | The database user name to connect.                                                  |
| `db_alias=<Database username password alias>`                 | Password of the database user taken from the Oracle wallet.                         |
| `dbconnect_string=<Database connect string>`                  | Database connect string                                                             |
| `ldap_host=<OID host>`                                        | OID host.                                                                           |
| `ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>` | OID non ssl port or OID ssl port.                                                   |
| `keystore=<path to keystore>`                                 | Path to the keystore.                                                               |
| `keystore_alias=<keystore password alias>`                    | Keystore password taken from the Oracle wallet.                                     |
| `ldap_user_dn=<DN of OID user>`                               | DN of OID user which is used for authenticating and executing a command in the OID. |
| `ldap_alias=<OID user password alias> `                       | OID user password taken from the Oracle wallet.                                     |
| `wallet_location=<wallet location>`                           | Path to Oracle wallet when using the wallet.                                        |

##### Usage Notes

Proxy Authentication is a process typically employed in an environment with a middle tier such as a firewall, wherein the end user authenticates to the middle tier, which then authenticates to the directory on the user's behalf—as its proxy. The middle tier logs into the directory as a proxy user. A proxy user can switch identities and, once logged into the directory, switch to the end user's identity. It can perform operations on the end user's behalf, using the authorization appropriate to that particular end user.

##### Examples

Examples include removing a target database user from the proxy permission object in an enterprise domain in the realm with and without SSL port connectivity to OID.

Example 7-101 Removing the Target User from the Proxy Permission Object with SSL Port Conectivity to OID and Using Passwords Stored in the Oracle Wallet

    eusm removeTargetUser proxy_permission=PROXY01 domain_name=OracleDefaultDomain realm_dn=dc=yy,dc=company,dc=com database_name=dbtest1 target_user=PROXY_TEST dbuser=system db_alias=dbadmin1 dbconnect_string=zzzz10-yy.yy.company.com:1531:dbtest1 ldap_host=xxxxx.zz.company.com ldap_port=3131 keystore=/etc/myapp/keyStore keystore_alias=keystore1 ldap_user_dn=cn=orcladmin ldap_alias=ldabadmin1 wallet_location=/oracle/product/db_1/wallets

Example 7-102 Removing the Target User from the Proxy Permission Object with SSL Port Conectivity to OID

    eusm removeTargetUser proxy_permission=PROXY01 domain_name=OracleDefaultDomain realm_dn=dc=yy,dc=company,dc=com database_name=dbtest1 target_user=PROXY_TEST dbuser=system dbconnect_string=zzzz10-yy.yy.company.com:1531:dbtest1 ldap_host=xxxxx.zz.company.com ldap_port=3131 keystore=/etc/myapp/keyStore ldap_user_dn=cn=orcladmin

Example 7-103 Removing the Target User from the Proxy Permission Object with non-SSL Port Conectivity to OID

    eusm removeTargetUser proxy_permission=PROXY01 domain_name=OracleDefaultDomain realm_dn=dc=yy,dc=company,dc=com database_name=dbtest1 target_user=PROXY_TEST dbuser=system dbconnect_string=zzzz10-yy.yy.company.com:1531:dbtest1 ldap_host=xxxxx.zz.company.com ldap_port=3060 ldap_user_dn=cn=orcladmin

#### 7.3.34 grantProxyPerm

Maps an enterprise user to the database user through the proxy permission object.

##### Syntax

    grantProxyPerm
         proxy_permission=<proxy permission name>
         domain_name=<domain name>
         realm_dn=<DN of the realm>
         [user_dn=<Distinguished name of user>]
         [group_dn=<Distinguished name of group>]
         ldap_host=<OID host>
         ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>
         keystore=<path to keystore>
         keystore_alias=<keystore password alias>
         ldap_user_dn=<DN of OID user>
         ldap_alias=<OID user password alias>
         wallet_location=<wallet location>

##### Options

Each option must be prefixed with a space. Multiple options can be concatenated and prefixed with single space.

| Option                                                        | Description                                                                         |
|:--------------------------------------------------------------|:------------------------------------------------------------------------------------|
| `proxy_permission=<proxy permission name>`                    | Name of the proxy permission.                                                       |
| `domain_name=<domain name>`                                   | Name of the domain.                                                                 |
| `realm_dn=<DN of the realm> `                                 | DN of the realm.                                                                    |
| `[user_dn=<Distinguished name of user>]`                      | DN of the user.                                                                     |
| `[group_dn=<Distinguished name of group>]`                    | DN of the group.                                                                    |
| `ldap_host=<OID host>`                                        | OID host.                                                                           |
| `ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>` | OID non ssl port or OID ssl port.                                                   |
| `keystore=<path to keystore>`                                 | Path to the keystore.                                                               |
| `keystore_alias=<keystore password alias>`                    | Keystore password taken from the Oracle wallet.                                     |
| `ldap_user_dn=<DN of OID user>`                               | DN of OID user which is used for authenticating and executing a command in the OID. |
| `ldap_alias=<OID user password alias>`                        | OID user password taken from the Oracle wallet.                                     |
| `wallet_location=<wallet location>`                           | Path to Oracle wallet when using the wallet.                                        |

##### Usage Notes

Proxy Authentication is a process typically employed in an environment with a middle tier such as a firewall, wherein the end user authenticates to the middle tier, which then authenticates to the directory on the user's behalf—as its proxy. The middle tier logs into the directory as a proxy user. A proxy user can switch identities and, once logged into the directory, switch to the end user's identity. It can perform operations on the end user's behalf, using the authorization appropriate to that particular end user.

##### Examples

Examples include mapping the enterprise user to the database user through the proxy permission object in the realm with and without SSL port connectivity to OID.

Example 7-104 Mapping the Enterprise User to the Database User Through the PROXY01 Permission Object with SSL Port Conectivity to OID and Using Passwords Stored in the Oracle Wallet

    eusm grantProxyPerm proxy_permission=PROXY01 domain_name=OracleDefaultDomain realm_dn=dc=yy,dc=company,dc=com user_dn=cn=test_user,cn=Users,dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3131 keystore=/etc/myapp/keyStore keystore_alias=keystore1 ldap_user_dn=cn=orcladmin ldap_alias=ldabadmin1 wallet_location=/oracle/product/db_1/wallets

Example 7-105 Mapping the Enterprise User to the Database User Through the PROXY01 Permission Object with SSL Port Conectivity to OID

    eusm grantProxyPerm proxy_permission=PROXY01 domain_name=OracleDefaultDomain realm_dn=dc=yy,dc=company,dc=com user_dn=cn=test_user,cn=Users,dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3131 keystore=/etc/myapp/keyStore ldap_user_dn=cn=orcladmin

Example 7-106 Mapping the Enterprise User to the Database User Through the PROXY01 Permission Object with non-SSL Port Conectivity to OID

    eusm grantProxyPerm proxy_permission=PROXY01 domain_name=OracleDefaultDomain realm_dn=dc=yy,dc=company,dc=com user_dn=cn=test_user,cn=Users,dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3060 ldap_user_dn=cn=orcladmin

#### 7.3.35 revokeProxyPerm

Revokes a proxy permission object.

##### Syntax

    revokeProxyPerm
         proxy_permission=<proxy permission name>
         domain_name=<domain name>
         realm_dn=<DN of the realm>
         [user_dn=<Distinguished name of user>]
         [group_dn=<Distinguished name of group>]
         ldap_host=<OID host>
         ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>
         keystore=<path to keystore>
         keystore_alias=<keystore password alias>
         ldap_user_dn=<DN of OID user>
         ldap_alias=<OID user password alias>
         wallet_location=<wallet location>

##### Options

Each option must be prefixed with a space. Multiple options can be concatenated and prefixed with single space.

| Option                                                        | Description                                                                         |
|:--------------------------------------------------------------|:------------------------------------------------------------------------------------|
| `proxy_permission=<proxy permission name>`                    | Name of the proxy permission.                                                       |
| `domain_name=<domain name>`                                   | Name of the domain.                                                                 |
| `realm_dn=<DN of the realm> `                                 | DN of the realm.                                                                    |
| `[user_dn=<Distinguished name of user>]`                      | DN of the user.                                                                     |
| `[group_dn=<Distinguished name of group>]`                    | DN of the group.                                                                    |
| `ldap_host=<OID host>`                                        | OID host.                                                                           |
| `ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>` | OID non ssl port or OID ssl port.                                                   |
| `keystore=<path to keystore>`                                 | Path to the keystore.                                                               |
| `keystore_alias=<keystore password alias>`                    | Keystore password taken from the Oracle wallet.                                     |
| `ldap_user_dn=<DN of OID user>`                               | DN of OID user which is used for authenticating and executing a command in the OID. |
| `ldap_alias=<OID user password alias>`                        | OID user password taken from the Oracle wallet.                                     |
| `wallet_location=<wallet location>`                           | Path to Oracle wallet when using the wallet.                                        |

##### Usage Notes

Proxy Authentication is a process typically employed in an environment with a middle tier such as a firewall, wherein the end user authenticates to the middle tier, which then authenticates to the directory on the user's behalf—as its proxy. The middle tier logs into the directory as a proxy user. A proxy user can switch identities and, once logged into the directory, switch to the end user's identity. It can perform operations on the end user's behalf, using the authorization appropriate to that particular end user.

##### Examples

Examples include revoking proxy permission object PROXY01 from the database user in the realm with and without SSL port connectivity to OID.

Example 7-107 Revoking Proxy Permission Object PROXY01 From the User with SSL Port Conectivity to OID and Using Passwords Stored in the Oracle Wallet

    eusm revokeProxyPerm proxy_permission=PROXY01 domain_name=OracleDefaultDomain realm_dn=dc=yy,dc=company,dc=com user_dn=cn=test_user,cn=Users,dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3131 keystore=/etc/myapp/keyStore keystore_alias=keystore1 ldap_user_dn=cn=orcladmin ldap_alias=ldabadmin1 wallet_location=/oracle/product/db_1/wallets

Example 7-108 Revoking Proxy Permission Object PROXY01 From the User with SSL Port Conectivity to OID

    eusm revokeProxyPerm proxy_permission=PROXY01 domain_name=OracleDefaultDomain realm_dn=dc=yy,dc=company,dc=com user_dn=cn=test_user,cn=Users,dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3131 keystore=/etc/myapp/keyStore ldap_user_dn=cn=orcladmin

Example 7-109 Revoking Proxy Permission Object PROXY01 From the User with non-SSL Port Conectivity to OID

    eusm revokeProxyPerm proxy_permission=PROXY01 domain_name=OracleDefaultDomain realm_dn=dc=yy,dc=company,dc=com user_dn=cn=test_user,cn=Users,dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3060 ldap_user_dn=cn=orcladmin

#### 7.3.36 listProxyPermissions

Lists proxy permissions. Input is the domain name.

##### Syntax

     listProxyPermissions
         domain_name=<domain name>
         realm_dn=<DN of the realm>
         ldap_host=<OID host>
         ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>
         keystore=<path to keystore>
         keystore_alias=<keystore password alias>
         ldap_user_dn=<DN of OID user>
         ldap_alias=<OID user password alias>
         wallet_location=<wallet location>

##### Options

Each option must be prefixed with a space. Multiple options can be concatenated and prefixed with single space.

| Option                                                        | Description                                                                         |
|:--------------------------------------------------------------|:------------------------------------------------------------------------------------|
| `domain_name=<domain name>`                                   | Name of the domain.                                                                 |
| `realm_dn=<DN of the realm> `                                 | DN of the realm.                                                                    |
| `ldap_host=<OID host>`                                        | OID host.                                                                           |
| `ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>` | OID non ssl port or OID ssl port.                                                   |
| `keystore=<path to keystore>`                                 | Path to the keystore.                                                               |
| `keystore_alias=<keystore password alias>`                    | Keystore password taken from the Oracle wallet.                                     |
| `ldap_user_dn=<DN of OID user>`                               | DN of OID user which is used for authenticating and executing a command in the OID. |
| `ldap_alias=<OID user password alias>`                        | OID user password taken from the Oracle wallet.                                     |
| `wallet_location=<wallet location>`                           | Path to Oracle wallet when using the wallet.                                        |

##### Usage Notes

Proxy Authentication is a process typically employed in an environment with a middle tier such as a firewall, wherein the end user authenticates to the middle tier, which then authenticates to the directory on the user's behalf—as its proxy. The middle tier logs into the directory as a proxy user. A proxy user can switch identities and, once logged into the directory, switch to the end user's identity. It can perform operations on the end user's behalf, using the authorization appropriate to that particular end user.

##### Examples

Examples include listing the proxy permissions for the enterprise domain in the realm with and without SSL port connectivity to OID.

Example 7-110 Listing the Proxy Permissions for the Domain with SSL Port Conectivity to OID and Using Passwords Stored in the Oracle Wallet

    eusm listProxyPermissions domain_name=OracleDefaultDomain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3131 keystore=/etc/myapp/keyStore keystore_alias=keystore1 ldap_user_dn=cn=orcladmin ldap_alias=ldabadmin1 wallet_location=/oracle/product/db_1/wallets

Example 7-111 Listing the Proxy Permissions for the Domain with SSL Port Conectivity to OID

    eusm listProxyPermissions domain_name=OracleDefaultDomain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3131 keystore=/etc/myapp/keyStore ldap_user_dn=cn=orcladmin

Example 7-112 Listing the Proxy Permissions for the Domain with non-SSL Port Conectivity to OID

    eusm listProxyPermissions domain_name=OracleDefaultDomain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3060 ldap_user_dn=cn=orcladmin

#### 7.3.37 listProxyPermissionsOfUser

Lists the proxy permissions for the user. Input is the user distinguished name.

##### Syntax

    listProxyPermissionsOfUser
         user_dn=<Distinguished name of user>
         realm_dn=<DN of the realm>
         ldap_host=<OID host>
         ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>
         keystore=<path to keystore>
         keystore_alias=<keystore password alias>
         ldap_user_dn=<DN of OID user>
         ldap_alias=<OID user password alias>
         wallet_location=<wallet location>

##### Options

Each option must be prefixed with a space. Multiple options can be concatenated and prefixed with single space.

| Option                                                        | Description                                                                         |
|:--------------------------------------------------------------|:------------------------------------------------------------------------------------|
| `user_dn=<Distinguished name of user>`                        | DN of the user.                                                                     |
| `realm_dn=<DN of the realm> `                                 | DN of the realm.                                                                    |
| `ldap_host=<OID host>`                                        | OID host.                                                                           |
| `ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>` | OID non ssl port or OID ssl port.                                                   |
| `keystore=<path to keystore>`                                 | Path to the keystore.                                                               |
| `keystore_alias=<keystore password alias>`                    | Keystore password taken from the Oracle wallet.                                     |
| `ldap_user_dn=<DN of OID user>`                               | DN of OID user which is used for authenticating and executing a command in the OID. |
| `ldap_alias=<OID user password alias> `                       | OID user password taken from the Oracle wallet.                                     |
| `wallet_location=<wallet location>`                           | Path to Oracle wallet when using the wallet.                                        |

##### Usage Notes

Proxy Authentication is a process typically employed in an environment with a middle tier such as a firewall, wherein the end user authenticates to the middle tier, which then authenticates to the directory on the user's behalf—as its proxy. The middle tier logs into the directory as a proxy user. A proxy user can switch identities and, once logged into the directory, switch to the end user's identity. It can perform operations on the end user's behalf, using the authorization appropriate to that particular end user.

##### Examples

Examples include listing the proxy permissions for the user in the realm with and without SSL port connectivity to OID.

Example 7-113 List the Proxy Permission for the User with SSL Port Conectivity to OID and Use Passwords Stored in the Oracle Wallet

    eusm listProxyPermissionsOfUser user_dn=cn=test_user,cn=Users,dc=yy,dc=company,dc=com realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3131 keystore=/etc/myapp/keyStore keystore_alias=keystore1 ldap_user_dn=cn=orcladmin ldap_alias=ldabadmin1 wallet_location=/oracle/product/db_1/wallets

Example 7-114 List the Proxy Permission for the User with SSL Port Conectivity to OID

    eusm listProxyPermissionsOfUser user_dn=cn=test_user,cn=Users,dc=yy,dc=company,dc=com realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3131 keystore=/etc/myapp/keyStore ldap_user_dn=cn=orcladmin

Example 7-115 List the Proxy Permission for the User with non-SSL Port Conectivity to OID

    eusm listProxyPermissionsOfUser user_dn=cn=test_user,cn=Users,dc=yy,dc=company,dc=com realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3060 ldap_user_dn=cn=orcladmin

#### 7.3.38 listProxyPermissionInfo

Lists the proxy permission information.

##### Syntax

    listProxyPermissionInfo
         proxy_permission=<proxy permission name>
         domain_name=<domain name>
         realm_dn=<DN of the realm>
         ldap_host=<OID host>
         ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>
         keystore=<path to keystore>
         keystore_alias=<keystore password alias>
         ldap_user_dn=<DN of OID user>
         ldap_alias=<OID user password alias>
         wallet_location=<wallet location>

##### Options

Each option must be prefixed with a space. Multiple options can be concatenated and prefixed with single space.

| Option                                                        | Description                                                                         |
|:--------------------------------------------------------------|:------------------------------------------------------------------------------------|
| `proxy_permission=<proxy permission name>`                    | Name of the proxy permission.                                                       |
| `domain_name=<domain name>`                                   | Name of the domain.                                                                 |
| `realm_dn=<DN of the realm> `                                 | DN of the realm.                                                                    |
| `ldap_host=<OID host>`                                        | OID host.                                                                           |
| `ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>` | OID non ssl port or OID ssl port.                                                   |
| `keystore=<path to keystore>`                                 | Path to the keystore.                                                               |
| `keystore_alias=<keystore password alias>`                    | Keystore password taken from the Oracle wallet.                                     |
| `ldap_user_dn=<DN of OID user>`                               | DN of OID user which is used for authenticating and executing a command in the OID. |
| `ldap_alias=<OID user password alias>`                        | OID user password taken from the Oracle wallet.                                     |
| `wallet_location=<wallet location>`                           | Path to Oracle wallet when using the wallet.                                        |

##### Usage Notes

Proxy Authentication is a process typically employed in an environment with a middle tier such as a firewall, wherein the end user authenticates to the middle tier, which then authenticates to the directory on the user's behalf—as its proxy. The middle tier logs into the directory as a proxy user. A proxy user can switch identities and, once logged into the directory, switch to the end user's identity. It can perform operations on the end user's behalf, using the authorization appropriate to that particular end user.

##### Examples

Examples include listing the proxy permission information for the enterprise domain in the realm with and without SSL port connectivity to OID.

Example 7-116 List Proxy Permission Information with SSL Port Conectivity to OID and Using Passwords Stored in the Oracle Wallet

    eusm listProxyPermissionInfo proxy_permission=PROXY01 domain_name=OracleDefaultDomain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3131 keystore=/etc/myapp/keyStore keystore_alias=keystore1 ldap_user_dn=cn=orcladmin ldap_alias=ldabadmin1 wallet_location=/oracle/product/db_1/wallets

Example 7-117 List Proxy Permission Information with SSL Port Conectivity to OID

    eusm listProxyPermissionInfo proxy_permission=PROXY01 domain_name=OracleDefaultDomain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3131 keystore=/etc/myapp/keyStore ldap_user_dn=cn=orcladmin

Example 7-118 List Proxy Permission Information with non-SSL Port Conectivity to OID

    eusm listProxyPermissionInfo proxy_permission=PROXY01 domain_name=OracleDefaultDomain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3060 ldap_user_dn=cn=orcladmin

#### 7.3.39 listTargetUsersInDB

Lists the target users in the database.

##### Syntax

    listTargetUsersInDB
         dbuser=<Database user name to connect>
         db_alias=<Database username password alias>
         dbconnect_string=<Database connect string>
         wallet_location=<wallet location>

##### Options

Each option must be prefixed with a space. Multiple options can be concatenated and prefixed with single space.

| Option                                         | Description                                                 |
|:-----------------------------------------------|:------------------------------------------------------------|
| `dbuser=<Database user name to connect>`       | The database user name to connect.                          |
| `db_alias=<Database username password alias> ` | Password of the database user taken from the Oracle wallet. |
| `dbconnect_string=<Database connect string>`   | Database connect string                                     |
| `wallet_location=<wallet location>`            | Path to Oracle wallet when using the wallet.                |

##### Usage Notes

None.

##### Examples

Listing the target users in the database.

Example 7-119 Listing the Target Users in the Database and Using Passwords Stored in the Oracle Wallet

    eusm listTargetUsersInDB dbuser=system db_alias=dbadmin1 dbconnect_string=zzzz10-yy.yy.company.com:1531:dbtest1 wallet_location=/oracle/product/db_1/wallets

Example 7-120 Listing the Target Users in the Database

    eusm listTargetUsersInDB dbuser=system dbconnect_string=zzzz10-yy.yy.company.com:1531:dbtest1

#### 7.3.40 setDBOIDAuth

Sets the database-OID authentication method.

##### Syntax

    setDBOIDAuth
         realm_dn=<DN of the realm>
         dboid_auth=<Default DB OID authentication>
         ldap_host=<OID host>
         ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>
         keystore=<path to keystore>
         keystore_alias=<keystore password alias>
         ldap_user_dn=<DN of OID user>
         ldap_alias=<OID user password alias>
         wallet_location=<wallet location>

##### Options

Each option must be prefixed with a space. Multiple options can be concatenated and prefixed with single space.

| Option                                                        | Description                                                                         |
|:--------------------------------------------------------------|:------------------------------------------------------------------------------------|
| `realm_dn=<DN of the realm> `                                 | DN of the realm.                                                                    |
| `dboid_auth=<Default DB OID authentication>`                  | Default DB OID authentication.                                                      |
| `ldap_host=<OID host>`                                        | OID host.                                                                           |
| `ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>` | OID non ssl port or OID ssl port.                                                   |
| `keystore=<path to keystore>`                                 | Path to the keystore.                                                               |
| `keystore_alias=<keystore password alias> `                   | Keystore password taken from the Oracle wallet.                                     |
| `ldap_user_dn=<DN of OID user>`                               | DN of OID user which is used for authenticating and executing a command in the OID. |
| `ldap_alias=<OID user password alias>`                        | OID user password taken from the Oracle wallet.                                     |
| `wallet_location=<wallet location>`                           | Path to Oracle wallet when using the wallet.                                        |

##### Usage Notes

The OID authentication method can be either  SSL or PASSWORD.

##### Examples

Examples include setting the database-OID authentication method in the realm with and without SSL port connectivity to OID.

Example 7-121 Setting the Database-OID Authentication Method with SSL Port Conectivity to OID and Using Passwords Stored in the Oracle Wallet

    eusm setDBOIDAuth realm_dn=dc=yy,dc=company,dc=com dboid_auth=SSL ldap_host=xxxxx.zz.company.com ldap_port=3131 keystore=/etc/myapp/keyStore keystore_alias=keystore1 ldap_user_dn=cn=orcladmin ldap_alias=ldabadmin1 wallet_location=/oracle/product/db_1/wallets

Example 7-122 Setting the Database-OID Authentication Method with SSL Port Conectivity to OID

    eusm setDBOIDAuth realm_dn=dc=yy,dc=company,dc=com dboid_auth=SSL ldap_host=xxxxx.zz.company.com ldap_port=3131 keystore=/etc/myapp/keyStore ldap_user_dn=cn=orcladmin

Example 7-123 Setting the Database-OID Authentication Method with non-SSL Port Conectivity to OID

    eusm setDBOIDAuth realm_dn=dc=yy,dc=company,dc=com dboid_auth=SSL ldap_host=xxxxx.zz.company.com ldap_port=3060 ldap_user_dn=cn=orcladmin

#### 7.3.41 listDBOIDAuth

Lists the database-OID authentication method.

##### Syntax

    listDBOIDAuth
         realm_dn=<DN of the realm>
         ldap_host=<OID host>
         ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>
         keystore=<path to keystore>
         keystore_alias=<keystore password alias>
         ldap_user_dn=<DN of OID user>
         ldap_alias=<OID user password alias>
         wallet_location=<wallet location>

##### Options

Each option must be prefixed with a space. Multiple options can be concatenated and prefixed with single space.

| Option                                                        | Description                                                                         |
|:--------------------------------------------------------------|:------------------------------------------------------------------------------------|
| `realm_dn=<DN of the realm> `                                 | DN of the realm.                                                                    |
| `ldap_host=<OID host>`                                        | OID host.                                                                           |
| `ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>` | OID non ssl port or OID ssl port.                                                   |
| `keystore=<path to keystore>`                                 | Path to the keystore.                                                               |
| `keystore_alias=<keystore password alias>`                    | Keystore password taken from the Oracle wallet.                                     |
| `ldap_user_dn=<DN of OID user>`                               | DN of OID user which is used for authenticating and executing a command in the OID. |
| `ldap_alias=<OID user password alias>`                        | OID user password taken from the Oracle wallet.                                     |
| `wallet_location=<wallet location>`                           | Path to Oracle wallet when using the wallet.                                        |

##### Usage Notes

The OID authentication method can be either  SSL or PASSWORD.

##### Examples

Examples include listing the database-OID authentication method in the realm with and without SSL port connectivity to OID.

Example 7-124 Listing the Database-OID Authentication Method with SSL Port Conectivity to OID and Using Passwords Stored in the Oracle Wallet

    eusm listDBOIDAuth realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3131 keystore=/etc/myapp/keyStore keystore_alias=keystore1 ldap_user_dn=cn=orcladmin ldap_alias=ldabadmin1 wallet_location=/oracle/product/db_1/wallets

Example 7-125 Listing the Database-OID Authentication Method with SSL Port Conectivity to OID

    eusm listDBOIDAuth realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3131 keystore=/etc/myapp/keyStore ldap_user_dn=cn=orcladmin

Example 7-126 Listing the Database-OID Authentication Method with non-SSL Port Conectivity to OID

    eusm listDBOIDAuth realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3060 ldap_user_dn=cn=orcladmin

#### 7.3.42 addToPwdAccessibleDomains

Adds a domain to the password accessible domains group in the realm.

##### Syntax

    addToPwdAccessibleDomains
         realm_dn=<DN of the realm>
         domain_name=<name of enterprise domain>
         ldap_host=<OID host>
         ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>
         keystore=<path to keystore>
         keystore_alias=<keystore password alias>
         ldap_user_dn=<DN of OID user>
         ldap_alias=<OID user password alias>
         wallet_location=<wallet location>

##### Options

Each option must be prefixed with a space. Multiple options can be concatenated and prefixed with single space.

| Option                                                        | Description                                                                         |
|:--------------------------------------------------------------|:------------------------------------------------------------------------------------|
| `realm_dn=<DN of the realm> `                                 | DN of the realm.                                                                    |
| `domain_name=<domain name>`                                   | Name of the domain.                                                                 |
| `ldap_host=<OID host>`                                        | OID host.                                                                           |
| `ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>` | OID non ssl port or OID ssl port.                                                   |
| `keystore=<path to keystore>`                                 | Path to the keystore.                                                               |
| `keystore_alias=<keystore password alias>`                    | Keystore password taken from the Oracle wallet.                                     |
| `ldap_user_dn=<DN of OID user>`                               | DN of OID user which is used for authenticating and executing a command in the OID. |
| `ldap_alias=<OID user password alias>`                        | OID user password taken from the Oracle wallet.                                     |
| `wallet_location=<wallet location>`                           | Path to Oracle wallet when using the wallet.                                        |

##### Usage Notes

None.

##### Examples

Examples include adding to password accessible domains in the realm with and without SSL port connectivity to OID.

Example 7-127 Adding to Password Accessible Domains with SSL Port Conectivity to OID and Using Passwords Stored in the Oracle Wallet

    eusm addToPwdAccessibleDomains domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3131 keystore=/etc/myapp/keyStore keystore_alias=keystore1 ldap_user_dn=cn=orcladmin ldap_alias=ldabadmin1 wallet_location=/oracle/product/db_1/wallets

Example 7-128 Adding to Password Accessible Domains with SSL Port Conectivity to OID

    eusm addToPwdAccessibleDomains domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3131 keystore=/etc/myapp/keyStore ldap_user_dn=cn=orcladmin

Example 7-129 Adding to Password Accessible Domains with non-SSL Port Conectivity to OID

    eusm addToPwdAccessibleDomains domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3060 ldap_user_dn=cn=orcladmin

#### 7.3.43 removeFromPwdAccessibleDomains

Removes a domain from the password accessible domains group in the realm.

##### Syntax

    removeFromPwdAccessibleDomains
         realm_dn=<DN of the realm>
         domain_name=<name of enterprise domain>
         ldap_host=<OID host>
         ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>
         keystore=<path to keystore>
         keystore_alias=<keystore password alias>
         ldap_user_dn=<DN of OID user>
         ldap_alias=<OID user password alias>
         wallet_location=<wallet location>

##### Options

Each option must be prefixed with a space. Multiple options can be concatenated and prefixed with single space

| Option                                                        | Description                                                                         |
|:--------------------------------------------------------------|:------------------------------------------------------------------------------------|
| `realm_dn=<DN of the realm> `                                 | DN of the realm.                                                                    |
| `domain_name=<domain name>`                                   | Name of the domain.                                                                 |
| `ldap_host=<OID host>`                                        | OID host.                                                                           |
| `ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>` | OID non ssl port or OID ssl port.                                                   |
| `keystore=<path to keystore>`                                 | Path to the keystore.                                                               |
| `keystore_alias=<keystore password alias>`                    | Keystore password taken from the Oracle wallet.                                     |
| `ldap_user_dn=<DN of OID user>`                               | DN of OID user which is used for authenticating and executing a command in the OID. |
| `ldap_alias=<OID user password alias>`                        | OID user password taken from the Oracle wallet.                                     |
| `wallet_location=<wallet location>`                           | Path to Oracle wallet when using the wallet.                                        |

##### Usage Notes

None.

##### Examples

Examples include removing from password accessible domains in the realm with and without SSL port connectivity to OID.

Example 7-130 Removing from Password Accessible Domains with SSL Port Conectivity to OID and Using Passwords Stored in the Oracle Wallet

    eusm removeFromPwdAccessibleDomains domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3131 keystore=/etc/myapp/keyStore keystore_alias=keystore1 ldap_user_dn=cn=orcladmin ldap_alias=ldabadmin1 wallet_location=/oracle/product/db_1/wallets

Example 7-131 Removing from Password Accessible Domains with SSL Port Conectivity to OID

    eusm removeFromPwdAccessibleDomains domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3131 keystore=/etc/myapp/keyStore ldap_user_dn=cn=orcladmin

Example 7-132 Removing from Password Accessible Domains with non-SSL Port Conectivity to OID

    eusm removeFromPwdAccessibleDomains domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3060 ldap_user_dn=cn=orcladmin

#### 7.3.44 listPwdAccessibleDomains

Lists the password accessible domains in the realm.

##### Syntax

    listPwdAccessibleDomains
         realm_dn=<DN of the realm>
         ldap_host=<OID host>
         ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>
         keystore=<path to keystore>
         keystore_alias=<keystore password alias>
         ldap_user_dn=<DN of OID user>
         ldap_alias=<OID user password alias>
         wallet_location=<wallet location>

##### Options

Each option must be prefixed with a space. Multiple options can be concatenated and prefixed with single space.

| Option                                                        | Description                                                                         |
|:--------------------------------------------------------------|:------------------------------------------------------------------------------------|
| `realm_dn=<DN of the realm> `                                 | DN of the realm.                                                                    |
| `ldap_host=<OID host>`                                        | OID host.                                                                           |
| `ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>` | OID non ssl port or OID ssl port.                                                   |
| `keystore=<path to keystore>`                                 | Path to the keystore.                                                               |
| `keystore_alias=<keystore password alias>`                    | Keystore password taken from the Oracle wallet.                                     |
| `ldap_user_dn=<DN of OID user>`                               | DN of OID user which is used for authenticating and executing a command in the OID. |
| `ldap_alias=<OID user password alias>`                        | OID user password taken from the Oracle wallet.                                     |
| `wallet_location=<wallet location>`                           | Path to Oracle wallet when using the wallet.                                        |

##### Usage Notes

None.

##### Examples

Examples include listing the password accessible domains in the realm with and without SSL port connectivity to OID.

Example 7-133 Listing the Password Accessible Domains with SSL Port Conectivity to OID and Using Passwords Stored in the Oracle Wallet

    eusm listPwdAccessibleDomains realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3131 keystore=/etc/myapp/keyStore keystore_alias=keystore1 ldap_user_dn=cn=orcladmin ldap_alias=ldabadmin1 wallet_location=/oracle/product/db_1/wallets

Example 7-134 Listing the Password Accessible Domains with SSL Port Conectivity to OID

    eusm listPwdAccessibleDomains realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3131 keystore=/etc/myapp/keyStore ldap_user_dn=cn=orcladmin

Example 7-135 Listing the Password Accessible Domains with non-SSL Port Conectivity to OID

    eusm listPwdAccessibleDomains realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3060 ldap_user_dn=cn=orcladmin

#### 7.3.45 listRealmCommonAttr

Lists the realm common attributes.

##### Syntax

    listRealmCommonAttr
         realm_dn=<DN of the realm>
         ldap_host=<OID host>
         ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>
         keystore=<path to keystore>
         keystore_alias=<keystore password alias>
         ldap_user_dn=<DN of OID user>
         ldap_alias=<OID user password alias>
         wallet_location=<wallet location>

##### Options

Each option must be prefixed with a space. Multiple options can be concatenated and prefixed with single space.

| Option                                                        | Description                                                                         |
|:--------------------------------------------------------------|:------------------------------------------------------------------------------------|
| `realm_dn=<DN of the realm> `                                 | DN of the realm.                                                                    |
| `ldap_host=<OID host>`                                        | OID host.                                                                           |
| `ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>` | OID non ssl port or OID ssl port.                                                   |
| `keystore=<path to keystore>`                                 | Path to the keystore.                                                               |
| `keystore_alias=<keystore password alias>`                    | Keystore password taken from the Oracle wallet.                                     |
| `ldap_user_dn=<DN of OID user>`                               | DN of OID user which is used for authenticating and executing a command in the OID. |
| `ldap_alias=<OID user password alias>`                        | OID user password taken from the Oracle wallet.                                     |
| `wallet_location=<wallet location>`                           | Path to Oracle wallet when using the wallet.                                        |

##### Usage Notes

None.

##### Examples

Examples include listing the realm common attributes with and without SSL port connectivity to OID.

Example 7-136 Listing the Realm Common Attributes with SSL Port Conectivity to OID and Using Passwords Stored in the Oracle Wallet

    eusm listRealmCommonAttr realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3131 keystore=/etc/myapp/keyStore keystore_alias=keystore1 ldap_user_dn=cn=orcladmin ldap_alias=ldabadmin1 wallet_location=/oracle/product/db_1/wallets

Example 7-137 Listing the Realm Common Attributes with SSL Port Conectivity to OID

    eusm listRealmCommonAttr realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3131 keystore=/etc/myapp/keyStore ldap_user_dn=cn=orcladmin

Example 7-138 Listing the Realm Common Attributes with non-SSL Port Conectivity to OID

    eusm listRealmCommonAttr realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3060 ldap_user_dn=cn=orcladmin

#### 7.3.46 createAppCtxNamespace

Adds a new namespace.

##### Syntax

    createAppCtxNamespace
         namespace=<namespace name>
         domain_name=<domain name>
         realm_dn=<DN of the realm>
         ldap_host=<OID host>
         ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>
         keystore=<path to keystore>
         keystore_alias=<keystore password alias>
         ldap_user_dn=<DN of OID user>
         ldap_alias=<OID user password alias>
         wallet_location=<wallet location>

##### Options

Each option must be prefixed with a space. Multiple options can be concatenated and prefixed with single space.

| Option                                                        | Description                                                                         |
|:--------------------------------------------------------------|:------------------------------------------------------------------------------------|
| `namespace=<namespace name>`                                  | Name of the namespace.                                                              |
| `domain_name=<domain name>`                                   | Name of the domain.                                                                 |
| `realm_dn=<DN of the realm> `                                 | DN of the realm.                                                                    |
| `ldap_host=<OID host>`                                        | OID host.                                                                           |
| `ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>` | OID non ssl port or OID ssl port.                                                   |
| `keystore=<path to keystore>`                                 | Path to the keystore.                                                               |
| `keystore_alias=<keystore password alias>`                    | Keystore password taken interactively at the prompt or from the Oracle wallet.      |
| `ldap_user_dn=<DN of OID user>`                               | DN of OID user which is used for authenticating and executing a command in the OID. |
| `ldap_alias=<OID user password alias>`                        | OID user password taken interactively at the prompt or from the Oracle wallet.      |
| `wallet_location=<wallet location>`                           | Path to Oracle wallet when using the wallet.                                        |

##### Usage Notes

None.

##### Examples

Examples include adding a new domain namespace in the realm with and without SSL port connectivity to OID.

Example 7-139 Adding a New Domain Namespace with SSL Port Conectivity to OID and Using Passwords Stored in the Oracle Wallet

    eusm createAppCtxNamespace namespace=ns1 domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3131 keystore=/etc/myapp/keyStore keystore_alias=keystore1 ldap_user_dn=cn=orcladmin ldap_alias=ldabadmin1 wallet_location=/oracle/product/db_1/wallets

Example 7-140 Adding a New Domain Namespace with SSL Port Conectivity to OID

    eusm createAppCtxNamespace namespace=ns1 domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3131 keystore=/etc/myapp/keyStore ldap_user_dn=cn=orcladmin

Example 7-141 Adding a New Domain Namespace with non-SSL Port Conectivity to OID

    eusm createAppCtxNamespace namespace=ns1 domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3060 ldap_user_dn=cn=orcladmin

#### 7.3.47 deleteAppCtxNamespace

Deletes a namespace.

##### Syntax

    deleteAppCtxNamespace
         namespace=<namespace name>
         domain_name=<domain name>
         realm_dn=<DN of the realm>
         ldap_host=<OID host>
         ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>
         keystore=<path to keystore>
         keystore_alias=<keystore password alias>
         ldap_user_dn=<DN of OID user>
         ldap_alias=<OID user password alias>
         wallet_location=<wallet location>

##### Options

Each option must be prefixed with a space. Multiple options can be concatenated and prefixed with single space.

| Option                                                        | Description                                                                         |
|:--------------------------------------------------------------|:------------------------------------------------------------------------------------|
| `namespace=<namespace name>`                                  | Name of the namespace.                                                              |
| `domain_name=<domain name>`                                   | Name of the domain.                                                                 |
| `realm_dn=<DN of the realm> `                                 | DN of the realm.                                                                    |
| `ldap_host=<OID host>`                                        | OID host.                                                                           |
| `ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>` | OID non ssl port or OID ssl port.                                                   |
| `keystore=<path to keystore>`                                 | Path to the keystore.                                                               |
| `keystore_alias=<keystore password alias>`                    | Keystore password taken from the Oracle wallet.                                     |
| `ldap_user_dn=<DN of OID user>`                               | DN of OID user which is used for authenticating and executing a command in the OID. |
| `ldap_alias=<OID user password alias>`                        | OID user password taken from the Oracle wallet.                                     |
| `wallet_location=<wallet location>`                           | Path to Oracle wallet when using the wallet.                                        |

##### Usage Notes

None.

##### Examples

Examples include deleting a domain namespace from the realm with and without SSL port connectivity to OID.

Example 7-142 Deleting a Domain Namespace with SSL Port Conectivity to OID and Using Passwords Stored in the Oracle Wallet

    eusm deleteAppCtxNamespace namespace=ns1 domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3131 keystore=/etc/myapp/keyStore keystore_alias=keystore1 ldap_user_dn=cn=orcladmin ldap_alias=ldabadmin1 wallet_location=/oracle/product/db_1/wallets

Example 7-143 Deleting a Domain Namespace with SSL Port Conectivity to OID

    eusm deleteAppCtxNamespace namespace=ns1 domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3131 keystore=/etc/myapp/keyStore ldap_user_dn=cn=orcladmin

Example 7-144 Deleting a Domain Namespace with non-SSL Port Conectivity to OID

    eusm deleteAppCtxNamespace namespace=ns1 domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3060 ldap_user_dn=cn=orcladmin

#### 7.3.48 listAppCtxNamespaces

Lists the namespaces.

##### Syntax

    listAppCtxNamespaces
         domain_name=<domain name>
         realm_dn=<DN of the realm>
         ldap_host=<OID host>
         ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>
         keystore=<path to keystore>
         keystore_alias=<keystore password alias>
         ldap_user_dn=<DN of OID user>
         ldap_alias=<OID user password alias>
         wallet_location=<wallet location>

##### Options

Each option must be prefixed with a space. Multiple options can be concatenated and prefixed with single space.

| Option                                                        | Description                                                                         |
|:--------------------------------------------------------------|:------------------------------------------------------------------------------------|
| `domain_name=<domain name>`                                   | Name of the domain.                                                                 |
| `realm_dn=<DN of the realm> `                                 | DN of the realm.                                                                    |
| `ldap_host=<OID host>`                                        | OID host.                                                                           |
| `ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>` | OID non ssl port or OID ssl port.                                                   |
| `keystore=<path to keystore>`                                 | Path to the keystore.                                                               |
| `keystore_alias=<keystore password alias>`                    | Keystore password taken from the Oracle wallet.                                     |
| `ldap_user_dn=<DN of OID user>`                               | DN of OID user which is used for authenticating and executing a command in the OID. |
| `ldap_alias=<OID user password alias>`                        | OID user password taken from the Oracle wallet.                                     |
| `wallet_location=<wallet location>`                           | Path to Oracle wallet when using the wallet.                                        |

##### Usage Notes

None.

##### Examples

Examples include listing the domain namespaces in the realm with and without SSL port connectivity to OID.

Example 7-145 Listing the Namespaces with SSL Port Conectivity to OID and Using Passwords Stored in the Oracle Wallet

    eusm listAppCtxNamespaces domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3131 keystore=/etc/myapp/keyStore keystore_alias=keystore1 ldap_user_dn=cn=orcladmin ldap_alias=ldabadmin1 wallet_location=/oracle/product/db_1/wallets

Example 7-146 Listing the Namespaces with SSL Port Conectivity to OID

    eusm listAppCtxNamespaces domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3131 keystore=/etc/myapp/keyStore ldap_user_dn=cn=orcladmin

Example 7-147 Listing the Namespaces with non-SSL Port Conectivity to OID

    eusm listAppCtxNamespaces domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3060 ldap_user_dn=cn=orcladmin

#### 7.3.49 createAppCtxAttribute

Adds a new attribute.

##### Syntax

    createAppCtxAttribute
         attribute_name=<attribute name>
         namespace=<namespace name>
         domain_name=<domain name>
         realm_dn=<DN of the realm>
         ldap_host=<OID host>
         ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>
         keystore=<path to keystore>
         keystore_alias=<keystore password alias>
         ldap_user_dn=<DN of OID user>
         ldap_alias=<OID user password alias>
         wallet_location=<wallet location>

##### Options

Each option must be prefixed with a space. Multiple options can be concatenated and prefixed with single space.

| Option                                                        | Description                                                                         |
|:--------------------------------------------------------------|:------------------------------------------------------------------------------------|
| `attribute_name=<attribute name>`                             | Name of the attribute.                                                              |
| `namespace=<namespace name>`                                  | Name of the namespace.                                                              |
| `domain_name=<domain name>`                                   | Name of the domain.                                                                 |
| `realm_dn=<DN of the realm> `                                 | DN of the realm.                                                                    |
| `ldap_host=<OID host>`                                        | OID host.                                                                           |
| `ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>` | OID non ssl port or OID ssl port.                                                   |
| `keystore=<path to keystore>`                                 | Path to the keystore.                                                               |
| `keystore_alias=<keystore password alias>`                    | Keystore password taken from the Oracle wallet.                                     |
| `ldap_user_dn=<DN of OID user>`                               | DN of OID user which is used for authenticating and executing a command in the OID. |
| `ldap_alias=<OID user password alias>`                        | OID user password taken from the Oracle wallet.                                     |
| `wallet_location=<wallet location>`                           | Path to Oracle wallet when using the wallet.                                        |

##### Usage Notes

None.

##### Examples

Examples include adding a new attribute to a domain namespace in the realm with and without SSL port connectivity to OID.

Example 7-148 Adding a New Attribute with SSL Port Conectivity to OID and Using Passwords Stored in the Oracle Wallet

    eusm createAppCtxAttribute attribute_name=attr1 namespace=ns1 domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3131 keystore=/etc/myapp/keyStore keystore_alias=keystore1 ldap_user_dn=cn=orcladmin ldap_alias=ldabadmin1 wallet_location=/oracle/product/db_1/wallets

Example 7-149 Adding a New Attribute with SSL Port Conectivity to OID

    eusm createAppCtxAttribute attribute_name=attr1 namespace=ns1 domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3131 keystore=/etc/myapp/keyStore ldap_user_dn=cn=orcladmin

Example 7-150 Adding a New Attribute with non-SSL Port Conectivity to OID

    eusm createAppcCtxAttribute attribute_name=attr1 namespace=ns1 domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3060 ldap_user_dn=cn=orcladmin

#### 7.3.50 deleteAppCtxAttribute

Deletes an attribute.

##### Syntax

    deleteAppCtxAttribute
         attribute_name=<attribute name>
         namespace=<namespace name>
         domain_name=<domain name>
         realm_dn=<DN of the realm>
         ldap_host=<OID host>
         ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>
         keystore=<path to keystore>
         keystore_alias=<keystore password alias>
         ldap_user_dn=<DN of OID user>
         ldap_alias=<OID user password alias>
         wallet_location=<wallet location>

##### Options

Each option must be prefixed with a space. Multiple options can be concatenated and prefixed with single space.

| Option                                                        | Description                                                                         |
|:--------------------------------------------------------------|:------------------------------------------------------------------------------------|
| `attribute_name=<attribute name>`                             | Name of the attribute.                                                              |
| `namespace=<namespace name>`                                  | Name of the namespace.                                                              |
| `domain_name=<domain name>`                                   | Name of the domain.                                                                 |
| `realm_dn=<DN of the realm> `                                 | DN of the realm.                                                                    |
| `ldap_host=<OID host>`                                        | OID host.                                                                           |
| `ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>` | OID non ssl port or OID ssl port.                                                   |
| `keystore=<path to keystore>`                                 | Path to the keystore.                                                               |
| `keystore_alias=<keystore password alias>`                    | Keystore password taken from the Oracle wallet.                                     |
| `ldap_user_dn=<DN of OID user>`                               | DN of OID user which is used for authenticating and executing a command in the OID. |
| `ldap_alias=<OID user password alias>`                        | OID user password taken from the Oracle wallet.                                     |
| `wallet_location=<wallet location>`                           | Path to Oracle wallet when using the wallet.                                        |

##### Usage Notes

None.

##### Examples

Examples include deleting an attribute from a domain namespace in the realm with and without SSL port connectivity to OID.

Example 7-151 Deleting Attributes with SSL Port Conectivity to OID and Using Passwords Stored in the Oracle Wallet

    eusm deleteAppCtxAttribute attribute_name=attr1 namespace=ns1 domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3131 keystore=/etc/myapp/keyStore keystore_alias=keystore1 ldap_user_dn=cn=orcladmin ldap_alias=ldabadmin1 wallet_location=/oracle/product/db_1/wallets

Example 7-152 Deleting Attributes with SSL Port Conectivity to OID

    eusm deleteAppCtxAttribute attribute_name=attr1 namespace=ns1 domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3131 keystore=/etc/myapp/keyStore ldap_user_dn=cn=orcladmin

Example 7-153 Deleting Attributes with non-SSL Port Conectivity to OID

    eusm deleteAppCtxAttribute attribute_name=attr1 namespace=ns1 domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3060 ldap_user_dn=cn=orcladmin

#### 7.3.51 listAppCtxAttributes

Lists the attributes.

##### Syntax

    listAppCtxAttributes
         namespace=<namespace name>
         domain_name=<domain name>
         realm_dn=<DN of the realm>
         ldap_host=<OID host>
         ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>
         keystore=<path to keystore>
         keystore_alias=<keystore password alias>
         ldap_user_dn=<DN of OID user>
         ldap_alias=<OID user password alias>
         wallet_location=<wallet location>

##### Options

Each option must be prefixed with a space. Multiple options can be concatenated and prefixed with single space.

| Option                                                        | Description                                                                         |
|:--------------------------------------------------------------|:------------------------------------------------------------------------------------|
| `namespace=<namespace name>`                                  | Name of the namespace.                                                              |
| `domain_name=<domain name>`                                   | Name of the domain.                                                                 |
| `realm_dn=<DN of the realm> `                                 | DN of the realm.                                                                    |
| `ldap_host=<OID host>`                                        | OID host.                                                                           |
| `ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>` | OID non ssl port or OID ssl port.                                                   |
| `keystore=<path to keystore>`                                 | Path to the keystore.                                                               |
| `keystore_alias=<keystore password alias>`                    | Keystore password taken from the Oracle wallet.                                     |
| `ldap_user_dn=<DN of OID user>`                               | DN of OID user which is used for authenticating and executing a command in the OID. |
| `ldap_alias=<OID user password alias>`                        | OID user password taken from the Oracle wallet.                                     |
| `wallet_location=<wallet location>`                           | Path to Oracle wallet when using the wallet.                                        |

##### Usage Notes

None.

##### Examples

Examples include listing the domain namespace attributes in the realm with and without SSL port connectivity to OID.

Example 7-154 Listing Attributes with SSL Port Conectivity to OID and Using Passwords Stored in the Oracle Wallet

    eusm listAppCtxAttributes namespace=ns1 domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3131 keystore=/etc/myapp/keyStore keystore_alias=keystore1 ldap_user_dn=cn=orcladmin ldap_alias=ldabadmin1 wallet_location=/oracle/product/db_1/wallets

Example 7-155 Listing Attributes with SSL Port Conectivity to OID

    eusm listAppCtxAttributes namespace=ns1 domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3131 keystore=/etc/myapp/keyStore ldap_user_dn=cn=orcladmin

Example 7-156 Example Title with non-SSL Port Conectivity to OID

    eusm listAppCtxAttributes namespace=ns1 domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3060 ldap_user_dn=cn=orcladmin

#### 7.3.52 createAppCtxAttributeValue

Adds a new attribute value.

##### Syntax

    createAppCtxAttributeValue
         attribute_value=<value of the attribute>
         attribute_name=<attribute name>
         namespace=<namespace name>
         domain_name=<domain name>
         realm_dn=<DN of the realm>
         ldap_host=<OID host>
         ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>
         keystore=<path to keystore>
         keystore_alias=<keystore password alias>
         ldap_user_dn=<DN of OID user>
         ldap_alias=<OID user password alias>
         wallet_location=<wallet location>

##### Options

Each option must be prefixed with a space. Multiple options can be concatenated and prefixed with single space.

| Option                                                        | Description                                                                         |
|:--------------------------------------------------------------|:------------------------------------------------------------------------------------|
| `attribute_value=<value of the attribute>`                    | Value of the attribute.                                                             |
| `attribute_name=<attribute name>`                             | Name of the attribute.                                                              |
| `namespace=<namespace name>`                                  | Name of the namespace.                                                              |
| `domain_name=<domain name>`                                   | Name of the domain.                                                                 |
| `realm_dn=<DN of the realm> `                                 | DN of the realm.                                                                    |
| `ldap_host=<OID host>`                                        | OID host.                                                                           |
| `ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>` | OID non ssl port or OID ssl port.                                                   |
| `keystore=<path to keystore>`                                 | Path to the keystore.                                                               |
| `keystore_alias=<keystore password alias>`                    | Keystore password taken from the Oracle wallet.                                     |
| `ldap_user_dn=<DN of OID user>`                               | DN of OID user which is used for authenticating and executing a command in the OID. |
| `ldap_alias=<OID user password alias>`                        | OID user password taken from the Oracle wallet.                                     |
| `wallet_location=<wallet location>`                           | Path to Oracle wallet when using the wallet.                                        |

##### Usage Notes

None.

##### Examples

Examples include adding a new attribute value to an attribute to a domain namespace in the realm with and without SSL port connectivity to OID.

Example 7-157 Adding a New Attribute Value with SSL Port Conectivity to OID and Using Passwords Stored in the Oracle Wallet

    eusm createAppCtxAttributeValue attribute_value=val1 attribute_name=attr1 namespace=ns1 domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3131 keystore=/etc/myapp/keyStore keystore_alias=keystore1 ldap_user_dn=cn=orcladmin ldap_alias=ldabadmin1 wallet_location=/oracle/product/db_1/wallets

Example 7-158 Adding a New Attribute Value with SSL Port Conectivity to OID

    eusm createAppCtxAttributeValue attribute_value=val1 attribute_name=attr1 namespace=ns1 domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3131 keystore=/etc/myapp/keyStore ldap_user_dn=cn=orcladmin

Example 7-159 Adding a New Attribute Value with non-SSL Port Conectivity to OID

    eusm createAppCtxAttributeValue attribute_value=val1 attribute_name=attr1 namespace=ns1 domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3060 ldap_user_dn=cn=orcladmin

#### 7.3.53 deleteAppCtxAttributeValue

Deletes an attribute value.

##### Syntax

    deleteAppCtxAttributeValue
         attribute_value=<value of the attribute>
         attribute_name=<attribute name>
         namespace=<namespace name>
         domain_name=<domain name>
         realm_dn=<DN of the realm>
         ldap_host=<OID host>
         ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>
         keystore=<path to keystore>
         keystore_alias=<keystore password alias>
         ldap_user_dn=<DN of OID user>
         ldap_alias=<OID user password alias>
         wallet_location=<wallet location>

##### Options

Each option must be prefixed with a space. Multiple options can be concatenated and prefixed with single space.

| Option                                                        | Description                                                                         |
|:--------------------------------------------------------------|:------------------------------------------------------------------------------------|
| `attribute_value=<value of the attribute>`                    | Value of the attribute.                                                             |
| `attribute_name=<attribute name>`                             | Name of the attribute.                                                              |
| `namespace=<namespace name>`                                  | Name of the namespace.                                                              |
| `domain_name=<domain name>`                                   | Name of the domain.                                                                 |
| `realm_dn=<DN of the realm> `                                 | DN of the realm.                                                                    |
| `ldap_host=<OID host>`                                        | OID host.                                                                           |
| `ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>` | OID non ssl port or OID ssl port.                                                   |
| `keystore=<path to keystore>`                                 | Path to the keystore.                                                               |
| `keystore_alias=<keystore password alias>`                    | Keystore password taken from the Oracle wallet.                                     |
| `ldap_user_dn=<DN of OID user>`                               | DN of OID user which is used for authenticating and executing a command in the OID. |
| `ldap_alias=<OID user password alias>`                        | OID user password taken from the Oracle wallet.                                     |
| `wallet_location=<wallet location>`                           | Path to Oracle wallet when using the wallet.                                        |

##### Usage Notes

None.

##### Examples

Examples include deleting an attribute value from an attribute in a domain namespace in the realm with and without SSL port connectivity to OID.

Example 7-160 Deleting an Attribute Value with SSL Port Conectivity to OID and Using Passwords Stored in the Oracle Wallet

    eusm deleteAppCtxAttributeValue attribute_value=val1 attribute_name=attr1 namespace=ns1 domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3131 keystore=/etc/myapp/keyStore keystore_alias=keystore1 ldap_user_dn=cn=orcladmin ldap_alias=ldabadmin1 wallet_location=/oracle/product/db_1/wallets

Example 7-161 Deleting an Attribute Value with SSL Port Conectivity to OID

    eusm deleteAppCtxAttributeValue attribute_value=val1 attribute_name=attr1 namespace=ns1 domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3131 keystore=/etc/myapp/keyStore ldap_user_dn=cn=orcladmin

Example 7-162 Deleting an Attribute Value with non-SSL Port Conectivity to OID

    eusm deleteAppCtxAttributeValue attribute_value=val1 attribute_name=attr1 namespace=ns1 domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3060 ldap_user_dn=cn=orcladmin

#### 7.3.54 listAppCtxAttributeValues

Lists the attribute values.

##### Syntax

    listAppCtxAttributeValues
         attribute_name=<attribute name>
         namespace=<namespace name>
         domain_name=<domain name>
         realm_dn=<DN of the realm>
         ldap_host=<OID host>
         ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>
         keystore=<path to keystore>
         keystore_alias=<keystore password alias>
         ldap_user_dn=<DN of OID user>
         ldap_alias=<OID user password alias>
         wallet_location=<wallet location>

##### Options

Each option must be prefixed with a space. Multiple options can be concatenated and prefixed with single space.

| Option                                                        | Description                                                                         |
|:--------------------------------------------------------------|:------------------------------------------------------------------------------------|
| `attribute_name=<attribute name>`                             | Name of the attribute.                                                              |
| `namespace=<namespace name>`                                  | Name of the namespace.                                                              |
| `domain_name=<domain name>`                                   | Name of the domain.                                                                 |
| `realm_dn=<DN of the realm> `                                 | DN of the realm.                                                                    |
| `ldap_host=<OID host>`                                        | OID host.                                                                           |
| `ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>` | OID non ssl port or OID ssl port.                                                   |
| `keystore=<path to keystore>`                                 | Path to the keystore.                                                               |
| `keystore_alias=<keystore password alias>`                    | Keystore password taken from the Oracle wallet.                                     |
| `ldap_user_dn=<DN of OID user>`                               | DN of OID user which is used for authenticating and executing a command in the OID. |
| `ldap_alias=<OID user password alias>`                        | OID user password taken from the Oracle wallet.                                     |
| `wallet_location=<wallet location>`                           | Path to Oracle wallet when using the wallet.                                        |

##### Usage Notes

None.

##### Examples

Examples include listing the attribute values for an attribute for a domain namespace in the realm with and without SSL port connectivity to OID.

Example 7-163 Listing the Attribute Values with SSL Port Conectivity to OID and Using Passwords Stored in the Oracle Wallet

    eusm listAppCtxAttributeValues attribute_name=attr1 namespace=ns1 domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3131 keystore=/etc/myapp/keyStore keystore_alias=keystore1 ldap_user_dn=cn=orcladmin ldap_alias=ldabadmin1 wallet_location=/oracle/product/db_1/wallets

Example 7-164 Listing the Attribute Values with SSL Port Conectivity to OID

    eusm listAppCtxAttributeValues attribute_name=attr1 namespace=ns1 domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3131 keystore=/etc/myapp/keyStore ldap_user_dn=cn=orcladmin

Example 7-165 Listing the Attribute Values with non-SSL Port Conectivity to OID

    eusm listAppCtxAttributeValues attribute_name=attr1 namespace=ns1 domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3060 ldap_user_dn=cn=orcladmin

#### 7.3.55 createAppCtxUsers

Adds a new user for an attribute value.

##### Syntax

    createAppCtxUsers
         user_dn=<Distinguished name of user>
         attribute_value=<value of the attribute>
         attribute_name=<attribute name>
         namespace=<namespace name>
         domain_name=<domain name>
         realm_dn=<DN of the realm>
         ldap_host=<OID host>
         ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>
         keystore=<path to keystore>
         keystore_alias=<keystore password alias>
         ldap_user_dn=<DN of OID user>
         ldap_alias=<OID user password alias>
         wallet_location=<wallet location>

##### Options

Each option must be prefixed with a space. Multiple options can be concatenated and prefixed with single space.

| Option                                                        | Description                                                                         |
|:--------------------------------------------------------------|:------------------------------------------------------------------------------------|
| `user_dn=<Distinguished name of user>`                        | DN of the user.                                                                     |
| `attribute_value=<value of the attribute>`                    | Value of the attribute.                                                             |
| `attribute_name=<attribute name>`                             | Name of the attribute.                                                              |
| `namespace=<namespace name>`                                  | Name of the namespace.                                                              |
| `domain_name=<domain name>`                                   | Name of the domain.                                                                 |
| `realm_dn=<DN of the realm> `                                 | DN of the realm.                                                                    |
| `ldap_host=<OID host>`                                        | OID host.                                                                           |
| `ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>` | OID non ssl port or OID ssl port.                                                   |
| `keystore=<path to keystore>`                                 | Path to the keystore.                                                               |
| `keystore_alias=<keystore password alias>`                    | Keystore password taken from the Oracle wallet.                                     |
| `ldap_user_dn=<DN of OID user>`                               | DN of OID user which is used for authenticating and executing a command in the OID. |
| `ldap_alias=<OID user password alias>`                        | OID user password taken from the Oracle wallet.                                     |
| `wallet_location=<wallet location>`                           | Path to Oracle wallet when using the wallet.                                        |

##### Usage Notes

None.

##### Examples

Examples include adding a new user for an attribute value to an attribute to a domain namespace in the realm with and without SSL port connectivity to OID.

Example 7-166 Adding a New User for an Attribute Value with SSL Port Conectivity to OID and Using Passwords Stored in the Oracle Wallet

    eusm createAppCtxUsers user_dn=cn=test_user,cn=Users,dc=yy,dc=company,dc=com attribute_value=val1 attribute_name=attr1 namespace=ns1 domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3131 keystore=/etc/myapp/keyStore keystore_alias=keystore1 ldap_user_dn=cn=orcladmin ldap_alias=ldabadmin1 wallet_location=/oracle/product/db_1/wallets

Example 7-167 Adding a New User for an Attribute Value with SSL Port Conectivity to OID

    eusm createAppCtxUsers user_dn=cn=test_user,cn=Users,dc=yy,dc=company,dc=com attribute_value=val1 attribute_name=attr1 namespace=ns1 domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3131 keystore=/etc/myapp/keyStore ldap_user_dn=cn=orcladmin

Example 7-168 Adding a New User for an Attribute Value with non-SSL Port Conectivity to OID

    eusm createAppCtxUsers user_dn=cn=test_user,cn=Users,dc=yy,dc=company,dc=com attribute_value=val1 attribute_name=attr1 namespace=ns1 domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3060 ldap_user_dn=cn=orcladmin

#### 7.3.56 deleteAppCtxUsers

Deletes a user from an attribute value.

##### Syntax

    deleteAppCtxUsers
         user_dn=<Distinguished name of user>
         attribute_value=<value of the attribute>
         attribute_name=<attribute name>
         namespace=<namespace name>
         domain_name=<domain name>
         realm_dn=<DN of the realm>
         ldap_host=<OID host>
         ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>
         keystore=<path to keystore>
         keystore_alias=<keystore password alias>
         ldap_user_dn=<DN of OID user>
         ldap_alias=<OID user password alias>
         wallet_location=<wallet location>

##### Options

Each option must be prefixed with a space. Multiple options can be concatenated and prefixed with single space.

| Option                                                        | Description                                                                         |
|:--------------------------------------------------------------|:------------------------------------------------------------------------------------|
| `user_dn=<Distinguished name of user>`                        | DN of the user.                                                                     |
| `attribute_value=<value of the attribute>`                    | Value of the attribute.                                                             |
| `attribute_name=<attribute name>`                             | Name of the attribute.                                                              |
| `namespace=<namespace name>`                                  | Name of the namespace.                                                              |
| `domain_name=<domain name>`                                   | Name of the domain.                                                                 |
| `realm_dn=<DN of the realm> `                                 | DN of the realm.                                                                    |
| `ldap_host=<OID host>`                                        | OID host.                                                                           |
| `ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>` | OID non ssl port or OID ssl port.                                                   |
| `keystore=<path to keystore>`                                 | Path to the keystore.                                                               |
| `keystore_alias=<keystore password alias>`                    | Keystore password taken from the Oracle wallet.                                     |
| `ldap_user_dn=<DN of OID user>`                               | DN of OID user which is used for authenticating and executing a command in the OID. |
| `ldap_alias=<OID user password alias>`                        | OID user password taken from the Oracle wallet.                                     |
| `wallet_location=<wallet location>`                           | Path to Oracle wallet when using the wallet.                                        |

##### Usage Notes

None.

##### Examples

Examples include deleting a user from an attribute value for an attribute in a domain namespace in the realm with and without SSL port connectivity to OID.

Example 7-169 Deleting a User from an Attribute Value with SSL Port Conectivity to OID and Using Passwords Stored in the Oracle Wallet

    eusm deleteAppCtxUsers user_dn=cn=test_user,cn=Users,dc=yy,dc=company,dc=com attribute_value=val1 attribute_name=attr1 namespace=ns1 domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3131 keystore=/etc/myapp/keyStore keystore_alias=keystore1 ldap_user_dn=cn=orcladmin ldap_alias=ldabadmin1 wallet_location=/oracle/product/db_1/wallets

Example 7-170 Deleting a User from an Attribute Value with SSL Port Conectivity to OID

    eusm deleteAppCtxUsers user_dn=cn=test_user,cn=Users,dc=yy,dc=company,dc=com attribute_value=val1 attribute_name=attr1 namespace=ns1 domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3131 keystore=/etc/myapp/keyStore ldap_user_dn=cn=orcladmin

Example 7-171 Deleting a User from an Attribute Value with non-SSL Port Conectivity to OID

    eusm deleteAppCtxUsers user_dn=cn=test_user,cn=Users,dc=yy,dc=company,dc=com attribute_value=val1 attribute_name=attr1 namespace=ns1 domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3060 ldap_user_dn=cn=orcladmin

#### 7.3.57 listAppCtxUsers

Lists all users for an attribute value.

##### Syntax

    listAppCtxUsers
         attribute_value=<value of the attribute>
         attribute_name=<attribute name>
         namespace=<namespace name>
         domain_name=<domain name>
         realm_dn=<DN of the realm>
         ldap_host=<OID host>
         ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>
         keystore=<path to keystore>
         keystore_alias=<keystore password alias>
         ldap_user_dn=<DN of OID user>
         ldap_alias=<OID user password alias>
         wallet_location=<wallet location>

##### Options

Each option must be prefixed with a space. Multiple options can be concatenated and prefixed with single space.

| Option                                                        | Description                                                                         |
|:--------------------------------------------------------------|:------------------------------------------------------------------------------------|
| `attribute_value=<value of the attribute>`                    | Value of the attribute.                                                             |
| `attribute_name=<attribute name>`                             | Name of the attribute.                                                              |
| `namespace=<namespace name>`                                  | Name of the namespace.                                                              |
| `domain_name=<domain name>`                                   | Name of the domain.                                                                 |
| `realm_dn=<DN of the realm> `                                 | DN of the realm.                                                                    |
| `ldap_host=<OID host>`                                        | OID host.                                                                           |
| `ldap_port=<OID non ssl port> | ldap_ssl_port=<OID ssl port>` | OID non ssl port or OID ssl port.                                                   |
| `keystore=<path to keystore>`                                 | Path to the keystore.                                                               |
| `keystore_alias=<keystore password alias>`                    | Keystore password taken from the Oracle wallet.                                     |
| `ldap_user_dn=<DN of OID user>`                               | DN of OID user which is used for authenticating and executing a command in the OID. |
| `ldap_alias=<OID user password alias>`                        | OID user password taken from the Oracle wallet.                                     |
| `wallet_location=<wallet location>`                           | Path to Oracle wallet when using the wallet.                                        |

##### Usage Notes

None.

##### Examples

Examples include listing all users for an attribute value for an attribute for a domain namespace in the realm with and without SSL port connectivity to OID.

Example 7-172 Listing All Users for an Attribute Value with SSL Port Conectivity to OID and Using Passwords Stored in the Oracle Wallet

    eusm listAppCtxUsers attribute_value=val1 attribute_name=attr1 namespace=ns1 domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3131 keystore=/etc/myapp/keyStore keystore_alias=keystore1 ldap_user_dn=cn=orcladmin ldap_alias=ldabadmin1 wallet_location=/oracle/product/db_1/wallets

Example 7-173 Listing All Users for an Attribute Value with SSL Port Conectivity to OID

    eusm listAppCtxUsers attribute_value=val1 attribute_name=attr1 namespace=ns1 domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3131 keystore=/etc/myapp/keyStore ldap_user_dn=cn=orcladmin

Example 7-174 Listing All Users for an Attribute Value with non-SSL Port Conectivity to OID

    eusm listAppcCtxUsers attribute_value=val1 attribute_name=attr1 namespace=ns1 domain_name=test_domain realm_dn=dc=yy,dc=company,dc=com ldap_host=xxxxx.zz.company.com ldap_port=3060 ldap_user_dn=cn=orcladmin
