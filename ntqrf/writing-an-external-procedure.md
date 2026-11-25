Using a third-generation programming language, you can write functions to be built into DLLs and started by `EXTPROC`.

The following is a simple Microsoft Visual C++ example of an external procedure called `FIND_MAX`:

**Note:**

Because external procedures are built into DLLs, they must be explicitly exported. In this example, the `DLLEXPORT`storage class modifier exports the function `FIND_MAX` from a dynamic link library.

    #include <windows.h>
    #define NullValue -1
    /*
      This function tests if x is at least as big as y.
    */
    long __declspec(dllexport) find_max(long    x,
                    short   x_indicator,
    long    y,
    short y_indicator,
                    short *ret_indicator)
    {
       /* It can be tricky to debug DLL's that are being called by a process
          that is spawned only when needed, as in this case.
          Therefore try using the DebugBreak(); command.
          This starts your debugger.  Uncomment the line with DebugBreak();
          in it and you can step right into your code.
       */
       /* DebugBreak();  */

       /* First check to see if you have any nulls. */
       /* Just return a null if either x or y is null. */

       if ( x_indicator==NullValue || y_indicator==NullValue) {
          *ret_indicator = NullValue;
          return(0);
       } else {
          *ret_indicator = 0;       /* Signify that return value is not null. */
          if (x >= y) return x;
          else return y;
       }
    }

**Parent topic:** [About Building External Procedures](about-building-external-procedures.md)
