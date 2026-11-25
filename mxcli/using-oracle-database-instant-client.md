You can build a C/C++ application that uses Oracle Database Instant Client and connect to an Oracle Database server. If you want to build a 64-bit application and use `instantclient_19_8/sdk/demo.mk` file, then perform the following steps:

1.  Edit the `instantclient_19_8/sdk/demo.mk` file and set the `CC` and `cc` to your `gcc` location.
2.  Compile the C/C++ application using the flags specified in the `demo.mk` file, namely,` -idirafter . -DMAC_OSX -D_GNU_SOURCE -D_REENTRANT -g -m64 -mmacosx-version-min=10.13 <c_file_name> -I../include`.
3.  Start `make -f demo.mk buildoci EXE=cdemo81 OBJS=cdemo81.o` for a working demonstration of the options.
4.  Add the Java Library Path in the `ott` script, if you notice the following issue:
    `Exception in thread "main" java.lang.UnsatisfiedLinkError: no ocijdbc18 in java.library.path`
    `-Djava.library.path=``location_of_libocijdbc18`

    For example, if `libocijdbc18.dylib` is in the `/home/oracle/OTN/instantclient_19_8/` path, then you must add the following line in the `ott` script:

    `JAVA_PATH=-Djava.library.path=/home/oracle/OTN/instantclient_19_8/`

    and run the following command:

    `exec java $JAVA_PATH $JREOPTIONS oracle.ott.c.CMain nlslang=${NLS_LANG} $args`
5.  Modify `ICLIBHOME` in `demo.mk` to include the path to the libraries.
    For example, if the libraries are located in `/home/oracle/OTN/instantclient_19_8/`, then place it in the `demo.mk` file:
    `ICLIBHOME=/home/oracle/OTN/instantclient_19_8/`

The compilation options are as follows:

`-idirafter . -DMAC_OSX -D_GNU_SOURCE -D_REENTRANT -g -m64 -mmacosx-version-min=10.13 <c_file_name> -I../include`

The link options are as follows:

`-g -m64 -mmacosx-version-min=10.13 -rpath full_path_to_instantclient_19_8_libs application_name -L../../ -locci -lclntsh -lpthread`

**Parent topic:** [Oracle Database Instant Client Postinstallation Tasks](oracle-database-client-postinstallation-tasks.md)
