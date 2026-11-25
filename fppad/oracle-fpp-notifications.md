## Oracle Fleet Patching and Provisioning Notifications

The Oracle Fleet Patching and Provisioning Server is the central repository for the software homes available to the data center. Therefore, it is essential for administrators throughout the data center to be aware of changes to the inventory that may impact their areas of responsibility.

You can create subscriptions to image series events. Oracle Fleet Patching and Provisioning notifies a subscribed role or number of users by email of any changes to the images available in the series, including addition or removal of an image. Each series may have a unique group of subscribers.

Also, when a working copy of a gold image is added to or deleted from an `rhpclient`-less target, the owner of the working copy and any additional users can be notified by email. If you want to enable notifications for additional Oracle Fleet Patching and Provisioning events, you can create a user-defined action as described in the next section.

**Parent topic:** [Advanced Oracle Fleet Patching and Provisioning Configurations](advanced-oracle-fpp-configurations.md)
