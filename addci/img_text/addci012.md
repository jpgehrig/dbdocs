Calling an External Procedure

- In the External Address Space:

  - extproc is called either by /data_cartridge_dir/libdatastream.so or Listener

  - extproc calls to PL/SQL within the Oracle Address Space

- In the Oracle Address Space:

  - PL/SQL accesses Oracle Database through Oracle Server

  - PL/SQL calls to the Listener or /data_cartridge_dir/libdatastream.so within the External Address Space
