.

### Step 1: Install cURL

The examples used in this document use the cURL command-line tool to demonstrate how to access the Oracle Database REST API. To connect securely to the REST server, you must install a version of cURL that supports SSL

To install cURL on your system:

1.  In your browser, navigate to the cURL home page at <http://curl.haxx.se> and click Download in the navigation menu.

2.  On the cURL Releases and Downloads page, locate the SSL-enabled version of the cURL software that corresponds to your operating system. Click the link to download the ZIP file, and extract the executable to the desired folder.

When running cURL from a Windows command shell only, you must provide an SSL certificate authority (CA) file or bundle to authenticate against the Verisign CS certificate.

1.  Navigate to the cURL CA Extract page at <http://curl.haxx.se/docs/caextract.html> and download the cacert.pem SSL CA certificate file in the folder where you installed cURL.

2.  Open a command window, navigate to the directory where you installed cURL, and set the cURL environment variable, `CURL_CA_BUNDLE`, to the location of the SSL CA certificate file. For example, on a Windows system you would enter:

    `C:\curl> set CURL_CA_BUNDLE=cacert.pem`

You are now ready to send REST requests to the Database REST API instance using cURL. See [Authentication](Authentication.md), and [Use cURL](Use-cURL.md).
