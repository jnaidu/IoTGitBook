# IoT Platform Overview

This release of the Covisint Internet of Things Platform introduces features that offer full support for the fundamental IoT use case of monitoring the health of connected products. In this use case, one or more monitoring applications that are subscribed to specific queues receive data about an ecosystem of connected products via the IoT platform. Upcoming releases will add features to fully support more complex IoT use cases for connected products.

The current release includes features that support core IoT capabilities, briefly described below. Leveraging the comprehensive IoT Core, a developer is able to implement more complex IoT scenarios which include remote control of products and the orchestration of external stakeholders to data and commands, to name a few.

## Secure and Control
These features help protect and govern identity, data, connectivity, commands, and relationships among people, systems, and devices. Identity Provisioning provides secure device registration and token (JWT) issuance. Identity Relationship Management allows definition of groups of people, devices, organizations, and other groups. It also provides a flexible group attribute definition model. Identity Authentication includes device authentication (JWT token). Secure Data Transport allows encryption of all network and payload traffic between cloud services, gateways and devices; logs all CRUD operations in a persistent log for auditing and compliance reporting; allows third party applications to retrieve and analyze audit records; and allows the ability to restrict who can access what data, based on event routing.

## Connect
These features support creating and managing connectivity and data among people, systems, and devices. Gateway Services allow partners to integrate their own gateways or third party gateways. The Event Data Hub routes all data from the device to the application; validates client sending and performs encryption and decryption of payload as necessary; provides initial analytics support for condition based alerting; collects data and routes based on pub-sub model; and publishes to short term and long term data storage. Messaging Services include support for MQTT and JMS streams.

## Manage
These features help coordinate and orchestrate the lifecycles of people, systems, and devices. Lifecycle Management provides support for adding and removing devices, and initial device state management. Notification services (rule-based) include alerts based on conditions set at the data point level, and enable publishing of alerts to subscribed applications.

## Build
These features enable the creation of applications and integrations to harvest value from interactions among connected people, systems, and devices. API Services (extensive microservices API) include device definition (data points, attributes, commands, identity), device management, connectivity gateway-platform (MQTT, JMS), ecosystem management (groups), and pub-sub of applications to ecosystem events.

The technologies used to develop applications on this platform release include Java SDKs and REST APIs (See APIs sections).

This Health Monitoring release provides proactive support by identifying and diagnosing potential faults and malfunctions, then contacting the affected stakeholders and directing them to solutions. By monitoring the health of a connected device, Covisint's IoT Platform allows customers and users to mitigate and avoid operational risks, while increasing safety and reducing costs.
The technologies used to develop applications on this platform release include Java SDKs and REST APIs (See APIs sections).

