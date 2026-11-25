## Verifying Signed Oracle Instant Client RPM Packages

Use the `rpm` command to perform operations such as listing and verifying the signature fingerprint for Oracle Instant Client RPM packages for Oracle Linux 7 and Oracle Linux 8.

Ensure that the RPM signature fingerprint matches the expected key fingerprint and also verify the RPM package has a signature. Before you start this process, perform the following tasks:

1.  List the installed keys on your system:

        rpm -qa gpg-pubkey

    The output of this command is similar to the following:

        gpg-pubkey-ad986da3-5cabf60d
        gpg-pubkey-16c083cd-49af3996

2.  Import the GPG keys (optional):

        rpm --import GPG-KEY

    **Note:**

    Depending on your verification purpose you can install any GPG keys in the RPM database on your system to verify the signed packages.

### Scenario 1: To verify an RPM package that has a signature with the key not installed on the system by default

1.  Run the `rpm -qip` command to check the Oracle Instant Client Basic RPM package fingerprint. For example, for Linux x86-64:

        rpm -qip oracle-instantclient19.27-basic-19.27.0.0.0-1.x86_64.rpm | grep Signature

    The output of this command is similar to the following:

        warning: oracle-instantclient19.27-basic-19.27.0.0.0-1.x86_64.rpm: Header V3 RSA/SHA256 Signature, key ID 8d8b756f: NOKEY
        Signature: RSA/SHA256, Mon 09 Jan 2023 07:38:06 PM GMT, Key ID bc4d06a08d8b756f

2.  Run the `rpm --checksig --verbose` command to verify the package and print headers statuses and fingerprint details for the Oracle Instant Client Basic RPM package. For example, for Linux x86-64:

        rpm --checksig --verbose oracle-instantclient19.27-basic-19.27.0.0.0-1.x86_64.rpm

    The output of this command is similar to the following:

        oracle-instantclient19.27-basic-19.27.0.0.0-1.x86_64.rpm:
        Header V3 RSA/SHA256 Signature, key ID 8d8b756f: NOKEY

    This output verifies the Oracle Instant Client Basic RPM package signature by printing the key ID and returning `NOKEY` verification status as the GPG key with this ID is not present in the RPM key management system.

### Scenario 2: To verify RPM package with both signature and key installed

1.  Run the `rpm -qip` command to check the Oracle Instant Client Basic RPM package fingerprint. For example, for Linux x86-64:

        rpm -qip oracle-instantclient19.27-basic-19.27.0.0.0-1.x86_64.rpm | grep Signature

    The output of this command is similar to the following:

        Signature: RSA/SHA256, Fri 06 Jan 2023 11:11:04 PM GMT, Key ID 82562ea9ad986da3

2.  Run the `rpm --checksig --verbose` command to verify the package and print headers statuses and fingerprint details for Oracle Instant Client Basic RPM package. For example, for Linux x86-64:

        rpm --checksig --verbose oracle-instantclient19.27-basic-19.27.0.0.0-1.x86_64.rpm

    The output of this command is similar to the following:

        oracle-instantclient19.27-basic-19.27.0.0.0-1.x86_64.rpm:
        Header V3 RSA/SHA256 Signature, key ID ad986da3: OK
            Header SHA256 digest: OK
            Header SHA1 digest: OK
            Payload SHA256 digest: OK
            V3 RSA/SHA256 Signature, key ID ad986da3: OK
            MD5 digest: OK

    This output verifies the Oracle Instant Client Basic RPM package signature with the key and displays the fingerprint.

**Related Topics**

- [Oracle Linux Keys](https://linux.oracle.com/security/gpg/)
- [yum.oracle.com FAQs](https://yum.oracle.com/faq.html#a10)

**Parent topic:** [Verifying Oracle Instant Client Code Signing](enable-client-code-signing.md)
