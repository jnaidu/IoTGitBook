
# Creating an IoT Solution


## Purpose

This section is intended to be a guide for solution developers and partners to develop their IoT solution on top of Covisint platform. It illustrates steps involved in developing an IoT solution by using an example use case. A sample request and response is provided to guide the user. For a complete list of APIs, refer to the API documentation at this link:

https://s-platform-covs.portal.stg.covapp.io/learn/iot/-/book/covisint-iot/api_reference_guide.html

## Prerequisite
The assumption is that the IoT solution instance already exists and the following application is built on top of this solution instance.

## Use Case: Rental Car Company

### Description
In this health monitoring use case, a Rental Car Company uses the Covisint IoT platform to proactively detect faults in the vehicle and provide support at the nearest service center. The car is equipped with a gateway that scans the engine fault code every minute and wirelessly transmits the code to Covisint IoT platform in the cloud. An application is subscribed to these engine fault codes from all the cars in the fleet. Whenever a fault is detected on the car, the application alerts the user to direct that car to the nearest service center. The following sections describe how to model a car, model an event and how to connect an application to receive all events on Covisint IoT platform.













