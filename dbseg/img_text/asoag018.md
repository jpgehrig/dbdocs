# Description of the illustration asoag018.gif

This is a text description of asoag018.gif, an image which shows the steps to authenticate clients when SSL is used with other authentication methods as follows:

1.  A client seeks to connect to an Oracle server.

2.  SSL performs a handshake during which the server authenticates itself to the client and both the client and server establish which cipher suite to use.

3.  Once the SSL handshake is successfully completed, the user seeks access to the database.

4.  The Oracle server authenticates the user with the authentication server using a non-SSL authentication method such as Kerberos or RADIUS.

5.  Upon validation by the authentication server, the Oracle server grants access and authorization to the user. Then the user can access the database securely by using SSL.
