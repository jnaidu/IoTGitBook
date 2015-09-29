# Features

## Key capabilities provided in this release are as follows:

### IoT Core Services:
* Ability to define devices: There are templates for devices, and a device’s attributes can be described so that a message from a sensor on the device will carry the device type and attributes.
* Ability to collect data from the device ecosystem: An ecosystem could be a fleet of cars equipped to forward the data to an event hub within our platform. Data is sent in a protocol called MQTT, which is the industry standard data format for industrial IoT.
* Ability to process data: The event hub publishes the data to the applications and APIs. If the data is published to a queue, 3rd party applications that are subscribed to that queue do not receive published data, but will be able to read the data from the queue.
* Ability of 3rd party apps to consume data: An application can be programmed to react to data by using specific kinds of data to trigger specific kinds of responses—an alert is published and can be read from a specific queue and sent by the application to the user, or a support person can get instructions to contact the driver of a car that shows signs of overheating.


### IoT Messaging Services:
* Ability to send commands to devices: Devices can be subscribed to receive commands from applications. Applications can send a command defined in a command template to a particular device. Command sent to a particular command stream is received by all the devices subscribed to that stream.
* Ability to send/receive Events to/from devices: Applications can subscribe to Events from Devices, and Devices can subscribe to Events from Applications. Route and Stream in the data hub are used to manage subscriptions.
