## Setup Wizard Installation Options for Creating Images

Before you start the setup wizards for your Oracle Database or Oracle Grid Infrastructure installation, decide if you want to use any of the available image-creation options.

In image-based installations, you can start your Oracle Database installation or Oracle Grid Infrastructure installation by running the setup wizard `setup.exe`. This wizard comes with the following image-creation options:

**Note:**

`setup.exe` is the recommended setup wizard for installing both Oracle Database and Oracle Grid Infrastructure.

Table 7-3 Image-Creation Options for Setup Wizard

| Option                 | Description                                                                               |
|:-----------------------|:------------------------------------------------------------------------------------------|
| `-createGoldImage`     | Creates a gold image from the current Oracle home.                                        |
| `-destinationLocation` | Specify the complete path, or location, where the gold image will be created.             |
| `-exclFiles`           | Specify the complete paths to the files to be excluded from the newly created gold image. |
| `—help`                | Displays help for all the available options.                                              |

For example:

    setup.exe -createGoldImage -destinationLocation c:\my_images

Where:

`c:\my_images` is the file location where the image zip file is created.

**Parent topic:** [Installing and Configuring Oracle Grid Infrastructure for a Standalone Server](install-configure-oracle-grid-infrastructure-standalone-server.md)
