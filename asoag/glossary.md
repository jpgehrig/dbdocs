## Glossary

### actual data

In Oracle Data Redaction, the data in a protected table or view. An example of actual data could be the number `123456789`, and the redacted data version of this number could be `999996789`.

**Parent topic:** Glossary

### auto-login TDE wallet

A software keystore that is protected by a system-generated password and does not need to be explicitly opened by a security administrator. Auto-login TDE wallets are automatically opened when accessed and can be used on any computer that runs an Oracle database. For example, consider an Oracle RAC environment that has four nodes, and each node is on a different computer. This environment uses an auto-login keystore. When a `REKEY` operation is performed on node 1, the auto-login and password-based keystores must be copied to the computers that host nodes 2, 3, and 4. In this configuration, the auto-login keystores will be opened on all four nodes when required.

**Parent topic:** Glossary

### cipher suite

A set of authentication, encryption, and data integrity algorithms used to exchange messages between network nodes using Transport Layer Security (TLS). During a TLS handshake, for example, the two nodes negotiate to see which cipher suite they will use when transmitting messages back and forth.

**Parent topic:** Glossary

### ciphertext

Message text that has been encrypted.

See also encrypted text.

**Parent topic:** Glossary

### data redaction

The ability to mask data with different values in real time, that is, at the moment a user tries to access the data. You can mask all of the data, a partial subset of the data, or display random values in place of the data. It does not change the actual data in the database.

**Parent topic:** Glossary

### decryption

The process of converting an encrypted message (the ciphertext), back to its original message (plaintext).

**Parent topic:** Glossary

### encrypted text

Text that has been encrypted, using an encryption algorithm and an encryption key; the output stream of an encryption process. The text is not readable or decipherable, without decrypting it first. Also called ciphertext.

**Parent topic:** Glossary

### encryption

The process of converting an original message (plaintext) to an encrypted message (ciphertext).

**Parent topic:** Glossary

### external keystore

A container that stores a Transparent Data Encryption key for a hardware security module. (The previous term for external keystore was hardware keystore.) An external keystore can be Oracle Key Vault or Oracle Cloud Infrastructure (OCI) Key Management Service (KMS). External keystores provide centralized key management for TDE-enabled databases.

**Parent topic:** Glossary

### hardware security module

A physical device that provides secure storage for encryption keys. Oracle does not support third-party hardware security modules to provide key management for Transparent Data Encryption-enabled databases. (See My Oracle Support note [2310066.1](https://support.oracle.com/epmos/faces/DocumentDisplay?_afrLoop=392345372613593&id=2310066.1&_adf.ctrl-state=tsma1yzfn_52) for more information.) Oracle Key Vault can provide third-party hardware security modules to provide root-of-trust to Oracle Key Vault. See [Oracle Key Vault Root of Trust HSM Configuration Guide](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/asoag&id=OKVHM-GUID-A3CAE519-F583-4639-BD77-93289D64DF5C).

**Parent topic:** Glossary

### inference

A query that is designed to find data by repeatedly trying queries. For example, to find the users who earn the highest salaries, an intruder could use the following query:

    SELECT FIRST_NAME, LAST_NAME, SALARY FROM HR.EMPLOYEES WHERE SALARY > 16000 ORDER BY SALARY DESC;

    FIRST_NAME           LAST_NAME                     SALARY
    -------------------- ------------------------- ----------
    Steven               King                           24000
    Neena                Kochhar                        17000
    Lex                  De Haan                        17000

**Parent topic:** Glossary

### key pair

A public key and its associated private key. See public and private key pair.

**Parent topic:** Glossary

### keystore

A general term for any container that stores encryption keys, such as Transparent Data Encryption keys and other encrypted data. It can refer to a TDE wallet, which is specific to Oracle Database, or to an external keystore, which is specific to Oracle Key Vault or Oracle Cloud Interface (OCI) Key Management Service (KMS).

**Parent topic:** Glossary

### local auto-login TDE wallet

A TDE wallet that is local and restricted to the computer on which it was created.

See also auto-login TDE wallet.

**Parent topic:** Glossary

### mask

The ability to redact data from a user or an application.

**Parent topic:** Glossary

### Oracle-managed tablespace

An Oracle-supplied tablespace that contains information necessary for the correct functioning (confidentiality, integrity, and availability) of the database system. This information includes the system's data dictionary, the system's temporary sort area, the system's undo segment, and the system's auxiliary data. This information is only expected to be updated internally by the Oracle database server itself, and does not normally be updated directly by users.

**Parent topic:** Glossary

### password-based TDE wallet

A TDE wallet that must be opened with a password before it can be accessed.

**Parent topic:** Glossary

### plaintext

Message text that has not been encrypted.

**Parent topic:** Glossary

### private key

In public-key cryptography, this key is the private key that is known only to its owner. It is primarily used for encrypting message digests used with digital signatures.

See public and private key pair.

**Parent topic:** Glossary

### public key

One of two keys that are used in public key cryptography, the other key being the private key. In typical public key cryptography usage, the public key is used to encrypt data or verify digital signatures. The the private key is used to decrypt data or generate digital signatures. The public key, unlike the private key, can be made available to anyone whereas the private key must remain secret.

See public and private key pair.

**Parent topic:** Glossary

### public key encryption

The process where the sender of a message encrypts the encryption key of the recipient. Upon delivery, the message is decrypted by the recipient using its private key.

**Parent topic:** Glossary

### public and private key pair

A set of two related numbers used for encryption and decryption, where one is called the private key and the other is called the public key. Public keys are typically made widely available, while private keys are held by their respective owners. Data encrypted with either a public key or a private key from a key pair can be decrypted with its associated key from the key pair.

**Parent topic:** Glossary

### public key infrastructure (PKI)

Information security technology utilizing the principles of public key cryptography. Public key cryptography involves encrypting and decrypting information using a shared public and private key pair. Provides for secure, private communications within a public network.

**Parent topic:** Glossary

### redacted data

Masked data that is displayed to the querying user. For example, if the actual data is `3714-4963-5398-4321`, then the redacted data could appear, depending on the Data Redaction policy, as `XXXX-XXXX-XXXX-4321`.

**Parent topic:** Glossary

### salt

In cryptography, a way to strengthen the security of encrypted data. Salt is a random string that is added to the data before it is encrypted, making it more difficult for attackers to steal the data by matching patterns of ciphertext to known ciphertext samples. Salt is often also added to passwords, before the passwords are hashed, to avoid dictionary attacks, a method that attackers use to determine sensitive passwords. The addition of salt to a password before hashing makes it more difficult for intruders to match the hash values (sometimes called verifiers) with their dictionary list of common password hash values, because they do not know the salt beforehand.

**Parent topic:** Glossary

### software keystore

See TDE wallet,

**Parent topic:** Glossary

### tablespace encryption key

An encryption key for the encryption of a tablespace. The TDE tablespace encryption key encrypts the tablespace encryption key, which in turn encrypts and decrypts data in the tablespace.

**Parent topic:** Glossary

### TDE master encryption key

A key that is stored within a TDE wallet or a external keystore. For table encryption, this key encrypts the TDE table key, and for tablespace encryption, it encrypts the tablespace encryption key.

See also keystore.

**Parent topic:** Glossary

### TDE table key

An encryption key that is associated with a table whose columns are marked for encryption. The TDE master encryption key encrypts this table encryption key.

**Parent topic:** Glossary

### TDE wallet

A container that stores a Transparent Data Encryption a TDE master encryption key for use as an auto-login TDE wallet, a local auto-login TDE wallet, or a password-based TDE wallet to store and manage security credentials for an individual entity. TDE wallets are specific to Oracle Database only. A Wallet Resource Locator (WRL) provides all of the necessary information to locate the TDE wallet. TDE wallets were previously referred to as software keystores.

**Parent topic:** Glossary

### wallet obfuscation

The ability to store and access an Oracle TDE wallet without querying the user for a password before access (supports single sign-on (SSO)).

**Parent topic:** Glossary

### Wallet Resource Locator (WRL)

A tool that provides all of the necessary information to locate a TDE wallet. It is a path to an operating system directory that contains a TDE wallet.

**Parent topic:** Glossary
