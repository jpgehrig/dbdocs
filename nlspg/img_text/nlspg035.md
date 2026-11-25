# Description of the illustration

This image shows 3 clients whose locales are English, Japanese, and Hebrew. The English client uses the ISO 8859-1 character set over an HTTP connection to a monolingual application with English locale in Application Server A. The Japanese client uses the Shift-JIS character set over an HTTP connection to a monolingual application with Japanese locale in Application Server A. The Hebrew client uses the ISO 8859-8 character set over an HTTP connection to a monolingual application with Hebrew locale in Application Server B.

Application Server A contains the following:

- Monolingual application: English locale

- Application server instance 1

- Monolingual application: Japanese locale

- Application server instance 2

The English application uses the WE8MSWIN1252 Oracle character set over an Oracle Net connection to an Oracle Unicode database. The Japanese application uses the JA16SJIS Oracle character set over an Oracle Net connection to the same Oracle Unicode database.

Application Server B contains the following:

- Monolingual application: Hebrew locale

- Application server instance 3

The Hebrew application uses the IW8MSWIN1255 Oracle character set over an Oracle Net connection to the same Oracle Unicode database.
