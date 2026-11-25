## Client Machine Configuration

The client machine used for remote based graphic user interface (GUI) installation of Oracle Real Application Clusters (Oracle RAC) into Podman containers used this configuration.

- Client: `user-client-1`
- CPU cores: 1 socket with 1 core, with 2 threads for each core. Intel<sup>®</sup> Xeon<sup>®</sup> Platinum 8167 M CPU at 2.00 GHz
- Memory
  - RAM: 8 GB
  - Swap memory: 8 GB
- Network card and IP: `ens3`, `10.0.20.57/24`
- Linux operating system: Oracle Linux Server release 7.7, kernel `4.14.35-1902.300.11.el7uek.x86_64`
- Packages:
  - X Window System
  - Gnome

**Parent topic:** [Example of Installing Oracle Grid Infrastructure and Oracle RAC on Podman](example-installing-oracle-grid-infrastructure-and-oracle-rac-podman.md)
