
# Use Case


## Purpose

This section is intended as a guide for solution developers and partners to develop their IoT solution on top of Covisint platform. It illustrates steps involved in developing an IoT solution by using example use cases. A sample request and response is provided to guide the user. For a complete list of APIs, refer to IoT Platform API Reference Guide.

## Pre-requisite
Assumption is that assumes that the prerequisite IoT solution or the realm already exists and the following solution is built on top of this realm.

## Use Case: Rental Car Company

### Description
This is a health monitoring use case where a Rental Car Company is using Covisint IoT platform to proactively detect faults in the vehicle and provide support at the nearest service center. The car is equipped with a gateway which can scan the engine fault code every minute and wirelessly transmits the code to Covisint IoT platform in the cloud. An application is subscribed to these engine fault codes from all the cars in the fleet. Whenever a fault is detect on the car, the application alerts the user to direct that car to the nearest service center. In the following sections, we describe how to model a car, model an event and how to connect an application to receive all events on Covisint IoT platform.