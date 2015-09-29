
# **Domain Model**


## IoT Solution
IoT Solution is a logical grouping of several solution instances developed to address a particular problem. An IoT solution can consist of zero or more solution instances.


## Instance
Instance is a logical grouping of devices and applications inside an application environment dedicated for a specific purpose. An instance consists of a library of command templates, attribute types, event templates used to model the device. An instance can have multiple applications which are associated with the devices.


## Application
Application refers to any external software, which is affiliated with devices. Applications can subscribe to events from devices and send commands to devices through streams. An application can have several streams.


## Device Template
Device Template describes a device in a generic form. It is mainly composed of attribute, command, and event templates. A library of device templates can be created in an instance. A device based on this template will inherit all the attribute, command, and event properties. Multiple device instances can be created with one device template.

## Attribute Type
Attribute Type describes the attributes or the properties of the device. It can either describe a variable or a constant attribute. Constants such as manufacturer, model, etc. are set once through the life of the device and variables such as temperature, set point, etc. keep changing over the life of the device. A library of attribute types can be created in an instance and shared across device templates.

## Command Template
Command Template describes the format of the command that the end device can act on. A command template captures the command and its associated parameters. A library of command templates can be created in an instance and shared across device templates.

## Event Template
Event Template is used to model the format of the events that the device can produce. Event templates can be bound to attribute type. If bound, then the attribute type is updated on event changes. A library of event templates can be constructed in an instance and used across multiple device templates.

## Event Threshold Policy
Event Threshold Policy describes a set of actions that need to be executed when certain conditions are met on a specified event. Every time an event is generated, the event threshold policy is executed to check if the conditions are met. If so, an alert is generated, indicating that the policy was satisfied. An event threshold policy can be attached to any event, and an event can have zero or more event threshold policies.

## Event Source
Event Source describes the list of events or a group of events. Events can be grouped based on event templates and device templates or devices.

## Device
Device is an instance of a device template. It inherits the device attributes, commands, and events described in the template. Devices communicate over streams, and can have zero or more streams.

## Stream
Stream is a data pipe that transfers messages between devices and applications. A stream can either be an application stream or a device stream. Each stream has publisher, consumer, and alert topics. Routes are used to connect publisher and subscriber. A stream can have multiple routes.

## Route
Route connects producers and consumers of messages. A route can either be an event or a command route, and is defined over device and application streams.



![](IoT_Domain_Model.jpg)

