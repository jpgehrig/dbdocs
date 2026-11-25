Microsoft releases operating system patches, called Service Packs, on a quarterly basis. Service Packs are a collection of bug fixes and product enhancements to the basic Windows Server release.

In general, apply Service Packs as soon as it is safe to do so, because they fix bugs and can improve Windows Server performance or functionality.

While Service Packs are supposed to fix bugs, they sometimes introduce new problems as well. In general, it is safest to wait a few weeks after a Service Pack is released before implementing it. This allows time for other field sites to report any problems with the Service Pack release.

The latest Windows Server Service Packs can be downloaded as self-extracting archives from [`http://support.microsoft.com`](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/ntqrf&id=winserver_service_pack)

Unless you can be certain that the Service Pack works without flaws on Windows Server, create an `Uninstall` directory. This enables the Service Pack to be removed and the original configuration to be restored.

Service Pack files overwrite similarly-named files in the previous Windows Server configuration. However, Service Pack files can be overwritten in turn by setup programs that copy files from the original installation media.

For example, installing a new network protocol or a printer driver usually requires copying files from the original Windows Server installation media. When Service Pack files are comprehensively or selectively overwritten, the Service Pack must be reapplied.

**Parent topic:** [Tuning Windows to Optimize Oracle Database](tuning-windows-to-optimize-oracle-database.md)
