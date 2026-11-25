This method initializes the `OracleMembership` provider with the property values specified in the ASP.NET application configuration file (`web.config`).

### Declaration

    // C#
    public override void Initialize(string name, NameValueCollection config);

### Parameters

- `name`

  The name of the `OracleMembership` provider instance to initialize.

- `config`

  A collection of name/value pairs representing the provider-specific attributes specified in the configuration for this provider.

### Exceptions

`ArgumentNullException` - The `config` parameter is a null value.

`InvalidOperationException` - An attempt is made to call the `Initialize` method on a provider after the provider has already been initialized.

`HttpException` - The current trust level is less than Low.

`System.Configuration.Provider.ProviderException` - One of the following is true in the application configuration file:

- The `enablePasswordRetrieval`, `enablePasswordReset`, `requiresQuestionAndAnswer`, or `requiresUniqueEmail` attribute is set to a value other than a Boolean value.

- The `maxInvalidPasswordAttempts` or `passwordAttemptWindow` attribute is set to a value that is not a positive integer.

- The `minRequiredPasswordLength` attribute is set to a value that is not a positive integer, or the value is greater than 128.

- The `minRequiredNonalphanumericCharacters` attribute is set to a negative integer, or the value is greater than 128.

- The value for the `passwordStrengthRegularExpression` attribute is not a valid regular expression.

- The value for the `applicationName` attribute is greater than 256 characters.

- The value for `passwordFormat` attribute is an invalid `MembershipPasswordFormat` enumeration value.

- The `passwordFormat` attribute is set to `Hashed`, and the `enablePasswordRetrieval` attribute is set to `true`.

- The `passwordFormat` attribute is set to `Encrypted`, and the `machineKey` configuration element specifies `AutoGenerate` for the `decryptionKey` attribute.

- The `connectionStringName` attribute is empty or does not exist in the application configuration file.

- The value of the connection string for the `connectionStringName` attribute value is empty, or the specified `connectionStringName` does not exist in the application configuration file.

- The value for the `commandTimeout` attribute is set to a negative integer.

- The application configuration file for this `OracleMembershipProvider` instance contains an unrecognized attribute.

### Remarks

The `Initialize` method is not intended to be called directly by the application.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleMembershipProvider Class](OracleMembershipProviderClass.md)

- [OracleMembershipProvider Members](OracleMembershipProviderMembers.md)
