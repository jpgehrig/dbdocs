Learn how to manage Event Viewer.

Setting `AUDIT_TRAIL` to `db` or `os` causes more records to be written to Event Viewer. This can fill up the Event Viewer log file. Follow these procedures to increase log file size:

1.  Right-click the event log in which you want to set size, and select Properties.
    The event Log Properties window appears.
2.  Use the up and down arrow keys to set the size you want in the Maximum log size box.
3.  Under When maximum event log size is reached, select one of the options that you want. The options are as follows:
    - Overwrite events as needed (oldest events first)

    - Archive the log when full, do not overwrite events

    - Do not overwrite events (clear log manually)
4.  If you want to clear the log contents, click Clear Log.
5.  Click OK.
    You return to Event Viewer.

    **Note:**

    Audit information cannot be spooled to a file. `AUDIT_FILE_DEST` is supported on Windows to write XML format audit files when `AUDIT_TRAIL` is set to `XML` or `XML,EXTENDED` format and thus must be added to the initialization parameter file.

**Parent topic:** [About Event Viewer](about-event-viewer.md)
