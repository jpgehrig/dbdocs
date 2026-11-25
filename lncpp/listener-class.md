The `Listener` class encapsulates the ability to listen for `Message`s, on behalf of registered `Agent`s, at specified queues.

Table 13-23 Summary of Listener Methods

| Method                | Summary                                                                                      |
|:----------------------|:---------------------------------------------------------------------------------------------|
| Listener()            | `Listener` class constructor.                                                                |
| getAgentList()        | Retrieves the list of `Agent`s for which the `Listener` provides its services.               |
| getTimeOutForListen() | Retrieves the time out for a call.                                                           |
| listen()              | Listens for `Message`s and returns the name of the `Agent` for whom a `Message` is intended. |
| setAgentList()        | Specifies the list of `Agent`s for which the `Listener` provides its services.               |
| setTimeOutForListen() | Specifies the time out for a listen() call.                                                  |

### 13.17.1 Listener()

`Listener` class constructor.

| Syntax                                                                                             | Description                                                                                                                                         |
|:---------------------------------------------------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------|
| `Listener(`<br>`   const Connection* conn);`                                                       | Creates a `Listener` object.                                                                                                                        |
| `Listener(`<br>`   const Connection* conn`<br>`   vector<Agent> &aglist,`<br>`   int waitTime=0);` | Creates a `Listener` object and sets the list of `Agent`s on behalf of which it listens on queues. Also sets the waiting time; default: no waiting. |

| Parameter  | Description                                                                                              |
|:-----------|:---------------------------------------------------------------------------------------------------------|
| `conn`     | The connection of the new `Listener` object.                                                             |
| `aglist`   | The list of agents on behalf of which the `Listener` object waits on queues; clients of this `Listener`. |
| `waitTime` | The time to wait on queues for messages of interest for the clients; in seconds.                         |

### 13.17.2 getAgentList()

Retrieves the list of `Agent`s for which the `Listener` provides its services.

#### Syntax

    vector<Agent> getAgentList() const;

### 13.17.3 getTimeOutForListen()

Retrieves the time out for a call.

#### Syntax

    int getTimeOutForListen() const;

### 13.17.4 listen()

Listens for `Message`s on behalf of specified `Agent`s for the amount of time specified by a previous setTimeOutForListen() call. Returns the `Agent` for which there is a `Message`.

Note that this is a blocking call. Before this call, complete the following steps:

- Registers each Agent listener through a setAgentList() call.

- Make a blocking call to setTimeOutForListen() that returns when a `Message` for one of the `Agent`s on the list arrives. If no `Message`s arrive before the wait time expires, the call returns an error.

#### Syntax

    Agent listen();

### 13.17.5 setAgentList()

Specifies the list of `Agent`s for which the `Listener` provides its services.

#### Syntax

    void setAgentList(
       vector<Agent>& agList);

| Parameter | Description           |
|:----------|:----------------------|
| `agList`  | The list of `Agent`s. |

### 13.17.6 setTimeOutForListen()

Specifies the time out for a listen() call.

#### Syntax

    void setTimeOutForListen(
       int waitTime);

| Parameter  | Description                                                                                               |
|:-----------|:----------------------------------------------------------------------------------------------------------|
| `waitTime` | The time interval, in seconds, during which the `Listener` is waiting for `Message`s at specified queues. |
