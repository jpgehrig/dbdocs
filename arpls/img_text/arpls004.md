# Description of the illustration arpls004.eps

This illustration shows the final steps in the target session.

The steps are:

- Continue execution and wait for the next event DBMS_DEBUG.continue()

- If the program terminated, detach the session using DBMS_DEBUG.detach_session()

- If it did not terminate, resume the process by showing the stack.
