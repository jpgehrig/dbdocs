Oracle Database and configuration tools can use the login credentials of the Windows user currently logged on to connect to Active Directory without having to reenter the login credentials.

This feature has the following benefits:

- Oracle clients and databases can securely connect to Active Directory and retrieve the net service name.

- Oracle configuration tools can connect automatically to Active Directory and configure Oracle Database and net service name objects. The enabled tools include Oracle Net Configuration Assistant and Database Configuration Assistant.

- Oracle clients can make secure access over the internet to avoid anonymous binds to the directory. The enhanced security enables the sites to restrict access to Database Service by setting access control (ACL) on Database Service DN in Directory Server. The enhancement gives clients the option to use authenticated binds for LDAP name lookup. Clients have access to Database Service object if the object (DN of Database Service Entry) has been configured with restrictive access control.

### Configuration on machines that require authenticated name lookups

Add the following entry in `sqlnet.ora` to enable authenticated name lookup:

    names.ldap_authenticate_bind = TRUE

**Parent topic:** [Overview of Oracle Components That Integrate with Active Directory](overview-of-oracle-components-that-integrate-with-active-directory.md)
