This property gets the password compatibility mode.

### Declaration

    // C#
    public string PasswordCompatMode {get;}

### Property Value

A `string`.

### Remarks

The default value is `Framework20`. The other acceptable value is `Framework40`. The string value is case-sensitive.

To customize a provider, ASP.NET developers can set a string value for this property through the `web.config` file using the case-sensitive `passwordCompatMode` attribute.

When `passwordFormat` attribute is set to `Hashed`, the value of `System.Web.Security.Membership.HashAlgorithmType` property is used to hash password for a Membership user during the creation and validation of the user.

The value for `HashAlgorithmType` property can be set in the `web.config` file through the case-sensitive attribute `hashAlgorithmType`, as in the following example:

    <membership defaultProvider="OracleMembershipProvider" hashAlgorithmType="SHA1"/>

If `hashAlgorithmType` attribute is not specified in the` web.config` file, `SHA1` will be used. With .NET Framework 2.0, the other valid value for `hashAlgorithmType` is `MD5`.

With .NET Framework 4, if a new application that does not have existing Membership users and would like to use one of the other variants of `SHA` and `HMACSHA` hash algorithm types, the `passwordCompatMode` attribute must be set to `Framework40` and the `hashAlgorithmType` attribute must be set to the desired type, such as `SHA256`, `HMACSHA256`, `HMACSHA384`, or `HMACSHA512`. Nevertheless, `SHA1` and `MD5` are still supported when `passwordCompatMode` is set to `Framework40`.

### Example

The following is a `web.config` example that sets `hashAlgorithmType` to `HMACSHA25` and `passwordCompatMode` to `Framework40`.

    <!-- Enable and customize OracleMembershipProvider settings -->
    <membership defaultProvider="MyOracleMembershipProvider" hashAlgorithmType="HMACSHA256">
                 <providers>
        <add name="MyOracleMembershipProvider"
        type="Oracle.Web.Security.OracleMembershipProvider, Oracle.Web,
        Version=4.112.2.0, Culture=neutral, PublicKeyToken=89b483f429c47342"
        ConnectionStringName="my_membership_app_con_string"
        applicationName="my_membership_app"
        enablePasswordRetrieval="false"
        enablePasswordReset="true"
        requiresQuestionAndAnswer="true"
        requiresUniqueEmail="true"
        passwordFormat="Hashed"
        maxInvalidPasswordAttempts="4"
        minRequiredPasswordLength="9"
                    passwordCompatMode="Framework40"
        passwordAttemptWindow="8"/>
              </providers>
    </membership>

Once one `hashAlgorithmType` is used to create a Membership user, the same `hashAlgorithmType` must be used to validate the user. If `hashAlgorithmType` is changed, the user will not be validated successfully. Thus, the same `hashAlgorithmType` must be used for a given application during its lifetime.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleMembershipProvider Class](OracleMembershipProviderClass.md)

- [OracleMembershipProvider Members](OracleMembershipProviderMembers.md)
