## Configuring DNS for Domain Delegation to Grid Naming Service

You must configure the DNS to send GNS name resolution requests using DNS forwarders.

If the DNS server is running on a Windows server that you administer, then the following steps must be performed to configure DNS:

1.  Click Start, then select Programs. Select Administrative Tools and then click DNS manager.
    The DNS server configuration wizard starts automatically.
2.  Use the wizard to create an entry for the GNS virtual IP address, where the address is a valid DNS name.
    For example, if the cluster name is `mycluster`, and the domain name is `example.com`, and the IP address is `192.0.2.1`, you could create an entry similar to the following:
        mycluster-gns-vip.example.com: 192.0.2.1

    The address you provide must be routable.

    **Note:**

    The domain name may not contain underscores. Windows may allow the use of underscore characters, but this practice violates the Internet Engineering Task Force RFC 952 standard and is not supported by Oracle.
3.  To configure DNS forwarders, click Start, select Administrative Tools, and then select DNS.
4.  Right-click ServerName, where ServerName is the name of the server, and then click the Forwarders tab.
5.  Click New, then type the name of the DNS domain for which you want to forward queries in the DNS domain box, for example, `clusterdomain.example.com`. Click OK.
6.  In the selected domain's forwarder IP address box, type the GNS VIP address, and then click Add.
7.  Click OK to exit.

**Note:**

Experienced DNS administrators may want to create a reverse lookup zone to enable resolution of reverse lookups. A reverse lookup resolves an IP address to a host name with a Pointer Resource (PTR) record. If you have reverse DNS zones configured, then you can automatically create associated reverse records when you create your original forward record.

**See Also:**

Oracle Grid Infrastructure Installation Guide for your platform or your operating system documentation for more information about configuring DNS for domain delegation to GNS if the DNS server is running on a different operating system.

**Parent topic:** [Domain Delegation to Grid Naming Service](domain-delegation-to-grid-naming-service.md)
