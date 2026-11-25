If the AutoUpgrade preupgrade report instructs you to upgrade the time zone files after completing the database upgrade, and you do not set AutoUpgrade to complete this task for you, then use the `DBMS_DST` PL/SQL package to upgrade the time zone file.

**Note:**

By default, if time zone files need to be updated, then AutoUpgrade typically performs this task for you. However, if you explicitly disable the time zone file upgrade in your AutoUpgrade configuration file, then you should perform this task either as part of your upgrade plan, or at a later point in time.

**Related Topics**

- [Upgrading Time Zone Data Using the DBMS_DST Package](../nlspg/datetime-data-types-and-time-zone-support.md)
- [My Oracle Support Doc ID 1585343.1](https://support.oracle.com/rs?type=doc&id=1585343.1)

**Parent topic:** [Recommended and Best Practices to Complete After Upgrading Oracle Database](recommended-and-best-practices-complete-upgrading-oracle-database.md)
