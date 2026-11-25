Microsoft Certificate Stores are repositories for storing digital certificates and their associated properties.

Windows operating systems store digital certificates and certificate revocation lists in logical and physical stores. Logical stores contain pointers to public key objects in physical stores. Logical stores enable public key objects to be shared between users, computers, and services without requiring storage of duplicates of objects for each user, computer, or services. Public key objects are physically stored in the certificate authority of the local computer or, for some user certificates, in Active Directory. Standard system certificate stores defined by Microsoft include:

- MY or Personal

- CA

- ROOT

MY or Personal holds a user's certificates for which the associated private key is available. The MY certificate store maintains certificate properties that indicate the Cryptographic Service Provider (CSP) associated with the private key. An application uses this information to obtain the private key from the CSP for the associated certificate. CA holds issuing or intermediate certificate authority (CA) certificates. ROOT holds only self-signed CA certificates for trusted root CAs.

**Parent topic:** [About Windows Public Key Infrastructure](about-windows-public-key-infrastructure.md)
