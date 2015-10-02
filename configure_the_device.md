# Configure the Device
In order for the device to connect to Covisint IoT Platform, the connectivity and message processing information needs to be flashed onto the device. In this example, the gateway in the car be configured as described below.

## CONNECTIVITY CONFIGURATION INFORMATION
Flash connectivity configuration information onto the device.
```
Host – The host name of the Covisint IoT MQTT Broker for your solution
Port – The port of the Covisint IoT MQTT Broker for your solution
consumerTopic – The consumer MQTT topic name which will contain all commands
producerTopic – the producer MQTT topic name which will be used to publish events from the device.
clientId – the id to be passed to the MQTT broker when publishing events and subscribing to commands. For both cases, the device will need to append another unique character to uniquely identify the consumer clientId and producer clientId.
Username – the username required to provide when connecting to the MQTT broker. Basic authentication.
Password – the password required to provide when connecting to the MQTT broker. Basic authentication.
```
## MESSAGE PROCESSING CONFIGURATION INFORMATION
Flash message processing configuration information onto the device
```
ownerId -  the device Id.
consumerPrivateKey – The key used to decrypt the incoming commands from the broker.
producerPublicKey – The key used to encrypt the event message which will be published to the producer topic.
Password – the password for the device. When device security set to basic.
Username – the username of the device. When device security set to basic.
```