# Description of the illustration habpt005.eps

The illustration shows network routes before site failover. From top to bottom, it shows the client, the Internet, the client tier of the primary and secondary sites, the application server tier of the primary and secondary sites, and the database server tier of the primary and secondary sites.

The client tier of the primary site contains two routers, an active firewall and a standby firewall, and a WAN traffic manager. There is a "heartbeat" between the two firewalls. The routers are connected to each other, to both firewalls, and to the WAN traffic manager. There is a firewall between the client tier and the application server tier.

The application server tier of the primary site contains active and standby switches, active and standby hardware-based load balancers, application/web servers, IMAP servers, LDAP servers, and an active firewall and a standby firewall. The switches are connected to each other and to their load balancers. The switches are also connected to the 3 kinds of servers. The active switches are connected to the active firewall, and the standby switches are connected to the standby firewall. There is a heartbeat between the two firewalls. There is a firewall between the application server tier and the database server tier.

The database server tier of the primary site contains active and standby switches, a router, two RAC instances, and a RAC database. There is a heartbeat between the active and standby switches. There are two heartbeats between the RAC instances. Both kinds of switches are connected to both RAC instances. The instances are connected to the database.

The components of the secondary site are identical to the components of the primary site.

The route of the client request is described in the text preceding the figure.

End of image description.
