You can install and configure any type of software using Fleet Patching and Provisioning user actions. Review this procedure to automate deployment of Apache Web Server using Fleet Patching and Provisioning.

Fleet Patching and Provisioning supports creation of work flows to deploy and manage all types of software.

1.  Create the script to install Apache Web server:
    1.  On the Fleet Patching and Provisioning Server, download and extract the Apache Web server installation kit.
    2.  Create the script to install, configure, and start the Apache Web server.
2.  Register the script as a user action with Fleet Patching and Provisioning. Run the following command from the Fleet Patching and Provisioning Server:
        rhpctl useraction -useraction apachestart
        -actionscript /user1/useractions/apacheinstall.sh
        -post -optype ADD_WORKINGCOPY -onerror ABORT

    The command adds the `apachestart` user action for the action script stored in the specified directory. As per the specified properties, the user action runs after the `ADD_WORKINGCOPY` operation and aborts if there is any error.
3.  Create an image type and associate the user action with the image type:
        rhpctl add imagetype -imagetype apachetype -basetype SOFTWARE
        -useraction "apachestart"

    The command creates a new image type called `apachetype`, a derivative of the basic image type `SOFTWARE` with an associated user action `apacherstart`.
4.  Create a gold image of the image type:
        rhpctl import image -image apacheinstall -path /user1/apache2219_kit/
        -imagetype apachetype

    The command creates a gold image `apacheinstall` with the script for Apache Web server installation, in the specified path based on the `imagetype` created earlier.

    To view the properties of this image, run the `rhpctl query image -image apacheinstall` command.
5.  Deploy a working copy of the gold image on the target:
        rhpctl add workingcopy -workingcopy apachecopy -image apacheinstall
        -path /user1/apacheinstallloc -sudouser user1
        -sudopath /usr/local/bin/sudo -node node1 -user user1
        -useractiondata "/user1/apachehome:1080:2.2.19

    Fleet Patching and Provisioning provisions the software to the target and runs the script `apachestart` specified in the user action. You provide the Apache Web server configuration details such as port number with the `useractiondata` option. If the target is a Fleet Patching and Provisioning Client, then you need not specify `sudo` credentials.

You can create other user actions and automate installation and configuration of software homes using Fleet Patching and Provisioning.

**Parent topic:** [Fleet Patching and Provisioning Use Cases](fleet-patching-and-provisioning-use-cases.md)
