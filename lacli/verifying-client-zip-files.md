## Verifying Signed Oracle Instant Client Zip Files

Use the Java utility `jarsigner` to verify the integrity of your Oracle Instant Client zip files.

To verify the integrity of the Oracle Instant Client installation zip files before you extract the installation files:

1.  Go to the directory where you have downloaded the zip file.
2.  Run the `jarsigner` command with the `-verify` option to quickly check your installation zip file:
        jarsigner -verify instant_client_zip_file

    For example, to check the Oracle Instant Client Basic package zip file for Linux x86-64:

        jarsigner -verify instantclient-basic-linux.x64-19.27.0.0.0dbru.zip
        jar verified.
3.  If you want detailed certificate information, then use the `-verify` option along with the `-verbose:summary` and `-certs` options. For example:
        jarsigner -verify -verbose:summary -certs instantclient-basic-linux.x64-19.27.0.0.0dbru.zip

For more `jarsigner` options, type `jarsigner -h` or review the [jarsigner reference documentation.](https://docs.oracle.com/en/java/javase/11/tools/jarsigner.html)

**Parent topic:** [Verifying Oracle Instant Client Code Signing](enable-client-code-signing.md)
