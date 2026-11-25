## E  Oracle Database FIPS 140-2 Settings

Oracle supports the Federal Information Processing Standard (FIPS) standard for 140-2.

- About the Oracle Database FIPS 140-2 Settings
  Federal Information Processing Standards (FIPS) are standards and guidelines for federal computer systems that are developed by the U.S. National Institute of Standards and Technology (NIST).
- Configuring FIPS 140-2 for Transparent Data Encryption and DBMS_CRYPTO
  The `DBFIPS_140` initialization parameter configures FIPS mode.
- Configuration of FIPS 140-2 for Transport Layer Security
  The `SSLFIPS_140` parameter configures FIPS mode for Transport Layer Security (TLS).
- Configuration of FIPS 140-2 for Native Network Encryption
  You can configure FIPS 140-2 for native network encryption by setting a parameter in the `sqlnet.ora` file for both the server and the client.
- Postinstallation Checks for FIPS 140-2
  After you configure the FIPS 140-2 settings, you must verify permissions in the operating system.
- Verifying FIPS 140-2 Connections
  You can use trace files and other methods to verify the FIPS 140-2 connections.

**Parent topic:** [Appendixes](part_7.md)

### E.1 About the Oracle Database FIPS 140-2 Settings

Federal Information Processing Standards (FIPS) are standards and guidelines for federal computer systems that are developed by the U.S. National Institute of Standards and Technology (NIST).

FIPS was developed in accordance with the Federal Information Security Management Act (FISMA). Although FIPS was developed for use by the federal government, many private sector entities voluntarily use these standards.

FIPS 140-2 specifies the security requirements that will be satisfied by a cryptographic module, providing four increasing, qualitative levels intended to cover a range of potential applications and environments. Security Level 1 conforms to the FIPS 140-2 algorithms, key sizes, integrity checks, and other requirements that are imposed by the regulations. FIPS 140-2 Security Level 1 requires no physical security mechanisms in the module beyond the requirement for production-grade equipment. As a result, this level allows software cryptographic functions to be performed in a general-purpose computer running on a specified operating environment.

When FIPS 140-2 settings are configured for the Oracle Database, the database uses FIPS 140-2 Level 1 validated cryptographic libraries to protect data at rest and in transit over the network. Oracle Database uses these cryptographic libraries for native network encryption, Transparent Data Encryption (TDE) of columns and tablespaces (including Oracle SecureFiles), Transport Layer Security (TLS), and the `DBMS_CRYPTO` PL/SQL package.

Oracle Database currently uses Dell BSAFE, formerly known as RSA BSAFE, as the FIPS 140-2 level 1 validated cryptography library. To verify the current status of the FIPS certification, you can find information at the Computer Security Resource Center (CSRC) Web site address from the National Institute of Standards and Technology:

[[`http://csrc.nist.gov/groups/STM/cmvp/validation.html`](http://csrc.nist.gov/groups/STM/cmvp/validation.html)` `](http://csrc.nist.gov/groups/STM/cmvp/validation.html)

You can find information specific to FIPS by searching the validated cryptographic modules for vendor "RSA" and Module Name "BSAFE."

Note that Oracle Database FIPS settings enforce the use of FIPS-approved algorithms for the Oracle database only. Third-party vendor software used with Oracle Database running in FIPS mode must use only these FIPS-approved algorithms, or else the vendor software will encounter failures.

**Parent topic:** Oracle Database FIPS 140-2 Settings

### E.2 Configuring FIPS 140-2 for Transparent Data Encryption and DBMS_CRYPTO

The `DBFIPS_140` initialization parameter configures FIPS mode.

1.  To configure Transparent Data Encryption and the `DBMS_CRYPTO` PL/SQL package program units to run in FIPS mode, set the `DBFIPS_140` initialization parameter to `TRUE`.
    The effect of this parameter depends on the platform.
2.  Restart the database.

Table E-1 describes how the `DBFIPS_140` parameter affects various platforms.

Table E-1 How the DBFIPS_140 Initialization Parameter Affects Platforms

| Platform                                               | Effect of Setting DBFIPS_140 to TRUE or FALSE                                                                                                                                                                                                                                               |
|:-------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Linux or Windows on Intel x86_64                       | • `TRUE`: TDE and `DBMS_CRYPTO` program units use Micro Edition Suite (MES) 4.6 FIPS mode, which uses RSA BSAFE Crypto-C Micro Edition (CCME) 4.1.5<br>• `FALSE`: TDE and `DBMS_CRYPTO` program units use Intel Performance Primitives (IPP)                                                |
| Solaris 11.1+ on either SPARC T-series or Intel x86_64 | • `TRUE`: TDE and `DBMS_CRYPTO` program units use Micro Edition Suite (MES) 4.6 FIPS mode, which uses RSA BSAFE Crypto-C Micro Edition (CCME) 4.1.5<br>• `FALSE`: TDE and `DBMS_CRYPTO` program units use Solaris Cryptographic Framework (SCF)/UCrypto (separately validated for FIPS 140) |
| Other operating systems or hardware                    | • `TRUE`: TDE and `DBMS_CRYPTO` program units use MES 4.6 FIPS mode, which uses RSA BSAFE Crypto-C Micro Edition (CCME) 4.1.5<br>• `FALSE`: TDE and `DBMS_CRYPTO` program units use MES 4.6 non-FIPS mode                                                                                   |

Be aware that setting `DBFIPS_140` to `TRUE` and thus using the underlying library in FIPS mode incurs a certain amount of overhead when the library is first loaded for each process. This is due to the verification of the signature and the execution of the self tests on the library. Once the library is loaded, then there is no other impact on performance.

**Related Topics**

- [Oracle Database Reference](../refrn/DBFIPS_140.md)

**Parent topic:** Oracle Database FIPS 140-2 Settings

### E.3 Configuration of FIPS 140-2 for Transport Layer Security

The `SSLFIPS_140` parameter configures FIPS mode for Transport Layer Security (TLS).

- Configuring the SSLFIPS_140 and SSLFIPS_LIB Parameters for Transport Layer Security
  To configure FIPS 140-2 for TLS, you must set the `SSLFIPS_140` parameter. If you are using the Oracle Instant Client, then you must set the `SSLFIPS_LIB` parameter as well.
- Approved TLS Cipher Suites for FIPS 140-2
  A cipher suite is a set of authentication, encryption, and data integrity algorithms that exchange messages between network nodes.

**Parent topic:** Oracle Database FIPS 140-2 Settings

#### E.3.1 Configuring the SSLFIPS_140 and SSLFIPS_LIB Parameters for Transport Layer Security

To configure FIPS 140-2 for TLS, you must set the `SSLFIPS_140` parameter. If you are using the Oracle Instant Client, then you must set the `SSLFIPS_LIB` parameter as well.

The `SSLFIPS_140` parameter configures the Transport Layer Security (TLS) adapter to run in FIPS mode. `SSLFIPS_LIB` sets the location of the FIPS library.

1.  Ensure that the `fips.ora` file is either located in the `$ORACLE_HOME``/ldap/admin` directory, or is in a location pointed to by the `FIPS_HOME` environment variable.
2.  In the `fips.ora` file, set the `SSLFIPS_140` and `SSLFIPS_LIB` parameters.
    - Set `SSLFIPS_140` to `TRUE` so that the TLS adapter can run in FIPS mode. For example:

          SSLFIPS_140=TRUE

      This parameter is `FALSE` by default.

    - If you are using Oracle Instant Client, then set `SSLFIPS_LIB` to the location of the FIPS library. For example:

          SSLFIPS_LIB=$ORACLE_HOME/lib
3.  Repeat this procedure in any Oracle Database home for any database server or client.

When you set `SSLFIPS_140` to `TRUE`, Transport Layer Security cryptographic operations take place in the embedded RSA/Micro Edition Suite (MES) library in FIPS mode. These cryptographic operations are accelerated by the CPU when hardware acceleration is available and properly configured in the host hardware and software.

If you set `SSLFIPS_140` to `FALSE`, then Transport Layer Security cryptographic operations take place in the embedded RSA/Micro Edition Suite (MES) library in non-FIPS mode, and as with the `TRUE` setting, the operations are accelerated if possible.

**Note:**

The `SSLFIPS_140` parameter replaces the `SQLNET.SSLFIPS_140` parameter used in Oracle Database 10g release 2 (10.2). You must set the parameter in the `fips.ora` file, and not the `sqlnet.ora` file.

**Parent topic:** Configuration of FIPS 140-2 for Transport Layer Security

#### E.3.2 Approved TLS Cipher Suites for FIPS 140-2

A cipher suite is a set of authentication, encryption, and data integrity algorithms that exchange messages between network nodes.

During a TLS handshake, for example, the two nodes negotiate to see as to which cipher suite they will use when transmitting messages back and forth.

##### Configuring Specific Cipher Suites

Oracle Database TLS cipher suites are automatically set to FIPS approved cipher suites. If you want to configure specific cipher suites, then you can do so by setting the `SSL_CIPHER_SUITES` parameter in the `sqlnet.ora` or the `listener.ora` file.

    SSL_CIPHER_SUITES=(SSL_cipher_suite1[,SSL_cipher_suite2[,..]])

You can also use Oracle Net Manager to set this parameter on the server and the client.

If a specific cipher suite is not specified, then Oracle Database will use the strongest cipher suite common to both the database server and client. The priority order of cipher suites to be selected are in order as they are listed in the preferred and less preferred cipher lists below. Oracle Database will not select 3DES cipher suites automatically due to their weakness; they must be configured explicitly.

##### Preferred Cipher Suites

The following cipher suites are approved for FIPS validation if you are using Transport Layer Security (TLS) version 1.2:

- `TLS_ECDHE_ECDSA_WITH_AES_256_GCM_SHA384`
- `TLS_ECDHE_ECDSA_WITH_AES_256_CBC_SHA384`
- `TLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256`
- `TLS_ECDHE_ECDSA_WITH_AES_128_CBC_SHA256`
- `TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384`
- `TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384`
- `TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256`
- `TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256`

The following cipher suites are approved for FIPS validation if you are using Transport Layer Security (TLS) version 1, 1.1, or 1.2:

- `TLS_ECDHE_ECDSA_WITH_AES_256_CBC_SHA`
- `TLS_ECDHE_ECDSA_WITH_AES_128_CBC_SHA`
- `TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA`
- `TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA`

##### 3DES-Based Cipher Suites

Oracle does not recommend 3DES-based cipher suites because of a weakness in their design. Oracle Database release 21c and later contains support for the following 3DES-based cipher suites. However, they are not enabled by default and must be explicitly configured through the `SSL_CIPHER_SUITES` parameter in the `sqlnet.ora` or the `listener.ora` file.

- `TLS_ECDHE_ECDSA_WITH_3DES_EDE_CBC_SHA`
- `TLS_ECDHE_RSA_WITH_3DES_EDE_CBC_SHA`
- `TLS_RSA_WITH_3DES_EDE_CBC_SHA`

**Related Topics**

- [Step 1C: Set the Transport Layer Security Cipher Suites on the Server (Optional)](configuring-secure-sockets-layer-authentication.md)
- [Step 2D: Set the Client Transport Layer Security Cipher Suites (Optional)](configuring-secure-sockets-layer-authentication.md)

**Parent topic:** Configuration of FIPS 140-2 for Transport Layer Security

### E.4 Configuration of FIPS 140-2 for Native Network Encryption

You can configure FIPS 140-2 for native network encryption by setting a parameter in the `sqlnet.ora` file for both the server and the client.

- About Configuration of FIPS 140-2 for Native Network Encryption
  The configuration of FIPS 140-2 for native network encryption is similar to that of Transport Layer Security (TLS).
- Configuring the FIPS_140 Parameter for Native Network Encryption
  To configure FIPS 140-2 for native network encryption, you must set the `FIPS_140` parameter in the `sqlnet.ora` file.

**Parent topic:** Oracle Database FIPS 140-2 Settings

#### E.4.1 About Configuration of FIPS 140-2 for Native Network Encryption

The configuration of FIPS 140-2 for native network encryption is similar to that of Transport Layer Security (TLS).

For network native encryption, you enable FIPS mode by setting `SSL_FIPS140` in the `sqlnet.ora` configuration file, instead of the `SSL_FIPS140` setting in `fips.ora`.

The algorithms that the FIPS library supports for native network encryption are as follows:

- Encryption: AES128, AES192, and AES256
- Checksumming: SHA1, SHA256, SHA384, and SHA512

**Parent topic:** Configuration of FIPS 140-2 for Native Network Encryption

#### E.4.2 Configuring the FIPS_140 Parameter for Native Network Encryption

To configure FIPS 140-2 for native network encryption, you must set the `FIPS_140` parameter in the `sqlnet.ora` file.

The `FIPS_140` parameter configures the native network encryption adapter to run in FIPS mode.

1.  Locate the `sqlnet.ora` file that is used by the database client or database server
2.  Add the following line to the `sqlnet.ora` file:
        SQLNET.FIPS_140=TRUE
3.  Repeat this procedure in any Oracle Database home for any database server or client.

When `FIPS_140` is set to `TRUE`, native network encryption cryptographic operations take place in the embedded BSAFE Micro Edition Suite (MES) library in FIPS mode. These cryptographic operations are accelerated by the CPU when hardware acceleration is available and properly configured in the host hardware and software.

**Parent topic:** Configuration of FIPS 140-2 for Native Network Encryption

### E.5 Postinstallation Checks for FIPS 140-2

After you configure the FIPS 140-2 settings, you must verify permissions in the operating system.

The permissions are as follows:

- Set execute permissions on all Oracle executable files to prevent the execution of Oracle Cryptographic Libraries by users who are unauthorized to do so, in accordance with the system security policy.

- Set read and write permissions on all Oracle executable files to prevent accidental or deliberate reading or modification of Oracle Cryptographic Libraries by any user.

To comply with FIPS 140-2 Level 2 requirements, in the security policy, include procedures to prevent unauthorized users from reading, modifying or executing Oracle Cryptographic Libraries processes and the memory they are using in the operating system.

**Parent topic:** Oracle Database FIPS 140-2 Settings

### E.6 Verifying FIPS 140-2 Connections

You can use trace files and other methods to verify the FIPS 140-2 connections.

- Verifying FIPS 140-2 Connections for Transport Layer Security
  You can use trace files to check the FIPS 140-2 connections for Transport Layer Security (TLS).
- Verifying FIPS 140-2 Connections for Network Native Encryption
  You can use trace files to check the FIPS 140-2 connections for network native encryption.
- Verifying FIPS 140-2 Connections for Transparent Data Encryption and DBMS_CRYPTO
  You can check if FIPS mode is enabled by using SQL\*Plus.

**Parent topic:** Oracle Database FIPS 140-2 Settings

#### E.6.1 Verifying FIPS 140-2 Connections for Transport Layer Security

You can use trace files to check the FIPS 140-2 connections for Transport Layer Security (TLS).

1.  Add the following lines to `sqlnet.ora` to enable tracing:
        trace_directory_server=trace_directory
        trace_file_server=trace_file
        trace_level_server=trace_level

    For example:

        trace_directory=/private/oracle/owm
        trace_file_server=fips_trace.trc
        trace_level_server=16

    Trace level 16 is the minimum trace level required to check the results of the FIPS self-tests.
2.  Check the trace files by searching for `Provider Type: FIPS140`.

**Parent topic:** Verifying FIPS 140-2 Connections

#### E.6.2 Verifying FIPS 140-2 Connections for Network Native Encryption

You can use trace files to check the FIPS 140-2 connections for network native encryption.

1.  Add the following lines to `sqlnet.ora` to enable tracing:
        trace_directory_server=trace_directory
        trace_file_server=trace_file
        trace_level_server=trace_level

    For example:

        trace_directory=/private/oracle/owm
        trace_file_server=fips_trace.trc
        trace_level_server=16

    Trace level 16 is the minimum trace level required to check the results of the FIPS self-tests.
2.  Check the trace files by searching for `FIPS DAC check succeeded`.

**Parent topic:** Verifying FIPS 140-2 Connections

#### E.6.3 Verifying FIPS 140-2 Connections for Transparent Data Encryption and DBMS_CRYPTO

You can check if FIPS mode is enabled by using SQL\*Plus.

1.  Connect to the database instance by using SQL\*Plus.
2.  Execute the following `SHOW PARAMETER` command:
        SHOW PARAMETER DBFIPS_140

    Output similar to the following should appear:

        NAME                                 TYPE        VALUE
        ------------------------------------ ----------- ------------------------------
        DBFIPS_140                           boolean     TRUE

**Parent topic:** Verifying FIPS 140-2 Connections
