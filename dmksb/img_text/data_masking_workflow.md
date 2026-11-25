This flowchart shows how the security administrator creates masking definitions for use by the database administrator in cloning a production database and masking sensitive data in a test database.

Above the flowchart, the following text appears: The security administrator uses resources such as Oracle supplied masking templates to create masking definitions.

In the top half of the flowchart, the Identify Sensitive Information step appears in the top left and points to the Associate Mask Format with Sensitive Information step, which then points down to the Masking Definition step in the middle of the flowchart. The Import Oracle-Supplied Templates Using Self Update and Format Library steps also point to the Masking Definition step in the middle of the flowchart.

The Masking Definition step points to two sets of steps in the bottom half of the flowchart. The set of steps on the left side consists of the Clone Production to Staging step, which points to the Execute Mask step, which then points to the Test Database step. The set of steps on the right side consists of the Create Subset Definition step, which points to the Add Masking Definition step, which then points to the Export Dump from Production step, which then points to the Import into Test Database step.

Below the flowchart, the following text appears:

The database administrator uses masking definitions to mask sensitive data in a variety of ways:

- Clone production database and mask in a test database

- Export a masked dump from production database

- Export subsetted and masked dump from production database

End of image description.
