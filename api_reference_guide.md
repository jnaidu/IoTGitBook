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

