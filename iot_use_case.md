
# IoT Example


## Purpose

This section is intended as a guide for solution developers and partners to develop their IoT solution on top of Covisint platform. It illustrates steps involved in developing an IoT solution by using example use cases. A sample request and response is provided to guide the user. For a complete list of APIs, refer to IoT Platform API Reference Guide.

## Pre-requisite
Assumption is that the IoT solution instance already exists and the following application is built on top of this solution instance.

## Use Case: Rental Car Company

### Description
This is a health monitoring use case where a Rental Car Company is using Covisint IoT platform to proactively detect faults in the vehicle and provide support at the nearest service center. The car is equipped with a gateway which can scan the engine fault code every minute and wirelessly transmits the code to Covisint IoT platform in the cloud. An application is subscribed to these engine fault codes from all the cars in the fleet. Whenever a fault is detect on the car, the application alerts the user to direct that car to the nearest service center. In the following sections, we describe how to model a car, model an event and how to connect an application to receive all events on Covisint IoT platform.










### Configure The Device
In order for the device to connect to Covisint IoT Platform, the connectivity and message processing information needs to be flashed onto the device. In this example, the gateway in the car will have the following information.

#### CONNECTIVITY CONFIGURATION INFORMATION
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
#### MESSAGE PROCESSING CONFIGURATION INFORMATION
Flash message processing configuration information onto the device
```
ownerId -  the device Id.
consumerPrivateKey – The key used to decrypt the incoming commands from the broker.
producerPublicKey – The key used to encrypt the event message which will be published to the producer topic.
Password – the password for the device. When device security set to basic.
Username – the username of the device. When device security set to basic.
```
### Configure The Application
In order to establish a secure communication between the application and the Covisint IoT Platform, you will need the following connectivity and message processing information.

#### CONNECTIVITY CONFIGURATION INFORMATION
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
#### MESSAGE PROCESSING CONFIGURATION INFORMATION
Information you will need to publish commands and subscribe to events.
```
ownerId -  the application Id.
consumerPrivateKey – The key used to decrypt the incoming events and alerts from the broker.
producerPublicKey – The key used to encrypt the command message which will be published to the producer topic.
Password – the password for the device. When device security set to basic.
Username – the username of the device. When device security set to basic.
```
### Send Event From Device
To send an event from the car, the gateway on the car needs to perform the following steps:
1. Read engine fault code: The gateway will read the engine fault code every minute.
2. Construct message: The gateway will construct JSON string for the event. -
For example:
```
{ “engine_fault_code”: 10200 }
```
3. Encrypt message: The JSON event string needs to be encrypted using the producerPublicKey and encode the message in Base64 format.  
For example:
```
”ew0KInRlbXAiOiAyNS4zLA0KImh1bWlkaXR5Iiw1NC44DQp9”
```
4. Generate a messageID: A unique messageID is generated to identify the message.        
For Example:
```
“65eb9268-b0d1-4f75-a855-71eac716a351”
```
5. Construct event message: Construct a JSON message including messageID, deviceID, eventTemplateID and the encoded message.          
For Example:
```
{
    “messageID”: “65eb9268-b0d1-4f75-a855-71eac716a351”,
    “deviceID”: “7d7289e5-a45b-42a1-a762-1a662756e715”,
    “eventTemplateID”: “48c713f8-5b69-49f0-afb1-e5618ac9bae9”,
    “message”: “ew0KInRlbXAiOiAyNS4zLA0KImh1bWlkaXR5Iiw1NC44DQp9”
}
```
6. Send event: Send the event to IoT platform.
