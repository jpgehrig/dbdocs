# Description of the illustration asoag010.gif

This is a text description of asoag010.gif, an image which depicts the synchronous authentication sequence as follows:

1.  A user logs in by entering a connect string, passcode, or other value, and the client machine passes this data to the Oracle database server.

2.  The Oracle database server, acting as the RADIUS client, passes the data from the Oracle client to the RADIUS server.

3.  The RADIUS server passes the data to the appropriate authentication server for validation.

4.  The authentication server sends back to the RADIUS server either an access accept or an access reject message.

    Note: If the RADIUS server is the authentication server, the two preceeding steps are combined.

5.  The RADIUS server passes this response to the Oracle database server/RADIUS client.

6.  The Oracle database server/RADIUS client passes the response to the Oracle client.
