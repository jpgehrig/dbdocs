Database REST APIs uses a certificate authority (CA) certificate, issued by Verisign, to enable clients to connect securely to the server.

**Note:**

Ensure that you have the appropriate log-in credentials for creating, managing, and deleting Database REST API instances.

You access the Database REST API resources over HTTPS and must provide the following information for authentication:

- An SSL certificate authority (CA) certificate file or bundle to authenticate against the Verisign CA certificate.

- User name and password for your Database REST API account.

- Custom header,X-ID-TENANT-NAME, to identify the identity domain ID.

For example, to authenticate using cURL:

- Use the -u cURL option to pass the user name and password (for example, username and userPassword1!).

- Use the -H cURL option to pass the X-ID-TENANT-NAME custom header.

- When running cURL from a Windows command shell only, set the cURL environment variable, CURL_CA_BUNDLE, to the location of an SSL certificate authority (CA) certificate file or bundle to authenticate against the Verisign CA certificate. Alternatively, you can specify the location of your local CA certificate bundle on the command line, using the --cacert command line option.

You can download an SSL CA certificate bundle from  <http://curl.haxx.se/docs/caextract.html> or provide your own. For information about CA certificate verification using cURL, see:  <http://curl.haxx.se/docs/sslcerts.html>.

The following is an example syntax for cURL command:

    curl -i -X GET -u <username>:<password> -H <request-header>:<value> https://<subdomain>.<domain>.com:<port>/<resource-path>
