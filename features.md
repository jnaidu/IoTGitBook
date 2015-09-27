# Features

## Key capabilities provided in this release are as follows:

### IoT Core Services:
* Ability to model attributes of a device in a template: Attribute Type template is used to capture metadata of a device. It can either represent a constant or a variable characteristic of a device.
* Ability to model commands that a device can accept in a template: Command Template is used to capture the commands a device can accept. A list of arguments can also be modeled in a template.
* Ability to model events that a device can send in a template: Event Template is used to capture events that a device can send. Event can be the current status of an attribute from a given device.
* Ability to model a device as a template so that multiple instances of a device can be created using one template: Device Template is used to model a device. A Device Template consists of Attribute Types, Command Templates and Event Templates.
* Ability to manage devices in the platform: Device is an instance of a Device Template inheriting all the Attribute Types, Command Templates and Event Templates.
* Ability to manage applications in the platform: Applications that use the devices can be represented in the platform.
* Ability to represent a group of events as an Event Source: Event Source groups events based on Devices or Device Templates.
* Ability to model threshold policies on an incoming Event so as to generate alerts: Event Threshold Policy can be created on an Event Template. The policy is an expression, which when satisfied by an Event, an alert is generated.
* Ability to create Groups over Devices, Persons, and Applications: Groups can be created over Devices, Persons, and Applications. Entitlements and memberships can be defined in Groups.

### IoT Messaging Services:
* Ability to send commands to devices: Devices can be subscribed to receive commands from applications. Applications can send a command defined in a command template to a particular device. Command sent to a particular command stream is received by all the devices subscribed to that stream.
* Ability to send/receive Events to/from devices: Applications can subscribe to Events from Devices, and Devices can subscribe to Events from Applications. Route and Stream in the data hub are used to manage subscriptions.
