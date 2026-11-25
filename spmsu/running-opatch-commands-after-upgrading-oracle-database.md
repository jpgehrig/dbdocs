After you upgrade Oracle Database, you must run OPatch commands from the new Oracle home.

OPatch is a Java-based utility that you install with Oracle Universal Installer. Opatch is platform-independent. It runs on all supported operating systems. Another version of OPatch, called standalone OPatch, is also available. It runs on Oracle homes without Oracle Universal Installer.

Patches are a small collection of files copied over to an existing installation. They are associated with particular versions of Oracle products. When applied to the correct version of an installed product, patches result in an upgraded version of the product.

### Run Opatch to Check the Oracle Database Inventory

Log in as the Oracle installation owner, and run the `lsinventory` command from the new Oracle home. The command generates an accurate and complete inventory of the Oracle software installed on the system:

    opatch lsinventory –patch

Refer to My Oracle Support note 756671.1 regularly to obtain current recommendations regarding Release Updates (Updates) and Release Update Revisions (Revisions).

**Related Topics**

- <https://support.oracle.com/rs?type=doc&id=756671.1>

**Parent topic:** [Required Tasks to Complete After Upgrading Oracle Database](required-tasks-to-complete-after-upgrade.md)
