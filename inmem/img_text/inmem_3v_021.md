#

This graphic depicts double buffering in the In-Memory Area. Step 1 is “Mark original IMCU as old version as of SCN.” Step 2 is “Create a new version of IMCU by combining clean rows from original with latest version of changed rows.” Step 3 is “Track any DML operations that occur during IMCU creation in Journal.”
