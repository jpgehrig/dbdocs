# Description of the illustration asoag011.gif

This is a text description of asoag011.gif, an image which depicts a challenge-response, or asynchronous authentication sequence as follows:

1.  A user seeks a connection to the Oracle database server, and the client machine passes the data to the Oracle database server.

2.  The Oracle database server, acting as the RADIUS client, passes the data from the Oracle client to the RADIUS server.

3.  The RADIUS server passes the data to the appropriate authentication server for validation.

4.  The authentication server sends a challenge to the RADIUS server.

5.  The RADIUS server sends the challenge to the Oracle database server/RADIUS client (the three preceeding steps are combined if the RADIUS server is the authentication server).

6.  The Oracle database server/RADIUS client sends the challenge to the Oracle client where a graphical interface presents it to the user.

7.  The user provides a response to the challenge by various means which the Oracle client passes to the Oracle database server/RADIUS client.

8.  The Oracle database server/RADIUS client sends the user's response to the RADIUS server.

9.  The RADIUS server passes it to the appropriate authentication server for validation.

10. The authentication server sends back to the RADIUS server either an access accept or an access reject message.

11. The RADIUS server passes the response to the Oracle database server/RADIUS client. (The three preceeding steps are combined if the RADIUS server is the authentication server.)

12. The Oracle database server/RADIUS client passes it on to the Oracle client.
