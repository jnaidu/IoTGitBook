# DeviceTemplate
Using the Device template, a developer typically starts by creating a new device. In order to scale models, connect many Devices, and avoid repetitious definition of the property for each new Device, a developer can streamline this process using Device Templates. Prerequisite: Attributes, Events, Commands should be created in advance.

## POST: CREATE DEVICE TEMPLATE
Create a new device template.

URI: /deviceTemplates

SAMPLE REQUEST
```
{
    "creator": "",
    "creatorAppId": "",
    "realm": "{{newRealm}}",
 "name": [{ 
  "lang": "en_US", 
  "text": "{{deviceTemplateName}}"
 }],
 "description": [{ 
  "lang": "en_US", 
  "text": "{{deviceTemplateDescription}}"
 }],
 "attributes": [ "fa09d62c-3fb6-4ba6-8f1e-f3b9d1321b36" ],
 "events": [ "5b4e22e6-3089-409a-b561-a73c3c99128f" ],
 "commands":[ "823be4e2-dd3e-4887-b145-fbf6b2ab5f9e" ]
}
```
SAMPLE RESPONSE
```
{
  "id": "03c06624-0204-4d54-a70d-21ec9652c261",
  "version": "g2wAAAABaAJtAAAADKEXbw0nGpWEAAADuWEBag==",
  "creator": "",
  "creatorAppId": "",
  "creation": 1442229070062,
  "realm": "",
  "name": [
    {
      "lang": "en_US",
      "text": "{{deviceTemplateName}}"
    }
  ],
  "description": [
    {
      "lang": "en_US",
      "text": "{{deviceTemplateDescription}}"
    }
  ],
  "isActive": false
}
```
## GET: SEARCH DEVICE TEMPLATE
This method is used search device templates based on the filter parameters.

URI: /deviceTemplates

SAMPLE REQUEST
```
Accept: application/vnd.com.covisint.platform.deviceTemplate.v1+json;fetchattributetypes=true;fetchcommandtemplates=true;fetcheventtemplates=true
Content-Type: application/vnd.com.covisint.platform.deviceTemplate.v1+json
X-Realm: 
```
SAMPLE RESPONSE
[
  {
    "id": "03c06624-0204-4d54-a70d-21ec9652c261",
    "version": "g2wAAAABaAJtAAAADKEXbw0nGpWEAAADuWEBag==",
    "creator": "",
    "creatorAppId": "",
    "creation": 1442229070062,
    "realm": "",
    "name": [
      {
        "lang": "en_US",
        "text": "{{deviceTemplateName}}"
      }
    ],
    "description": [
      {
        "lang": "en_US",
        "text": "{{deviceTemplateDescription}}"
      }
    ],
    "isActive": false
  },
  {
    "id": "4ceb483f-6485-456e-bf5f-8f7b6b8238d8",
    "version": "g2wAAAABaAJtAAAADNYQX5stFD7wAAAA+2EBag==",
    "creator": "",
    "creatorAppId": "",
    "creation": 1441798080311,
    "realm": "",
    "name": [
      {
        "lang": "en_US",
        "text": "{{deviceTemplateName}}"
      }
    ],
    "description": [
      {
        "lang": "en_US",
        "text": "{{deviceTemplateDescription}}"
      }
    ],
    "isActive": false
  },
  {
    "id": "4bfc6847-fe51-4a54-8716-d92e733f898b",
    "version": "g2wAAAACaAJtAAAADCDMPMOaSUrqAAGGzmEBaAJtAAAADKEXbw0nFa7pAAABg2EBag==",
    "creator": "",
    "creatorAppId": "",
    "creation": 1441964016560,
    "realm": "",
    "name": [
      {
        "lang": "en_US",
        "text": "{{deviceTemplateName}}"
      }
    ],
    "description": [
      {
        "lang": "en_US",
        "text": "{{deviceTemplateDescription}}"
      }
    ],
    "isActive": true
  }
]

## GET: GET DEVICE TEMPLATE

This method is used to retrieve the requested device template.

URI: /deviceTemplates/ {deviceTemplateId}

SAMPLE REQUEST
```
Accept: application/vnd.com.covisint.platform.deviceTemplate.v1+json;fetchattributetypes=true;fetchcommandtemplates=true;fetcheventtemplates=true
Content-Type: application/vnd.com.covisint.platform.deviceTemplate.v1+json
X-Realm: 
```
SAMPLE RESPONSE
```
{
    "id": "4bfc6847-fe51-4a54-8716-d92e733f898b",
    "version": "g2wAAAACaAJtAAAADCDMPMOaSUrqAAGGzmEBaAJtAAAADKEXbw0nFa7pAAABg2EBag==",
    "creator": "",
    "creatorAppId": "",
    "creation": 1441964016560,
    "realm": "",
    "name": [
      {
        "lang": "en_US",
        "text": "{{deviceTemplateName}}"
      }
    ],
    "description": [
      {
        "lang": "en_US",
        "text": "{{deviceTemplateDescription}}"
      }
    ],
    "isActive": true
  },
```
## PUT: TAG DEVICE TEMPLATE
This method tags the specified device template.

URI:/deviceTemplates/{deviceTemplateId}/tags/{tag}

## DELETE: UNTAG DEVICE TEMPLATE
Removes a tag from the device template.

URI: /deviceTemplates/ {deviceTemplateId}/tags/{tag}

## POST: ACTIVATE DEVICE TEMPLATE
Activates the device template.  Invoking this on an active device template has no effect.

URI: /deviceTemplates/{deviceTemplateId}/tasks/activate

## POST: DEACTIVATE DEVICE TEMPLATE
Deactivates the device template.  Invoking this on an inactive device template has no effect.

URI: /deviceTemplates/ {deviceTemplateId}//tasks/deactivate