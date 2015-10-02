# Create an Instance of the Device from Template
From a device template, we can create multiple instances of a device. In this case, we create an instance of a car from a device template and activate the device in IoT platform.

## POST: CREATE DEVICE
Create device service creates an instance of a device for the given deviceTemplateId. The device will inherit the default attributes defined in the device template. This service returns a deviceId which acts as a handle for all other web service calls. However, the device is not yet active to be used.

ATTRIBUTES:

| Parameter | Type | Required? | Description |
| -- | -- | -- | -- |
| deviceTemplateId | String | True | Id of the device template |

SAMPLE REQUEST
```
{
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
    "creation": 1441588430324,
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
## PUT: UPDATE DEVICE
Update device service can be used to update the attributes, events or commands of the device. This service can be used to change the default values as well. In the example below, we will update the default value of the engine fault code to “10000.0”.

SAMPLE REQUEST
```
{



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
    "creation": 1441588430324,
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
## POST: ACTIVATE DEVICE
A device needs to be activated before use. Device can be activated in an update command or by this web service.

URI: /devices/{deviceId}/tasks/activate

ATTRIBUTES:

| Parameter | Type | Required? | Description |
| -- | -- | -- | -- |
| deviceId | String | True | Id of the device that needs to be activated |