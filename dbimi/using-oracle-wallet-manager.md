This chapter covers:

- About Oracle Wallet Manager

- Starting Oracle Wallet Manager

- General Process for Creating an Oracle Wallet

- Managing Oracle Wallets

- Managing Certificates for Oracle Wallets

**See Also:**

- [Oracle Database Security Guide](../dbseg/configuring-secure-sockets-layer-authentication.md) in the section that discusses all of the Oracle PKI components

- [Oracle Database Security Guide](../dbseg/using-the-orapki-utility-to-manage-pki-elements.md) in the appendix for information about the `orapki` command-line utility you can use to create wallets and issue certificates for testing purposes

- [Oracle Database Licensing Information](../dblic/Licensing-Information.md) for licensing information about the use of Oracle Wallet Manager

### 6.1 About Oracle Wallet Manager

This section contains:

- What Is Oracle Wallet Manager?

- Wallet Password Management

- Strong Wallet Encryption

- Microsoft Windows Registry Wallet Storage

- ACL Settings Needed for Wallet Files Created Using Wallet Manager

- Backward Compatibility

- Public-Key Cryptography Standards (PKCS) Support

- Multiple Certificate Support

- LDAP Directory Support

**See Also:**

[Oracle Database Security Guide](../dbseg/configuring-secure-sockets-layer-authentication.md) for information about public key infrastructure in an Oracle environment

#### 6.1.1 What Is Oracle Wallet Manager?

You can use Oracle Wallet Manager to manage public key security credentials on Oracle clients and servers. The wallets it creates can be read by Oracle Database, Oracle Application Server, and the Oracle Identity Management infrastructure.

Oracle Wallet Manager enables wallet owners to manage and edit the security credentials in their Oracle wallets. A wallet is a password-protected container used to store authentication and signing credentials, including private keys, certificates, and trusted certificates needed by SSL. You can use Oracle Wallet Manager to perform the following tasks:

- Creating wallets

- Generating certificate requests

- Opening wallets to access PKI-based services

- Saving credentials to hardware security modules, by using APIs that comply with the Public-Key Cryptography Standards \#11 ([PKCS \#11](glossary.md)) specification

- Uploading wallets to (and downloading them from) an LDAP directory

- Importing third-party [PKCS \#12](glossary.md) -format wallets

- Exporting Oracle wallets to a third-party environment

#### 6.1.2 Wallet Password Management

Oracle wallets are password protected. Oracle Wallet Manager includes an enhanced wallet password management module that enforces Password Management Policy guidelines, including the following:

- Minimum password length (8 characters)

- Maximum password length unlimited

- Alphanumeric character mix required

#### 6.1.3 Strong Wallet Encryption

Oracle Wallet Manager stores private keys associated with X.509 certificates and uses AES encryption.

#### 6.1.4 Microsoft Windows Registry Wallet Storage

Oracle Wallet Manager lets you store multiple Oracle wallets in a Windows file management system or in the user profile area of the Microsoft Windows system registry. Storing your wallets in the registry provides the following benefits:

- Better Access Control: Wallets stored in the user profile area of the registry are only accessible by the associated user. User access controls for the system thus become, by extension, access controls for the wallets. In addition, when a user logs out of a system, access to that user's wallets is effectively precluded.

- Easier Administration: Wallets are associated with specific user profiles, so no file permissions need to be managed, and the wallets stored in the profile are automatically deleted when the user profile is deleted. You can use Oracle Wallet Manager to create and manage the wallets in the registry.

The supported options are as follows:

- Open a wallet from the registry

- Save a wallet to the registry

- Save As to a different registry location

- Delete a wallet from the registry

- Open a wallet from the file system and save it to the registry

- Open a wallet from the registry and save it to the file system

**See Also:**

[Oracle Database Platform Guide for Microsoft Windows](../ntqrf/storing-oracle-wallets-in-windows-registry.md)

#### 6.1.5 ACL Settings Needed for Wallet Files Created Using Wallet Manager

On Microsoft Windows systems, beginning with Oracle Database 12c (Release 12.1), you may need to set file system ACLs manually, for example to grant access to wallets in the file system created using Wallet Manager. As Oracle Database services now run under a low-privileged user, a file may not be accessible by Oracle Database services unless the file system Access Control Lists (ACLs) grant access to the file. Though Oracle installation configures the ACLs in a way to ensure that you do not have to change ACLs manually for typical usage, it may be necessary to change ACLs manually.

**See:**

[Oracle Database Platform Guide for Microsoft Windows](../ntqrf/setting-file-system-acls-manually.md) for more information about setting File System ACLs manually

#### 6.1.6 Backward Compatibility

Oracle Wallet Manager is backward-compatible to Release 8.1.7.

#### 6.1.7 Public-Key Cryptography Standards (PKCS) Support

RSALaboratories, a division of RSA Security, Inc., has developed, in cooperation with representatives from industry, academia, and government, a family of basic cryptography standards called Public-Key Cryptography Standards, or PKCS for short. These standards establish interoperability between computer systems that use public-key technology to secure data across intranets and the Internet.

Oracle Wallet Manager stores [X.509](glossary.md) certificates and [private key](glossary.md)s in PKCS \#12 format, and generates certificate requests according to the [PKCS \#10](glossary.md) specification. These capabilities make the Oracle wallet structure interoperable with supported third-party PKI applications and provide wallet portability across operating systems.

Oracle Wallet Manager wallets can store credentials on hardware security modules that use APIs conforming to the PKCS \#11 specification. When a wallet is created with `PKCS11` chosen as the wallet type, then all keys stored in that wallet are saved to a hardware security module or token. Examples of such hardware devices include smart cards, [PCMCIA cards](glossary.md), smart diskettes, or other portable hardware devices that store private keys or perform cryptographic operations (or both).

**Note:**

To use Oracle Wallet Manager with PKCS \#11 integration on the 64-bit Solaris Operating System, enter the following at the command line:

    owm -pkcs11

**See Also:**

- "Importing User Certificates Created with a Third-Party Tool"

- "Exporting an Oracle Wallet to a Third-Party Environment"

- "Creating an Oracle Wallet to Store Hardware Security Module Credentials"

- To view PKCS standards documents, navigate to the following URL:

      PKCS Standards Documents

#### 6.1.8 Multiple Certificate Support

Oracle Wallet Manager enables you to store multiple [certificate](glossary.md)s in each wallet, supporting any of the following [Oracle PKI certificate usages](glossary.md):

- SSL authentication

- S/MIME signature

- S/MIME encryption

- Code-Signing

- CA Certificate Signing

Each certificate request you create generates a unique private/public key pair. The private key stays in the wallet and the public key is sent with the request to a certificate authority. When that certificate authority generates your certificate and signs it, you can import it only into the wallet that has the corresponding private key.

If the wallet also contains a separate certificate request, the private/public key pair corresponding to that request is of course different from the pair for the first certificate request. Sending this separate certificate request to a certificate authority can get you a separate signed certificate, which you can import into this same wallet

A single certificate request can be sent to a certificate authority multiple times to obtain multiple certificates. However, only one certificate corresponding to that certificate request can be installed in the wallet.

Oracle Wallet Manager uses the X.509 Version 3 `KeyUsage` extension to define Oracle PKI certificate usages (Table 6-1). A single certificate cannot be applied to all possible certificate usages. Table 6-2 and Table 6-3 show legal usage combinations.

Table 6-1 KeyUsage Values

| Value | Usage            |
|:------|:-----------------|
| 0     | digitalSignature |
| 1     | nonRepudiation   |
| 2     | keyEncipherment  |
| 3     | dataEncipherment |
| 4     | keyAgreement     |
| 5     | keyCertSign      |
| 6     | cRLSign          |
| 7     | encipherOnly     |
| 8     | decipherOnly     |

When installing a certificate, Oracle Wallet Manager maps the `KeyUsage` extension values to Oracle PKI certificate usages as specified in Table 6-2 and Table 6-3.

Table 6-2 Oracle Wallet Manager Import of User Certificates to an Oracle Wallet

| KeyUsage Value                                     | Critical?(1) | Usage                                                        |
|:---------------------------------------------------|:-------------|:-------------------------------------------------------------|
| none                                               | NA           | Certificate is importable for SSL or S/MIME encryption use.  |
| 0 alone or along with any values excluding 5 and 2 | NA           | Accept certificate for S/MIME signature or code-signing use. |
| 1 alone                                            | Yes          | Not importable                                               |
| 1 alone                                            | No           | Accept certificate for S/MIME signature or code-signing use. |
| 2 alone or along with any combination excluding 5  | NA           | Accept certificate for SSL or S/MIME encryption use.         |
| 5 alone or along with any other values             | NA           | Accept certificate for CA certificate signing use.           |
| Any settings not listed previously                 | Yes          | Not importable.                                              |
| Any settings not listed previously                 | No           | Certificate is importable for SSL or S/MIME encryption use.  |

<sup>Footnote 1</sup> If the KeyUsage extension is critical, the certificate cannot be used for other purposes.

Table 6-3 Oracle Wallet Manager Import of Trusted Certificates to an Oracle Wallet

| KeyUsage Value                         | Critical?(2) | Usage           |
|:---------------------------------------|:-------------|:----------------|
| none                                   | NA           | Importable.     |
| Any combination excluding 5            | Yes          | Not importable. |
| Any combination excluding 5            | No           | Importable      |
| 5 alone or along with any other values | NA           | Importable.     |

<sup>Footnote 2</sup> If the KeyUsage extension is marked critical, the certificate cannot be used for other purposes.

You should obtain, from the certificate authority, certificates with the correct `KeyUsage` value matching your required Oracle PKI certificate usage. A single wallet can contain multiple [key pair](glossary.md)s for the same usage. Each certificate can support multiple Oracle PKI certificate usages, as indicated by Table 6-2 and Table 6-3. Oracle PKI applications use the first certificate containing the required PKI certificate usage.

For example, for SSL usage, the first certificate containing the SSL Oracle PKI certificate usage is used.

If you do not have a certificate with SSL usage, then an `ORA-28885` error (`No certificate with required key usage found`) is returned.

#### 6.1.9 LDAP Directory Support

Oracle Wallet Manager can upload wallets to and retrieve them from an LDAP-compliant directory. Storing wallets in a centralized LDAP-compliant directory lets users access them from multiple locations or devices, ensuring consistent and reliable user authentication while providing centralized wallet management throughout the wallet life cycle. To prevent a user from accidentally overwriting functional wallets, only wallets containing an installed certificate can be uploaded.

Directory user entries must be defined and configured in the LDAP directory before Oracle Wallet Manager can be used to upload or download wallets for a user. If a directory contains Oracle8i (or prior) users, then they are automatically upgraded to use the wallet upload and download feature on first use.

Oracle Wallet Manager downloads a user wallet by using a simple password-based connection to the LDAP directory. However, for uploads it uses an SSL connection if the open wallet contains a certificate with SSL Oracle PKI certificate usage. If an SSL certificate is not present in the wallet, password-based authentication is used.

**Note:**

The directory password and the wallet password are independent and can be different. Oracle recommends that these passwords be maintained to be consistently different, where neither one can logically be derived from the other.

**See Also:**

- "Uploading an Oracle Wallet to an LDAP Directory".

- "Downloading an Oracle Wallet from an LDAP Directory"

- "Multiple Certificate Support", for more information about Oracle PKI certificate usage.

### 6.2 Starting Oracle Wallet Manager

To start Oracle Wallet Manager:

- (UNIX) At the command line, enter the following command:

      owm

  To use Oracle Wallet Manager with PKCS \#11 integration on the 64-bit Solaris Operating System, enter this command:

      owm -pkcs11

  (This guide assumes that you are not using the PKCS#11 integration.)

- (Windows) Select Start, Programs, Oracle-HOME_NAME, Integrated Management Tools, Wallet Manager

### 6.3 General Process for Creating an Oracle Wallet

Oracle wallets provide a necessary repository in which you can securely store your user certificates and the [trust point](glossary.md) you need to validate the certificates of your peers.

The following steps provide an overview of the complete wallet creation process:

1.  Use Oracle Wallet Manager to create a new wallet.
2.  Generate a certificate request. When you create a new wallet with Oracle Wallet Manager, the tool automatically prompts you to create a certificate request.
3.  Send the certificate request to the CA you want to use. You can copy and paste the certificate request text into an e-mail message, or you can export the certificate request to a file. The certificate request becomes part of your wallet. It must remain there until you remove its associated certificate.
4.  When the CA sends your signed user certificate and its associated [trusted certificate](glossary.md), then you can import these certificates in the following order. The user certificates and trusted certificates in the PKCS \#7 format can be imported at the same time.
    - First import the CA's trusted certificate into your wallet. This step may be optional if the new user certificate has been issued by one of the CAs whose trusted certificate is already present in Oracle Wallet Manager by default.

    - After you have successfully imported the trusted certificate, then import the user certificate that the CA sent to you into your wallet.
5.  (Optional) Set the auto login feature for your wallet.
    Typically, this feature, which enables PKI-based access to services without a password, is required for most wallets. It is required for database server and client wallets. It is only optional for products that take the wallet password at the time of startup.

After completing the preceding process, you have a wallet that contains a user certificate and its associated trust points.

**See Also:**

For more information about these steps, refer to "Managing Certificates for Oracle Wallets"

### 6.4 Managing Oracle Wallets

This section describes how to create a new Oracle wallet and perform associated wallet management tasks, such as generating certificate requests, exporting certificate requests, and importing certificates into wallets, in the following subsections:

- What Is Oracle Wallet Manager?

- Wallet Password Management

- Strong Wallet Encryption

- Microsoft Windows Registry Wallet Storage

- ACL Settings Needed for Wallet Files Created Using Wallet Manager

- Backward Compatibility

- Public-Key Cryptography Standards (PKCS) Support

- Multiple Certificate Support

- LDAP Directory Support

#### 6.4.1 Required Guidelines for Creating Oracle Wallet Passwords

Because an Oracle wallet contains user credentials that can be used to authenticate the user to multiple databases, it is especially important to choose a strong wallet password. A malicious user who guesses the wallet password can access all the databases to which the wallet owner has access.

Passwords must contain at least eight characters that consist of alphabetic characters combined with numbers or special characters.

**Note:**

It is strongly recommended that you avoid choosing easily guessed passwords based on user names, phone numbers, or government identification numbers. This prevents a potential attacker from using personal information to deduce the users' passwords. It is also a prudent security practice for users to change their passwords periodically, such as once in each month or once in each quarter.

When you change passwords, you must regenerate auto-login wallets.

**See Also:**

- "Wallet Password Management".

- "Using Auto Login for Oracle Wallets to Enable Access Without Human Intervention"

#### 6.4.2 Creating a New Oracle Wallet

You can use Oracle Wallet Manager to create PKCS \#12 wallets (the standard default wallet type) that store credentials in a directory on your file system. It can also be used to create PKCS \#11 wallets that store credentials on a hardware security module for servers, or private keys on tokens for clients. The following sections explain how to create both types of wallets by using Oracle Wallet Manager.

This section describes the following topics:

- Creating a Standard Oracle Wallet

- Creating an Oracle Wallet to Store Hardware Security Module Credentials

##### 6.4.2.1 Creating a Standard Oracle Wallet

Unless you have a hardware security module (a PKCS \#11 device), then you should use a standard wallet that stores credentials in a directory on your file system.

To create a standard Oracle wallet, perform the following tasks:

1.  Start Oracle Wallet Manager.
    - (UNIX) At the command line, enter the following command:

          owm

    - (Windows) Select Start, Programs, Oracle-HOME_NAME, Integrated Management Tools, Wallet Manager
2.  From the Wallet menu, select New.
    If you have not yet created a directory for the wallet, then you are prompted to create this directory. By default, the wallet directory is created in the `/oracle/owm/wallets/``user_name` directory.

    The New Wallet dialog box appears.
3.  Enter the following information:
    - Password and Confirm Password: Enter a password in these two fields. Ensure that you follow the guidelines in "Required Guidelines for Creating Oracle Wallet Passwords". This password protects unauthorized use of your credentials.

    - Wallet Type: Select Standard.
4.  Click OK.
    An alert is displayed, and informs you that a new empty wallet has been created. It prompts you to decide whether you want to add a certificate request.
5.  When prompted to create a certificate request, select one of the following options:
    - Yes: See "Adding a Certificate Request".

    - No: If you select No, then you are returned to the Oracle Wallet Manager main window. The new wallet you just created is displayed in the left window pane. The certificate has a status of \[Empty\], and the wallet displays its default trusted certificates.
6.  From the Wallet menu, select Save In System Default to save the new wallet.
    If you do not have permission to save the wallet in the system default, then you can save it to another location. This location must be used in the SSL configuration for clients and servers.

    A message at the bottom of the window confirms that the wallet was successfully saved.

##### 6.4.2.2 Creating an Oracle Wallet to Store Hardware Security Module Credentials

To create an Oracle wallet to store credentials on a hardware security module that complies with PKCS \#11:

1.  Start Oracle Wallet Manager.
    - (UNIX) At the command line, enter the following command:

          owm

    - (Windows) Select Start, Programs, Oracle-HOME_NAME, Integrated Management Tools, Wallet Manager
2.  From the Wallet menu, select New.
    The New Wallet dialog box appears.
3.  Enter the following information:
    - Password and Confirm Password: Enter a password in these two fields. Ensure that you follow the guidelines in "Required Guidelines for Creating Oracle Wallet Passwords". This password protects unauthorized use of your credentials.

    - Wallet Type: Select PKCS11.
4.  Click OK to continue.
    The PKCS11 Information window appears.
5.  In the PKCS11 Information window, enter the following information: From the Select Hardware Vendor list, select a vendor name.
    - Hardware Vendor: Select the vendor name. SafeNET and nCipher hardware have been certified to interoperate with Oracle wallets.

    - PKCS11 library filename field, enter the path to the directory where the PKCS11 library is stored, or click Browse to find it by searching the file system.

    - Smart Card password: Enter this password. The smart card password, which is different from the wallet password, is stored in the wallet.
6.  Click OK.
    An alert is displayed, and informs you that a new empty wallet has been created. It prompts you to decide whether you want to add a certificate request.
7.  When prompted to create a certificate request, select one of the following options:
    - Yes: See "Adding a Certificate Request".

    - No: If you select No, then you are returned to the Oracle Wallet Manager main window. The new wallet you just created is displayed in the left window pane. The certificate has a status of \[Empty\], and the wallet displays its default trusted certificates.
8.  From the Wallet menu, select Save In System Default to save the new wallet.
    If you do not have permission to save the wallet in the system default, you can save it to another location.

    A message at the bottom of the window confirms that the wallet was successfully saved.

    If you change the smart card password or move the PKCS \#11 library, an error message displays when you try to open the wallet. Then you are prompted to enter the new smart card password or the new path to the library.

#### 6.4.3 Opening an Existing Oracle Wallet

1.  Start Oracle Wallet Manager.
    - (UNIX) At the command line, enter the following command:

          owm

    - (Windows) Select Start, Programs, Oracle-HOME_NAME, Integrated Management Tools, Wallet Manager
2.  From the Wallet menu, select Open.
    The Select Directory dialog box appears.
3.  Navigate to the directory location in which the wallet is located, and select the directory.
4.  Click OK.
    The Open Wallet dialog box appears.
5.  In the Wallet Password field, enter the wallet password.
6.  Click OK.
    The main window appears and a message displays at the bottom of the window indicating that the wallet opened successfully. The wallet's certificate and its trusted certificates appear in the left window pane.

#### 6.4.4 Closing an Oracle Wallet

1.  Start Oracle Wallet Manager.
    - (UNIX) At the command line, enter the following command:

          owm

    - (Windows) Select Start, Programs, Oracle-HOME_NAME, Integrated Management Tools, Wallet Manager
2.  From the Wallet menu, select Close.

A message is displayed at the bottom of the window to confirm that the wallet is closed.

#### 6.4.5 Exporting an Oracle Wallet to a Third-Party Environment

1.  Use Oracle Wallet Manager to save the wallet file.

    1.  Start Oracle Wallet Manager.

        (UNIX) At the command line, enter the following command:

            owm

        (Windows) Select Start, Programs, Oracle-HOME_NAME, Integrated Management Tools, Wallet Manager

    2.  Ensure that the wallet is open by selecting Wallet from the panel, and from the Wallet menu, select Open. When prompted, select the wallet directory location, and then enter your wallet password.

    3.  From the Wallet menu,. select Save.

2.  Follow the procedure specific to your third-party product to import an operating system PKCS \#12 wallet file created by Oracle Wallet Manager (called `ewallet.p12` on UNIX and Windows platforms).

    **Note:**

    - Oracle Wallet Manager supports multiple certificates for each wallet, yet current browsers typically support import of single-certificate wallets only. For these browsers, you must export an Oracle wallet containing a single key-pair.

    - Oracle Wallet Manager supports wallet export to only Netscape Communicator 4.7.2 and later, OpenSSL, and Microsoft Internet Explorer 5.0 and later.

#### 6.4.6 Exporting an Oracle Wallet to a Tools That Does Not Support PKCS \#12

You can export a wallet to a text-based PKI format if you want to put a wallet into a tool that does not support PKCS \#12. Individual components are formatted according to the standards listed in Table 6-4. Within the wallet, only those certificates with SSL key usage are exported with the wallet.

To export a wallet to text-based PKI format:

1.  Start Oracle Wallet Manager.
    - (UNIX) At the command line, enter the following command:

          owm

    - (Windows) Select Start, Programs, Oracle-HOME_NAME, Integrated Management Tools, Wallet Manager
2.  If the wallet is closed, then open it by selecting Open from the Wallet menu. When prompted, select the wallet directory location, and then enter your wallet password.
3.  From the Operations menu, select Export Wallet.
    The Export Wallet dialog box is displayed.
4.  Enter the destination file system directory for the wallet, or navigate to the directory structure under Folders.
5.  Enter the destination file name for the wallet.
6.  Click OK to return to the main window.

Table 6-4 PKI Wallet Encoding Standards

| Component            | Encoding Standard |
|:---------------------|:------------------|
| Certificate chains   | X509v3            |
| Trusted certificates | X509v3            |
| Private keys         | PKCS \#8          |

#### 6.4.7 Uploading an Oracle Wallet to an LDAP Directory

To upload an Oracle wallet to an LDAP directory, Oracle Wallet Manager uses SSL if the specified wallet contains an SSL certificate. Otherwise, it lets you enter the directory password.

To prevent accidental destruction of your wallet, Oracle Wallet Manager will not permit you to execute the upload option unless the target wallet is currently open and contains at least one user certificate.

To upload a wallet:

1.  Start Oracle Wallet Manager.
    - (UNIX) At the command line, enter the following command:

          owm

    - (Windows) Select Start, Programs, Oracle-HOME_NAME, Integrated Management Tools, Wallet Manager
2.  If the wallet is closed, then open it by selecting Open from the Wallet menu. When prompted, select the wallet directory location, and then enter your wallet password.
3.  From the Wallet menu, select Upload Into The Directory Service.
    Oracle Database checks wallet certificates for SSL key usage.
4.  Depending on whether the wallet has a certificate with SSL key usage, do one of the following:
    - If at least one certificate has SSL key usage: When prompted, enter the LDAP directory server host name and port information, then click OK. Oracle Wallet Manager attempts connection to the LDAP directory server using SSL. A message is displayed indicating whether the wallet was uploaded successfully or it failed.

    - If no certificates have SSL key usage: When prompted, enter the user's [distinguished name (DN)](glossary.md), the LDAP server host name, and port information, and then click OK. Oracle Wallet Manager attempts connection to the LDAP directory server using simple password authentication mode, assuming that the wallet password is the same as the directory password.

      If the connection fails, then a dialog box prompts for the directory password of the specified DN. Oracle Wallet Manager attempts connection to the LDAP directory server using this password and displays a warning message if the attempt fails. Otherwise, Oracle Wallet Manager displays a status message at the bottom of the window indicating that the upload was successful.

**Note:**

- You should ensure that the distinguished name used matches a corresponding user entry of object class `inetOrgPerson` in the LDAP directory.

- When uploading a wallet with an SSL certificate, use the SSL port. When uploading a wallet that does not contain an SSL certificate, use the non-SSL port.

#### 6.4.8 Downloading an Oracle Wallet from an LDAP Directory

When you download an Oracle wallet from an LDAP directory, the wallet becomes resident in working memory. It is not saved to the file system unless you explicitly save it using any of the save options described in the following sections.

**See Also:**

- "Saving Changes to an Oracle Wallet"

- "Saving the Open Wallet to a New Location"

- "Saving an Oracle Wallet to the System Default Directory Location"

To download a wallet from an LDAP directory:

1.  Start Oracle Wallet Manager.
    - (UNIX) At the command line, enter the following command:

          owm

    - (Windows) Select Start, Programs, Oracle-HOME_NAME, Integrated Management Tools, Wallet Manager
2.  From the Wallet menu, select Download From The Directory Service.
    The Download From Directory Service dialog box prompts for the distinguished name (DN), and the LDAP directory password, host name, and port information. Oracle Wallet Manager uses simple password authentication to connect to the LDAP directory.
3.  Depending on whether or not the downloading operation succeeds, do one of the following:
    - If the download operation fails: Check to make sure that you have correctly entered the user's DN, and the LDAP server host name and port information. The port used must be the non-SSL port.

    - If the download is successful: Click OK to open the downloaded wallet. Oracle Wallet Manager attempts to open that wallet using the directory password. If the operation fails after using the directory password, then a dialog box prompts for the wallet password.

      If Oracle Wallet Manager cannot open the target wallet using the wallet password, then check to make sure you entered the correct password. Otherwise a message displays at the bottom of the window, indicating that the wallet was downloaded successfully.

#### 6.4.9 Saving Changes to an Oracle Wallet

1.  Start Oracle Wallet Manager.
    - (UNIX) At the command line, enter the following command:

          owm

    - (Windows) Select Start, Programs, Oracle-HOME_NAME, Integrated Management Tools, Wallet Manager
2.  If the wallet is closed, then open it by selecting Open from the Wallet menu. When prompted, select the wallet directory location, and then enter your wallet password.
3.  From the Wallet menu, select Save.

A message at the bottom of the window confirms that the wallet changes were successfully saved to the wallet in the selected directory location.

#### 6.4.10 Saving the Open Wallet to a New Location

1.  Start Oracle Wallet Manager.
    - (UNIX) At the command line, enter the following command:

          owm

    - (Windows) Select Start, Programs, Oracle-HOME_NAME, Integrated Management Tools, Wallet Manager
2.  If the wallet is closed, then open it by selecting Open from the Wallet menu. When prompted, select the wallet directory location, and then enter your wallet password.
3.  From the Wallet menu, select Save As.
    The Select Directory dialog box appears.
4.  Select a directory location in which to save the wallet.
5.  Click OK.
    The following message is displayed if a wallet already exists in the selected location:

        A wallet already exists in the selected path. Do you want to overwrite it?

    Select Yes to overwrite the existing wallet or No to save the wallet to another location.

    A message at the bottom of the window confirms that the wallet was successfully saved to the selected directory location.

#### 6.4.11 Saving an Oracle Wallet to the System Default Directory Location

1.  Start Oracle Wallet Manager.
    - (UNIX) At the command line, enter the following command:

          owm

    - (Windows) Select Start, Programs, Oracle-HOME_NAME, Integrated Management Tools, Wallet Manager
2.  If the wallet is closed, then open it by selecting Open from the Wallet menu. When prompted, select the wallet directory location, and then enter your wallet password.
3.  From the Wallet menu, select Save In System Default.

A message at the bottom of the window confirms that the wallet was successfully saved in the system default wallet location as follows for UNIX and Windows platforms:

- (UNIX) `$ORACLE_HOME``/owm/wallets/``username` if the `ORACLE_HOME` environment variable has been set.

  `./owm/wallets/``username` if the `ORACLE_HOME` environment variable is not set.

- (WINDOWS) `ORACLE_HOME``\owm\wallets\``username` if the `ORACLE_HOME` environment variable has been set.

  `.\owm\wallets\``username` if the `ORACLE_HOME` environment variable is not set.

**Note:**

- SSL uses the wallet that is saved in the system default directory location.

- Some Oracle applications are not able to use the wallet if it is not in the system default location. Check the Oracle documentation for your specific application to determine whether wallets must be placed in the default wallet directory location.

#### 6.4.12 Deleting an Oracle Wallet

1.  Start Oracle Wallet Manager.
    - (UNIX) At the command line, enter the following command:

          owm

    - (Windows) Select Start, Programs, Oracle-HOME_NAME, Integrated Management Tools, Wallet Manager
2.  If the wallet is closed, then open it by selecting Open from the Wallet menu. When prompted, select the wallet directory location, and then enter your wallet password.
3.  From the Wallet menu, select Delete.
    The Delete Wallet dialog box appears.
4.  Do the following:
    - Wallet Location: Review the displayed wallet location to verify that you are deleting the correct wallet.

    - Wallet Password: Enter the wallet password.
5.  Click OK.
6.  In the Confirmation dialog box, click OK.

**Note:**

- Any open wallet in application memory will remain in memory until the application exits. Therefore, deleting a wallet that is currently in use does not immediately affect system operation.

- Do not use Oracle Wallet Manager to delete Transparent Data Encryption keystores. See [Oracle Database Advanced Security Guide](../asoag/managing-keystore-and-tde-master-encryption-key.md) for information about deleting keystores.

#### 6.4.13 Changing the Oracle Wallet Password

An Oracle wallet password change is effective immediately. The wallet is saved to the currently selected directory, encrypted with the password.

**Note:**

If you are using a wallet with auto login enabled, you must regenerate the auto login wallet after changing the password. See "Using Auto Login for Oracle Wallets to Enable Access Without Human Intervention" for more information.

To change the password for a wallet:

1.  Start Oracle Wallet Manager.
    - (UNIX) At the command line, enter the following command:

          owm

    - (Windows) Select Start, Programs, Oracle-HOME_NAME, Integrated Management Tools, Wallet Manager
2.  If the wallet is closed, then open it by selecting Open from the Wallet menu. When prompted, select the wallet directory location, and then enter your wallet password.
3.  From the Wallet menu, select Change Password.
    The Change Wallet Password dialog box appears.
4.  Enter the following information:
    - Old Wallet Password: Enter the current wallet password.

    - New Wallet Password and Confirm Wallet Password: Enter the new password.
5.  Click OK.

A message at the bottom of the window confirms that the password was successfully changed.

**See Also:**

- "Required Guidelines for Creating Oracle Wallet Passwords"

- "Wallet Password Management", for password policy restrictions

#### 6.4.14 Using Auto Login for Oracle Wallets to Enable Access Without Human Intervention

This section contains:

- About Using Auto Login for Oracle Wallets

- Enabling Auto Login for Oracle Wallets

- Disabling Auto Login for Oracle Wallets

##### 6.4.14.1 About Using Auto Login for Oracle Wallets

The auto login feature for wallets is the ability to enable PKI-based access to services without requiring human intervention to supply the necessary passwords. Enabling auto login creates an obfuscated copy of the wallet, which is then used automatically until the auto login feature is disabled for that wallet.

Auto login wallets are protected by file system permissions. When auto login is enabled for a wallet, only the operating system user who created it can manage it, through the Oracle Wallet Manager.

You must enable auto login if you want single sign-on access to multiple Oracle databases: such access is normally disabled, by default. Sometimes the obfuscated auto login wallets are called "SSO wallets" because they support single sign-on capability.

##### 6.4.14.2 Enabling Auto Login for Oracle Wallets

1.  Start Oracle Wallet Manager.
    - (UNIX) At the command line, enter the following command:

          owm

    - (Windows) Select Start, Programs, Oracle-HOME_NAME, Integrated Management Tools, Wallet Manager
2.  If the wallet is closed, then open it by selecting Open from the Wallet menu. When prompted, select the wallet directory location, and then enter your wallet password.
3.  From the Wallet menu, select the Auto Login check box.
    A message at the bottom of the window indicates that auto login is enabled.

##### 6.4.14.3 Disabling Auto Login for Oracle Wallets

1.  Start Oracle Wallet Manager.
    - (UNIX) At the command line, enter the following command:

          owm

    - (Windows) Select Start, Programs, Oracle-HOME_NAME, Integrated Management Tools, Wallet Manager
2.  If the wallet is closed, then open it by selecting Open from the Wallet menu. When prompted, select the wallet directory location, and then enter your wallet password.
3.  From the Wallet menu, deselect the Auto Login check box.
    A message at the bottom of the window indicates that auto login is disabled.

### 6.5 Managing Certificates for Oracle Wallets

This section contains:

- About Managing Certificates for Oracle Wallets

- Managing User Certificates for Oracle Wallets

- Managing Trusted Certificates for Oracle Wallets

#### 6.5.1 About Managing Certificates for Oracle Wallets

All certificates are signed data structures that bind a network identity with a corresponding public key.

Table 6-5 describes the two types of certificates distinguished in this chapter.

Table 6-5 Types of Certificates

| Certificate Type     | Examples                                                                                                                     |
|:---------------------|:-----------------------------------------------------------------------------------------------------------------------------|
| User certificates    | Certificates issued to servers or users to prove an end entity's identity in a public key/private key exchange               |
| Trusted certificates | Certificates representing entities whom you trust, such as certificate authorities who sign the user certificates they issue |

**Note:**

Before you can install a user certificate, ensure that the wallet contains the trusted certificate representing the certificate authority who issued that user certificate. However, whenever you create a new wallet, several publicly trusted certificates are automatically installed, since they are so widely used. If the necessary certificate authority is not represented, then you must install its certificate first.

Also, you can import using the PKCS#7 certificate chain format, which gives you the user certificate and the CA certificate at the same time.

#### 6.5.2 Managing User Certificates for Oracle Wallets

This section contains:

- About Managing User Certificates

- Adding a Certificate Request

- Importing the User Certificate into an Oracle Wallet

- Importing Certificates and Wallets Created by Third Parties

- Removing a User Certificate from an Oracle Wallet

- Removing a Certificate Request

- Exporting a User Certificate

- Exporting a User Certificate Request

##### 6.5.2.1 About Managing User Certificates

User certificates, including server certificates, are used by end users, smart cards, or applications, such as Web servers. For example, if a CA issues a certificate for a Web server, placing its [distinguished name (DN)](glossary.md) in the Subject field, then the Web server is the certificate owner, thus the "user" for this user certificate.

##### 6.5.2.2 Adding a Certificate Request

You can add multiple certificate requests with Oracle Wallet Manager. When adding multiple requests, Oracle Wallet Manager automatically populates each subsequent request dialog box with the content of the initial request that you can then edit.

The actual certificate request becomes part of the wallet. You can reuse any certificate request to obtain a new certificate. However, you cannot edit an existing certificate request. Store only a correctly filled out certificate request in a wallet.

To create a PKCS \#10 certificate request:

1.  Start Oracle Wallet Manager.
    - (UNIX) At the command line, enter the following command:

          owm

    - (Windows) Select Start, Programs, Oracle-HOME_NAME, Integrated Management Tools, Wallet Manager
2.  If the wallet is closed, then open it by selecting Open from the Wallet menu. When prompted, select the wallet directory location, and then enter your wallet password.
3.  From the Operations menu, select Add Certificate Request.
    The Create Certificate Request dialog box is displayed.

    The online Help for Oracle Wallet Manager becomes unresponsive when modal dialog boxes appear, such as the one for entering certificate request information. The online Help becomes responsive once the modal dialog box is closed.
4.  Enter the information specified in Table 6-6.
5.  Click OK.
    A message informs you that a certificate request was successfully created. You can either copy the certificate request text from the body of this dialog panel and paste it into an e-mail message to send to a certificate authority, or you can export the certificate request to a file. At this point, Oracle Wallet Manager has created your private/public key pair and stored it in the wallet. When the certificate authority issues your certificate, it will also be stored in the wallet and associate it with its corresponding private key.
6.  Click OK.
    The status of the certificate changes to \[Requested\].

    **See Also:**

    "Exporting a User Certificate Request"

Table 6-6 Certificate Request: Fields and Descriptions

| Field Name          | Description                                                                                                                                                                                                              |
|:--------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Common Name         | Mandatory. Enter the name of the user's or service's identity. Enter a user's name in first name /last name format.<br>Example: Eileen.Sanger                                                                            |
| Organizational Unit | Optional. Enter the name of the identity's organizational unit. Example: Finance.                                                                                                                                        |
| Organization        | Optional. Enter the name of the identity's organization. Example: XYZ Corp.                                                                                                                                              |
| Locality/City       | Optional. Enter the name of the locality or city in which the identity resides.                                                                                                                                          |
| State/Province      | Optional. Enter the full name of the state or province in which the identity resides.<br>Enter the full state name, because some certificate authorities do not accept two–letter abbreviations.                         |
| Country             | Mandatory. Select Country to view a list of country abbreviations. Select the country in which the organization is located.                                                                                              |
| DN                  | Mandatory. Select the Algorithm (Key Size/Elliptic Curve) list to view a list of key sizes to use when creating the public/private key pair. Refer to Table 6-7 to evaluate the key size.                                |
| Advanced            | Optional. Select Advanced to view the Advanced Certificate Request dialog panel. Use this field to edit or customize the identity's distinguished name (DN). For example, you can edit the full state name and locality. |

Table 6-7 lists the available key sizes and the relative security each size provides. Typically, CAs use key sizes of 1024 or 2048. When certificate owners wish to keep their keys for a longer duration, they choose 3072 or 4096 bit keys.

Table 6-7 Available Key Sizes

| Key Size     | Relative Security Level |
|:-------------|:------------------------|
| 512 or 768   | Not regarded as secure. |
| 1024 or 2048 | Secure.                 |
| 3072 or 4096 | Very secure.            |

##### 6.5.2.3 Importing the User Certificate into an Oracle Wallet

When the Certificate Authority grants you a certificate, it may send you an e-mail that has your certificate in text (BASE64) form or attached as a binary file. You can import the user certificate using the following methods:

- Importing the User Certificate from the Text of the Certificate Authority Email

- Importing the User Certificate from a File

**Note:**

Certificate authorities may send your certificate in a PKCS \#7 certificate chain or as an individual X.509 certificate. Oracle Wallet Manager can import both types.

PKCS \#7 certificate chains are a collection of certificates, including the user's certificate and all of the supporting trusted CA and subCA certificates.

In contrast, an X.509 certificate file contains an individual certificate without the supporting certificate chain.

However, before you can import any such individual certificate, the signer's certificate must be a Trusted Certificate in the wallet.

##### Importing the User Certificate from the Text of the Certificate Authority Email

Copy the certificate, represented as text (BASE64), from the e-mail message. Include the lines `Begin Certificate` and `End Certificate.`

1.  Start Oracle Wallet Manager.

    - (UNIX) At the command line, enter the following command:

          owm

    - (Windows) Select Start, Programs, Oracle-HOME_NAME, Integrated Management Tools, Wallet Manager

2.  If the wallet is closed, then open it by selecting Open from the Wallet menu. When prompted, select the wallet directory location, and then enter your wallet password.

3.  Select Operations, Import User Certificate.

    The Import Certificate dialog box is displayed.

4.  Select Paste the certificate, and then click OK.

    Another Import Certificate dialog box is displayed with the following message:

        Please provide a base64 format certificate and paste it below.

5.  Paste the certificate into the dialog box, and click OK.

    1.  If the certificate received is in PKCS#7 format, it is installed, and all the other certificates included with the PKCS#7 data are placed in the Trusted Certificate list.

    2.  If the certificate received is not in PKCS#7 format, and the certificate of its CA is not already in the Trusted Certificates list, then more must be done. Oracle Wallet Manager will ask you to import the certificate of the CA that issued your certificate. This CA certificate will be placed in the Trusted Certificates list. (If the CA certificate was already in the Trusted Certificates list, your certificate is imported without additional steps.)

    After either (a) or (b) succeeds, a message at the bottom of the window confirms that the certificate was successfully installed. You are returned to the Oracle Wallet Manager main panel, and the status of the corresponding entry in the left panel subtree changes to \[Ready\].

**Note:**

The standard X.509 certificate includes the following start and end text:

- -----BEGIN CERTIFICATE-----
      -----END CERTIFICATE-----

A typical PKCS#7 certificate includes more, as described earlier, and includes the following start and end text:

- -----BEGIN PKCS7-----
      -----END PKCS7-----

You can use the standard Ctrl+c to copy, including all dashes, and Ctrl+v to paste.

##### Importing the User Certificate from a File

The user certificate in the file can be in either text (BASE64) or binary (`der`) format.

1.  Start Oracle Wallet Manager.

    - (UNIX) At the command line, enter the following command:

          owm

    - (Windows) Select Start, Programs, Oracle-HOME_NAME, Integrated Management Tools, Wallet Manager

2.  If the wallet is closed, then open it by selecting Open from the Wallet menu. When prompted, select the wallet directory location, and then enter your wallet password.

3.  Select Operations, Import User Certificate. The Import Certificate dialog box is displayed.

4.  Select Select a file that contains the certificate, and click OK. Another Import Certificate dialog box is displayed.

5.  Enter the path or folder name of the certificate file location.

6.  Select the name of the certificate file (for example, `cert.txt`, `cert.der`).

7.  Click OK.

    1.  If the certificate received is in PKCS#7 format, it is installed, and all the other certificates included with the PKCS#7 data are placed in the Trusted Certificate list.

    2.  If the certificate received is not in PKCS#7 format, and the certificate of its CA is not already in the Trusted Certificates list, then more must be done. Oracle Wallet Manager will ask you to import the certificate of the CA that issued your certificate. This CA certificate will be placed in the Trusted Certificates list. (If the CA certificate was already in the Trusted Certificates list, your certificate is imported without additional steps.)

    After either (a) or (b) succeeds, a message at the bottom of the window confirms that the certificate was successfully installed. You are returned to the Oracle Wallet Manager main panel, and the status of the corresponding entry in the left panel subtree changes to \[Ready\].

##### 6.5.2.4 Importing Certificates and Wallets Created by Third Parties

Third-party certificates are those created from certificate requests that were not generated using Oracle Wallet Manager. These third-party certificates are actually wallets, in the Oracle sense, because they contain more than just the user certificate; they also contain the private key for that certificate. Furthermore, they include the chain of trusted certificates validating that the certificate was created by a trustworthy entity.

Oracle Wallet Manager makes these wallets available in a single step by importing them in PKCS#12 format, which includes all three elements described earlier: the user certificate, the private key, and the trusted certificates. It supports the following PKCS \#12-format certificates:

- Netscape Communicator 4.x and later

- Microsoft Internet Explorer 5.x and later

Oracle Wallet Manager adheres to the PKCS#12 standard, so certificates exported by any PKCS#12-compliant tool should be usable with Oracle Wallet Manager.

Such third-party certificates cannot be stored into existing Oracle wallets because they would lack the private key and chain of trusted authorities. Therefore, each such certificate is exported and retrieved instead as an independent PKCS#12 file, that is, as its own wallet.

##### Importing User Certificates Created with a Third-Party Tool

Once a third party generates the wallet, you need to import it to make use of it, as described in this section.

To import a certificate created with a third-party tool:

1.  Follow the procedures for your particular product to export the certificate.
    Perform the actions indicated in the exporting product to include the private key in the export, and specify the new password to protect the exported certificate. Also include all associated trust points. (Under PKCS \#12, browsers do not necessarily export [trusted certificate](glossary.md)s, other than the signer's own certificate. You may need to add additional certificates to authenticate to your peers. You can use Oracle Wallet Manager to import trusted certificates.)

    The resulting file, containing the certificate, the private key, and the trust points, is the new wallet that enables the third-party certificate to be used.
2.  Place the wallet where it will be easily found, by copying it to the correct system and directory.
    To be used by particular applications or servers, such as a web server or an LDAP server, wallets must be located precisely. Each application has its own expectations as to which directory it will search to find the needed wallet.
3.  For use with UNIX or Windows applications or servers, ensure that the wallet is named `ewallet.p12`.
    For other operating systems, refer to the Oracle documentation for that specific operating system.

    Once a third-party certificate is stored as `ewallet.p12`, you can open and manage it using Oracle Wallet Manager. You will have to supply the password you created when exporting this wallet.

**Note:**

The password will be required whenever the associated application starts up or otherwise needs the certificate. To make such access automatic, refer to "Using Auto Login for Oracle Wallets to Enable Access Without Human Intervention".

However, if the private key for the desired certificate is held in a separate hardware security module, you will not be able to import that certificate.

##### 6.5.2.5 Removing a User Certificate from an Oracle Wallet

1.  Start Oracle Wallet Manager.
    - (UNIX) At the command line, enter the following command:

          owm

    - (Windows) Select Start, Programs, Oracle-HOME_NAME, Integrated Management Tools, Wallet Manager
2.  If the wallet is closed, then open it by selecting Open from the Wallet menu. When prompted, select the wallet directory location, and then enter your wallet password.
3.  In the left panel subtree, select the certificate that you want to remove.
4.  From the Operations menu, select Remove User Certificate.
5.  In the Confirmation dialog box, select Yes to return to the Oracle Wallet Manager main panel.
    The certificate displays a status of \[Requested\].

##### 6.5.2.6 Removing a Certificate Request

You must remove a certificate before removing its associated request.

To remove a certificate request:

1.  Start Oracle Wallet Manager.
    - (UNIX) At the command line, enter the following command:

          owm

    - (Windows) Select Start, Programs, Oracle-HOME_NAME, Integrated Management Tools, Wallet Manager
2.  If the wallet is closed, then open it by selecting Open from the Wallet menu. When prompted, select the wallet directory location, and then enter your wallet password.
3.  In the left panel subtree, select the certificate request that you want to remove.
4.  From the Operations menu, select Remove Certificate Request.
5.  In the Confirmation dialog box, click Yes.

##### 6.5.2.7 Exporting a User Certificate

To save the certificate in a file system directory, export the certificate as follows:

1.  Start Oracle Wallet Manager.
    - (UNIX) At the command line, enter the following command:

          owm

    - (Windows) Select Start, Programs, Oracle-HOME_NAME, Integrated Management Tools, Wallet Manager
2.  If the wallet is closed, then open it by selecting Open from the Wallet menu. When prompted, select the wallet directory location, and then enter your wallet password.
3.  In the left panel subtree, select the certificate that you want to export.
4.  From the Operations menu, select Export User Certificate.
    The Export Certificate dialog box appears.
5.  Enter the following information:
    - Enter path or folder name: Enter the file system directory location where you want to save your certificate, or navigate to the directory structure under Folders.

    - Enter file name: Enter a file name for your certificate.
6.  Click Save.
    A message confirms that the certificate was successfully exported to the file. You are returned to the Oracle Wallet Manager main window.

**See Also:**

"Exporting an Oracle Wallet to a Third-Party Environment" for information about exporting wallets. Oracle Wallet Manager supports storing multiple certificates in a single wallet, yet current browsers typically support only single-certificate wallets. For these browsers, you must export an Oracle wallet that contains a single key-pair.

##### 6.5.2.8 Exporting a User Certificate Request

To save the certificate request in a file system directory, export the certificate request as follows:

1.  Start Oracle Wallet Manager.
    - (UNIX) At the command line, enter the following command:

          owm

    - (Windows) Select Start, Programs, Oracle-HOME_NAME, Integrated Management Tools, Wallet Manager
2.  If the wallet is closed, then open it by selecting Open from the Wallet menu. When prompted, select the wallet directory location, and then enter your wallet password.
3.  In the left panel subtree, select the certificate request that you want to export.
4.  From the Operations menu, select Export Certificate Request.
    The Export Certificate Request dialog box appears.
5.  Enter the following information:
    - Enter path or folder name: Enter the file system directory location where you want to save your certificate, or navigate to the directory structure under Folders.

    - Enter file name: Enter a file name for your certificate.
6.  Click OK.
    A message confirms that the certificate request was successfully exported to the file. You are returned to the Oracle Wallet Manager main window.

#### 6.5.3 Managing Trusted Certificates for Oracle Wallets

Managing trusted certificates includes the following tasks:

- Importing a Trusted Certificate

- Removing a Trusted Certificate

- Exporting a Trusted Certificate to Another File System Location

- Exporting All Trusted Certificates to Another File System Location

##### 6.5.3.1 Importing a Trusted Certificate

You can import a trusted certificate into a wallet in either of two ways: paste the trusted certificate from an e-mail that you receive from the certificate authority, or import the trusted certificate from a file.

Oracle Wallet Manager automatically installs trusted certificates from VeriSign, RSA, Entrust, and GTE CyberTrust when you create a new wallet.

This section contains:

- Copying and Pasting Text-Only (BASE64) Trusted Certificates

- Importing a File That Contains the Trusted Certificate

##### Copying and Pasting Text-Only (BASE64) Trusted Certificates

1.  Copy the trusted certificate from the body of the email message you received that contained the user certificate. Include the lines `BEGIN CERTIFICATE` and `END CERTIFICATE.`

    You can use the Ctrl+c keyboard shortcut to copy the user certificate.

2.  Start Oracle Wallet Manager.

    - (UNIX) At the command line, enter the following command:

          owm

    - (Windows) Select Start, Programs, Oracle-HOME_NAME, Integrated Management Tools, Wallet Manager

3.  If the wallet is closed, then open it by selecting Open from the Wallet menu. When prompted, select the wallet directory location, and then enter your wallet password.

4.  From the Operations menu, select Import Trusted Certificate.

    The Import Trusted Certificate dialog box appears.

5.  Select the Paste the certificate option and then click OK.

    Another Import Trusted Certificate dialog box appears with the following message:

        Please paste a BASE64 format certificate below.

6.  Paste the certificate into the window, and click OK.

    You can use the Ctrl+v keyboard shortcut to paste the certificate.

    A message informs you that the trusted certificate was successfully installed.

7.  Click OK.

    You are returned to the Oracle Wallet Manager main panel, and the trusted certificate is displayed at the bottom of the Trusted Certificates tree.

##### Importing a File That Contains the Trusted Certificate

1.  Ensure that you had saved the file that contains the trusted certificate in either text (BASE64) or binary (`der`) format.
2.  Start Oracle Wallet Manager.
    - (UNIX) At the command line, enter the following command:

          owm

    - (Windows) Select Start, Programs, Oracle-HOME_NAME, Integrated Management Tools, Wallet Manager
3.  If the wallet is closed, then open it by selecting Open from the Wallet menu. When prompted, select the wallet directory location, and then enter your wallet password.
4.  From the Operations menu, select Import Trusted Certificate.
    The Import Trusted Certificate dialog box appears.
5.  Select the Select a file that contains the certificate option and then click OK.
    The Import Trusted Certificate dialog box appears.
6.  Enter the following information:
    - Enter path or folder name: Enter the file system directory location where the certificate is stored, or navigate to the directory structure under Folders.

    - Enter file name: Select the name of the trusted certificate file (for example, `cert.txt``)`.
7.  Click OK.
    A message informs you that the trusted certificate was successfully imported into the wallet.
8.  Click OK to exit the dialog box.
    You are returned to the Oracle Wallet Manager main panel, and the trusted certificate is displayed at the bottom of the Trusted Certificates tree.

##### 6.5.3.2 Removing a Trusted Certificate

You cannot remove a trusted certificate if it has been used to sign a user certificate still present in the wallet. To remove such trusted certificates, you must first remove the certificates it has signed. Also, you cannot verify a certificate after its trusted certificate has been removed from your wallet.

To remove a trusted certificate from a wallet:

1.  Start Oracle Wallet Manager.
    - (UNIX) At the command line, enter the following command:

          owm

    - (Windows) Select Start, Programs, Oracle-HOME_NAME, Integrated Management Tools, Wallet Manager
2.  If the wallet is closed, then open it by selecting Open from the Wallet menu. When prompted, select the wallet directory location, and then enter your wallet password.
3.  Select the trusted certificate listed in the Trusted Certificates tree.
4.  From the Operations menu, select Remove Trusted Certificate.
    A dialog box warns you that your user certificate will no longer be verifiable by its recipients if you remove the trusted certificate that was used to sign it.
5.  Select Yes.
    The selected trusted certificate is removed from the Trusted Certificates tree.

##### 6.5.3.3 Exporting a Trusted Certificate to Another File System Location

1.  Start Oracle Wallet Manager.
    - (UNIX) At the command line, enter the following command:

          owm

    - (Windows) Select Start, Programs, Oracle-HOME_NAME, Integrated Management Tools, Wallet Manager
2.  If the wallet is closed, then open it by selecting Open from the Wallet menu. When prompted, select the wallet directory location, and then enter your wallet password.
3.  In the left panel subtree, select the trusted certificate that you want to export.
4.  From the Operations menu, select Export Trusted Certificate.
    The Export Trusted Certificate dialog box appears.
5.  Enter the following information:
    - Enter path or folder name: Enter a file system directory in which you want to save your trusted certificate, or navigate to the directory structure under Folders.

    - Enter file name: Enter a file name to save your trusted certificate.
6.  Click OK.
    You are returned to the Oracle Wallet Manager main window.

##### 6.5.3.4 Exporting All Trusted Certificates to Another File System Location

1.  Start Oracle Wallet Manager.
    - (UNIX) At the command line, enter the following command:

          owm

    - (Windows) Select Start, Programs, Oracle-HOME_NAME, Integrated Management Tools, Wallet Manager
2.  If the wallet is closed, then open it by selecting Open from the Wallet menu. When prompted, select the wallet directory location, and then enter your wallet password.
3.  From the Operations menu, select Export All Trusted Certificates.
    The Export Trusted Certificate dialog box appears.
4.  Enter the following information:
    - Enter path or folder name: Enter a file system directory location where you want to save your trusted certificates, or navigate to the directory structure under Folders.

    - Enter file name: Enter a file name to save your trusted certificates.
5.  Click OK.
    You are returned to the Oracle Wallet Manager main window.
