## Gold Image Distribution Among Oracle Fleet Patching and Provisioning Servers

Oracle Fleet Patching and Provisioning can automatically share and synchronize gold images between Oracle Fleet Patching and Provisioning Servers.

In the Oracle Fleet Patching and Provisioning architecture, one Oracle Fleet Patching and Provisioning Server manages a set of Oracle Fleet Patching and Provisioning Clients and `rhpclient`-less targets within a given data center or network segment of a data center. If you have more than one data center or a segmented data center, you must have more than one Oracle Fleet Patching and Provisioning Server.

In the Oracle Fleet Patching and Provisioning architecture, one Oracle Fleet Patching and Provisioning Server manages a set of Oracle Fleet Patching and Provisioning Clients and `rhpclient`-less targets within a given data center or network segment of a data center. If you have more than one data center or a segmented data center, then you must have more than one Oracle Fleet Patching and Provisioning Server to facilitate large-scale standardization across multiple estates.

Oracle Fleet Patching and Provisioning Servers retain the ability to create and manage gold images private to their scope, so local customizations are seamlessly supported.

You must first establish a peer relationship between two Oracle Fleet Patching and Provisioning Servers. Registration uses the names of the Oracle Fleet Patching and Provisioning Server clusters. The names of the two clusters can be the same but there is one naming restriction: an Oracle Fleet Patching and Provisioning Server, such as `FPPS_1`, cannot register a peer Oracle Fleet Patching and Provisioning Server if that peer has the same name as an Oracle Fleet Patching and Provisioning Client or `rhpclient`-less target within the management domain of `FPPS_1`.

The following steps show how you can establish a peer relationship between two Oracle Fleet Patching and Provisioning Servers. Note that super user or root credentials are not required in this process.

1.  On the first Oracle Fleet Patching and Provisioning Server (`FPPS_1`), create a file containing the server configuration information.
        $ rhpctl export server -serverdata file_path
2.  Copy the server configuration file created on `FPPS_1` to a second Oracle Fleet Patching and Provisioning Server (`FPPS_2`).
3.  On the second Oracle Fleet Patching and Provisioning Server (`FPPS_2`), complete the registration of `FPPS_2`.
        $ rhpctl register server -server FPPS_1_cluster_name
            -serverdata server_cfg_file_copied_from_FPPS_1
4.  On `FPPS_2`, create a file containing the server configuration information.
        $ rhpctl export server -serverdata file_path
5.  Copy the server configuration file created on `FPPS_2` to `FPPS_1`.
6.  On the first Oracle Fleet Patching and Provisioning Server (`FPPS_1`), complete the registration of`FPPS_1`.
        $ rhpctl register server -server FPPS_2_cluster_name
            -serverdata server_cfg_file_copied_from_FPPS_2

After you register an Oracle Fleet Patching and Provisioning Server as a peer, the following command displays the peer (or peers) of the server:

    $ rhpctl query peerserver

You can inspect the images on a peer Oracle Fleet Patching and Provisioning Server, as follows:

    $ rhpctl query image -server server_cluster_name

The preceding command displays all images on a specific peer Oracle Fleet Patching and Provisioning Server. Additionally, you can specify a peer server along with the `-image ``image_name` parameter to display details of a specific image on a specific peer server.

An Oracle Fleet Patching and Provisioning Server can have multiple peers. Oracle does not support chained relationships between peers, however, such as, if `FPPS_1` is a peer of `FPPS_2`, and `FPPS_2` is also a peer of `FPPS_3`, then no relationship is established or implied between `FPPS_1` and `FPPS_3`, although you can make them peers if you want.

Retrieve a copy or copies of gold images from a peer Oracle Fleet Patching and Provisioning Server, as follows:

    $ rhpctl instantiate image -server server_cluster_name

Running the `rhpctl instantiate image` command activates an auto-update mechanism. From that point on, when you create gold images on a peer Oracle Fleet Patching and Provisioning Server, such as `FPPS_2`, they are candidates for being automatically copied to the Oracle Fleet Patching and Provisioning Server that performed the instantiate operation, such as `FPPS_1`. Whether a new gold image is automatically copied depends on that relevance of the image to any instantiate parameters that you may include in the command:

- `-all`: Creates an automatic push for all gold images created on `FPPS_2` to `FPPS_1`

- `-image ``image_name`: Creates an automatic push for all new descendant gold images of the named image created on `FPPS_2` to `FPPS_1`. A descendant of the named image is an image that is created on `FPPS_2` using the `rhpctl add image` command.

- `-series ``series_name`: Creates an automatic push for all gold images added to the named series on `FPPS_2` to `FPPS_1`

- `-imagetype ``image_type`: Creates an automatic push for all gold images created of the named image type on `FPPS_2` to `FPPS_1`

To stop receiving updates that were established by the `rhpctl instantiate image` command, run `rhpctl uninstantiate image` and specify the peer Oracle Fleet Patching and Provisioning Server and one of the following: all, image name, image series name, or image type.

End the peer relationship, as follows, on any one of the Oracle Fleet Patching and Provisioning Servers:

    $ rhpctl unregister server -server server_cluster_name

**Related Topics**

- [rhpctl export server](server-commands.md)
- [rhpctl register server](server-commands.md)
- [rhpctl query peerserver](peerserver-commands.md)
- [rhpctl query image](image-commands.md)
- [rhpctl instantiate image](image-commands.md)
- [rhpctl uninstantiate image](image-commands.md)
- [rhpctl unregister server](server-commands.md)

**Parent topic:** [Advanced Oracle Fleet Patching and Provisioning Configurations](advanced-oracle-fpp-configurations.md)
