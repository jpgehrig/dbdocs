The following is an example of configuring BMC using `ipmitool` (version 1.8.6).

1.  Log in as `root`.

2.  Verify that `ipmitool` can communicate with the BMC using the IPMI driver by using the command `bmc info`, and looking for a device ID in the output. For example:

        # ipmitool bmc info
        Device ID                 : 32
        .
        .
        .

    If `ipmitool` is not communicating with the BMC, then review the section Configuring the BMC and ensure that the IPMI driver is running.

3.  Enable IPMI over LAN using the following procedure

    1.  Determine the channel number for the channel used for IPMI over LAN. Beginning with channel 1, run the following command until you find the channel that displays LAN attributes (for example, the IP address):

            # ipmitool lan print 1

            . . .
            IP Address Source       : 0x01
            IP Address              : 140.87.155.89
            . . .

    2.  Turn on LAN access for the channel found. For example, where the channel is 1:

            # ipmitool -I bmc lan set 1 access on

4.  Configure IP address settings for IPMI using the static IP addressing procedure:

    - Using static IP Addressing

      If the BMC shares a network connection with ILOM, then the IP address must be on the same subnet. You must set not only the IP address, but also the proper values for netmask, and the default gateway. For example, assuming the channel is 1:

          # ipmitool -I bmc lan set 1 ipaddr 192.168.0.55
          # ipmitool -I bmc lan set 1 netmask 255.255.255.0
          # ipmitool -I bmc lan set 1 defgw ipaddr 192.168.0.1

      Note that the specified address (`192.168.0.55`) is associated only with the BMC, and does not respond to normal pings.

5.  Establish an administration account with a username and password, using the following procedure (assuming the channel is 1):

    1.  Set BMC to require password authentication for ADMIN access over LAN. For example:

            # ipmitool -I bmc lan set 1 auth ADMIN MD5,PASSWORD

    2.  List the account slots on the BMC, and identify an unused slot less than the maximum ID and not listed, for example, ID 4 in the following example. Note that some slots may be reserved and not available for reuse on some hardware.

            # ipmitool user summary 1
            Maximum IDs         : 20
            Enabled User Count  : 3
            Fixed Name Count    : 2
            # ipmitool user list 1
            ID  Name     Enabled Callin  Link Auth  IPMI Msg   Channel Priv Lim
            1            true    false   false      true       USER
            2   root     true    false   false      true       ADMINISTRATOR
            3   sysoper  true    true    false      true       OPERATOR
            12  default  true    true    false      true       NO ACCESS
            13           true    false   true       false      CALLBACK


        In the example above, there are 20 possible slots, and the first unused slot is number 4.

    3.  Assign the desired administrator user name and password and enable messaging for the identified slot. (Note that for IPMI v1.5 the user name and password can be at most 16 characters). Also, set the privilege level for that slot when accessed over LAN (channel 1) to ADMIN (level 4). For example, where `username` is the administrative user name, and `password` is the password:

            # ipmitool user set name 4 username
            # ipmitool user set password 4 password
            # ipmitool user enable 4
            # ipmitool channel setaccess 1 4 privilege=4
            # ipmitool channel setaccess 1 4 link=on
            # ipmitool channel setaccess 1 4 ipmi=on

    4.  Verify the setup using the command `lan print 1`. The output should appear similar to the following. Note that the items in bold text are the settings made in the preceding configuration steps, and comments or alternative options are indicated within brackets \[\]:

            # ipmitool lan print 1
            Set in Progress         : Set Complete
            Auth Type Support       : NONE MD2 MD5 PASSWORD
            Auth Type Enable        : Callback : MD2 MD5
                                    : User     : MD2 MD5
                                    : Operator : MD2 MD5
                                    : Admin    : MD5 PASSWORD
                                    : OEM      : MD2 MD5
            IP Address Source       : DHCP Address [or Static Address]
            IP Address              : 192.168.0.55
            Subnet Mask             : 255.255.255.0
            MAC Address             : 00:14:22:23:fa:f9
            SNMP Community String   : public
            IP Header               : TTL=0x40 Flags=0x40 Precedence=…
            Default Gateway IP      : 192.168.0.1
            Default Gateway MAC     : 00:00:00:00:00:00
            .
            .
            .
            # ipmitool channel getaccess 1 4
            Maximum User IDs     : 10
            Enabled User IDs     : 2

            User ID              : 4
            User Name            : username [This is the administration user]
            Fixed Name           : No
            Access Available     : call-in / callback
            Link Authentication  : enabled
            IPMI Messaging       : enabled
            Privilege Level      : ADMINISTRATOR

6.  Verify that the BMC is accessible and controllable from a remote node in your cluster using the bmc info command. For example, if `node2-ipmi` is the network host name assigned the IP address of `node2`'s BMC, then to verify the BMC on node `node2` from `node1`, with the administrator account `username`, enter the following command on `node1`:

        $ ipmitool -H node2-ipmi -U username lan print 1

    You are prompted for a password. Provide the IPMI password.

    If the BMC is correctly configured, then you should see information about the BMC on the remote node. If you see an error message, such as `Error: Unable to establish LAN session`, then you must check the BMC configuration on the remote node.

7.  Repeat this process for each cluster member node. If the IPMI administrator account credentials on each cluster member node are not identical, then IPMI will fail during configuration.

**Parent topic:** [Enabling Intelligent Platform Management Interface (IPMI)](enabling-ipmi.md)
