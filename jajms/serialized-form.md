Skip navigation links

- [Overview](overview-summary.md)
- Package
- Class
- [Tree](overview-tree.md)
- [Deprecated](deprecated-list.md)
- [Index](index-all.md)
- [Help](help-doc.md)

**Oracle® Database Advanced Queuing Java API Reference
19c**
E96513-01

- Prev
- Next

<!-- -->

- [Frames](index.md)
- No Frames

<!-- -->

- [All Classes](allclasses-noframe.md)

# Serialized Form

- ## Package javax.jms

  - ## Class [javax.jms.IllegalStateException](javax/jms/IllegalStateException.md) extends [JMSException](javax/jms/JMSException.md) implements Serializable

  - ## Class [javax.jms.InvalidClientIDException](javax/jms/InvalidClientIDException.md) extends [JMSException](javax/jms/JMSException.md) implements Serializable

  - ## Class [javax.jms.InvalidDestinationException](javax/jms/InvalidDestinationException.md) extends [JMSException](javax/jms/JMSException.md) implements Serializable

  - ## Class [javax.jms.InvalidSelectorException](javax/jms/InvalidSelectorException.md) extends [JMSException](javax/jms/JMSException.md) implements Serializable

  - ## Class [javax.jms.JMSException](javax/jms/JMSException.md) extends java.lang.Exception implements Serializable

    - ## Serialized Fields

      - #### errorCode

            java.lang.String errorCode

        Vendor-specific error code.

      - #### linkedException

            java.lang.Exception linkedException

        `Exception` reference.

  - ## Class [javax.jms.JMSSecurityException](javax/jms/JMSSecurityException.md) extends [JMSException](javax/jms/JMSException.md) implements Serializable

  - ## Class [javax.jms.MessageEOFException](javax/jms/MessageEOFException.md) extends [JMSException](javax/jms/JMSException.md) implements Serializable

  - ## Class [javax.jms.MessageFormatException](javax/jms/MessageFormatException.md) extends [JMSException](javax/jms/JMSException.md) implements Serializable

  - ## Class [javax.jms.MessageNotReadableException](javax/jms/MessageNotReadableException.md) extends [JMSException](javax/jms/JMSException.md) implements Serializable

  - ## Class [javax.jms.MessageNotWriteableException](javax/jms/MessageNotWriteableException.md) extends [JMSException](javax/jms/JMSException.md) implements Serializable

  - ## Class [javax.jms.ResourceAllocationException](javax/jms/ResourceAllocationException.md) extends [JMSException](javax/jms/JMSException.md) implements Serializable

  - ## Class [javax.jms.TransactionInProgressException](javax/jms/TransactionInProgressException.md) extends [JMSException](javax/jms/JMSException.md) implements Serializable

  - ## Class [javax.jms.TransactionRolledBackException](javax/jms/TransactionRolledBackException.md) extends [JMSException](javax/jms/JMSException.md) implements Serializable

- ## Package oracle.jms

  - ## Class [oracle.jms.AQjmsConnectionFactory](oracle/jms/AQjmsConnectionFactory.md) extends java.lang.Object implements Serializable

    - ## Serialized Fields

      - #### hostname

            java.lang.String hostname

      - #### oracle_sid

            java.lang.String oracle_sid

      - #### portno

            int portno

      - #### jdbc_driver

            java.lang.String jdbc_driver

      - #### jdbc_conn_str

            java.lang.String jdbc_conn_str

      - #### user

            java.lang.String user

      - #### passwd

            java.lang.String passwd

      - #### classname

            java.lang.String classname

      - #### jdbc_info

            java.util.Properties jdbc_info

      - #### data_source

            javax.sql.DataSource data_source

      - #### compliant

            boolean compliant

  - ## Class oracle.jms.AQjmsConsumerClosedException extends [JMSException](javax/jms/JMSException.md) implements Serializable

  - ## Class [oracle.jms.AQjmsDestination](oracle/jms/AQjmsDestination.md) extends java.lang.Object implements Serializable

    - ## Serialized Fields

      - #### type

            int type

      - #### owner

            java.lang.String owner

      - #### name

            java.lang.String name

      - #### table

            java.lang.String table

      - #### pload_type

            int pload_type

      - #### p_data_type

            java.lang.String p_data_type

      - #### property

            AQjmsDestinationProperty property

      - #### dest_properties

            java.util.Hashtable dest_properties

      - #### trans_list

            java.util.Hashtable trans_list

      - #### secure

            boolean secure

      - #### is_temp

            boolean is_temp

      - #### temp_cons

            int temp_cons

  - ## Class oracle.jms.AQjmsDestinationClosedException extends [JMSException](javax/jms/JMSException.md) implements Serializable

  - ## Class [oracle.jms.AQjmsDestinationProperty](oracle/jms/AQjmsDestinationProperty.md) extends oracle.AQ.AQQueueProperty implements Serializable

  - ## Class [oracle.jms.AQjmsException](oracle/jms/AQjmsException.md) extends [JMSException](javax/jms/JMSException.md) implements Serializable

  - ## Class oracle.jms.AQjmsIllegalStateException extends [IllegalStateException](javax/jms/IllegalStateException.md) implements Serializable

  - ## Class oracle.jms.AQjmsInvalidDestinationException extends [InvalidDestinationException](javax/jms/InvalidDestinationException.md) implements Serializable

  - ## Class oracle.jms.AQjmsInvalidSelectorException extends [InvalidSelectorException](javax/jms/InvalidSelectorException.md) implements Serializable

  - ## Class oracle.jms.AQjmsMessageEOFException extends [MessageEOFException](javax/jms/MessageEOFException.md) implements Serializable

  - ## Class oracle.jms.AQjmsMessageFormatException extends [MessageFormatException](javax/jms/MessageFormatException.md) implements Serializable

    - ## Serialized Fields

      - #### err_code

            int err_code

  - ## Class oracle.jms.AQjmsMessageNotReadableException extends [MessageNotReadableException](javax/jms/MessageNotReadableException.md) implements Serializable

  - ## Class oracle.jms.AQjmsMessageNotWriteableException extends [MessageNotWriteableException](javax/jms/MessageNotWriteableException.md) implements Serializable

  - ## Class [oracle.jms.AQjmsParseException](oracle/jms/AQjmsParseException.md) extends [JMSException](javax/jms/JMSException.md) implements Serializable

  - ## Class [oracle.jms.AQjmsQueueConnectionFactory](oracle/jms/AQjmsQueueConnectionFactory.md) extends [AQjmsConnectionFactory](oracle/jms/AQjmsConnectionFactory.md) implements Serializable

  - ## Class oracle.jms.AQjmsServerNotReachableException extends [JMSException](javax/jms/JMSException.md) implements Serializable

  - ## Class oracle.jms.AQjmsTempLobTruncateException extends [JMSException](javax/jms/JMSException.md) implements Serializable

    - ## Serialized Fields

      - #### isFromBlob

            boolean isFromBlob

  - ## Class [oracle.jms.AQjmsTopicConnectionFactory](oracle/jms/AQjmsTopicConnectionFactory.md) extends [AQjmsConnectionFactory](oracle/jms/AQjmsConnectionFactory.md) implements Serializable

  - ## Class [oracle.jms.AQjmsXAConnectionFactory](oracle/jms/AQjmsXAConnectionFactory.md) extends [AQjmsConnectionFactory](oracle/jms/AQjmsConnectionFactory.md) implements Serializable

    - ## Serialized Fields

      - #### m_xaDS

            javax.sql.XADataSource m_xaDS

      - #### m_xaresFactory

            oracle.jms.AQjmsXAResourceFactory m_xaresFactory

  - ## Class oracle.jms.AQjmsXAException extends javax.transaction.xa.XAException implements Serializable

  - ## Class [oracle.jms.AQjmsXAQueueConnectionFactory](oracle/jms/AQjmsXAQueueConnectionFactory.md) extends [AQjmsQueueConnectionFactory](oracle/jms/AQjmsQueueConnectionFactory.md) implements Serializable

    - ## Serialized Fields

      - #### m_xaDS

            javax.sql.XADataSource m_xaDS

      - #### m_xaresFactory

            oracle.jms.AQjmsXAResourceFactory m_xaresFactory

  - ## Class [oracle.jms.AQjmsXATopicConnectionFactory](oracle/jms/AQjmsXATopicConnectionFactory.md) extends [AQjmsTopicConnectionFactory](oracle/jms/AQjmsTopicConnectionFactory.md) implements Serializable

    - ## Serialized Fields

      - #### m_xaDS

            javax.sql.XADataSource m_xaDS

      - #### m_xaresFactory

            oracle.jms.AQjmsXAResourceFactory m_xaresFactory

  - ## Class oracle.jms.ParseException extends java.lang.Exception implements Serializable

    - ## Serialized Fields

      - #### specialConstructor

            boolean specialConstructor

        This variable determines which constructor was used to create this object and thereby affects the semantics of the "getMessage" method (see below).

      - #### currentToken

            oracle.jms.Token currentToken

        This is the last token that has been consumed successfully. If this object has been created due to a parse error, the token followng this token will (therefore) be the first error token.

      - #### expectedTokenSequences

            int[][] expectedTokenSequences

        Each entry in this array is an array of integers. Each array of integers represents a sequence of tokens (by their ordinal values) that is expected at this point of the parse.

      - #### tokenImage

            java.lang.String[] tokenImage

        This is a reference to the "tokenImage" array of the generated parser within which the parse error occurred. This array is defined in the generated ...Constants interface.

      - #### eol

            java.lang.String eol

        The end of line string for this machine.

  - ## Class oracle.jms.TokenMgrError extends java.lang.Error implements Serializable

    - ## Serialized Fields

      - #### errorCode

            int errorCode

        Indicates the reason why the exception is thrown. It will have one of the above 4 values.

  - ## Class oracle.jms.Tset extends java.lang.Object implements Serializable

    serialVersionUID:
    -2483619647567846128L

    - ## Serialized Fields

      - #### m_val

            boolean m_val

Skip navigation links

- [Overview](overview-summary.md)
- Package
- Class
- [Tree](overview-tree.md)
- [Deprecated](deprecated-list.md)
- [Index](index-all.md)
- [Help](help-doc.md)

**Oracle® Database Advanced Queuing Java API Reference
19c**
E96513-01

- Prev
- Next

<!-- -->

- [Frames](index.md)
- No Frames

<!-- -->

- [All Classes](allclasses-noframe.md)

Copyright © 2001, 2019, Oracle and/or its affiliates. All rights reserved.
