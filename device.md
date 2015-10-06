# Device
The physical device that produces data and sends it to platform needs to be created.

## POST: CREATE DEVICE
Create a new device.

Prerequisite - Device Template should already have been created.

URI: /devices

SAMPLE REQUEST
```
{
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
  "id": "412793ad-d113-4a59-87e3-f99bce746b7e",
  "version": "g2wAAAABaAJtAAAADNYQX5stnA6MAAAEGmEBag==",
  "creation": 1442291747936,
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
  "parentDeviceTemplateId": "03c06624-0204-4d54-a70d-21ec9652c261",
  "attributes": {},
  "isActive": false
}
```
## GET: SEARCH DEVICE 
This method is used to search device based on the filter parameters.

URI: /devices

SAMPLE REQUEST
```
Accept: application/vnd.com.covisint.platform.device.v1+json
Content-Type: application/vnd.com.covisint.platform.device.v1+json
Authorization	Bearer 34jhbf9uinvun98v098eijre
```
SAMPLE RESPONSE
```
[
  {
    "id": "cfb8e081-bcf1-4455-b2d3-ee165567e235",
    "version": "g2wAAAACaAJtAAAADCDMPMOaTHweAAE6KGEBaAJtAAAADKEXbw0ttADjAAABt2EBag==",
    "creation": 1441964728334,
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
    "parentDeviceTemplateId": "4bfc6847-fe51-4a54-8716-d92e733f898b",
    "attributes": {},
    "isActive": false
  },
  {
    "id": "412793ad-d113-4a59-87e3-f99bce746b7e",
    "version": "g2wAAAABaAJtAAAADNYQX5stnA6MAAAEGmEBag==",
    "creation": 1442291747936,
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
    "parentDeviceTemplateId": "03c06624-0204-4d54-a70d-21ec9652c261",
    "attributes": {},
    "isActive": false
  }
]
```
## GET: GET DEVICE 
This method is used to retrieve the requested device.

URI: /devices/{deviceId}

SAMPLE REQUEST
```
Accept: application/vnd.com.covisint.platform.device.v1+json
Content-Type: application/vnd.com.covisint.platform.device.v1+json
Authorization	Bearer 34jhbf9uinvun98v098eijre
```
SAMPLE RESPONSE
```
{
  "id": "cfb8e081-bcf1-4455-b2d3-ee165567e235",
  "version": "g2wAAAACaAJtAAAADCDMPMOaTHweAAE6KGEBaAJtAAAADKEXbw0ttADjAAABt2ECag==",
  "creation": 1441964728334,
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
  "parentDeviceTemplateId": "4bfc6847-fe51-4a54-8716-d92e733f898b",
  "attributes": {},
  "isActive": false
}
```
## PUT: TAG DEVICE
This method tags the specified device.

URI: /devices/ {deviceId}/tags/{tag}

## DELETE: UNTAG DEVICE
Removes a tag from the device.

URI: /devices/ {deviceId}/tags/{tag}

## POST: ACTIVATE DEVICE
Activates the device.  Invoking this on an active device has no effect.

URI: /devices/{deviceId}/tasks/deactivate