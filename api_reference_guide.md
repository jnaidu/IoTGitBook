# IoT APIs
This document captures all the endpoints available in September Release and captures sample request and response for the APIs.

## AttributeType
Attribute Type captures device properties in a template. A library of attribute types can be created inside and IoT solution and used in various device templates. Following operations are available on attribute type.

### POST: CREATE ATTRIBUTE TYPE
Create a new attribute type template.

URI: /attributeTypes

SAMPLE REQUEST
```
{
    "creator": "referenceImpl",
    "creatorAppId": "referenceImplApp",
    "realm": "IOTPAASQA_ITEST",
    "name": "temperature",
    "description": [{ 
      "lang": "en_us", 
      "text": "temperature attribute."
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
    "creator": "referenceImpl",
    "creatorAppId": "referenceImplApp",
    "creation": 1441377362856,
    "realm": "IOTPAASQA_ITEST",
    "name": "temperature",
    "description": [
      {
        "lang": "en_us",
        "text": "temperature attribute."
      }
    ],
    "type": "decimal",
    "isActive": false,
    "defaultValue": 1
}
```
### GET: SEARCH ATTRIBUTE TYPE
This method is used search attribute types based on the given filter parameters.

URI: /attributeTypes

SAMPLE REQUEST
```
{
    "id": "65eb9268-b0d1-4f75-a855-71eac716a351",
    "name": "temperature",
}
```
SAMPLE RESPONSE
```
{
    "id": "65eb9268-b0d1-4f75-a855-71eac716a351",
    "version": 0,
    "creator": "referenceImpl",
    "creatorAppId": "referenceImplApp",
    "creation": 1441377362856,
    "realm": "IOTPAASQA_ITEST",
    "name": "temperature",
    "description": [
      {
        "lang": "en_us",
        "text": "temperature attribute."
      }
    ],
    "type": "decimal",
    "isActive": false,
    "defaultValue": 1
}
```
### GET: GET ATTRIBUTE TYPE
This method is used to retrieve a particular attribute type.

URI: /attributeTypes/{attributeTypeId}

SAMPLE REQUEST
```
Accept	application/vnd.com.covisint.platform.stream.v1+json
Content-Type 	application/vnd.com.covisint.platform.stream.v1+json
x-realm	 IOTPAASQA_ITEST
x-requestor	 referenceImpl
x-requestor-app	 referenceImplApp
```
SAMPLE RESPONSE
```
{
    "id": "65eb9268-b0d1-4f75-a855-71eac716a351",
    "version": 0,
    "creator": "referenceImpl",
    "creatorAppId": "referenceImplApp",
    "creation": 1441377362856,
    "realm": "IOTPAASQA_ITEST",
    "name": "temperature",
    "description": [
      {
        "lang": "en_us",
        "text": "temperature attribute."
      }
    ],
    "type": "decimal",
    "isActive": false,
    "defaultValue": 1
}
```
### PUT: TAG ATTRIBUTE TYPE
This method tags the specified attribute type.

URI: /attributeTypes/{attributeTypeId}/tags/{tag}

### DELETE: UNTAG ATTRIBUTE TYPE
Removes a tag from the attribute type.
```
/attributeTypes/{attributeTypeId}/tags/{tag}
```
### POST: ACTIVATE ATTRIBUTE TYPE
Activates the attribute type template.  Invoking this on an active attribute type has no effect. Attribute type has to be active before use.

URI: /attributeTypes/{attributeTypeId}/tasks/activate

### POST: DEACTIVATE ATTRIBUTE TYPE
Deactivates the attribute type template.  Invoking this on an inactive attribute type has no effect.

URI: /attributeTypes/{attributeTypeId}/tasks/deactivate

## EventTemplate
Device produces an “Event” when values of its attributes change. In order to scale models, connect many Devices, and avoid repetitious definition of the attributes for each new Device, a developer can streamline this process using Event Templates.

### POST: CREATE EVENT TEMPLATE
Create a new event template.

URI: /eventTemplates

SAMPLE REQUEST
```
{
    "creator": "integrationTester",
    "creatorAppId": "integrationTesterApp",
    "realm": "{{newRealm}}",
    "name": "{{eventName}}",
    "description": [
        {
            "lang": "en_US",
            "text": "{{eventDescription}}"
        }    
    ],
    "eventFields": [
        {
            "name": "{{eventFeild1Name}}",
            "type": "decimal"
        },
        {
            "name": "{{eventFeild2Name}}",
            "type": "decimal"
        }
    ],
    "isActive": true,
    "tags": [ "weather", "temp" ]
}
```
SAMPLE RESPONSE
```
{
  "id": "8d6ff5b4-f2f7-473d-889a-0c9cf2064493",
  "version": "g2wAAAABaAJtAAAADNYQX5sthJnpAABOyWEBag==",
  "creator": "integrationTester",
  "creatorAppId": "integrationTesterApp",
  "creation": 1441949748924,
  "realm": "IOT1",
  "name": "{{eventName}}",
  "description": [
    {
      "lang": "en_US",
      "text": "{{eventDescription}}"
    }
  ],
  "eventFields": [
    {
      "name": "{{eventFeild1Name}}",
      "type": "decimal"
    },
    {
      "name": "{{eventFeild2Name}}",
      "type": "decimal"
    }
  ],
  "isActive": false
}
```
### GET: SEARCH EVENT TEMPLATE
This method is used search event templates based on the given filter parameters.

URI: /eventTemplates

SAMPLE REQUEST
```
Accept: application/vnd.com.covisint.platform.eventTemplate.v1+json
Content-Type: application/vnd.com.covisint.platform.eventTemplate.v1+json
X-Realm: IOT1
```
SAMPLE RESPONSE
```
[
  {
    "id": "8d6ff5b4-f2f7-473d-889a-0c9cf2064493",
    "version": "g2wAAAACaAJtAAAADKEXbw0nGFeJAAAnxmECaAJtAAAADNYQX5sthJnpAABOyWEEag==",
    "creator": "integrationTester",
    "creatorAppId": "integrationTesterApp",
    "creation": 1441949748924,
    "realm": "IOT1",
    "name": "{{eventName}}",
    "description": [
      {
        "lang": "en_US",
        "text": "{{eventDescription}}"
      }
    ],
    "eventFields": [
      {
        "name": "{{eventFeild1Name}}",
        "type": "decimal",
        "boundAttributeTypeId": "119b02b8-ddf1-4265-88ac-cdc746b5e283"
      },
      {
        "name": "{{eventFeild2Name}}",
        "type": "decimal"
      }
    ],
    "isActive": false
  }
]
```
### GET: GET EVENT TEMPLATE
This method is used to retrieve the requested event template.

URI: /eventTemplates/{eventTemplateId}

SAMPLE REQUEST
```
Accept: application/vnd.com.covisint.platform.eventtemplate.v1+json;charset=UTF-8
Content-Type: application/vnd.com.covisint.platform.eventtemplate.v1+json;charset=UTF-8
X-Realm: IOT1
```
SAMPLE RESPONSE
```
{
  "id": "8d6ff5b4-f2f7-473d-889a-0c9cf2064493",
  "version": "g2wAAAACaAJtAAAADKEXbw0nGFeJAAAnxmECaAJtAAAADNYQX5sthJnpAABOyWEEag==",
  "creator": "integrationTester",
  "creatorAppId": "integrationTesterApp",
  "creation": 1441949748924,
  "realm": "IOT1",
  "name": "{{eventName}}",
  "description": [
    {
      "lang": "en_US",
      "text": "{{eventDescription}}"
    }
  ],
  "eventFields": [
    {
      "name": "{{eventFeild1Name}}",
      "type": "decimal",
      "boundAttributeTypeId": "119b02b8-ddf1-4265-88ac-cdc746b5e283"
    },
    {
      "name": "{{eventFeild2Name}}",
      "type": "decimal"
    }
  ],
  "isActive": false
}
```
### PUT: TAG EVENT TEMPLATE
This method tags the specified event template.

URI: /eventTemplates/ {eventTemplateId}/tags/{tag}

### DELETE: UNTAG EVENT TEMPLATE
Removes a tag from the event template.

URI: /eventTemplates/ {eventTemplateId}/tags/{tag}

### POST: ACTIVATE EVENT TEMPLATE
Activates the event template.  Invoking this on an active event template has no effect.

URI: /eventTemplates/ {eventTemplateId}/tasks/activate

