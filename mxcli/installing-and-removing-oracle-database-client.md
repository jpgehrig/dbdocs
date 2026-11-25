The Oracle Database Instant Client software is available on the Oracle Instant Client downloads page.

- Installing Non-Notarized Oracle Instant Client Software Using Zip Files
- Installing Notarized Oracle Instant Client Software Using DMG Files
- Removing the Oracle Database Instant Client Software

### Installing Non-Notarized Oracle Instant Client Software Using Zip Files

Download and install non-notarized Oracle Database Instant Client 19c zip files by completing the following steps:

1.  Download the Oracle Instant Client for Mac OS X (Intel) (64-bit) package from the Oracle Instant Client Downloads page:
    [`https://www.oracle.com/database/technologies/instant-client/downloads.html`](http://www.oracle.com/technetwork/database/features/instant-client/index-097480.html)
2.  Create a directory on your computer, for example, `instantclient`. Choose a directory to install the Oracle Instant Client and unzip the downloaded zip file in that directory. The unzipped file creates the `instantclient_19_8` directory.
3.  Set the `NLS_LANG` environment variable to the required character set. For example, an `NLS_LANG` of `american_america.utf8` is a valid setting. It is in the following format: `[NLS_LANGUAGE]_[NLS_TERRITORY].[NLS_CHARACTERSET]`.
    This completes the installation of Oracle Database Instant Client.

    **Note:**

    Non-notarized zip files will be discontinued in future releases.

**Related Topics**

- [Instant Client Light Requirements](instant-client-light-requirements.md)

**Parent topic:** Installing and Removing Oracle Database Instant Client

### Installing Notarized Oracle Instant Client Software Using DMG Files

1.  Download the Oracle Instant Client for Mac OS X (Intel) (64-bit) disk image (DMG) files from the Oracle Instant Client Downloads page:
    [`https://www.oracle.com/database/technologies/instant-client/downloads.html`](http://www.oracle.com/technetwork/database/features/instant-client/index-097480.html)
2.  Mount all the DMG packages.
    1.  `/usr/bin/hdiutil mount ``dmg_file_name`
3.  Run the following steps to copy the volume contents to `/Users/``user-name``/Downloads/instantclient_19_8`.
    1.  `cd /Volumes/instantclient-*-macos.x64-19.8.0.0.0dbru`
    2.  `sh ./install_ic.sh`
    3.  In Mac Finder, eject the mounted Oracle Instant Client packages.

**Parent topic:** Installing and Removing Oracle Database Instant Client

### Removing the Oracle Database Instant Client Software

To remove the Oracle Database Instant Client software, delete the `instantclient_19_8` directory.

**Parent topic:** Installing and Removing Oracle Database Instant Client
