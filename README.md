# IoT Platform Overview

This Covisint IoT Platform release is built around Device Health Monitoring. Health Monitoring (HM) is the ability of the system to monitor key aspects of device functionality, and alert stakeholders (customers, users) to device behavior that could result in malfunction, and ultimately failure. This release will be followed by more releases based on more advanced use cases.

Health Monitoring provides proactive support by identifying and diagnosing potential faults and malfunctions, then contacting the affected stakeholders and directing them to solutions.

By monitoring the health of a connected device, Covisint's IoT Platform allows customers and users to mitigate and avoid operational risks, while increasing safety and reducing costs.

The diagram below shows how a complex connected product (thing) connects to the Covisint IoT Platform (cloud), then to an external operator/maintainer facing application to monitor the product’s health, or level of satisfactory functionality. The ecosystem operator/maintainer, or a notification application, then responds by sending an alert to the user, prompting attention to the connected product.

The technologies used to develop applications on this platform release include Java SDKs and ReST APIs (See APIs section).

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

