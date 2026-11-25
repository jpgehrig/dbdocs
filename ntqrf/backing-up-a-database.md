The technique for backing up a database depends on the archiving mode of the database and whether you are making a component-based or a volume-based backup.

Oracle recommends shadow copies taken in a component mode for backing up the Oracle Database using VSS writer. The Oracle VSS writer defines the components that include the set of database files. The Oracle VSS writer then saves the redo generated during hot backup mode when the snapshot was created in the backup writer metadata document.

The component hierarchy defined by the Oracle VSS writer is illustrated in Oracle VSS Writer Component Hierarchy.

Figure 5-1 Oracle VSS Writer Component Hierarchy

![Description of Figure 5-1 follows](img/comp.gif)
[Description of "Figure 5-1 Oracle VSS Writer Component Hierarchy"](img_text/comp.md)

**Related Topics**

- [About Component-Based Backups](about-component-based-backups.md)

**Parent topic:** [Configuring the Windows Firewall](configuring-the-windows-firewall-postinstallation.md)
