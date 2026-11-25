# Description of Web Coverage Service Architecture illustration

This image illustrates the Web Coverage Service (WCS) architecture, which is introduced before the illustration.

The Client portion at the top shows WCS communicating with requests and responses with the middles tier using key-value pair XML and SOAP for posts.

The Middle Tier part in the middle shows a J2EE container that contains a WCS instance. the container issues requests to the file system and to GDAL, and GDAL issues rrequests to the file system. The middle tier communicates with the database using JDBC and OCI.

The Database part at the bottom has spatial capabilities that communicate with the middle tier using JDBC and OCI.
