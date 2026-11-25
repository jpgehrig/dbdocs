1\. Tomcat log file:

Check `TOMCAT_HOME/logs/catalina.out` for any errors after deploying the application.

2\. Additional Logging:

Enable logging in Tomcat to find logging messages in the code.

**Note:**

Refer <https://tomcat.apache.org/tomcat-8.0-doc/logging.html> for more information

### Debugging UI Related Issues

1\. Browser Version:

This application has been tested on Firefox (version 52) and Chrome (version 58) successfully.

2\. Browser Console:

Look for errors in the browser console to find and debug issues.

3\. Monitor Network Traffic:

Track network traffic to find out the requests being made, and the responses to the requests. A return status higher than 400 indicates errors. If you find errors in the range of 400 t 500 inspect the Tomcat log files for debugging.

Inspect the `JSON` responses from various calls to the backend server.

4\. Additional Logging:

Edit the packaged HTML files, and add `console.log(...)` to add extra logging.
