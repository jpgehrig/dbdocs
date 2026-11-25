## Setting-Up Hardware and Operating System Components for OMS

Verify if HugePages is available, configure the PMEM device, and create and mount a DAX-capable file system on the device.

- [Verifying HugePages Availability](verifying-hugepages-on-oms.md)
  Ensure that the underlying Linux kernel supports HugePages.
- [Configuring PMEM Devices](configuring-pmem-devices.md)
  On your Intel Persistent Memory (PMEM) device, use the `ipmctl` utility to configure the PMEM mode and the `ndctl` utility for namespace management.
- [Setting-Up a DAX-Capable File System](setting-up-dax-file-system-oms.md)
  Learn how to create and mount a DAX-capable file system.
- [Create an Uber File for Oracle Memory Speed](create-uber-file-oms.md)
  After mounting the DAX file system, create an uber file for the Oracle Memory Speed (OMS) file system.

**Parent topic:** [Deploying the Oracle Memory Speed File System](deploying_oms.md)
