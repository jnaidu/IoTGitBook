# AttributeType
Attribute Type captures device properties in a template. A library of attribute types can be created inside an IoT solution and used in various device templates. The following operations are available on attribute type.

## POST: CREATE ATTRIBUTE TYPE
Create a new attribute type template.

URI: /attributeTypes

SAMPLE REQUEST
```
{
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
    "creation": 1441377362856,
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
## GET: SEARCH ATTRIBUTE TYPE
This method is used to search attribute types based on the given filter parameters.

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
    "creation": 1441377362856,
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
## GET: GET ATTRIBUTE TYPE
This method is used to retrieve a particular attribute type.

URI: /attributeTypes/{attributeTypeId}

SAMPLE REQUEST
```
Accept    application/vnd.com.covisint.platform.attributeType.v1+json
Content-Type     application/vnd.com.covisint.platform.attributeType.v1+json
Authorization	Bearer 34jhbf9uinvun98v098eijre=
```
SAMPLE RESPONSE
```
{
    "id": "65eb9268-b0d1-4f75-a855-71eac716a351",
    "version": 0,
    "creation": 1441377362856,
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
## PUT: TAG ATTRIBUTE TYPE
This method tags the specified attribute type.

URI: /attributeTypes/{attributeTypeId}/tags/{tag}

## DELETE: UNTAG ATTRIBUTE TYPE
Removes a tag from the attribute type.
```
/attributeTypes/{attributeTypeId}/tags/{tag}
```
## POST: ACTIVATE ATTRIBUTE TYPE
Activates the attribute type template.  Invoking this on an active attribute type has no effect. Attribute type must be active before use.

URI: /attributeTypes/{attributeTypeId}/tasks/activate

## POST: DEACTIVATE ATTRIBUTE TYPE
Deactivates the attribute type template.  Invoking this on an inactive attribute type has no effect.

URI: /attributeTypes/{attributeTypeId}/tasks/deactivate