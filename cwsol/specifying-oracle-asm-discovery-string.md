When an Oracle ASM instance is initialized, Oracle ASM discovers and examines the contents of all of the disks that are in the paths that you designated with values in the `ASM_DISKSTRING` initialization parameter.

The value for the `ASM_DISKSTRING` initialization parameter is an operating system–dependent value that Oracle ASM uses to limit the set of paths that the discovery process uses to search for disks. The exact syntax of a discovery string depends on the platform, ASMLib libraries, and whether Oracle Exadata disks are used. The path names that an operating system accepts are always usable as discovery strings.

The default value of `ASM_DISKSTRING` might not find all disks in all situations. In addition, if your installation uses multipathing software, then the software might place pseudo-devices in a path that is different from the operating system default.

**See Also:**

- [Oracle Automatic Storage Management Administrator's Guide](../ostmg/init-params-asm-instance.md) for more information about the initialization parameter `ASM_DISKSTRING`

- See "Oracle ASM and Multipathing" in [Oracle Automatic Storage Management Administrator's Guide](../ostmg/considerations-asm-storage.md) for information about configuring Oracle ASM to work with multipathing, and consult your multipathing vendor documentation for details.

**Parent topic:** [Configuring Storage for Oracle Automatic Storage Management](configuring-storage-for-oracle-automatic-storage-management.md)
