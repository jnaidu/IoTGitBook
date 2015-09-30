# Key Features

This section describes the capabilities provided in this release, similar to the ones listed below.

* **_Ability to define devices_**: There are templates for devices, and a device’s attributes can be described so that a message from a sensor on the device will carry the device type and attributes.
* **_Ability to collect data from the device ecosystem_**: An ecosystem could be a fleet of cars equipped to forward the data to an event hub within our platform. Data is sent in a protocol called MQTT, which is the industry standard data format for industrial IoT.
* **_Ability to process data_**: The event hub publishes the data to the applications and APIs. If the data is published to a queue, 3rd party applications that are subscribed to that queue do not receive published data, but will be able to read the data from the queue.
* **_Ability of 3rd party apps to consume data_**: An application can be programmed to react to data by using specific kinds of data to trigger specific kinds of responses—an alert is published and can be read from a specific queue and sent by the application to the user, or a support person can get instructions to contact the driver of a car that shows signs of overheating.