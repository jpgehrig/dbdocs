The `POST_WTRCMD=UNTIL_SNAPSHOT` command instructs the writer to perform recovery to the snapshot creation time.

Run the following command:

`POST_WTRCMD=UNTIL_SNAPSHOT`

This command instructs the writer to perform recovery to the snapshot creation time. The writer extracts the system change number of the redo logs stored in the database component and performs recovery until the system change number.

**Parent topic:** [About Integrating VSS with Third-Party Requester Applications](about-integrating-vss-with-third-party-requester-applications.md)
