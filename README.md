# IoT Platform Overview

This Covisint IoT Platform release is built around Device Health Monitoring. Health Monitoring (HM) is the ability of the system to monitor key aspects of device functionality, and alert stakeholders (customers, users) to device behavior that could result in malfunction, and ultimately failure. This release will be followed by more releases based on more advanced use cases.
The IoT Platform has five core capabilities. They are Secure & Control, Connect, Manage, Build, and Analyze. The Health Monitoring release enhances Secure & Control, Connect, Manage, and Build. These enhancements are detailed as follows:

## Secure and Control
* Identity Provisioning
    * Secure device registration and token (JWT) issuance
* Identity Relationship Management
    * Allow definition of groups of people, devices, organizations, and other groups
    * Flexible group attribute definition model
    * Add/remove to groups
* Identity Auth
    * Device authentication (Cert, Basic Auth, JWT token)
* Secure Data Transport
    * Encrypt all network and payload traffic between cloud services, gateways and devices
    * Log all CRUD operations in a persistent log for auditing and compliance reporting
    * Allow 3rd party applications to retrieve and analyze audit records
    * Ability to restrict who can access what data based on event routing

## Connect
* Gateway Services
    * Partners can integrate their own gateways or 3rd party gateways
* Event Data Hub
    * All data routes through the hub
    * Validates client sending and performs encryption and decryption of payload as necessary
    * Initial analytics support for condition based alerting
    * Collects data and routes based on pub / sub model
    * Publishes to short term and long term data storage
* Messaging Services
    * Support for MQTT and JMS streams

## Manage
* Device Registry
    * Service which allows collection of devices and their metadata to be managed enabling device specific inquiries
* Lifecycle Management
    * Support for adding / removing devices
    * Initial device state management
* Notification services: Rule based
    * Alerts based on conditions set at the data point level
    * Enable publishing of alerts to subscribed applications







![](IoTOverview.jpg)

##Fleet Management Use Case
 This release of the IoT Platform enables a fleet manager to monitor vehicle health while operating a fleet of cars. This is achieved by the transfer of data about a potential problem with the vehicle through the Platform (cloud), to monitoring applications, then back to the driver as an alert. The alert then offers solutions to the problem.

For example:
1. Data about an event in a car (ex. temperature gauge shows overheating) is transferred via MQTT to an event data hub.
3. An event processing engine processes the data.
4. The data is published to an alert queue.
5. A notification application that is subscribed to the alert queue receives the alert.
7. The notification application sends an alert to the fleet support team.
8. The support team is then able to contact the driver and, with knowledge of the driver’s location relative to the nearest fleet outlet, direct the driver to go trade the car in for a new one.

