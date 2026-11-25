# Description of the illustration dbr_replay_cust_options.gif

The heading Replay Workload: Customize Options appears on the upper left portion of the page. Below the heading are values for the Database, Replay Name, and Logged In As fields.

The upper right portion of the page states "Step 5 of 8." The Cancel and Back buttons appear to the left of this text, and a Next button appears to the right of this text.

There are two tabs: Connection Mappings, and Replay Parameters. The Connection Mappings tab is open.

The text at the top of this tab reads: "Replay Clients must establish connections to the replay database. Specify connector details to the replay database using either a single connector descriptor or net service name." A tip follows this that reads: "Connections must point to the replay database for a successful replay."

Below this text is a Capture Name drop-down with Capture12_1 selected.

Below these are two radio buttons with the first one selected, and each radio button has user input fields. The first radio button has the following text: "Use a single connect descriptor for all client connections." A Test Connection button appears to the right of this text. The user input text is as follows:

(DESCRIPTION=(ADDRESS_LIST=(ADDRESS=(PROTOCOL=TCP)(HOST=hostname.example.com)(PORT=15045)))(CONNECT_DATA=(SID=t0)))

The second radio button has the following text: "Use a single TNS net service name for all client connections." The following tip text appears below the input field for this radio button: "All Replay Clients must be able to resolve the net service name (for example, through a local tnsnames.ora file)."

End of description.
