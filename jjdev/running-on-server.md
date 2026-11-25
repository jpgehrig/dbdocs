You may want to write Java code that runs in a certain way on the server and in another way on the client. In general, Oracle does not recommend this. In fact, JDBC enable you to write portable code that avoids this problem, even though the drivers used in the server and client are different.

If you want to determine whether your code is running on the server, then use the `System.getProperty()` method, as follows:

    System.getProperty ("oracle.jserver.version")

The `getProperty()` method returns the following:

- A `String` that represents Oracle Database release, if running on the server

- `null`, if running on the client
