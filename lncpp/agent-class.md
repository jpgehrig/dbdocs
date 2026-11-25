The `Agent` class represents an agent in the Advanced Queuing context.

Table 13-3 Summary of Agent Methods

| Method        | Summary                                     |
|:--------------|:--------------------------------------------|
| Agent()       | `Agent` class constructor.                  |
| getAddress()  | Returns the address of the `Agent`.         |
| getName()     | Returns the name of the `Agent`.            |
| getProtocol() | Returns the protocol of the `Agent`.        |
| isNull()      | Tests whether the `Agent` object is `NULL`. |
| operator=()   | Assignment operator for `Agent`.            |
| setAddress()  | Sets address of the `Agent `object.         |
| setName()     | Sets name of the `Agent `object.            |
| setNull()     | Sets `Agent` object to `NULL`.              |
| setProtocol() | Sets protocol of the `Agent `object.        |

### 13.3.1 Agent()

Agent class constructor.

| Syntax                                                                                                                                  | Description                                                                     |
|:----------------------------------------------------------------------------------------------------------------------------------------|:--------------------------------------------------------------------------------|
| `Agent(`<br>`   const Environment *env);`                                                                                               | Creates an `Agent` object initialized to its default values.                    |
| `Agent(`<br>`   const Agent& agent); `                                                                                                  | Copy constructor.                                                               |
| `Agent(`<br>`   const Environment *env,`<br>`   const string& name,`<br>`   const string& address,`<br>`   unsigned int protocol = 0);` | Creates an `Agent` object with specified `Agent`'s name, address, and protocol. |

| Parameter  | Description    |
|:-----------|:---------------|
| `env`      | Environment    |
| `name`     | Name           |
| `agent`    | Original agent |
| `address`  | Address        |
| `protocol` | Protocol       |

### 13.3.2 getAddress()

Returns a string containing `Agent`'s address.

#### Syntax

    string getAddress() const;

### 13.3.3 getName()

Returns a string containing `Agent`'s name.

#### Syntax

    string getName() const;

### 13.3.4 getProtocol()

Returns a numeric code representing `Agent`'s protocol.

#### Syntax

    unsigned int getProtocol() const;

### 13.3.5 isNull()

Tests whether the Agent object is `NULL`. If the Agent object is `NULL`, then `TRUE` is returned; otherwise, `FALSE` is returned.

#### Syntax

    bool isNull() const;

### 13.3.6 operator=()

Assignment operator for `Agent` class.

#### Syntax

    void operator=(
    const Agent& agent);

| Parameter | Description                  |
|:----------|:-----------------------------|
| `agent`   | The original `Agent` object. |

### 13.3.7 setAddress()

Sets the address of the `Agent` object.

#### Syntax

    void setAddress(
       const string& addr);

| Parameter | Description                     |
|:----------|:--------------------------------|
| `addr`    | The name of the `Agent` object. |

### 13.3.8 setName()

Sets the name of the `Agent` object.

#### Syntax

    void setName(
       const string& name);

| Parameter | Description                     |
|:----------|:--------------------------------|
| `name`    | The name of the `Agent` object. |

### 13.3.9 setNull()

Sets the `Agent` object to `NULL`. Unless operating in an inner scope, this call should be made before terminating the `Connection` used to create this `Agent`.

#### Syntax

    void setNull();

### 13.3.10 setProtocol()

Sets the protocol of the `Agent` object.

#### Syntax

    void setProtocol(
       unsigned int protocol = 0);

| Parameter  | Description                         |
|:-----------|:------------------------------------|
| `protocol` | The protocol of the `Agent` object. |
