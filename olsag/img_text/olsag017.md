# Description of the illustration olsag017.gif

This illustration depicts trusted stored program unit execution. User 1 has execute privilege on a stored program unit owned by User 2. When User 1 invokes the procedure, it executes with User 2's system and object privileges. Row access, however, is mediated by User 1's Oracle Label Security session labels and privileges (because User 1 invoked the procedure).
