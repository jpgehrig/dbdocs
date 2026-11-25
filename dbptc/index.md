In this article, you can learn about patch delivery methods for Oracle Database 19c and later versions.

- Introduction to Oracle Database Patch Maintenance
  One of the duties of a DBA is to maintain the Oracle Database software. There are two maintenance strategies.
- Proactive Maintenance with RUs and MRPs
  Proactive maintenance is accomplished by proactively applying a routine quarterly patch bundle (Release Update) that is available from the My Oracle Support (MOS) Customer Portal for each Oracle Database software release.
- Reactive Maintenance with One-off Patches
  All methods allow one-off patches to be installed, but the version of a one-off patch that is required may vary depending on the patching method.
- Which Patching Method to Use?
  For Linux x86-64 platforms, MRPs provide a method to apply all Oracle recommended fixes easily for the current RU.
- Patch Conflict Resolution
  If interim patches are used in conjunction with one of the proactive patching methods, then there may be patch conflicts.
- Frequently Asked Questions
  This section lists frequently asked questions.
- Current Database Proactive Patches
  The following table gives information on available proactive database related patches by platform, environment, and version.
- Documentation Accessibility

## Introduction to Oracle Database Patch Maintenance

One of the duties of a DBA is to maintain the Oracle Database software. There are two maintenance strategies.

**Reactive Patches** react to specific maintenance issues. They are characterized as follows:

- Usually delivered as “Interim Patches”
- Historically known as “one-off” patches
- Are provided on demand for a given “defect, version, platform” combination
- Go through basic sanity tests
- Certain reactive fixes may be included in future Release Updates

**Proactive Patches** provide recommended updates for all Oracle Database customers. They are characterized as follows:

- Address high impact bugs that affect a given configuration
- Contain proven low risk fixes
- Include cumulative of prior fixes
- Go through extra levels of testing, determined by the features affected by the patch
- Are available on "My Oracle Support" by clicking on the "Patches & Updates" tab
- Are available as Release Updates (RU) and Monthly Recommended Patches (MRPs)

**Note:**

Starting in October 2022, Oracle introduces the Monthly Recommended Patches (MRP) option for proactive patch maintenance, which is available for Oracle Database 19c on Linux x86-64 platforms. The Release Update Revision process (RUR) is deprecated and will be discontinued. Release Updates (RUs) continue to be available for all platforms, and for releases supported for patch updates. See Introducing Monthly Recommended Patches (MRPs) and FAQ (Doc ID 2898740.1) and Sunsetting of 19c RURs and FAQ (Doc ID 2898381.1).

For more information about preparing a maintenance plan for your release, see the following My Oracle Support notes:

- Primary Note for Database Proactive Patch Program (Doc ID 888.1)
- Oracle Database 19c Important Recommended One-off Patches (Doc ID 555.1)
- Release Schedule of Current Database Releases (Doc ID 742060.1)

**Related Topics**

- [Introducing Monthly Recommended Patches (MRPs) and FAQ (Doc ID 2898740.1)](https://support.oracle.com/rs?type=doc&id=2898740.1)
- [Sunsetting of 19c RURs and FAQ (Doc ID 2898381.1)](https://support.oracle.com/rs?type=doc&id=2898381.1)
- [Primary Note for Database Proactive Patch Program (Doc ID 888.1)](https://support.oracle.com/rs?type=doc&id=888.1)
- [Oracle Database 19c Important Recommended One-off Patches (Doc ID 555.1)](https://support.oracle.com/rs?type=doc&amp;id=555.1)
- [Release Schedule of Current Database Releases (Doc ID 742060.1)](https://support.oracle.com/rs?type=doc&id=742060.1)

**Parent topic:** Patch Delivery Methods for Oracle Database

## Proactive Maintenance with RUs and MRPs

Proactive maintenance is accomplished by proactively applying a routine quarterly patch bundle (Release Update) that is available from the My Oracle Support (MOS) Customer Portal for each Oracle Database software release.

Release Updates (RUs) are release quarterly: Third Tuesday of January, April, July and October. Each RU will be given a maximum of six Monthly Recommended Patches (MRPs), released monthly.

Patch updates are announced in the following locations

- Primary Note for Database Proactive Patch Program (Doc ID 888.1)
- Monthly Recommended Patches (MRPs)
- Critical Patch Updates, Security Alerts and Bulletins

Quarterly patch updates are announced on the Critical Patch Updates, Security Alerts and Bulletins page each page each January, April, July, and October. Monthly Recommended Patches are released each month in between a quarterly Release Update, and are cumulative bundles of recommended patches. To receive email notifications when quarterly patch bundles are available, subscribe to Oracle Security alerts.

- Release Updates (RUs)
  RUs are highly tested bundles of critical fixes which enable you to avoid known issues. They usually contain the following type of fixes: security, regression (bug), optimizer, and functional (which may include feature extensions as well).
- Monthly Recommended Patches (MRP)
  Starting with update 19.17, Oracle is providing MRPs for Linux x86-64 to provide proactive patching between Release Updates.
- RUs and MRPs Content Differences
  There are content differences between release updates (RUs) and monthly recommended patches (MRPs).
- Additional Proactive Patches
  In addition to RUs and MRPs, there are quarterly full stack download patches and combo patches, as well as other proactive patches.
- Proactive Patching Strategy
  Oracle recommends that you keep your database and Oracle Grid Infrastructure software current by applying Release Updates (RUs).

**Related Topics**

- [Primary Note for Database Proactive Patch Program (Doc ID 888.1)](https://support.oracle.com/rs?type=doc&id=888.1)
- [Subscribe to Oracle Security Alerts](https://www.oracle.com/security-alerts/securityemail.html)

**Parent topic:** Patch Delivery Methods for Oracle Database

### Release Updates (RUs)

RUs are highly tested bundles of critical fixes which enable you to avoid known issues. They usually contain the following type of fixes: security, regression (bug), optimizer, and functional (which may include feature extensions as well).

Oracle recommends that you stay current by using RUs. By doing this, you minimize the chance of encountering known bugs and security vulnerabilities.

The nomenclature for the RU patches is a five-field number, such as 19.7.0.0.0.

- The first of the five fields indicates the year that this annual set of new features (also known as, this release) was first available.
- The second field shows the RU level that has been applied against that annual new features release. 19.7.0.0 would designate the seventh quarterly RU for Oracle Database 19c. Please note that several of the initial RUs are internal to Oracle and the first publicly available RU is often the forth quarterly RU, as in 19.4.0.0. That first publicly available RU is provided the next quarter after the release is publicly available.
- The third field refers to the RUR (Discontinued January 2023).
- The fourth field is reserved for future use and is currently always set to 0.
- Although only the first three fields are commonly used, the fifth field may show a numerical value that redundantly clarifies the release date of the RU, such as 19.7.0.0.200414.

**Parent topic:** Proactive Maintenance with RUs and MRPs

### Monthly Recommended Patches (MRP)

Starting with update 19.17, Oracle is providing MRPs for Linux x86-64 to provide proactive patching between Release Updates.

In October 2022, starting with RU 19.17, Oracle is modifying its proactive patch program between Release Updates to use Monthly Recommended Patches. Release Update Revisions (RURs) are deprecated, and planned to be discontinued after January 2023. MRPs provide many of the same features of the RUR patches. However, they are offered only for Oracle Database 19c on Linux x86-64 platforms.

MRPs will be delivered for each RU in the 6 months following each RU's release, starting with Oracle Database 19c RU19.17 (mid-October, 2022). MRPs will include the fixes documented in "Oracle Database Important Recommended Patches" (My Oracle Support Doc ID 555.1), plus the prior MRPs for the RU. While RUs will continue to be available on all supported platforms, MRPs will only be offered on Linux x86-64 platforms. Customers can continue to request one-off patches on all supported platforms. If a particular month does not have new recommended fixes for an RU, then no MRP will be released, and an annotation will be added in the relevant My Oracle Support notes to avoid confusion. Merge patches will be provided if there are conflicts between one-off patches and the latest MRP for an RU.

MRPs are a collection of one-off patches bundled together. Unlike an RU, an MRP does not affect the release revision number. The release number continues to be designated by the RU number. The MOS Conflict Checker will treat the MRP fixes as it does with other bundled patches, and regular conflict resolution will take place. The patches in an MRP are tracked in the Oracle Inventory directory (`oraInventory`), which is updated to indicate which one-off are installed from the MRP.

MRPs are provided as separate patches for the database (RDBMS), Oracle Clusterware (OCW), Advanced Cluster File System (ACFS) and Rapid Home Provisioning (RHP). Each MRP is packaged as a bundle of One-off patches that you can apply by using the command `opatch napply`. You can apply or rollback by using the `opatchauto` tool.

Each MRP includes the latest critical and regression fixes, but also contains the critical content that was released six months prior. By choosing to wait on taking new RU content by six months, you can take a more conservative approach to Oracle Database software maintenance, but you still risk the chance of hitting known issues that are fixed in the most recent RU. The main benefit of this patching strategy is that, if there are any regressions reported on the base RU or succeeding MRP, then they will be fixed in later MRPs.

MRPs are characterized as follows:

- MRPs are cumulative: each new MRP will contain the patches in any earlier MRPs released for a given release update, as well as the current set of one-off patches that Oracle recommends for the RU plus the current set of recommended one-off patches for the RU documented in Oracle Database 19c Important Recommended One-off Patches (Doc ID 555.1)
- MRPs do not change the release number
- MRPs are deployed using Opatchauto
- MRPs are available only on the Linux x86-64 platform

**Related Topics**

- [Oracle Database 19c Important Recommended One-off Patches (Doc ID 555.1)](https://support.oracle.com/rs?type=doc&amp;id=555.1)

**Parent topic:** Proactive Maintenance with RUs and MRPs

### RUs and MRPs Content Differences

There are content differences between release updates (RUs) and monthly recommended patches (MRPs).

The following table describes the differences:

| Criteria                                | Release Update (RU)     | MRPs                                       |
|:----------------------------------------|:------------------------|:-------------------------------------------|
| Cadence                                 | Quarterly               | Monthly for Release 19c on Linux x86-64    |
| Zero downtime (ZDT)                     | RAC Rolling             | RAC Rolling                                |
| Security fixes                          | Included                | May include CPU Alerts and high CVSS fixes |
| Regression fixes                        | Included                | Included                                   |
| Proactive functional fixes              | Included                | Not included                               |
| Optimizer plan changes (off by default) | Included                | Not included                               |
| Functional enhancements (minor)         | Included                | Not included                               |
| Emergency one-offs                      | Included                | Included                                   |
| Supported operating systems             | All supported platforms | Release 19c on Linux x86-64                |

Monthly Recommended Patches (MRPs) are offered for Oracle Database 19c on Linux x86-64. Both RUs and MRPs are cumulative bundle patches. Each of them include all the fixes of the previous patches. You can install directly whatever bundle patch as long as its year digits are the same as the digits of your current installation and the bundle was released at the same time or after your current installed version.

For Oracle Database on Linux x86-64 platforms, RUs and MRPs are designed to coexist and allow future RUs and MRPs to be installed.

Moving from one MRP to the next (for example 221115 to 221220) results in taking up all the functional fixes in the underlying RU (in this case 19.17), but with an additional month of more recent patch updates.

**Parent topic:** Proactive Maintenance with RUs and MRPs

### Additional Proactive Patches

In addition to RUs and MRPs, there are quarterly full stack download patches and combo patches, as well as other proactive patches.

Quarterly Full Stack Download Patch and Combo Patch

Oracle delivers a number of different patches packaged together. For example:

- Quarterly Full Stack Download Patch for Exadata, which includes the quarterly Grid Infrastructure RU along with the OJVM update and other Exadata system patches in a single download.
- Combo Patch of OJVM RU and Database RU

Other Proactive Patches

Oracle produces some proactive patches for very specific purposes outside of the normal update and revision cycle. Such patches are usually delivered as "Interim Patches". For example, special time zone patches are released every six months for customers who require systems to use latest time zone data.

**Note:**

If you are using Oracle Grid Infrastructure software in addition to Oracle Database software, then you should use the parallel Oracle Grid Infrastructure RU. These Oracle Grid Infrastructure RUs include everything that the parallel database RU contains.

**Parent topic:** Proactive Maintenance with RUs and MRPs

### Proactive Patching Strategy

Oracle recommends that you keep your database and Oracle Grid Infrastructure software current by applying Release Updates (RUs).

RUs include the most recent security, regression, and critical fixes. Applying RUs minimizes the chance of encountering known bugs and security vulnerabilities. Staying current with RUs reduces the likelihood of requiring separate interim one-off patches, which lead to unique software baselines and a potential for ongoing costly patch maintenance.

Example 1-1 Apply the next RU each quarter

The following table shows an example of how you can apply a release update each quarter. Starting in October, you install RU 19.17.0. In January, you install RU 19.18.0. In April, you install RU 19.19.0. In July, you install RU 19.20.0. In October, you install RU 19.21.0.

| Patch Type | October | January | April   | July    | October |
|:-----------|:--------|:--------|:--------|:--------|:--------|
| RU         | 19.17.0 | 19.18.0 | 19.19.0 | 19.20.0 | 19.21.0 |

Example 1-2 Apply the Monthly Recommended Patches (MRP) for an RU each month on Linux x86-64

Another proactive patching strategy for Linux-x86-64 platforms is to regularly apply the latest Monthly Recommended Patch (MRP) for a specific Release Update that is already installed. MRPs are created for six (6) months for each RU release, and made external on the third Tuesday of the month. MRPs are provided only for the 19c release from the 19.17 RU onward on Linux x86-64 platforms.

MRPs are installed using the `Opatchauto` utility. The MRP tracking patch Abstract or Subject indicates to which database RU the MRP applies, and the release date for the MRP in the form of RU-number.MRP-number, where `RU-number` is the numeric value of the RU, and MRP-number is the numeric value of the MRP. The MRP number designates the date on which the MRP is released.

For example:

    Patch 34522319 - DATABASE MRP 19.17.0.0.221115

This MRP patch indicates that patch 34522319 is an Oracle Database MRP that can be applied on top of RU 19.17, and the MRP release date is 2022 (year) 11 (month), and 15 (day), corresponding to 15 November 2022.

The following tables show an example of how you can apply RU 19.17.0, released October 18, 2022, and then proceed to update that RU with MRPs for six months, starting in November 2022 and continuing until April 2023, when the last MRP for 19.17.0 is released. In May 2023, you then update to RU 19.18.0, released in January 2023, and update RU 19.18.0 with the April 2023 or May 2023 MRP for RU 19.18.0. In the tables, n/a designates a month where an MRP does not apply, because the RU that it updates is not released.

Table 1-1 Patch Schedule for RU 19.17.0

| MRP                | October 2022 | November 2022 | December 2022 | January 2022 | February 2022 | March 2022 | April 2022 |
|:-------------------|:-------------|:--------------|:--------------|:-------------|:--------------|:-----------|:-----------|
| MRP for 19.17.0 RU | n/a          | 221115        | 221220        | 230117       | 230221        | 230321     | 23418      |

Table 1-2 Patch Schedule for RU 19.18.0

| MRP                | January 2023 | February 2023 | March 2023 | April 2023 | May 2023 | June 2023 | July 2023 |
|:-------------------|:-------------|:--------------|:-----------|:-----------|:---------|:----------|:----------|
| MRP for 19.18.0 RU | n/a          | 230221        | 230321     | 230418     | 230516   | 230620    | 230718    |

**Parent topic:** Proactive Maintenance with RUs and MRPs

## Reactive Maintenance with One-off Patches

All methods allow one-off patches to be installed, but the version of a one-off patch that is required may vary depending on the patching method.

Windows platforms do not support normal “one-off patches”. See [My Oracle Support Note 2337415.1](https://support.oracle.com/knowledge/Oracle%20Database%20Products/2337415_1.html) for details of current and historic proactive patches.

The one-off patches are delivered as standalone on request for a given “defect, version, platform” combination (also known as “Interim Patches”).

- One-off patches are provided on top of any release or updates for supported version as long as technically feasible.
- One-off patches go through basic sanity tests.
- One-off patches are considered for inclusion in an update based on technical severity or blast radius.

Oracle recommends you to apply the update including the fix. For an additional discussion of the pros and cons of asking for one-off bug fixes instead of waiting on RUs, see [My Oracle Support Note 2648544.1.](https://support.oracle.com/knowledge/Oracle%20Cloud/2648544_1.html)

**Parent topic:** Patch Delivery Methods for Oracle Database

## Which Patching Method to Use?

For Linux x86-64 platforms, MRPs provide a method to apply all Oracle recommended fixes easily for the current RU.

Each MRP provides update content, month by month after the RU associated with that monthly update is released, up to six months after the release date of the RU. By waiting to install a new update content by three or six months, you take a more conservative approach to Oracle Database software maintenance, but you still risk the chance of hitting known issues fixed in the most recent updates.

Additionally, you should install the following:

- The OJVM patches where Oracle Database uses the JVM
- Interim patches only for specific issues that you know apply to your environment
- A minimum of interim patches

Installing the latest update is a good way to reduce the need for interim patches.

**Parent topic:** Patch Delivery Methods for Oracle Database

## Patch Conflict Resolution

If interim patches are used in conjunction with one of the proactive patching methods, then there may be patch conflicts.

For the quarterly proactive patches (Quarterly Exadata Patch, RU, and MRPs), Oracle proactively produces new interim patches for existing patches that would conflict. The new interim patches are usually released at the same time as the proactive patches.

For information about resolving patch conflicts, see the My Oracle Support notes for patch conflicts.

**Related Topics**

- [My Oracle Support Patch Conflict Checker Overview](https://support.oracle.com/rs?type=doc&amp;id=1941934.1)
- [How to Use the My Oracle Support Conflict Checker Tool for Patches Installed with OPatch](https://support.oracle.com/rs?type=doc&amp;id=1091294.1)
- [Database Patch Conflict Resolution (Doc ID 1321267.1)](https://support.oracle.com/rs?type=doc&amp;id=1321267.1)

**Parent topic:** Patch Delivery Methods for Oracle Database

## Frequently Asked Questions

This section lists frequently asked questions.

Do proactive patches include optimizer fixes?

- "Windows Database Bundle Patch" can include optimizer fixes.
- Oracle Database RUs can include optimizer fixes for issues that arise from inaccurate optimizer results, but only in a form that enables or disables them individually, as required. RUs include optimizer fixes in the "disabled by default" state. For more information, see [My Oracle Support Note 2147007.1](https://support.oracle.com/knowledge/Oracle%20Database%20Products/2147007_1.html), "Automatic Fix Control Persistence (FCP) for Database Proactive Bundle Patch ".

How can I tell what patching method an installation uses?

Review the `opatch lsinventory` output to see what patches are applied. RUs and RURs include a description of the patch name and version in the output.

What is the difference between "Windows Database Bundle Patch" and "QFSDP for Exadata" and so on?

These bundles are targeted at different environments. The latest versions include the same update content, but all other content is specific to the target environment. There may be some other common content but there are differences in content.

Do proactive patches affect the database version as reported in trace files and database views like `V$VERSION`?

For Oracle Database 19c (19.3.0.0), the patch level in the `ORACLE_HOME` is reflected in the `opatch lsinventory` data, and for some patch types, the patch level is reflected in `DBA_REGISTRY` or `DBA_REGISTRY_HISTORY`. The `DBA_REGISTRY_SQLPATCH` view tells you the SQL patches that are applied to the database.

Should I ask for a one-off bug fix or wait for the next RU?

For a discussion of the pros and cons of asking for one-off bug fixes instead of waiting on RUs, see [My Oracle Support Note 2648544.1](https://support.oracle.com/knowledge/Oracle%20Cloud/2648544_1.html).

How to apply patches? Use either the `opatch` utility or the `OPLAN` utility?

Refer to the README to learn how to install patches.

OPatch - Where Can I Find the Latest Version of OPatch?

See [My Oracle Support Note 6880880.1](https://support.oracle.com/epmos/faces/DocumentDisplay?id=274526.1&displayIndex=1) or [My Oracle Support Note 224346.1](https://support.oracle.com/knowledge/Oracle%20Database%20Products/224346_1.html)

**Parent topic:** Patch Delivery Methods for Oracle Database

## Current Database Proactive Patches

The following table gives information on available proactive database related patches by platform, environment, and version.

The short names that are used in the Methods column in the table are expanded in [My Oracle Support Note 2337415.1](https://support.oracle.com/knowledge/Oracle%20Database%20Products/2337415_1.html).

| Platform          | Environment | DB Version                  | Methods                                 |
|:------------------|:------------|:----------------------------|:----------------------------------------|
| Unix platforms    | Exadata     | 19.3.0.0 and later releases | QFSDP for Exadata, OJVM Update, TZ      |
| Linux Platforms   | Exadata     | 19.3.0.0 and later releases | QFSDP for Exadata, OJVM Update, TZ, MRP |
| Unix platforms    | RAC         | 19.3.0.0 and later releases | GI Update, OJVM Update, Combo, TZ       |
| Linux platforms   | RAC         | 19.3.0.0 and later releases | GI Update, OJVM Update, Combo, TZ, MRP  |
| Unix platforms    | Non-RAC     | 19.3.0.0 and later releases | DB Update, OJVM Update, Combo, TZ       |
| Linux platforms   | Non-RAC     | 19.3.0.0 and later releases | DB Update, OJVM Update, Combo, TZ, MRP  |
| Windows platforms | All         | 19.3.0.0                    | Windows Bundles, TZ                     |

**Parent topic:** Patch Delivery Methods for Oracle Database

## Documentation Accessibility

For information about Oracle's commitment to accessibility, visit the Oracle Accessibility Program website at <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=docacc>.

### Access to Oracle Support

Oracle customers that have purchased support have access to electronic support through My Oracle Support. For information, visit <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=info> or visit <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=trs> if you are hearing impaired.

**Parent topic:** Patch Delivery Methods for Oracle Database

------------------------------------------------------------------------

Title and Copyright Information

Oracle Database Oracle Database Patch Maintenance, Release 19c and Later Releases

F31334-03

October 2022

[Copyright © ](./sp_common/en/cpyr.md)2020, 2022, Oracle and/or its affiliates.
