## User Actions for Common Fleet Patching and Provisioning Tasks

You can use Fleet Patching and Provisioning user actions to perform many tasks, such as installing and configuring any type of software and running scripts.

### Deploying a Web Server

The following procedure demonstrates automated deployment of Apache Web Server using Fleet Patching and Provisioning:

1.  Create a script to install Apache Web server, as follows:
    1.  On the Fleet Patching and Provisioning Server, download and extract the Apache Web server installation kit.
    2.  Create the script to install, configure, and start the Apache Web server.

2.  Register the script as a user action with Fleet Patching and Provisioning by running the following command on the Fleet Patching and Provisioning Server:

        rhpctl useraction -useraction apachestart
        -actionscript /user1/useractions/apacheinstall.sh
        -post -optype ADD_WORKINGCOPY -onerror ABORT

    The preceding command adds the `apachestart` user action for the action script stored in the specified directory. As per the specified properties, the user action runs after the `ADD_WORKINGCOPY` operation and terminates if there is any error.

3.  Create an image type and associate the user action with the image type, as follows:

        rhpctl add imagetype -imagetype apachetype -basetype SOFTWARE
        -useraction "apachestart"

    The preceding command creates a new image type called `apachetype`, a derivative of the basic image type, `SOFTWARE`, with an associated user action `apachestart`.

4.  Create a gold image of the image type, as follows:

        rhpctl import image -image apacheinstall -path /user1/apache2219_kit/
        -imagetype apachetype

    The preceding command creates a gold image, `apacheinstall`, with the script for Apache Web server installation, in the specified path, based on the `imagetype` you created earlier.

    To view the properties of this image, run the `rhpctl query image -image apacheinstall` command.

5.  Deploy a working copy of the gold image on the destination host, as follows:

        rhpctl add workingcopy -workingcopy apachecopy -image apacheinstall
        -path /user1/apacheinstallloc -sudouser user1
        -sudopath /usr/local/bin/sudo -node node1 -user user1
        -useractiondata "/user1/apachehome:1080:2.2.19"

    Oracle FPP provisions the software to the destination host and runs the `apachestart` script specified in the user action. You can provide the Apache Web server configuration details such as port number with the `useractiondata` option. If the destination host is an Oracle FPP Client, then you need not specify `sudo` credentials.

### Registering Multiple Scripts Using a Single User Action

Run multiple scripts as part of a user action plug-in by registering a wrapper script and bundled custom scripts. The wrapper script extracts the bundled scripts, which are copied under the directory of the wrapper script, and then runs those extracted scripts as necessary, similar to the following procedure:

1.  The following command creates a user action called `ohadd_ua`, and associates a wrapper script, `wc_add.sh`, with a zip file containing other scripts:

        rhpctl add useraction -useraction ohadd_ua -actionscript
        /scratch/crsusr/wc_add.sh -actionfile /scratch/crsusr/pack.zip -pre -runscope
        ALLNODES -optype ADD_WORKINGCOPY

    The wrapper script, `wc_add.sh`, extracts the `pack.zip` file into the script path, a temporary path to which the user action scripts are copied. The wrapper script can invoke any scripts contained in the file.

2.  The following command creates an image type, `sw_ua`, for the `ohadd_ua` user action:

        rhpctl add imagetype -imagetype sw_ua -useractions ohadd_ua -basetype SOFTWARE

3.  The following command creates an image called `swimgua` from the software specified in the path:

        rhpctl import image -image swimgua -path /tmp/custom_sw -imagetype sw_ua

4.  The following command adds a working copy called `wcua` and runs the `wc_add.sh` script:

        rhpctl add workingcopy -workingcopy wcua -image swimgua -client destination_cluster

**Parent topic:** [Oracle Fleet Patching and Provisioning Use Cases](fleet-patching-provisioning-use-cases.md)
