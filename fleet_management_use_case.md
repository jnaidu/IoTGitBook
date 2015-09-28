# Fleet Management Use Case
 This release of the IoT Platform enables a fleet manager to monitor vehicle health while operating a fleet of cars. This is achieved by the transfer of data about a potential problem with the vehicle through the Platform (cloud), to monitoring applications, then back to the driver as an alert. The alert then offers solutions to the problem.

For example:
1. Data about an event in a car (ex. temperature gauge shows overheating) is transferred via MQTT to an event data hub.
3. An event processing engine processes the data.
4. The data is published to an alert queue.
5. A notification application that is subscribed to the alert queue receives the alert.
7. The notification application sends an alert to the fleet support team.
8. The support team is then able to contact the driver and, with knowledge of the driver’s location relative to the nearest fleet outlet, direct the driver to go trade the car in for a new one.