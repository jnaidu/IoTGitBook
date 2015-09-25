
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

SAMPLE RESPONSE
```
{
    "id": "65eb9268-b0d1-4f75-a855-71eac716a351",
    "version": 0,
    "creator": "solutionImpl",
    "creatorAppId": "solutionImplApp",
    "creation": 1441377362856,
    "realm": "IOT4RENTALCO",
    "name": "engine_fault",
    "description": [
      {
        "lang": "en_us",
        "text": "engine fault code attribute."
      }
    ],
    "type": "decimal",
    "defaultValue": 1.0,
    "isActive": true,
    "isFrozen": false
}
```
#### POST: CREATE EVENT TEMPLATE
Create Event Template service will create an event in the IoT solution library. The car can send engine fault code events every minute. This is captured in the following request.

SAMPLE REQUEST
```
{
    "creator": "solutionImpl",
    "creatorAppId": "solutionImplApp",
    "realm": "IOT4RENTALCO",
    "name": "engine fault event",
    "description": [{ 
      "lang": "en_us", 
      "text": "An event that sends engine fault code."
    }],
    "eventFields": [{
      "name": "engine_fault_code",
      "type": "decimal"
    }]   
    "isActive": true,
    "tags": [ "car", "engine", "fault" ]
}
```
SAMPLE RESPONSE
```
{
    "id": "48c713f8-5b69-49f0-afb1-e5618ac9bae9",
    "version": 0,
    "creator": "solutionImpl",
    "creatorAppId": "solutionImplApp",
    "realm": "IOT4RENTALCO",
    "creation": 1441377895153,
    "name": "engine_fault_event",
    "description": [{ 
      "lang": "en_us", 
      "text": "An event that sends engine fault code."
    }],
    "eventFields": [{
      "name": "engine_fault_code",
      "type": "decimal"
    }]   
    "isActive": true,
    "tags": [ "car", "engine", "fault" ]
}
```
#### POST: BIND EVENT FIELD TO ATTRIBUTE
Bind event field to attribute so that the attribute is updated with the latest value in the event. The bound attribute must have the same data type as the field. Using the eventID and the attributeID obtained in the previous requests, we will create a binding between the event and the attribute using this web service.

URI: /eventTemplates/{{eventID}}/tasks/bindEventField?attributeTypeId={{attributeTypeId}}

ATTRIBUTES:

| Parameter | Type | Required? | Description |
| -- | -- | -- | -- |
| eventId | String | True | Id of the event which needs to be bound to an attribute type |
| attributeTypeId | String | True | Id of the attribute type |

#### POST: CREATE DEVICE TEMPLATE
Create Device Template will create a template with all the listed attributes, events and commands. In the following sample, we create a device template of a car with engine fault code with the attribute id and the event id. By default the device template is not active unless specified in the request.

SAMPLE REQUEST
```
{
    "creator": "solutionImpl",
    "creatorAppId": "solutionImplApp",
    "realm": "IOT4RENTALCO",
    "name": [{
      "lang": "en_us", 
      "text": "Standard IoT Car"
    }],
    "description": [{ 
      "lang": "en_us", 
      "text": "A standard IoT car that can send engine fault code."
    }],
    "attributeTypes": [ "65eb9268-b0d1-4f75-a855-71eac716a351" ],
    "eventTemplates": [ "48c713f8-5b69-49f0-afb1-e5618ac9bae9" ]
}
```
SAMPLE RESPONSE
```
{
    "id": "4efa6ce8-5112-4aaf-92be-bde636c3488c",
    "version": "1",
    "creator": "solutionImpl",
    "creatorAppId": "solutionImplApp",
    "creation": 1441488130828,
    "realm": "IOT4RENTALCO",
    "name": [{
      "lang": "en_us", 
      "text": "Standard IoT Car"
    }],
    "description": [{ 
      "lang": "en_us", 
      "text": "A standard IoT car that can send engine fault code."
    }],
    "attributeTypes": [ "65eb9268-b0d1-4f75-a855-71eac716a351" ],
    "eventTemplates": [ "48c713f8-5b69-49f0-afb1-e5618ac9bae9" ],
    "isActive": false
}
```
#### POST: ACTIVATE DEVICE TEMPLATE
Device templates needs to be active before using it to create devices. A solution developer can activate a device template with this web service.

URI: /deviceTemplates/{{deviceTemplateId}}/tasks/activate

ATTRIBUTES:

| Parameter | Type | Required? | Description |
| -- | -- | -- | -- |
| deviceTemplateId | String | True | Id of the device template to activate |

### Create An Instance Of The Device From Template
From a device template, we can create multiple instances of a device. In this case, we create an instance of a car from a device template and activate the device in IoT platform.

#### POST: CREATE DEVICE
Create device service creates an instance of a device for the given deviceTemplateId. The device will inherit the default attributes defined in the device template. This service returns a deviceId which acts as a handle for all other web service calls. However, the device is not yet active to be used.

ATTRIBUTES:

| Parameter | Type | Required? | Description |
| -- | -- | -- | -- |
| deviceTemplateId | String | True | Id of the device template |

SAMPLE REQUEST
```
{
    "creator": "solutionImpl",
    "creatorAppId": "solutionImplApp",
    "realm": "IOT4RENTALCO",
    "name": [{
      "lang": "en_us", 
      "text": "Standard IoT Car – Instance 1"
    }],
    "description": [{ 
      "lang": "en_us", 
      "text": "A standard IoT car that can send engine fault code."
    }]
}
```
SAMPLE RESPONSE
```
{
    "id": "7d7289e5-a45b-42a1-a762-1a662756e715",
    "version": "1",
    "creator": "solutionImpl",
    "creatorAppId": "solutionImplApp",
    "creation": 1441588430324,
    "realm": "IOT4RENTALCO",
    "name": [{
      "lang": "en_us", 
      "text": "Standard IoT Car – Instance 1"
    }],
    "description": [{ 
      "lang": "en_us", 
      "text": "A standard IoT car that can send engine fault code."
    }],
    "parentDeviceTemplateId": "4efa6ce8-5112-4aaf-92be-bde636c3488c",
    "attributes": {
      "standard": [{
        "attributeTypeId": "65eb9268-b0d1-4f75-a855-71eac716a351",
        "value": 1
      }]
    },
    "observableEvents": [
      "48c713f8-5b69-49f0-afb1-e5618ac9bae9"
    ],
    "isActive": false
}
```
#### PUT: UPDATE DEVICE
Update device service can be used to update the attributes, events or commands of the device. This service can be used to change the default values as well. In the example below, we will update the default value of the engine fault code to “10000.0”.

SAMPLE REQUEST
```
{
    "creator": "solutionImpl",
    "creatorAppId": "solutionImplApp",
    "realm": "IOT4RENTALCO",
    "name": [{
      "lang": "en_us", 
      "text": "Standard IoT Car – Instance 1"
    }],
    "description": [{ 
      "lang": "en_us", 
      "text": "A standard IoT car that can send engine fault code."
    }],
    "attributes": {
      "standard": [{
        "attributeTypeId": "65eb9268-b0d1-4f75-a855-71eac716a351",
        "value": 10000.0
      }]
     },
     "observableEvents": [
       "48c713f8-5b69-49f0-afb1-e5618ac9bae9"
      ],
      "isActive": false
}
```
SAMPLE RESPONSE
```
{
    "id": "7d7289e5-a45b-42a1-a762-1a662756e715",
    "version": "1",
    "creator": "solutionImpl",
    "creatorAppId": "solutionImplApp",
    "creation": 1441588430324,
    "realm": "IOT4RENTALCO",
    "name": [{
      "lang": "en_us", 
      "text": "Standard IoT Car – Instance 1"
    }],
    "description": [{ 
      "lang": "en_us", 
      "text": "A standard IoT car that can send engine fault code."
    }],
    "parentDeviceTemplateId": "4efa6ce8-5112-4aaf-92be-bde636c3488c",
    "attributes": {
      "standard": [{
        "attributeTypeId": "65eb9268-b0d1-4f75-a855-71eac716a351",
        "value": 10000.0
      }]
     },
     "observableEvents": [
       "48c713f8-5b69-49f0-afb1-e5618ac9bae9"
      ],
     "isActive": false
}
```
#### POST: ACTIVATE DEVICE
A device needs to be activated before use. Device can be activated in an update command or by this web service.

URI: /devices/{deviceId}/tasks/activate

ATTRIBUTES:

| Parameter | Type | Required? | Description |
| -- | -- | -- | -- |
| deviceId | String | True | Id of the device that needs to be activated |

### Create Event Source And Threshold Policy For The Device
In order to receive an event from the device, we will have to create an event source with the deviceId and the eventTemplateId.

#### POST: CREATE EVENT SOURCE
Create event source service will create an event source on IoT platform. Event source is a group of events. Events can be grouped based on all the devices that have the particular event or specific devices that have the particular event. In the following example, we will create an engine fault event source for the specific device which we created.

SAMPLE REQUEST
```
{
    "creator": "solutionImpl",
    "creatorAppId": "solutionImplApp",
    "realm": "IOT4RENTALCO",
   "name": [{ 
      "lang": "en_US", 
      "text": "Engine fault event source"
    }],
   "description": [{ 
      "lang": "en_US", 
      "text": "A standard engine fault event source."
   }],
  "sourceDevices": [{
     "deviceId": [ "23f6db35-3416-4058-97a7-2e50e8b152e2" ],
     "eventTemplateId": [ "48c713f8-5b69-49f0-afb1-e5618ac9bae9" ]
   }]
}
```
SAMPLE RESPONSE
```
{
  "id": "231034ca-96ee-48bc-9937-aa964d8c9813",
  "version": "g2wAAAABaAJtAAAADCDMPMOaTHL2AAIpj2EBag==",
    "creator": "solutionImpl",
    "creatorAppId": "solutionImplApp",
  "creation": 1442863150834,
   "realm": "IOT4RENTALCO",
   "name": [{ 
      "lang": "en_US", 
      "text": "Engine fault event source"
    }],
   "description": [{ 
      "lang": "en_US", 
      "text": "A standard engine fault event source."
   }],
  "sourceDevices": [{
     "deviceId": [ "23f6db35-3416-4058-97a7-2e50e8b152e2" ],
     "eventTemplateId": [ "48c713f8-5b69-49f0-afb1-e5618ac9bae9" ]
   }]
}
```
#### POST: CREATE EVENT THRESHOLD POLICY
On the incoming events from the device, we can attach policies to detect if a certain condition has met. In the rental car usecase, we would like to detect if the engine fault code is greater than default value 10000.

