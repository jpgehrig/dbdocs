## Compatibility and Interoperability Between Oracle Database Releases

Learn how to understand and avoid compatibility and interoperability issues that can occur because of differences in Oracle Database releases.

Oracle Database releases can have differences that can result in compatibility and interoperability issues. These differences can affect both general database administration and existing applications.

- [About Oracle Database Release Numbers](oracle-database-release-numbers.md)
  Oracle Database releases are categorized by five numeric segments that indicate release information.
- [Convention for Referring to Release Numbers in Oracle Database Upgrade Guide](conventions-release-numbers-oracle.md)
  Review to understand how statements apply to releases.
- [What Is Oracle Database Compatibility?](what-is-oracle-database-compatibility.md)
  Before you upgrade, review compatibility between your earlier release Oracle Database and the new Oracle Database release as part of your upgrade plan.
- [What Is Interoperability for Oracle Database Upgrades?](what-is-interoperability-for-oracle-database-upgrades.md)
  In the context of upgrading Oracle Database, interoperability is the ability of different releases of Oracle Database to communicate and work in a distributed environment.
- [About Invalid Schema Objects and Database Upgrades](invalid-schema-objects-database-upgrades.md)
  Run `utlrp.sql` to validate invalid objects as part of your upgrade test plan.
- [About Upgrading Oracle OLAP Data Security Policies](upgrading-oracle-olap-data-security-policies.md)
  Security policies are stored differently starting with Oracle Database 12c. If your existing Oracle Database is 11g Release 11.2, then delete security roles.

**Parent topic:** [Introduction to Upgrading Oracle Database](intro-to-upgrading-oracle-database.md)
