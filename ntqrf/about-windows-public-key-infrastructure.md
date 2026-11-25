Learn about Windows public key infrastructure.

**Note:**

Microsoft Certificate Store integration works only with digital certificates that use Microsoft Enhanced Cryptographic Provider. To create these certificates, you must install Windows High Encryption Pack and select Microsoft Enhanced Cryptographic Provider. Also, when there are multiple certificates available for the same key usage (signature/key exchange), the first certificate retrieved is used for Oracle SSL.

- [About Microsoft Certificate Stores](about-microsoft-certificate-stores.md)
  Microsoft Certificate Stores are repositories for storing digital certificates and their associated properties.
- [About Microsoft Certificate Services](about-microsoft-certificate-services.md)
  Learn about Microsoft Certificate Services (MCS) and its associated modules.
- [Using Microsoft Certificate Stores with Oracle PKI Applications](using-microsoft-certificate-stores-with-oracle-pki-applications.md)
  Wallet Resource Locator (WRL) specifies that parameter `WALLET_LOCATN` in file `sqlnet.ora` identifies a particular PKI.

**Parent topic:** [Oracle PKI Integration with Windows](oracle-pki-integration-with-windows.md)
