# Description of the illustration asoag012.gif

This is a text description of asoag012.gif, an image which depicts how a network authentication service authenticates a user as follows:

1.  First, the user (client) requests authentication services from an authentication server. The user proves his or her identity by providing a token or password.

2.  After authenticating the user, the authentication server passes a ticket or credentials back to the client.

3.  The client can now take these credentials and pass them to the Oracle server while asking for a service, such as connection to a database.

4.  The Oracle server sends the credentials to the authentication server to verify their validity.

5.  The authentication server either accepts or rejects the credentials and sends a notification to the Oracle server.

6.  If the authentication server accepts the credentials, then the Oracle server performs the requested task for the user. If the credentials are not accepted, the requested service is denied.
