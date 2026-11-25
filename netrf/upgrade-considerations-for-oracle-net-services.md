## B Upgrade Considerations for Oracle Net Services

This appendix describes the coexistence and upgrade issues for Oracle Net Services.

- Anonymous Access to Oracle Internet Directory
  Typical users of directory naming (LDAP) require anonymous access to the Oracle Internet Directory for name lookup.

**Parent topic:** [Appendices](appendixes.md)

### B.1 Anonymous Access to Oracle Internet Directory

Typical users of directory naming (LDAP) require anonymous access to the Oracle Internet Directory for name lookup.

#### Oracle Internet Directory Setting

If you upgrade your Oracle Internet Directory software release 11g or later, then the default setting for Oracle Internet Directory changes to disallow anonymous access to the directory. The directory administrator must configure the directory to enable anonymous binds after upgrading the directory to release 11g. In addition, the way anonymous binds are configured in Oracle Internet Directory changed between Oracle Database 10g and Oracle Database 11g.

**Parent topic:** Upgrade Considerations for Oracle Net Services
