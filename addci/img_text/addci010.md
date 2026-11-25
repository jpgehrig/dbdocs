External Program Executing in Separate Address Space

In the External Address Space:

`extproc` is called either by `/sh_libs/extlib.so` or by `Listener`

`extproc` is called either by `/sh_libs/extlib.so` or by `Listener`

`extproc` calls to the Inter-Language Method Service within the Oracle Address Space

In the Oracle Address Space:

Inter-Language Method Service accesses Oracle Database through Oracle Server

Inter-Language Method Service calls to the `Listener` or `extproc` within the External Address Space
