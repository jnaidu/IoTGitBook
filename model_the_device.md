# Model The Device
The first step to creating an IoT solution in a health monitoring use case is to model the device, or the car, in IoT platform. A device template is used to represent a device of a particular kind and create multiple instances of it. A device template contains Attribute Type, Event Template and Command Template. In this case, the device template for a car will have Attribute Types and Event Templates. Since no commands sent out to the car, Command Templates are not modeled. 

First, create the library of attributes that are required to represent a car. Second, create a library of events that the gateway on the car can send. Lastly, all the required attributes and events required to represent a car are used to create a device template.

## POST: CREATE ATTRIBUTE TYPE
Create Attribute Type service will create an attribute in the IoT solution library. In this case, the basic attributes required to represent a car are: Manufacturer, Model, Year of Make, VIN number etc. In addition to this, we would need to model the engine fault code which is of our interest.

SAMPLE REQUEST
```
{
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
    "creation": 1441377362856,
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
## POST: CREATE EVENT TEMPLATE
Create Event Template service will create an event in the IoT solution library. The car can send engine fault code events every minute. This is captured in the following request.

SAMPLE REQUEST
```
{
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
## POST: BIND EVENT FIELD TO ATTRIBUTE
Bind event field to attribute so that the attribute is updated with the latest value in the event. The bound attribute must have the same data type as the field. Using the eventID and the attributeID obtained in the previous requests, we will create a binding between the event and the attribute using this web service.

URI: /eventTemplates/{{eventID}}/tasks/bindEventField?attributeTypeId={{attributeTypeId}}

ATTRIBUTES:

| Parameter | Type | Required? | Description |
| -- | -- | -- | -- |
| eventId | String | True | Id of the event which needs to be bound to an attribute type |
| attributeTypeId | String | True | Id of the attribute type |

## POST: CREATE DEVICE TEMPLATE
Create Device Template will create a template with all the listed attributes, events and commands. In the following sample, we create a device template of a car with engine fault code with the attribute id and the event id. By default the device template is not active unless specified in the request.

SAMPLE REQUEST
```
{
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
    "creation": 1441488130828,
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
## POST: ACTIVATE DEVICE TEMPLATE
Device templates needs to be active before using it to create devices. A solution developer can activate a device template with this web service.

URI: /deviceTemplates/{{deviceTemplateId}}/tasks/activate

ATTRIBUTES:

| Parameter | Type | Required? | Description |
| -- | -- | -- | -- |
| deviceTemplateId | String | True | Id of the device template to activate |