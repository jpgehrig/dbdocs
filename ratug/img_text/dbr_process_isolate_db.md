# Description of the illustration dbr_process_isolate_db.gif

The following warning appears at the top of the page:

"A captured workload can contain references to external systems that may only be meaningful in the capture environment. Replaying a workload with unresolved references to external systems may cause unexpected problems in the production environment. You should perform a replay in a COMPLETELY ISOLATED test environment that may include hosts, networks, e-mail servers, storage systems, and other devices. Make sure to resolve all references to external systems in the replay environment, so that replaying a workload cannot harm your production environment."

The heading "Isolate Test Database: References to External Systems" appears below the warning. Below the heading is the text "References to external systems may cause problems during the replay."

The following text precedes a bulleted list with three items: "Use the links below to verify potential references to external systems and modify those that are invalid."

The links are Database Links, Directory Objects, and Streams. The text for each of these links reads "This link takes you outside of the Database Replay process."

A tip follows the list that reads "There may be more references to external systems than those found via the above links."

End of description.
