
# Use Case


## Purpose

This section is intended as a guide for solution developers and partners to develop their IoT solution on top of Covisint platform. It illustrates steps involved in developing an IoT solution by using example use cases. A sample request and response is provided to guide the user. For a complete list of APIs, refer to IoT Platform API Reference Guide.

## Pre-requisite
Assumption is that assumes that the prerequisite IoT solution or the realm already exists and the following solution is built on top of this realm.

## Use Case: Rental Car Company

### Description
This is a health monitoring use case where a Rental Car Company is using Covisint IoT platform to proactively detect faults in the vehicle and provide support at the nearest service center. The car is equipped with a gateway which can scan the engine fault code every minute and wirelessly transmits the code to Covisint IoT platform in the cloud. An application is subscribed to these engine fault codes from all the cars in the fleet. Whenever a fault is detect on the car, the application alerts the user to direct that car to the nearest service center. In the following sections, we describe how to model a car, model an event and how to connect an application to receive all events on Covisint IoT platform.

### Model The Device
The first step is to model the device or the car in IoT platform. A device template is used to represent a device of a particular kind and create multiple instances of it. A device template contains Attribute Type, Event Template and Command Template. In this case, the device template for a car will have Attribute Types and Event Templates. Since we don’t have any commands sent out to the car, Command Templates are not modeled. 
First, we will create a library of attributes that are required to represent a car. Next, we will create a library of events that the gateway on the car can send. Lastly, all the required attributes and events required to represent a car are used to create a device template.

#### POST: CREATE ATTRIBUTE TYPE
Create Attribute Type service will create an attribute in the IoT solution library. In this case, the basic attributes required to represent a car are: Manufacturer, Model, Year of Make, VIN number etc. In addition to this, we would need to model the engine fault code which is of our interest.

SAMPLE REQUEST
```
{
    "creator": "solutionImpl",
    "creatorAppId": "solutionImplApp",
    "realm": "IOT4RENTALCO",
    "name": "engine_fault",
    "description": [{ 
      "lang": "en_us", 
      "text": "engine fault code attribute."
    }],
    "type": "decimal",
    "defaultValue": 1.0,
    "isActive": true,
    "isFrozen": false
}

```

