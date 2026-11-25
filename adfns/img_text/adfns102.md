# Description of the illustration adfns102.eps

The process includes these steps:

1.  A user visits a web page, follows a hypertext link, or submits data in a form, which causes the browser to send a HTTP request for a URL to an HTTP server.

2.  The HTTP server calls a stored subprogram on an Oracle Database according to the data encoded in the URL. The data in the URL takes the form of parameters to be passed to the stored subprogram.

3.  The stored subprogram invokes subprograms in the PL/SQL Web Toolkit. Typically, subprograms such as `HTP`.`Print` generate web pages dynamically. A generated web page varies depending on the database contents and the input parameters.

4.  The subprograms pass the dynamically generated page to the web server.

5.  The web server delivers the page to the client.
