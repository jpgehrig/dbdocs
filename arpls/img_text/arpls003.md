# Description of the illustration arpls003.eps

This illustration shows the continuation of steps in the target session.

The steps are:

- Initialize using DBMS_DEBUG.attach_session()

- Manipulate the breakpoints using:

  - DBMS_DEBUG.set_breakpoint()

  - DBMS_DEBUG.delete_breakpoint()

  - DBMS_DEBUG.disable_breakpoint()

  - DBMS_DEBUG.enable_breakpoint()

  - DBMS_DEBUG.show_breakpoint()

- Read first event from the target session using DBMS_DEBUG.synchronize()

- Show the stack using DBMS_DEBUG.print_backtrace()

- Get/set values using:

  - DBMS_DEBUG.get_value()

  - DBMS_DEBUG.set_value()

- Manipulate the breakpoints

- Show the source by using DBMS_DEBUG.show_source().
