Check to ensure that the host name for your server is resolvable.

Typically, the computer on which you want to install Oracle Database is connected to a network. Ensure that the computer host name is resolvable, either through a Domain Name System (DNS), a network information service (NIS), or a centrally-maintained TCP/IP host file, such as `/etc/hosts`. Use the `ping` command to ensure that your computer host name is resolvable. For example:

    ping myhostname
    pinging myhostname.example.com [192.0.2.2] with 32 bytes of data:
    Reply from 192.0.2.2: bytes=32 time=138ms TTL=56

**Parent topic:** [Configuring Operating Systems for Oracle Database on HP-UX Itanium](configuring-operating-systems-for-oracle-database-on-hp-ux-itanium.md)
