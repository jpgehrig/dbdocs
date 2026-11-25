The subscription class encapsulates the information and operations necessary for registering a subscriber for notification.

Table 13-47 Enumerated Values Used by Subscription Class

| Attribute      | Options                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
|:---------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `Presentation` | • `PRES_DEFAULT` indicates that the event notification should be in default format.<br>• `PRES_XML` indicates that the event notification should be in XML format.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `Protocol`     | • `PROTO_CBK` indicates that the client receives notifications through the default system protocol.<br>• `PROTO_MAIL` indicates that the client receives notifications through e-mail, like `xyz@oracle.com`. The database does not check if the e-mail is valid.<br>• `PROTO_SERVER` indicates that the client receives notifications through an invoked PL/SQL procedure in the database, like `schema.procedure`. The subscriber must have the appropriate permissions on the procedure.<br>• `PROTO_HTTP` indicates that the client receives notifications through an HTTP URL, like `http://www.oracle.com:80`. The database does not check if the URL is valid. |
| `Namespace`    | • `NS_ANONYMOUS` indicates that the registrations are made in an anonymous namespace.<br>• `NS_AQ` indicates that the registrations are made in the Oracle Database Advanced Queuing namespace.                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |

Table 13-48 Summary of Subscription Methods

| Method                     | Summary                                                                                                 |
|:---------------------------|:--------------------------------------------------------------------------------------------------------|
| Subscription()             | `Subscription` class constructor.                                                                       |
| getCallbackContext()       | Retrieves the callback context.                                                                         |
| getDatabaseServersCount()  | Retrieves the number of database servers in which the client is interested for the registration.        |
| getDatabaseServerNames()   | Returns the names of all the database servers where the client registered an interest for notification. |
| getNotifyCallback()        | Returns the pointer to the registered callback function.                                                |
| getPayload()               | Retrieves the payload that has been set on the `Subscription` object before posting.                    |
| getSubscriptionName()      | Retrieves the name of the `Subscription`.                                                               |
| getSubscriptionNamespace() | Retrieves the namespace of the `Subscription`.                                                          |
| getRecipientName()         | Retrieves the name of the `Subscription` recipient.                                                     |
| getPresentation()          | Retrieves the notification presentation mode.                                                           |
| getProtocol()              | Retrieves the notification protocol.                                                                    |
| isNull()                   | Determines if the `Subscription` is `NULL`.                                                             |
| operator=()                | Assignment operator for `Subscription`.                                                                 |
| setCallbackContext()       | Registers a callback function for OCI protocol.                                                         |
| setDatabaseServerNames()   | Specifies the database server distinguished names from which the client receives notifications.         |
| setNotifyCallback()        | Specifies the context passed to user callbacks                                                          |
| setNull()                  | Specifies the `Subscription` object to `NULL` and frees the memory associated with the object.          |
| setSubscriptionName()      | Specifies the name of the subscription.                                                                 |
| setSubscriptionNamespace() | Specifies the namespace in which the subscription is used.                                              |
| setPayload()               | Specifies the buffer content of the notification.                                                       |
| setRecipientName()         | Specifies the name of the recipient of the notification.                                                |
| setPresentation()          | Specifies the presentation mode in which the client receives notifications.                             |
| setProtocol()              | Specifies the protocol in which the client receives notifications.                                      |
| setSubscriptionName()      | Specifies the name of the subscription.                                                                 |
| setSubscriptionNamespace() | Specifies the namespace where the subscription is used.                                                 |
| setRecipientName()         | Specifies the name of the recipient of the notification.                                                |

### 13.32.1 Subscription()

`Subscription` class constructor.

| Syntax                                             | Description                                                |
|:---------------------------------------------------|:-----------------------------------------------------------|
| `Subscription (`<br>`   const Environment *env );` | Creates a `Subscription` within a specified `Environment`. |
| `Subscription(`<br>`   const Subscription& sub);`  | Copy constructor.                                          |

#### Syntax

    Subscription(const Subscription& sub);

| Parameter | Description                  |
|:----------|:-----------------------------|
| `env`     | The `Environment`.           |
| `sub`     | The original `Subscription`. |

### 13.32.2 getCallbackContext()

Retrieves the callback context.

#### Syntax

    void* getCallbackContext() const;

### 13.32.3 getDatabaseServersCount()

Returns the number of database servers in which the client is interested for the registration.

#### Syntax

    unsigned int getDatabaseServersCount() const;

### 13.32.4 getDatabaseServerNames()

Returns the names of all the database servers where the client registered an interest for notification.

#### Syntax

    vector<string> getDatabaseServerNames() const;

### 13.32.5 getNotifyCallback()

Returns the pointer to the callback function registered for this `Subscription`.

#### Syntax

    unsigned int (*getNotifyCallback() const)(
       Subscription& sub,
       NotifyResult *nr);

| Parameter | Description         |
|:----------|:--------------------|
| `sub`     | The `Subscription`. |
| `nr`      | The `NotifyResult`. |

### 13.32.6 getPayload()

Retrieves the payload that has been set on the `Subscription` object before posting.

#### Syntax

    Bytes getCPayload() const;

### 13.32.7 getSubscriptionName()

Retrieves the name of the subscription.

#### Syntax

    string getSubscriptionName() const;

### 13.32.8 getSubscriptionNamespace()

Retrieves the namespace of the subscription. The subscription name must be consistent with its namespace. Valid `Namespace` values are `NS_AQ` and `NS_ANONYMOUS`, as defined in Table 13-47.

#### Syntax

    Namespace getSubscriptionNamespace() const;

### 13.32.9 getRecipientName()

Retrieves the name of the recipient of the notification. Possible return values are E-mail address, the HTTP url and the PL/SQL procedure, depending on the protocol.

#### Syntax

    string getRecipientName() const;

### 13.32.10 getPresentation()

Retrieves the presentation mode in which the client receives notifications. Valid `Presentation` values are defined in Table 13-47.

#### Syntax

    Presentation getPresentation() const;

### 13.32.11 getProtocol()

Retrieves the protocol in which the client receives notifications. Valid `Protocol` values are defined in Table 13-47.

#### Syntax

    Protocol getProtocol() const;

### 13.32.12 isNull()

Returns `TRUE` if `Subscription` is `NULL` or `FALSE` otherwise.

#### Syntax

    bool isNull() const;

### 13.32.13 operator=()

Assignment operator for `Subscription`.

#### Syntax

    void operator=(
       const Subscription& sub);

| Parameter | Description                  |
|:----------|:-----------------------------|
| `sub`     | The original `Subscription`. |

### 13.32.14 setCallbackContext()

Registers a notification callback function when the protocol is `PROTO_CBK`, as defined in Table 13-47. Context registration is also included in this call.

#### Syntax

    void setCallbackContext(
       void *ctx);

| Parameter | Description      |
|:----------|:-----------------|
| `ctx`     | The context set. |

### 13.32.15 setDatabaseServerNames()

Specifies the list of database server distinguished names from which the client receives notifications.

#### Syntax

    void setDatabaseServerNames(
       const vector<string>& dbsrv);

| Parameter | Description                              |
|:----------|:-----------------------------------------|
| `dbsrv`   | The list of database distinguished names |

### 13.32.16 setNotifyCallback()

Sets the context that the client wants to get passed to the user callback. If the protocol is set to `PROTO_CBK` or not specified, this attribute must be set before registering the subscription handle.

#### Syntax

    void setNotifyCallback(
       unsigned int (*callback)(
                        Subscription& sub,
                        NotifyResult *nr));

| Parameter  | Description                 |
|:-----------|:----------------------------|
| `callback` | The user callback function. |
| `sub`      | The `Subscription` object.  |
| `nr`       | The `NotifyResult` object.  |

### 13.32.17 setNull()

Sets the `Subscription` object to `NULL` and frees the memory associated with the object.

#### Syntax

    void setNull();

### 13.32.18 setPayload()

Sets the buffer content that corresponds to the payload to be posted to the `Subscription`.

#### Syntax

    void setPayload(
       const Bytes& payload);

| Parameter | Description                  |
|:----------|:-----------------------------|
| `payload` | Content of the notification. |

### 13.32.19 setPresentation()

Sets the presentation mode in which the client receives notifications.

#### Syntax

    void setPresentation(
       Presentation pres);

| Parameter | Description                                   |
|:----------|:----------------------------------------------|
| `pres`    | Presentation mode, as defined in Table 13-47. |

### 13.32.20 setProtocol()

Sets the `Protocol` in which the client receives event notifications, as defined in Table 13-47.

#### Syntax

    void setProtocol(
       Protocol prot);

| Parameter | Description   |
|:----------|:--------------|
| `prot`    | Protocol mode |

### 13.32.21 setSubscriptionName()

Sets the name of the subscription. All subscriptions are identified by a subscription name, which consists of a sequence of bytes of specified length.

If the namespace is `NS_AQ`, the subscription name is:

- `SCHEMA.QUEUE` when registering on a single consumer queue

- `SCHEMA.QUEUE:CONSUMER_NAME` when registering on a multiconsumer queue

#### Syntax

    void setSubscriptionName(
       const string& name);

| Parameter | Description        |
|:----------|:-------------------|
| `name`    | Subscription name. |

### 13.32.22 setSubscriptionNamespace()

Sets the namespace where the subscription is used. The subscription name must be consistent with its namespace. Default value is `NS_AQ`.

#### Syntax

    void setSubscriptionNamespace(
       Namespace nameSpace);

| Parameter   | Description                                                             |
|:------------|:------------------------------------------------------------------------|
| `nameSpace` | Namespace in which the subscription is used, as defined in Table 13-47. |

### 13.32.23 setRecipientName()

Sets the name of the recipient of the notification.

#### Syntax

    void setRecipientName(
       const string& name);

| Parameter | Description                         |
|:----------|:------------------------------------|
| `name`    | Name of the notification recipient. |
