Learn about Microsoft Certificate Services (MCS) and its associated modules.

Microsoft Certificate Services (MCS) consists of the following modules:

- Server Engine

- Intermediary

- Policy

Server Engine handles all certificate requests. It interacts with other modules at each processing stage to ensure that the proper action is taken based on the state of the request. The Intermediary module receives requests for new certificate from clients and then submits them to Server Engine. The Policy module contains the set of rules controlling the issuance of certificates. This module may be upgraded or customized as needed.

**Parent topic:** [About Windows Public Key Infrastructure](about-windows-public-key-infrastructure.md)
