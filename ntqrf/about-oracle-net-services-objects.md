In Oracle Database Client 11g or later, directory clients may optionally be configured to authenticate with the directory while resolving DB names to connect strings.

This makes it possible for Oracle Net Services objects to be protected using ACLs.

There are many ways in which the identities of users may be defined in the directory, and how those users or certain groups of users may be given access to some or all Net Services. Oracle Database supplies no predefined groups, and has no procedures in the config tools for defining read-access restrictions on this data. Therefore, administrators must use standard object management tools from their directory system to manually create any necessary groups and ACLs. Existing identity structures may be referred to by Net Service ACLs.

The access definitions for objects are complex and may involve security properties which are inherited from parent nodes in the Directory Information Tree (DIT).

Oracle recommends that the administrators should refer to the relevant tools and documentation for the directory system they are using, and formulate or integrate access management for Oracle Net Services objects into a directory-wide policy and security implementation.

**Note:**

Pre-11g clients can only bind to the directory as anonymous, so any ACL protection on Net Services disables older clients. Access Control can only be implemented if all clients requiring access to these objects are 11g or later.

**Parent topic:** [Overview of Security Groups](overview-of-security-groups.md)
