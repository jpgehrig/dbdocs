When using Oracle features that support Active Directory, ensure that the Active Directory computer can be successfully reached using all possible TCP/IP host name forms to reach the domain controller.

For example, if the host name of the domain controller is `server1` in the domain `example.com`, then ensure that you can ping that computer using all of the following:

- `server1.example.com`

- `example.com`

- `server1`

Active Directory often issues referrals back to itself in one or more of these forms, depending upon the operation being performed. If any of the forms cannot reach the Active Directory computer, then some LDAP operations may fail.

**Parent topic:** [Overview of Microsoft Active Directory Support](overview-of-microsoft-active-directory-support.md)
