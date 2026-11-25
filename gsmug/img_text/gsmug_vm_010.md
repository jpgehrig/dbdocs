# Description of the illustration gsmug_vm_010

The graphic depicts replicated databases, both local and remote, in a GDS Configuration.

Read Write Service runs on the Primary/Master database.

Read Only Services run on the two Standby/Replica databases.

Client connections are load balanced between the READ ONLY Services running on the Standby/Replica databases (across data centers).
