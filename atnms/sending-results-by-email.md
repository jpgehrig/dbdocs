Optionally email the HTML report to one or more recipients using the `–sendemail` option.

### To send health check run results by email:

1.  Specify the recipients in the `NOTIFICATION_EMAIL` environment variable.
        $ ./orachk –sendemail “NOTIFICATION_EMAIL=email_recipients"

        $ ./exachk –sendemail “NOTIFICATION_EMAIL=email_recipients"

    Where email_recipients is a comma-delimited list of email addresses.
2.  Verify the email configuration settings using the `–testemail` option.

**Parent topic:** [Using Oracle ORAchk and Oracle EXAchk to Manually Generate Health Check Reports](manually-generate-health-check-reports.md)
