
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

SAMPLE REQUEST
```
{
    "creator": "solutionImpl",
    "creatorAppId": "solutionImplApp",
    "realm": "IOT4RENTALCO",
   "name”: “Engine fault detection policy”,
   "description": [{ 
      "lang": "en_US", 
      "text": "This policy detects engine fault greater than 10000"
   }],
  "condition": {
     "all": [ { “expr”: "greaterThan(f:engine_fault_code, v:decimal(10000))”
     }]
  }
}
```
SAMPLE RESPONSE
```
{
  "id": "da920956-c33c-4ef6-bb4e-6e106be6eb09",
  "version": "g2wAAAABaAJtAAAADCDMPMOaTHL2AAIpj2EBag==",
   "creator": "solutionImpl",
   "creatorAppId": "solutionImplApp",
  "creation": 1444763256834,
   "realm": "IOT4RENTALCO",
   "name”: “Engine fault detection policy”,
   "description": [{ 
      "lang": "en_US", 
      "text": "This policy detects engine fault greater than 10000"
   }],
  "condition": {
     "all": [ { “expr”: "greaterThan(f:engine_fault_code, v:decimal(10000))”
     }]
  }
}
```
#### POST: VALIDATE EVENT THRESHOLD POLICY
Event threshold policy can be validated by some sample values. The web service will return true if the value satisfied the policy or else false.

SAMPLE REQUEST
```
{
  “engine_fault_code”: 10200
}
```
SAMPLE RESPONSE
```
{
  “result”: true
}
```
### Create Event Stream For Device
In order to connect a device, we need to create a event stream for it. This event stream is a secure channel that allows the device to publish events and subscribe to commands. You will need the deviceId in order to create an event stream.

#### POST: CREATE STREAM
Create stream service will require information on the protocol used to connect to the device and all the security information.

SAMPLE REQUEST
```
{
    "creator": "solutionImpl",
    "creatorAppId": "solutionImplApp",
    "realm": "IOT4RENTALCO",
    "ownerId": "2bbb69c0-4551-4b91-b06b-c77a6865e44c",
    "name": [{
      "lang": "en_us", 
      "text": "Device Stream for Standard IoT Car – Instance 1"
    }],
    "streamType": "DEVICE",
    "protocolType": "MQTT",
    "protocolSecurityType": "BASIC",
    "ownerSecurityType": "BASIC",
    "payloadSecurityType": "ENCRYPTED",

    "streamConfiguration": {
       "pullingThreads": 1,
       "sleepTime": 10000,
       "quota": 1
    }

}
```
SAMPLE RESPONSE
```
{
    "id": "21a98b8e-745f-48ff-b4c5-fc2a2fa04149",
    "version": "g2wAAAABaAJtAAAADCDMPMOaSy7tAAE5SGEBag==",
    "creator": "solutionImpl",
    "creatorAppId": "solutionImplApp",
    "creation": 1441488610329,
    "realm": "IOT4RENTALCO",
    "ownerId": "2bbb69c0-4551-4b91-b06b-c77a6865e44c",
    "name": [{
      "lang": "en_us", 
      "text": "Standard IoT Car – Instance 1"
    }],
    "streamType": "DEVICE",
    "protocolType": "MQTT",
    "protocolSecurityType": "BASIC",
    "ownerSecurityType": "BASIC",
    "payloadSecurityType": "ENCRYPTED",
  "ownerId": "7d7289e5-a45b-42a1-a762-1a662756e715",
  "consumerTopic": "jms99b5cc42Q2179Q421cQb2faQ125810c7f8ee",
  "producerTopic": "jms97acaf26Q5976Q4b7cQ9a71Q1014232afd0a",
  "messageProcessorTopic": "9d7d813c-24c0-47ec-8534-d0fc1d028f2b",
  "streamConfiguration": {
    "logMode": "INFO",
    "pullingThreads": 5,
    "sleepTime": 60,
    "quota": 10
  },
  "protocolSecurityAttributes": [
    {
      "name": "clientId",
      "value": "7d02da38d2db4c93"
    },
    {
      "name": "password",
      "value": "in4k3lkmlk34"
    },
{
      "name": "port",
      "value": "6849"
    },
{
      "name": "host",
      "value": "10.96.2.116"
    },
{
      "name": "username",
      "value": "3kj4n4kj3n"
    }
  ],
  "payloadSecurityAttributes": [
    {
      "name": "consumerPrivateKey",
      "value": "MIIBTAIBADCCASwGByqGSM44BAEwggEfAoGBAP1/U4EddRIpUt9KnC7s5Of2EbdSPO9EAMMeP4C2USZpRV1AIlH7WT2NWPq/xfW6MPbLm1Vs14E7gB00b/JmYLdrmVClpJ+f6AR7ECLCT7up1/63xhv4O1fnxqimFQ8E+4P208UewwI1VBNaFpEy9nXzrith1yrv8iIDGZ3RSAHHAhUAl2BQjxUjC8yykrmCouuEC/BYHPUCgYEA9+GghdabPd7LvKtcNrhXuXmUr7v6OuqC+VdMCz0HgmdRWVeOutRZT+ZxBxCBgLRJFnEj6EwoFhO3zwkyjMim4TwWeotUfI0o4KOuHiuzpnWRbqN/C/ohNWLx+2J6ASQ7zKTxvqhRkImog9/hWuWfBpKLZl6Ae1UlZAFMO/7PSSoEFwIVAIjZ0t/tMemIc5sWThfv7AXzqXUV"
    },
    {
      "name": "producerPublicKey",
      "value": "MIIBtzCCASwGByqGSM44BAEwggEfAoGBAP1/U4EddRIpUt9KnC7s5Of2EbdSPO9EAMMeP4C2USZpRV1AIlH7WT2NWPq/xfW6MPbLm1Vs14E7gB00b/JmYLdrmVClpJ+f6AR7ECLCT7up1/63xhv4O1fnxqimFQ8E+4P208UewwI1VBNaFpEy9nXzrith1yrv8iIDGZ3RSAHHAhUAl2BQjxUjC8yykrmCouuEC/BYHPUCgYEA9+GghdabPd7LvKtcNrhXuXmUr7v6OuqC+VdMCz0HgmdRWVeOutRZT+ZxBxCBgLRJFnEj6EwoFhO3zwkyjMim4TwWeotUfI0o4KOuHiuzpnWRbqN/C/ohNWLx+2J6ASQ7zKTxvqhRkImog9/hWuWfBpKLZl6Ae1UlZAFMO/7PSSoDgYQAAoGADTl8YRZw6/79kehg6r6xZ/9yzqm05cAeIrh/VROlQc1U/5BCL3eglHjjArZ2hghje4WZ0QqprzJf/KlL3zHsEb+bmOf00gbIgsl0G+SXNiOcIFWVdYWPrU8XUCtu8EikdNDmDCjJhzU4+XZpxtkQtZJeQag+AlXefzBxCEkwufg="
    },
    {
      "name": "producerPrivateKey",
      "value": "MIIBSwIBADCCASwGByqGSM44BAEwggEfAoGBAP1/U4EddRIpUt9KnC7s5Of2EbdSPO9EAMMeP4C2USZpRV1AIlH7WT2NWPq/xfW6MPbLm1Vs14E7gB00b/JmYLdrmVClpJ+f6AR7ECLCT7up1/63xhv4O1fnxqimFQ8E+4P208UewwI1VBNaFpEy9nXzrith1yrv8iIDGZ3RSAHHAhUAl2BQjxUjC8yykrmCouuEC/BYHPUCgYEA9+GghdabPd7LvKtcNrhXuXmUr7v6OuqC+VdMCz0HgmdRWVeOutRZT+ZxBxCBgLRJFnEj6EwoFhO3zwkyjMim4TwWeotUfI0o4KOuHiuzpnWRbqN/C/ohNWLx+2J6ASQ7zKTxvqhRkImog9/hWuWfBpKLZl6Ae1UlZAFMO/7PSSoEFgIUWeAidocfQHqZ8Dvr7XUl8/ZpzHI="
    },
    {
      "name": "consumerPublicKey",
      "value": "MIIBuDCCASwGByqGSM44BAEwggEfAoGBAP1/U4EddRIpUt9KnC7s5Of2EbdSPO9EAMMeP4C2USZpRV1AIlH7WT2NWPq/xfW6MPbLm1Vs14E7gB00b/JmYLdrmVClpJ+f6AR7ECLCT7up1/63xhv4O1fnxqimFQ8E+4P208UewwI1VBNaFpEy9nXzrith1yrv8iIDGZ3RSAHHAhUAl2BQjxUjC8yykrmCouuEC/BYHPUCgYEA9+GghdabPd7LvKtcNrhXuXmUr7v6OuqC+VdMCz0HgmdRWVeOutRZT+ZxBxCBgLRJFnEj6EwoFhO3zwkyjMim4TwWeotUfI0o4KOuHiuzpnWRbqN/C/ohNWLx+2J6ASQ7zKTxvqhRkImog9/hWuWfBpKLZl6Ae1UlZAFMO/7PSSoDgYUAAoGBAKOrHnrPOMXe0Qz4F2DMcGELxaT+qgoVvdu+73alqg+vgX4IepFi8nKDroj+aqDtgSG+WhVMsvYleeoFZFCsVwD1gY5GSL8EyExdOAg0Nf/MTA8Dm8vdbK8UOVGN3o6dwvnRolsJ54MGT/93girk0mOwWWt3De9bDu+sE8tZRMcI"
    }
  ],
  "ownerSecurityAttributes": [
    {
      "name": "password",
      "value": "ea9fbdd3-b26f-4b2c-af60-f067d66e4bf2"
    },
    {
      "name": "salt",
      "value": "1f8401b2-36f1-455c-b531-2d099ab6fad4"
    },
    {
      "name": "passwordHash",
      "value": "d6fa153b9677008e3818f9f85e9f4c08"
    }
  ]
}
```
### Create Application
The rental car company’s application which will be monitoring the health of all the vehicles needs to be created in this IoT solution.

#### POST: CREATE APPLICATION
Create an application inside IoT solution. A unique applicationId for the application is returned.

SAMPLE REQUEST
```
{
    "creator": "solutionImpl",
    "creatorAppId": "solutionImplApp",
    "realm": "IOT4RENTALCO",
    "name": [{
      "lang": "en_us", 
      "text": "Car Health Monitor App"
    }],
    "description": [{ 
      "lang": "en_us", 
      "text": "An external partner application to monitor faults in car."
    }]
}
```
SAMPLE RESPONSE
```
{
    "id": "65eb9268-b0d1-4f75-a855-71eac716a351",
    "version": "0",
    "creator": "solutionImpl",
    "creatorAppId": "solutionImplApp",
    "creation": 1441377362856,
    "realm": "IOT4RENTALCO",
    "name": [{
      "lang": "en_us", 
      "text": "Car Health Monitor App"
    }],
    "description": [{ 
      "lang": "en_us", 
      "text": "An external partner application to monitor faults in car."
    }]
}
```
### Create Event Stream For Application
Create an event stream to connect an application. This event stream is a secure channel that allows the application to publish commands and subscribe to events. This service will require the applicationId in order to create an event stream.

#### POST: CREATE STREAM
Create an application stream using the applicationId and the security parameters.

SAMPLE REQUEST
```
{
    "creator": "solutionImpl",
    "creatorAppId": "solutionImplApp",
    "realm": "IOT4RENTALCO",
    "ownerId": "d6dc2178-f75b-4f7f-b314-22f3da2908d5",
    "name": [{
      "lang": "en_us", 
      "text": "Application Stream for Car Fault Monitor App"
    }],
    "streamType": "APPLICATION",
    "protocolType": "JMS",
    "protocolSecurityType": "BASIC",
    "ownerSecurityType": "BASIC",
    "payloadSecurityType": "ENCRYPTED",

    "streamConfiguration": {
       "pullingThreads": 5,
       "sleepTime": 60,
       "quota": 10
    }

}
```
SAMPLE RESPONSE
```
{
    "id": "c109ea32-9786-4f57-9668-12a4d96aa644",
    "version": "g2wAAAABaAJtAAAADCDMPMOaSy7tAAE5SGEBag==",
    "creator": "solutionImpl",
    "creatorAppId": "solutionImplApp",
    "creation": 1441799941388,
    "realm": "IOT4RENTALCO",
    "ownerId": "d6dc2178-f75b-4f7f-b314-22f3da2908d5",
    "name": [{
      "lang": "en_us", 
      "text": "Application Stream for Car Fault Monitor App"
    }],
    "streamType": "APPLICATION",
    "protocolType": "JMS",
    "protocolSecurityType": "BASIC",
    "ownerSecurityType": "BASIC",
    "payloadSecurityType": "ENCRYPTED",
  "consumerTopic": "jmscb82a5b7Q0a33Q43b8Qbfc2Q017a5e8c820f",
  "producerTopic": "jmsef7bdfc3Qf563Q44eeQ9e7fQd35e8efea80c",
  "alertConsumerTopic": "jms186d086dQ190aQ4b80Qaf73Q263ef77b4d90",
  "messageProcessorTopic": "c79c8402-fc3d-419e-bd77-ce1e4b5c2284",
  "streamConfiguration": {
    "logMode": "INFO",
    "pullingThreads": 5,
    "sleepTime": 60,
    "quota": 10
  },
  "protocolSecurityAttributes": [
    {
      "name": "accountId",
      "value": "a233b0a7-033e-49e6-a7a5-d49e748280f1"
    },
    {
      "name": "password",
      "value": "admin"
    },
    {
      "name": "jmsProvider",
      "value": "CovisintJMSProvider"
    },
    {
      "name": "port",
      "value": "6849"
    },
    {
      "name": "connectionFactory",
      "value": "CovisintQueueConnectionFactory"
    },
    {
      "name": "host",
      "value": "10.96.2.116"
    },
    {
      "name": "brokerName",
      "value": "Broker #1"
    },
    {
      "name": "providerURL",
      "value": "wmjmsnaming://Broker #1@10.96.2.116:6849/CovisintJMSProvider"
    },
    {
      "name": "initialContextFactory",
      "value": "com.webmethods.jms.naming.WmJmsNamingCtxFactory"
    },
    {
      "name": "username",
      "value": "admin"
    }
  ],
  "payloadSecurityAttributes": [
    {
      "name": "consumerPrivateKey",
      "value": "MIIBSwIBADCCASwGByqGSM44BAEwggEfAoGBAP1/U4EddRIpUt9KnC7s5Of2EbdSPO9EAMMeP4C2USZpRV1AIlH7WT2NWPq/xfW6MPbLm1Vs14E7gB00b/JmYLdrmVClpJ+f6AR7ECLCT7up1/63xhv4O1fnxqimFQ8E+4P208UewwI1VBNaFpEy9nXzrith1yrv8iIDGZ3RSAHHAhUAl2BQjxUjC8yykrmCouuEC/BYHPUCgYEA9+GghdabPd7LvKtcNrhXuXmUr7v6OuqC+VdMCz0HgmdRWVeOutRZT+ZxBxCBgLRJFnEj6EwoFhO3zwkyjMim4TwWeotUfI0o4KOuHiuzpnWRbqN/C/ohNWLx+2J6ASQ7zKTxvqhRkImog9/hWuWfBpKLZl6Ae1UlZAFMO/7PSSoEFgIULX67QTUsRDuQH3sIGDani7YiVvo="
    },
    {
      "name": "producerPublicKey",
      "value": "MIIBtzCCASwGByqGSM44BAEwggEfAoGBAP1/U4EddRIpUt9KnC7s5Of2EbdSPO9EAMMeP4C2USZpRV1AIlH7WT2NWPq/xfW6MPbLm1Vs14E7gB00b/JmYLdrmVClpJ+f6AR7ECLCT7up1/63xhv4O1fnxqimFQ8E+4P208UewwI1VBNaFpEy9nXzrith1yrv8iIDGZ3RSAHHAhUAl2BQjxUjC8yykrmCouuEC/BYHPUCgYEA9+GghdabPd7LvKtcNrhXuXmUr7v6OuqC+VdMCz0HgmdRWVeOutRZT+ZxBxCBgLRJFnEj6EwoFhO3zwkyjMim4TwWeotUfI0o4KOuHiuzpnWRbqN/C/ohNWLx+2J6ASQ7zKTxvqhRkImog9/hWuWfBpKLZl6Ae1UlZAFMO/7PSSoDgYQAAoGAXkkg/xc86SKNcEsfduvWFJhzQP/1VCjwLR3U0BSSR10SLodCsyHJtVtH8oqSIYm0n56NKs4aSXh7Lz7gWbBvTfQWXy3wi0bk1X4SmOf5ucFduvQyxp2gb8+UXFq68PblWJpzfUSTOXMmYUvHNb2krsh9GAz7A8X+SVnLMDNcdaE="
    },
    {
      "name": "producerPrivateKey",
      "value": "MIIBSwIBADCCASwGByqGSM44BAEwggEfAoGBAP1/U4EddRIpUt9KnC7s5Of2EbdSPO9EAMMeP4C2USZpRV1AIlH7WT2NWPq/xfW6MPbLm1Vs14E7gB00b/JmYLdrmVClpJ+f6AR7ECLCT7up1/63xhv4O1fnxqimFQ8E+4P208UewwI1VBNaFpEy9nXzrith1yrv8iIDGZ3RSAHHAhUAl2BQjxUjC8yykrmCouuEC/BYHPUCgYEA9+GghdabPd7LvKtcNrhXuXmUr7v6OuqC+VdMCz0HgmdRWVeOutRZT+ZxBxCBgLRJFnEj6EwoFhO3zwkyjMim4TwWeotUfI0o4KOuHiuzpnWRbqN/C/ohNWLx+2J6ASQ7zKTxvqhRkImog9/hWuWfBpKLZl6Ae1UlZAFMO/7PSSoEFgIUHZ8sk17MfIlrevtMyEVrN/qkbqk="
    },
    {
      "name": "consumerPublicKey",
      "value": "MIIBtzCCASwGByqGSM44BAEwggEfAoGBAP1/U4EddRIpUt9KnC7s5Of2EbdSPO9EAMMeP4C2USZpRV1AIlH7WT2NWPq/xfW6MPbLm1Vs14E7gB00b/JmYLdrmVClpJ+f6AR7ECLCT7up1/63xhv4O1fnxqimFQ8E+4P208UewwI1VBNaFpEy9nXzrith1yrv8iIDGZ3RSAHHAhUAl2BQjxUjC8yykrmCouuEC/BYHPUCgYEA9+GghdabPd7LvKtcNrhXuXmUr7v6OuqC+VdMCz0HgmdRWVeOutRZT+ZxBxCBgLRJFnEj6EwoFhO3zwkyjMim4TwWeotUfI0o4KOuHiuzpnWRbqN/C/ohNWLx+2J6ASQ7zKTxvqhRkImog9/hWuWfBpKLZl6Ae1UlZAFMO/7PSSoDgYQAAoGANQ/I9UyX0MZFAd7kYpLt2M1o864PD3qceWCvhka1a0iABgfIvp/420Xk4/CkfvjT7y8ChO+EUZjnAp8thrlkg8py/1wAdy5DID5dc9XerT/J6g1wrSd+4zBztm7gvEuj73UB9/0J71Ybxi2vXgBKyOYD6BH1erPLUswiQ0Big44="
    }
  ],
  "ownerSecurityAttributes": [
    {
      "name": "password",
      "value": "29360826-7a1f-48a9-9967-08feb161c456"
    },
    {
      "name": "salt",
      "value": "3da95573-b3e7-4cba-a18a-2cd6b9d91344"
    },
    {
      "name": "passwordHash",
      "value": "a154c8349ae2c6f66217b36ad685918d"
    }
  ]
}
```
### Subscribe To Events
After creating event streams for the device and the application, we need to specify how to route events. This is done by subscribing to appropriate stream and routing topic.

#### POST: CREATE ROUTE
This service is used to create a route between source and destination topics. With this message, any event sent by the device should be received by the application.

SAMPLE REQUEST
```
{
    "creator": "solutionImpl",
    "creatorAppId": "solutionImplApp",
    "realm": "IOT4RENTALCO",
    "routeType": "EVENT",
    "streamId": "a724dfc1-38a5-45c7-b609-8eefb66f65c8",
    "routeSourceId": "3fb1ad85-edc3-4586-8fc0-c564328e6a45",
    "routingTopic": "90f71720-519b-4b36-b7ae-6c38eb956c7d"
}
```
SAMPLE RESPONSE
```
  {
    "id": "1766682f-3d7c-47a7-8f9f-468bef155b4d",
    "version": "g2wAAAABaAJtAAAADCDMPMOaTGC2AAE5jWEBag==",
    "creator": "solutionImpl",
    "creatorAppId": "solutionImplApp",
    "realm": "IOT4RENTALCO",
    "creation": 1441819423946,
    "routeSourceId": "5acb7b8e017x",
    "routeType": "EVENT",
    "streamId": "stream01",
    "routingTopic": "RoutingTopic01"
  }
```
### Configure The De