# Configure the Application
In order to establish a secure communication between the application and the Covisint IoT Platform, you will need the following connectivity and message processing information.

## CONNECTIVITY CONFIGURATION INFORMATION
Information you will need to establish a secure communication.
```
Host – The host name of the Covisint JMS MQTT Broker for your solution
Port – The port of the Covisint IoT JMS Broker for your solution
jmsProvider – the provider name of the JMS broker
connectionFactory – the JMS connection factory for the JMS Broker
brokerName – the broker name to connect
providerURL – the JMS JNDI URL for connecting
initialContextFactory – the context factory class
consumerTopic – The consumer JMS queue name which will contain all events
producerTopic – the producer JMS queue name which will be used to publish commands to the device.
alertConsumerTopic – The alert consumer JMS queue name which will contain events that caused an alert
accountId – the id to be passed to the JMS broker when publishing commands and subscribing to events.
Username – the username required to provide when connecting to the JMS broker. Basic authentication.
Password – the password required to provide when connecting to the JMS broker. Basic authentication.
```
## MESSAGE PROCESSING CONFIGURATION INFORMATION
Information you will need to publish commands and subscribe to events.
```
ownerId -  the application Id.
consumerPrivateKey – The key used to decrypt the incoming events and alerts from the broker.
producerPublicKey – The key used to encrypt the command message which will be published to the producer topic.
Password – the password for the device. When device security set to basic.
Username – the username of the device. When device security set to basic.
```