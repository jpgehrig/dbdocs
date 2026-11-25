Oracle Data Provider for .NET opens a port to listen for database notifications when the following features are used:

- HA Events

- Load Balancing

- Continuous Query Notification

- AQ Notifications

All these features share the same port, which can be configured centrally by setting the `db` `notifications` port in an application or web configuration file.

If the configuration file does not exist or the `db` `notification` port is not specified, ODP.NET uses a valid, random port number. The configuration file may also request for a random port by specifying a `db` `notification` port value of `-1`. To specify a particular port in ODP.NET, Unmanaged Driver, for example, `1200`, an application or web configuration file can be used as follows:

    <configuration>
      <oracle.dataaccess.client>
        <settings>
          <add name="DbNotificationPort" value="1200"/>
        </settings>
      </oracle.dataaccess.client>
    </configuration>


To specify a particular port in ODP.NET, Managed Driver, an application or web configuration file can be used as follows:

    <configuration>
      <oracle.manageddataaccess.client>
        <version number="*">
          <settings>
            <setting name="DbNotificationPort" value="1200"/>
          </settings>
        </version>
      </oracle.manageddataaccess.client>
    </configuration>

The port number should be unique for each process running on a computer. Thus, the port number should be set uniquely for each application either programmatically or through an application config file. Note that if the specified port number is already in use or invalid, ODP.NET does not provide any errors.

When the process using ODP.NET starts, the application reads the `db` `notification` port number and listens on that port. Once the port is opened, the port number cannot be changed during the lifetime of the process.

**See Also:**

- "[Fast Application Notification](featRAC.md)"

- "[Runtime Connection Load Balancing](featRAC.md)"

- "[Continuous Query Notification Support](featChange.md)"

- "[Oracle Database Advanced Queuing Support](featAQ.md)"
