# Description of the illustration gsmug_vm_016

The graphic depicts replicated databases, both local and remote, in a GDS Configuration. Read Write Service runs on the Primary/Master database. Read Only Services are load balanced across the two Standby/Replica databases. Upon the failure of the local Standby/Replica, GDS fails over the Read Only Service to another available database (in this case Primary/Master) and load balance with the Read Only Service running on the remote Standby/Replica.
