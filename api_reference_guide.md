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

### POST: DEACTIVATE EVENT TEMPLATE
Deactivates the event template.  Invoking this on an inactive event template has no effect.

URI: /eventTemplates/ {eventTemplateId}//tasks/deactivate

## CommandTemplate
Command templates are created so that the response from devices can be captured in a standard form.

### POST: CREATE COMMAND TEMPLATE
Create a new command template.

URI: /commandTemplates

SAMPLE REQUEST
```
{   "creator": "integrationTester",     
	"creatorAppId": "integrationTesterApp",
	"realm": "{{newRealm}}",
	"name": "{{commandName}}",
	"isActive": true,
	"description": [       
		{   
			"lang": "en_US",           
			"text": "{{commandDescription}}"
		}   
	],   
	"args": [
		{         
			"name": "{{commandArg1}}",
			"description": [{        
			"lang": "en_us",        
			"text": "{{commandArg1Description}}"      
			}],      
			"type": "decimal",      
			"index": 1     
		},     
		{         
			"name": "{{commandArg2}}",      
			"description": [{        
			"lang": "en_us",        
			"text": "{{commandArg2Description}}"      
			}],      
			"type": "bool",      
			"index": 0     
		}       
	] 
}
```
SAMPLE RESPONSE
```
{
  "id": "141bd70d-b9ce-4ea1-b2a6-99e2acb43aeb",
  "version": "g2wAAAABaAJtAAAADNYQX5sthJnpAABQ7mEBag==",
  "creator": "Sam",
  "creatorAppId": "Sam's App",
  "creation": 1442223545432,
  "realm": "IOT1",
  "name": "{{commandName}}",
  "description": [
    {
      "lang": "en_US",
      "text": "{{commandDescription}}"
    }
  ],
  "args": [
    {
      "name": "{{commandArg2}}",
      "description": [
        {
          "lang": "en_us",
          "text": "{{commandArg2Description}}"
        }
      ],
      "type": "bool",
      "index": 0
    },
    {
      "name": "{{commandArg1}}",
      "description": [
        {
          "lang": "en_us",
          "text": "{{commandArg1Description}}"
        }
      ],
      "type": "decimal",
      "index": 1
    }
  ],
  "isActive": false
}
```
### GET: SEARCH COMMAND TEMPLATE
This method is used search event templates based on the given filter parameters.

URI: /commandTemplates

SAMPLE REQUEST
```
Accept: application/vnd.com.covisint.platform.commandTemplate.v1+json
Content-Type: application/vnd.com.covisint.platform.commandTemplate.v1+json
X-Realm: IOT1
```
SAMPLE RESPONSE
```
[
  {
    "id": "bc02b60f-90f8-4eed-ad17-8d10f8b9bfa8",
    "version": "g2wAAAABaAJtAAAADNYQX5stIjkQAAABW2EBag==",
    "creator": "integrationTester",
    "creatorAppId": "integrationTesterApp",
    "creation": 1441958618261,
    "realm": "IOT1",
    "name": "{{commandName}}",
    "description": [
      {
        "lang": "en_US",
        "text": "{{commandDescription}}"
      }
    ],
    "args": [
      {
        "name": "{{commandArg2}}",
        "description": [
          {
            "lang": "en_us",
            "text": "{{commandArg2Description}}"
          }
        ],
        "type": "bool",
        "index": 0
      },
      {
        "name": "{{commandArg1}}",
        "description": [
          {
            "lang": "en_us",
            "text": "{{commandArg1Description}}"
          }
        ],
        "type": "decimal",
        "index": 1
      }
    ],
    "isActive": false
  },
  {
    "id": "f58e3d66-47e9-4dd1-b255-64f24334bf38",
    "version": "g2wAAAABaAJtAAAADCDMPMOaSzKTAAE722EBag==",
    "creator": "Sam",
    "creatorAppId": "Sam's App",
    "creation": 1442217205007,
    "realm": "IOT1",
    "name": "{{commandName}}",
    "description": [
      {
        "lang": "en_US",
        "text": "{{commandDescription}}"
      }
    ],
    "args": [
      {
        "name": "{{commandArg2}}",
        "description": [
          {
            "lang": "en_us",
            "text": "{{commandArg2Description}}"
          }
        ],
        "type": "bool",
        "index": 0
      },
      {
        "name": "{{commandArg1}}",
        "description": [
          {
            "lang": "en_us",
            "text": "{{commandArg1Description}}"
          }
        ],
        "type": "decimal",
        "index": 1
      }
    ],
    "isActive": false
  },
  {
    "id": "c12249b9-a84f-4a8e-9048-1e7127db9694",
    "version": "g2wAAAABaAJtAAAADNYQX5swFAnfAAADdGEBag==",
    "creator": "integrationTester",
    "creatorAppId": "integrationTesterApp",
    "creation": 1442223526270,
    "realm": "IOT1",
    "name": "{{commandName}}",
    "description": [
      {
        "lang": "en_US",
        "text": "{{commandDescription}}"
      }
    ],
    "args": [
      {
        "name": "{{commandArg2}}",
        "description": [
          {
            "lang": "en_us",
            "text": "{{commandArg2Description}}"
          }
        ],
        "type": "bool",
        "index": 0
      },
      {
        "name": "{{commandArg1}}",
        "description": [
          {
            "lang": "en_us",
            "text": "{{commandArg1Description}}"
          }
        ],
        "type": "decimal",
        "index": 1
      }
    ],
    "isActive": false
  },
  {
    "id": "141bd70d-b9ce-4ea1-b2a6-99e2acb43aeb",
    "version": "g2wAAAABaAJtAAAADNYQX5sthJnpAABQ7mEBag==",
    "creator": "integrationTester",
    "creatorAppId": "integrationTesterApp",
    "creation": 1442223545432,
    "realm": "IOT1",
    "name": "{{commandName}}",
    "description": [
      {
        "lang": "en_US",
        "text": "{{commandDescription}}"
      }
    ],
    "args": [
      {
        "name": "{{commandArg2}}",
        "description": [
          {
            "lang": "en_us",
            "text": "{{commandArg2Description}}"
          }
        ],
        "type": "bool",
        "index": 0
      },
      {
        "name": "{{commandArg1}}",
        "description": [
          {
            "lang": "en_us",
            "text": "{{commandArg1Description}}"
          }
        ],
        "type": "decimal",
        "index": 1
      }
    ],
    "isActive": false
  }
]
```
### GET: GET COMMAND TEMPLATE
This method is used to retrieve the requested command template.

URI: /commandTemplates/ {commandTemplateId}

SAMPLE REQUEST
```
Accept: application/vnd.com.covisint.platform.commandTemplate.v1+json
Content-Type: application/vnd.com.covisint.platform.commandTemplate.v1+json
X-Realm: IOT1
```
SAMPLE RESPONSE
```
{
  "id": "bc02b60f-90f8-4eed-ad17-8d10f8b9bfa8",
  "version": "g2wAAAABaAJtAAAADNYQX5stIjkQAAABW2EBag==",
  "creator": "integrationTester",
  "creatorAppId": "integrationTesterApp",
  "creation": 1441958618261,
  "realm": "IOT1",
  "name": "{{commandName}}",
  "description": [
    {
      "lang": "en_US",
      "text": "{{commandDescription}}"
    }
  ],
  "args": [
    {
      "name": "{{commandArg2}}",
      "description": [
        {
          "lang": "en_us",
          "text": "{{commandArg2Description}}"
        }
      ],
      "type": "bool",
      "index": 0
    },
    {
      "name": "{{commandArg1}}",
      "description": [
        {
          "lang": "en_us",
          "text": "{{commandArg1Description}}"
        }
      ],
      "type": "decimal",
      "index": 1
    }
  ],
  "isActive": false
}
```
### PUT: TAG COMMAND TEMPLATE
This method tags the specified command template. 

URI: /commandTemplates/ {commandTemplateId}/tags/{tag}

### DELETE: UNTAG COMMAND TEMPLATE
Removes a tag from the event template.

URI: /commandTemplates/ {commandTemplateId}/tags/{tag}

### POST: ACTIVATE COMMAND TEMPLATE
Activates the command template.  Invoking this on an active command template has no effect.

URI: /commandTemplates/ {commandTemplateId}/tasks/activate

### POST: DEACTIVATE COMMAND TEMPLATE
Deactivates the command template.  Invoking this on an inactive command template has no effect.

URI: /eventTemplates/ {eventTemplateId}//tasks/deactivate

## DeviceTemplate
Using the Device template, a developer typically starts by creating a new device. In order to scale models, connect many Devices, and avoid repetitious definition of the property for each new Device, a developer can streamline this process using Device Templates. Prerequisite: Attributes, Events, Commands should be created in advance.

### POST: CREATE DEVICE TEMPLATE
Create a new device template.

URI: /deviceTemplates

SAMPLE REQUEST
```
{
    "creator": "integrationTester",
    "creatorAppId": "integrationTesterApp",
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
  "creator": "integrationTester",
  "creatorAppId": "integrationTesterApp",
  "creation": 1442229070062,
  "realm": "IOT1",
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
### GET: SEARCH DEVICE TEMPLATE
This method is used search device templates based on the filter parameters.

URI: /deviceTemplates

SAMPLE REQUEST
```
Accept: application/vnd.com.covisint.platform.deviceTemplate.v1+json;fetchattributetypes=true;fetchcommandtemplates=true;fetcheventtemplates=true
Content-Type: application/vnd.com.covisint.platform.deviceTemplate.v1+json
X-Realm: IOT1
```
SAMPLE RESPONSE
[
  {
    "id": "03c06624-0204-4d54-a70d-21ec9652c261",
    "version": "g2wAAAABaAJtAAAADKEXbw0nGpWEAAADuWEBag==",
    "creator": "integrationTester",
    "creatorAppId": "integrationTesterApp",
    "creation": 1442229070062,
    "realm": "IOT1",
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
    "creator": "integrationTester",
    "creatorAppId": "integrationTesterApp",
    "creation": 1441798080311,
    "realm": "IOT1",
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
    "creator": "integrationTester",
    "creatorAppId": "integrationTesterApp",
    "creation": 1441964016560,
    "realm": "IOT1",
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

### GET: GET DEVICE TEMPLATE

This method is used to retrieve the requested device template.

URI: /deviceTemplates/ {deviceTemplateId}

SAMPLE REQUEST
```
Accept: application/vnd.com.covisint.platform.deviceTemplate.v1+json;fetchattributetypes=true;fetchcommandtemplates=true;fetcheventtemplates=true
Content-Type: application/vnd.com.covisint.platform.deviceTemplate.v1+json
X-Realm: IOT1
```
SAMPLE RESPONSE
```
{
    "id": "4bfc6847-fe51-4a54-8716-d92e733f898b",
    "version": "g2wAAAACaAJtAAAADCDMPMOaSUrqAAGGzmEBaAJtAAAADKEXbw0nFa7pAAABg2EBag==",
    "creator": "integrationTester",
    "creatorAppId": "integrationTesterApp",
    "creation": 1441964016560,
    "realm": "IOT1",
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
### PUT: TAG DEVICE TEMPLATE
This method tags the specified device template.

URI:/deviceTemplates/{deviceTemplateId}/tags/{tag}

### DELETE: UNTAG DEVICE TEMPLATE
Removes a tag from the device template.

URI: /deviceTemplates/ {deviceTemplateId}/tags/{tag}

### POST: ACTIVATE DEVICE TEMPLATE
Activates the device template.  Invoking this on an active device template has no effect.

URI: /deviceTemplates/{deviceTemplateId}/tasks/activate

### POST: DEACTIVATE DEVICE TEMPLATE
Deactivates the device template.  Invoking this on an inactive device template has no effect.

URI: /deviceTemplates/ {deviceTemplateId}//tasks/deactivate

## Device
The physical device that produces data and sends it to platform needs to be created.

### POST: CREATE DEVICE
Create a new device. Prerequisite is Device Template should have been created.

URI: /devices

SAMPLE REQUEST
```
{
    "creator": "integrationTester",
    "creatorAppId": "integrationTesterApp",
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
  "id": "412793ad-d113-4a59-87e3-f99bce746b7e",
  "version": "g2wAAAABaAJtAAAADNYQX5stnA6MAAAEGmEBag==",
  "creator": "integrationTester",
  "creatorAppId": "integrationTesterApp",
  "creation": 1442291747936,
  "realm": "IOT1",
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
### GET: SEARCH DEVICE 
This method is used search device based on the filter parameters.

URI: /devices

SAMPLE REQUEST
```
Accept: application/vnd.com.covisint.platform.device.v1+json
Content-Type: application/vnd.com.covisint.platform.device.v1+json
X-Realm: IOT1
```
SAMPLE RESPONSE
```
[
  {
    "id": "cfb8e081-bcf1-4455-b2d3-ee165567e235",
    "version": "g2wAAAACaAJtAAAADCDMPMOaTHweAAE6KGEBaAJtAAAADKEXbw0ttADjAAABt2EBag==",
    "creator": "integrationTester",
    "creatorAppId": "integrationTesterApp",
    "creation": 1441964728334,
    "realm": "IOT1",
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
    "creator": "integrationTester",
    "creatorAppId": "integrationTesterApp",
    "creation": 1442291747936,
    "realm": "IOT1",
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
### GET: GET DEVICE 
This method is used to retrieve the requested device.

URI: /devices/{deviceId}

SAMPLE REQUEST
```
Accept: application/vnd.com.covisint.platform.device.v1+json
Content-Type: application/vnd.com.covisint.platform.device.v1+json
X-Realm: IOT1
```
SAMPLE RESPONSE
```
{
  "id": "cfb8e081-bcf1-4455-b2d3-ee165567e235",
  "version": "g2wAAAACaAJtAAAADCDMPMOaTHweAAE6KGEBaAJtAAAADKEXbw0ttADjAAABt2ECag==",
  "creator": "integrationTester",
  "creatorAppId": "integrationTesterApp",
  "creation": 1441964728334,
  "realm": "IOT1",
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
### PUT: TAG DEVICE
This method tags the specified device.

URI: /devices/ {deviceId}/tags/{tag}

### DELETE: UNTAG DEVICE
Removes a tag from the device.

URI: /devices/ {deviceId}/tags/{tag}

### POST: ACTIVATE DEVICE
Activates the device.  Invoking this on an active device has no effect.

URI: /devices/{deviceId}/tasks/deactivate

## Stream
Create a new stream.

### POST: CREATE STREAM
Create a new stream.

URI: /streams

SAMPLE REQUEST
```
{
  "creator": "integrationTester",
   "creatorAppId": "integrationTesterApp",
  "realm": "IOT1",
  "ownerId": "Admin",
  "name": [
    {
      "lang": "zh",
      "text": "流"
    },
    {
      "lang": "en",
      "text": "Stream test"
    }
  ],
  "streamType": "DEVICE",
  "protocolType": "MQTT",
  "deviceSecurityType": "BASIC",
  "payloadSecurityType": "ENCRYPTED"
}
```
SAMPLE RESPONSE
```
{
  "id": "af57ec91-c123-4b98-96da-40a04b28e40b",
  "version": "g2wAAAABaAJtAAAADCDMPMOaSx/qAAE8V2EBag==",
  "creator": "integrationTester",
  "creatorAppId": "integrationTesterApp",
  "creation": 1442303332104,
  "realm": "IOT1",
  "name": [
    {
      "lang": "en",
      "text": "Stream test"
    },
    {	
      "lang": "zh",
      "text": "流"
    }
  ],
  "streamType": "DEVICE",
  "protocolType": "MQTT",
  "payloadSecurityType": "ENCRYPTED",
  "ownerId": "Admin",
  "streamConfiguration": {
    "logMode": "INFO",
    "pullingThreads": 1,
    "sleepTime": 60,
    "quota": 10
  },
  "payloadSecurityAttributes": [
    {
      "name": "consumerPrivateKey",
      "value": "MIIBSwIBADCCASwGByqGSM44BAEwggEfAoGBAP1/U4EddRIpUt9KnC7s5Of2EbdSPO9EAMMeP4C2USZpRV1AIlH7WT2NWPq/xfW6MPbLm1Vs14E7gB00b/JmYLdrmVClpJ+f6AR7ECLCT7up1/63xhv4O1fnxqimFQ8E+4P208UewwI1VBNaFpEy9nXzrith1yrv8iIDGZ3RSAHHAhUAl2BQjxUjC8yykrmCouuEC/BYHPUCgYEA9+GghdabPd7LvKtcNrhXuXmUr7v6OuqC+VdMCz0HgmdRWVeOutRZT+ZxBxCBgLRJFnEj6EwoFhO3zwkyjMim4TwWeotUfI0o4KOuHiuzpnWRbqN/C/ohNWLx+2J6ASQ7zKTxvqhRkImog9/hWuWfBpKLZl6Ae1UlZAFMO/7PSSoEFgIUR/PBBma5H4RfGiXVh1cSGtXOrI0="
    },
    {
      "name": "producerPublicKey",
      "value": "MIIBtzCCASwGByqGSM44BAEwggEfAoGBAP1/U4EddRIpUt9KnC7s5Of2EbdSPO9EAMMeP4C2USZpRV1AIlH7WT2NWPq/xfW6MPbLm1Vs14E7gB00b/JmYLdrmVClpJ+f6AR7ECLCT7up1/63xhv4O1fnxqimFQ8E+4P208UewwI1VBNaFpEy9nXzrith1yrv8iIDGZ3RSAHHAhUAl2BQjxUjC8yykrmCouuEC/BYHPUCgYEA9+GghdabPd7LvKtcNrhXuXmUr7v6OuqC+VdMCz0HgmdRWVeOutRZT+ZxBxCBgLRJFnEj6EwoFhO3zwkyjMim4TwWeotUfI0o4KOuHiuzpnWRbqN/C/ohNWLx+2J6ASQ7zKTxvqhRkImog9/hWuWfBpKLZl6Ae1UlZAFMO/7PSSoDgYQAAoGAHogkEJzK8Q1/9qjL+EPdbGMaxACs8/0PQ8oNgZfCxkAF4jTJRtKK+6cerjf6N0kwe0bMKEhS1NnGRKM0AM3GW0/zx8EJkFdTtSBJPtsAeQNDeQHWmhYcq4YA2gXBP+n2F1NEVcgXFKROYy3zsTNsUG/xmVta15HeeG8FDnayY+Q="
    },
    {
      "name": "producerPrivateKey",
      "value": "MIIBSwIBADCCASwGByqGSM44BAEwggEfAoGBAP1/U4EddRIpUt9KnC7s5Of2EbdSPO9EAMMeP4C2USZpRV1AIlH7WT2NWPq/xfW6MPbLm1Vs14E7gB00b/JmYLdrmVClpJ+f6AR7ECLCT7up1/63xhv4O1fnxqimFQ8E+4P208UewwI1VBNaFpEy9nXzrith1yrv8iIDGZ3RSAHHAhUAl2BQjxUjC8yykrmCouuEC/BYHPUCgYEA9+GghdabPd7LvKtcNrhXuXmUr7v6OuqC+VdMCz0HgmdRWVeOutRZT+ZxBxCBgLRJFnEj6EwoFhO3zwkyjMim4TwWeotUfI0o4KOuHiuzpnWRbqN/C/ohNWLx+2J6ASQ7zKTxvqhRkImog9/hWuWfBpKLZl6Ae1UlZAFMO/7PSSoEFgIULku7TX6ezXhsWpg+xYaQZbtpJJc="
    },
    {
      "name": "consumerPublicKey",
      "value": "MIIBtzCCASwGByqGSM44BAEwggEfAoGBAP1/U4EddRIpUt9KnC7s5Of2EbdSPO9EAMMeP4C2USZpRV1AIlH7WT2NWPq/xfW6MPbLm1Vs14E7gB00b/JmYLdrmVClpJ+f6AR7ECLCT7up1/63xhv4O1fnxqimFQ8E+4P208UewwI1VBNaFpEy9nXzrith1yrv8iIDGZ3RSAHHAhUAl2BQjxUjC8yykrmCouuEC/BYHPUCgYEA9+GghdabPd7LvKtcNrhXuXmUr7v6OuqC+VdMCz0HgmdRWVeOutRZT+ZxBxCBgLRJFnEj6EwoFhO3zwkyjMim4TwWeotUfI0o4KOuHiuzpnWRbqN/C/ohNWLx+2J6ASQ7zKTxvqhRkImog9/hWuWfBpKLZl6Ae1UlZAFMO/7PSSoDgYQAAoGAKwzWUj8W72SPoPKBGHOzXJLYb2guqFQfWYgf2XeyFruGM39fTt2pesxHCp70kvNjPc8HYZMa9SfhsWHkL6gZfqaLLI3St7N7WdwCgipO1R+c55vBnaO2Ts+gF+80p9n/Y5Nay8PlvwMI5ZqpYEzth9NuETnh37uh/0prdIHag7g="
    }
  ]
}
```
### GET: SEARCH STREAM
This method is used to search stream based on the given filter parameters.

URI: /streams

SAMPLE REQUEST
```
Accept: application/vnd.com.covisint.platform.stream.v1+json 
X-Realm: IOT1
```
SAMPLE RESPONSE
```
{
  "id": "af57ec91-c123-4b98-96da-40a04b28e40b",
  "version": "g2wAAAABaAJtAAAADCDMPMOaSx/qAAE8V2EBag==",
  "creator": "integrationTester",
  "creatorAppId": "integrationTesterApp",
  "creation": 1442303332104,
  "realm": "IOT1",
  "name": [
    {
      "lang": "en",
      "text": "Stream test"
    },
    {
      "lang": "zh",
      "text": "流"
    }
  ],
  "streamType": "DEVICE",
  "protocolType": "MQTT",
  "payloadSecurityType": "ENCRYPTED",
  "ownerId": "Admin",
  "streamConfiguration": {
    "logMode": "INFO",
    "pullingThreads": 1,
    "sleepTime": 60,
    "quota": 10
  },
  "payloadSecurityAttributes": [
    {
      "name": "consumerPrivateKey",
      "value": "MIIBSwIBADCCASwGByqGSM44BAEwggEfAoGBAP1/U4EddRIpUt9KnC7s5Of2EbdSPO9EAMMeP4C2USZpRV1AIlH7WT2NWPq/xfW6MPbLm1Vs14E7gB00b/JmYLdrmVClpJ+f6AR7ECLCT7up1/63xhv4O1fnxqimFQ8E+4P208UewwI1VBNaFpEy9nXzrith1yrv8iIDGZ3RSAHHAhUAl2BQjxUjC8yykrmCouuEC/BYHPUCgYEA9+GghdabPd7LvKtcNrhXuXmUr7v6OuqC+VdMCz0HgmdRWVeOutRZT+ZxBxCBgLRJFnEj6EwoFhO3zwkyjMim4TwWeotUfI0o4KOuHiuzpnWRbqN/C/ohNWLx+2J6ASQ7zKTxvqhRkImog9/hWuWfBpKLZl6Ae1UlZAFMO/7PSSoEFgIUR/PBBma5H4RfGiXVh1cSGtXOrI0="
    },
    {
      "name": "producerPublicKey",
      "value": "MIIBtzCCASwGByqGSM44BAEwggEfAoGBAP1/U4EddRIpUt9KnC7s5Of2EbdSPO9EAMMeP4C2USZpRV1AIlH7WT2NWPq/xfW6MPbLm1Vs14E7gB00b/JmYLdrmVClpJ+f6AR7ECLCT7up1/63xhv4O1fnxqimFQ8E+4P208UewwI1VBNaFpEy9nXzrith1yrv8iIDGZ3RSAHHAhUAl2BQjxUjC8yykrmCouuEC/BYHPUCgYEA9+GghdabPd7LvKtcNrhXuXmUr7v6OuqC+VdMCz0HgmdRWVeOutRZT+ZxBxCBgLRJFnEj6EwoFhO3zwkyjMim4TwWeotUfI0o4KOuHiuzpnWRbqN/C/ohNWLx+2J6ASQ7zKTxvqhRkImog9/hWuWfBpKLZl6Ae1UlZAFMO/7PSSoDgYQAAoGAHogkEJzK8Q1/9qjL+EPdbGMaxACs8/0PQ8oNgZfCxkAF4jTJRtKK+6cerjf6N0kwe0bMKEhS1NnGRKM0AM3GW0/zx8EJkFdTtSBJPtsAeQNDeQHWmhYcq4YA2gXBP+n2F1NEVcgXFKROYy3zsTNsUG/xmVta15HeeG8FDnayY+Q="
    },
    {
      "name": "producerPrivateKey",
      "value": "MIIBSwIBADCCASwGByqGSM44BAEwggEfAoGBAP1/U4EddRIpUt9KnC7s5Of2EbdSPO9EAMMeP4C2USZpRV1AIlH7WT2NWPq/xfW6MPbLm1Vs14E7gB00b/JmYLdrmVClpJ+f6AR7ECLCT7up1/63xhv4O1fnxqimFQ8E+4P208UewwI1VBNaFpEy9nXzrith1yrv8iIDGZ3RSAHHAhUAl2BQjxUjC8yykrmCouuEC/BYHPUCgYEA9+GghdabPd7LvKtcNrhXuXmUr7v6OuqC+VdMCz0HgmdRWVeOutRZT+ZxBxCBgLRJFnEj6EwoFhO3zwkyjMim4TwWeotUfI0o4KOuHiuzpnWRbqN/C/ohNWLx+2J6ASQ7zKTxvqhRkImog9/hWuWfBpKLZl6Ae1UlZAFMO/7PSSoEFgIULku7TX6ezXhsWpg+xYaQZbtpJJc="
    },
    {
      "name": "consumerPublicKey",
      "value": "MIIBtzCCASwGByqGSM44BAEwggEfAoGBAP1/U4EddRIpUt9KnC7s5Of2EbdSPO9EAMMeP4C2USZpRV1AIlH7WT2NWPq/xfW6MPbLm1Vs14E7gB00b/JmYLdrmVClpJ+f6AR7ECLCT7up1/63xhv4O1fnxqimFQ8E+4P208UewwI1VBNaFpEy9nXzrith1yrv8iIDGZ3RSAHHAhUAl2BQjxUjC8yykrmCouuEC/BYHPUCgYEA9+GghdabPd7LvKtcNrhXuXmUr7v6OuqC+VdMCz0HgmdRWVeOutRZT+ZxBxCBgLRJFnEj6EwoFhO3zwkyjMim4TwWeotUfI0o4KOuHiuzpnWRbqN/C/ohNWLx+2J6ASQ7zKTxvqhRkImog9/hWuWfBpKLZl6Ae1UlZAFMO/7PSSoDgYQAAoGAKwzWUj8W72SPoPKBGHOzXJLYb2guqFQfWYgf2XeyFruGM39fTt2pesxHCp70kvNjPc8HYZMa9SfhsWHkL6gZfqaLLI3St7N7WdwCgipO1R+c55vBnaO2Ts+gF+80p9n/Y5Nay8PlvwMI5ZqpYEzth9NuETnh37uh/0prdIHag7g="
    }
  ]
}
```
### GET: GET STREAM
This method is used to retrieve stream by stream ID.

URI: /streams/{streamId}

SAMPLE REQUEST
```
Accept: application/vnd.com.covisint.platform.stream.v1+json
X-Realm: IOT1
```
SAMPLE RESPONSE
```
[
  {
    "id": "af57ec91-c123-4b98-96da-40a04b28e40b",
    "version": "g2wAAAABaAJtAAAADCDMPMOaSx/qAAE8V2EBag==",
    "creator": "integrationTester",
    "creatorAppId": "integrationTesterApp",
    "creation": 1442303332104,
    "realm": "IOT1",
    "name": [
      {
        "lang": "en",
        "text": "Stream test"
      },
      {
        "lang": "zh",
        "text": "流"
      }
    ],
    "streamType": "DEVICE",
    "protocolType": "MQTT",
    "payloadSecurityType": "ENCRYPTED",
    "ownerId": "Admin",
    "streamConfiguration": {
      "logMode": "INFO",
      "pullingThreads": 1,
      "sleepTime": 60,
      "quota": 10
    },
    "payloadSecurityAttributes": [
      {
        "name": "consumerPrivateKey",
        "value": "MIIBSwIBADCCASwGByqGSM44BAEwggEfAoGBAP1/U4EddRIpUt9KnC7s5Of2EbdSPO9EAMMeP4C2USZpRV1AIlH7WT2NWPq/xfW6MPbLm1Vs14E7gB00b/JmYLdrmVClpJ+f6AR7ECLCT7up1/63xhv4O1fnxqimFQ8E+4P208UewwI1VBNaFpEy9nXzrith1yrv8iIDGZ3RSAHHAhUAl2BQjxUjC8yykrmCouuEC/BYHPUCgYEA9+GghdabPd7LvKtcNrhXuXmUr7v6OuqC+VdMCz0HgmdRWVeOutRZT+ZxBxCBgLRJFnEj6EwoFhO3zwkyjMim4TwWeotUfI0o4KOuHiuzpnWRbqN/C/ohNWLx+2J6ASQ7zKTxvqhRkImog9/hWuWfBpKLZl6Ae1UlZAFMO/7PSSoEFgIUR/PBBma5H4RfGiXVh1cSGtXOrI0="
      },
      {
        "name": "producerPublicKey",
        "value": "MIIBtzCCASwGByqGSM44BAEwggEfAoGBAP1/U4EddRIpUt9KnC7s5Of2EbdSPO9EAMMeP4C2USZpRV1AIlH7WT2NWPq/xfW6MPbLm1Vs14E7gB00b/JmYLdrmVClpJ+f6AR7ECLCT7up1/63xhv4O1fnxqimFQ8E+4P208UewwI1VBNaFpEy9nXzrith1yrv8iIDGZ3RSAHHAhUAl2BQjxUjC8yykrmCouuEC/BYHPUCgYEA9+GghdabPd7LvKtcNrhXuXmUr7v6OuqC+VdMCz0HgmdRWVeOutRZT+ZxBxCBgLRJFnEj6EwoFhO3zwkyjMim4TwWeotUfI0o4KOuHiuzpnWRbqN/C/ohNWLx+2J6ASQ7zKTxvqhRkImog9/hWuWfBpKLZl6Ae1UlZAFMO/7PSSoDgYQAAoGAHogkEJzK8Q1/9qjL+EPdbGMaxACs8/0PQ8oNgZfCxkAF4jTJRtKK+6cerjf6N0kwe0bMKEhS1NnGRKM0AM3GW0/zx8EJkFdTtSBJPtsAeQNDeQHWmhYcq4YA2gXBP+n2F1NEVcgXFKROYy3zsTNsUG/xmVta15HeeG8FDnayY+Q="
      },
      {
        "name": "producerPrivateKey",
        "value": "MIIBSwIBADCCASwGByqGSM44BAEwggEfAoGBAP1/U4EddRIpUt9KnC7s5Of2EbdSPO9EAMMeP4C2USZpRV1AIlH7WT2NWPq/xfW6MPbLm1Vs14E7gB00b/JmYLdrmVClpJ+f6AR7ECLCT7up1/63xhv4O1fnxqimFQ8E+4P208UewwI1VBNaFpEy9nXzrith1yrv8iIDGZ3RSAHHAhUAl2BQjxUjC8yykrmCouuEC/BYHPUCgYEA9+GghdabPd7LvKtcNrhXuXmUr7v6OuqC+VdMCz0HgmdRWVeOutRZT+ZxBxCBgLRJFnEj6EwoFhO3zwkyjMim4TwWeotUfI0o4KOuHiuzpnWRbqN/C/ohNWLx+2J6ASQ7zKTxvqhRkImog9/hWuWfBpKLZl6Ae1UlZAFMO/7PSSoEFgIULku7TX6ezXhsWpg+xYaQZbtpJJc="
      },
      {
        "name": "consumerPublicKey",
        "value": "MIIBtzCCASwGByqGSM44BAEwggEfAoGBAP1/U4EddRIpUt9KnC7s5Of2EbdSPO9EAMMeP4C2USZpRV1AIlH7WT2NWPq/xfW6MPbLm1Vs14E7gB00b/JmYLdrmVClpJ+f6AR7ECLCT7up1/63xhv4O1fnxqimFQ8E+4P208UewwI1VBNaFpEy9nXzrith1yrv8iIDGZ3RSAHHAhUAl2BQjxUjC8yykrmCouuEC/BYHPUCgYEA9+GghdabPd7LvKtcNrhXuXmUr7v6OuqC+VdMCz0HgmdRWVeOutRZT+ZxBxCBgLRJFnEj6EwoFhO3zwkyjMim4TwWeotUfI0o4KOuHiuzpnWRbqN/C/ohNWLx+2J6ASQ7zKTxvqhRkImog9/hWuWfBpKLZl6Ae1UlZAFMO/7PSSoDgYQAAoGAKwzWUj8W72SPoPKBGHOzXJLYb2guqFQfWYgf2XeyFruGM39fTt2pesxHCp70kvNjPc8HYZMa9SfhsWHkL6gZfqaLLI3St7N7WdwCgipO1R+c55vBnaO2Ts+gF+80p9n/Y5Nay8PlvwMI5ZqpYEzth9NuETnh37uh/0prdIHag7g="
      }
    ]
  }
]
```
### PUT: UPDATE STREAM
Updates an existing stream.  Throws an error if {streamId} does not already exist.

URI: /streams/{streamId}

SAMPLE REQUEST
```
{
  "id": "877ac67d-5590-424a-b2f1-5ef129b714df",
  "version": "0",
  "creator": "integrationTester",
  "creatorAppId": "integrationTesterApp",
  "creation": 1442401643958,
  "realm": "IOT1",
  "name": [
    {
      "lang": "en",
      "text": "Stream test"
    },
    {
      "lang": "zh",
      "text": "流"
    }
  ],
  "streamType": "DEVICE",
  "protocolType": "MQTT",
  "payloadSecurityType": "ENCRYPTED",
  "ownerId": "Admin",
  "streamConfiguration": {
    "logMode": "INFO",
    "pullingThreads": 1,
    "sleepTime": 80,
    "quota": 10
  },
  "payloadSecurityAttributes": [
    {
      "name": "consumerPrivateKey",
      "value": "MIIBSwIBADCCASwGByqGSM44BAEwggEfAoGBAP1/U4EddRIpUt9KnC7s5Of2EbdSPO9EAMMeP4C2USZpRV1AIlH7WT2NWPq/xfW6MPbLm1Vs14E7gB00b/JmYLdrmVClpJ+f6AR7ECLCT7up1/63xhv4O1fnxqimFQ8E+4P208UewwI1VBNaFpEy9nXzrith1yrv8iIDGZ3RSAHHAhUAl2BQjxUjC8yykrmCouuEC/BYHPUCgYEA9+GghdabPd7LvKtcNrhXuXmUr7v6OuqC+VdMCz0HgmdRWVeOutRZT+ZxBxCBgLRJFnEj6EwoFhO3zwkyjMim4TwWeotUfI0o4KOuHiuzpnWRbqN/C/ohNWLx+2J6ASQ7zKTxvqhRkImog9/hWuWfBpKLZl6Ae1UlZAFMO/7PSSoEFgIUJFdoEHuwc0dNwDqaDXwGhXZttYk="
    },
    {
      "name": "producerPublicKey",
      "value": "MIIBuDCCASwGByqGSM44BAEwggEfAoGBAP1/U4EddRIpUt9KnC7s5Of2EbdSPO9EAMMeP4C2USZpRV1AIlH7WT2NWPq/xfW6MPbLm1Vs14E7gB00b/JmYLdrmVClpJ+f6AR7ECLCT7up1/63xhv4O1fnxqimFQ8E+4P208UewwI1VBNaFpEy9nXzrith1yrv8iIDGZ3RSAHHAhUAl2BQjxUjC8yykrmCouuEC/BYHPUCgYEA9+GghdabPd7LvKtcNrhXuXmUr7v6OuqC+VdMCz0HgmdRWVeOutRZT+ZxBxCBgLRJFnEj6EwoFhO3zwkyjMim4TwWeotUfI0o4KOuHiuzpnWRbqN/C/ohNWLx+2J6ASQ7zKTxvqhRkImog9/hWuWfBpKLZl6Ae1UlZAFMO/7PSSoDgYUAAoGBANU35vjNf2TkQyhZODnGXnyX/hS8sOZC6Chms6F8BlHAW2BwC1BbxF2QCbM3vg+bzSqjcCd7n6i6pkLfsUb+r9mrVFPzgQpTeIyJtlmMt7OBS8fJEp3dyNmHixbYyrj9yG8XRhEz6UBjVLdk46/5wXZUopjyOO/uXZMOL6BkPfH8"
    },
    {
      "name": "producerPrivateKey",
      "value": "MIIBTAIBADCCASwGByqGSM44BAEwggEfAoGBAP1/U4EddRIpUt9KnC7s5Of2EbdSPO9EAMMeP4C2USZpRV1AIlH7WT2NWPq/xfW6MPbLm1Vs14E7gB00b/JmYLdrmVClpJ+f6AR7ECLCT7up1/63xhv4O1fnxqimFQ8E+4P208UewwI1VBNaFpEy9nXzrith1yrv8iIDGZ3RSAHHAhUAl2BQjxUjC8yykrmCouuEC/BYHPUCgYEA9+GghdabPd7LvKtcNrhXuXmUr7v6OuqC+VdMCz0HgmdRWVeOutRZT+ZxBxCBgLRJFnEj6EwoFhO3zwkyjMim4TwWeotUfI0o4KOuHiuzpnWRbqN/C/ohNWLx+2J6ASQ7zKTxvqhRkImog9/hWuWfBpKLZl6Ae1UlZAFMO/7PSSoEFwIVAIPsYTDQkGIElKEFqXxFrkewHGbL"
    },
    {
      "name": "consumerPublicKey",
      "value": "MIIBuDCCASwGByqGSM44BAEwggEfAoGBAP1/U4EddRIpUt9KnC7s5Of2EbdSPO9EAMMeP4C2USZpRV1AIlH7WT2NWPq/xfW6MPbLm1Vs14E7gB00b/JmYLdrmVClpJ+f6AR7ECLCT7up1/63xhv4O1fnxqimFQ8E+4P208UewwI1VBNaFpEy9nXzrith1yrv8iIDGZ3RSAHHAhUAl2BQjxUjC8yykrmCouuEC/BYHPUCgYEA9+GghdabPd7LvKtcNrhXuXmUr7v6OuqC+VdMCz0HgmdRWVeOutRZT+ZxBxCBgLRJFnEj6EwoFhO3zwkyjMim4TwWeotUfI0o4KOuHiuzpnWRbqN/C/ohNWLx+2J6ASQ7zKTxvqhRkImog9/hWuWfBpKLZl6Ae1UlZAFMO/7PSSoDgYUAAoGBAKWcP+9dHXtXz2gzXUz504J+rx00vEGVV5XTO55AALl9+hXRJP2jW8QZaOBQaE3kUNFvOamBaerpVLAyeAGk9Zw/tSmidlBKKhxB6Ye7EcIM12Rij599IUn8D7C/ol6a9vj9Lj/dRMoO4EaOD3Qrm5wvR1C70FZ+KSRgp6+YKAVa"
    }
  ]
}
```
SAMPLE RESPONSE
```
{
  "id": "877ac67d-5590-424a-b2f1-5ef129b714df",
  "version": "g2wAAAACaAJtAAAADKEXbw0sq0pXAAAEtmEBaAJtAAAADNYQX5ssZoElAAAErGEBag==",
  "creator": "integrationTester",
  "creatorAppId": "integrationTesterApp",
  "creation": 1442401776937,
  "realm": "IOT1",
  "name": [
    {
      "lang": "en",
      "text": "Stream test"
    },
    {
      "lang": "zh",
      "text": "流"
    }
  ],
  "streamType": "DEVICE",
  "protocolType": "MQTT",
  "payloadSecurityType": "ENCRYPTED",
  "ownerId": "Admin",
  "streamConfiguration": {
    "logMode": "INFO",
    "pullingThreads": 1,
    "sleepTime": 80,
    "quota": 10
  },
  "payloadSecurityAttributes": [
    {
      "name": "consumerPrivateKey",
      "value": "MIIBSwIBADCCASwGByqGSM44BAEwggEfAoGBAP1/U4EddRIpUt9KnC7s5Of2EbdSPO9EAMMeP4C2USZpRV1AIlH7WT2NWPq/xfW6MPbLm1Vs14E7gB00b/JmYLdrmVClpJ+f6AR7ECLCT7up1/63xhv4O1fnxqimFQ8E+4P208UewwI1VBNaFpEy9nXzrith1yrv8iIDGZ3RSAHHAhUAl2BQjxUjC8yykrmCouuEC/BYHPUCgYEA9+GghdabPd7LvKtcNrhXuXmUr7v6OuqC+VdMCz0HgmdRWVeOutRZT+ZxBxCBgLRJFnEj6EwoFhO3zwkyjMim4TwWeotUfI0o4KOuHiuzpnWRbqN/C/ohNWLx+2J6ASQ7zKTxvqhRkImog9/hWuWfBpKLZl6Ae1UlZAFMO/7PSSoEFgIUJFdoEHuwc0dNwDqaDXwGhXZttYk="
    },
    {
      "name": "producerPublicKey",
      "value": "MIIBuDCCASwGByqGSM44BAEwggEfAoGBAP1/U4EddRIpUt9KnC7s5Of2EbdSPO9EAMMeP4C2USZpRV1AIlH7WT2NWPq/xfW6MPbLm1Vs14E7gB00b/JmYLdrmVClpJ+f6AR7ECLCT7up1/63xhv4O1fnxqimFQ8E+4P208UewwI1VBNaFpEy9nXzrith1yrv8iIDGZ3RSAHHAhUAl2BQjxUjC8yykrmCouuEC/BYHPUCgYEA9+GghdabPd7LvKtcNrhXuXmUr7v6OuqC+VdMCz0HgmdRWVeOutRZT+ZxBxCBgLRJFnEj6EwoFhO3zwkyjMim4TwWeotUfI0o4KOuHiuzpnWRbqN/C/ohNWLx+2J6ASQ7zKTxvqhRkImog9/hWuWfBpKLZl6Ae1UlZAFMO/7PSSoDgYUAAoGBANU35vjNf2TkQyhZODnGXnyX/hS8sOZC6Chms6F8BlHAW2BwC1BbxF2QCbM3vg+bzSqjcCd7n6i6pkLfsUb+r9mrVFPzgQpTeIyJtlmMt7OBS8fJEp3dyNmHixbYyrj9yG8XRhEz6UBjVLdk46/5wXZUopjyOO/uXZMOL6BkPfH8"
    },
    {
      "name": "producerPrivateKey",
      "value": "MIIBTAIBADCCASwGByqGSM44BAEwggEfAoGBAP1/U4EddRIpUt9KnC7s5Of2EbdSPO9EAMMeP4C2USZpRV1AIlH7WT2NWPq/xfW6MPbLm1Vs14E7gB00b/JmYLdrmVClpJ+f6AR7ECLCT7up1/63xhv4O1fnxqimFQ8E+4P208UewwI1VBNaFpEy9nXzrith1yrv8iIDGZ3RSAHHAhUAl2BQjxUjC8yykrmCouuEC/BYHPUCgYEA9+GghdabPd7LvKtcNrhXuXmUr7v6OuqC+VdMCz0HgmdRWVeOutRZT+ZxBxCBgLRJFnEj6EwoFhO3zwkyjMim4TwWeotUfI0o4KOuHiuzpnWRbqN/C/ohNWLx+2J6ASQ7zKTxvqhRkImog9/hWuWfBpKLZl6Ae1UlZAFMO/7PSSoEFwIVAIPsYTDQkGIElKEFqXxFrkewHGbL"
    },
    {
      "name": "consumerPublicKey",
      "value": "MIIBuDCCASwGByqGSM44BAEwggEfAoGBAP1/U4EddRIpUt9KnC7s5Of2EbdSPO9EAMMeP4C2USZpRV1AIlH7WT2NWPq/xfW6MPbLm1Vs14E7gB00b/JmYLdrmVClpJ+f6AR7ECLCT7up1/63xhv4O1fnxqimFQ8E+4P208UewwI1VBNaFpEy9nXzrith1yrv8iIDGZ3RSAHHAhUAl2BQjxUjC8yykrmCouuEC/BYHPUCgYEA9+GghdabPd7LvKtcNrhXuXmUr7v6OuqC+VdMCz0HgmdRWVeOutRZT+ZxBxCBgLRJFnEj6EwoFhO3zwkyjMim4TwWeotUfI0o4KOuHiuzpnWRbqN/C/ohNWLx+2J6ASQ7zKTxvqhRkImog9/hWuWfBpKLZl6Ae1UlZAFMO/7PSSoDgYUAAoGBAKWcP+9dHXtXz2gzXUz504J+rx00vEGVV5XTO55AALl9+hXRJP2jW8QZaOBQaE3kUNFvOamBaerpVLAyeAGk9Zw/tSmidlBKKhxB6Ye7EcIM12Rij599IUn8D7C/ol6a9vj9Lj/dRMoO4EaOD3Qrm5wvR1C70FZ+KSRgp6+YKAVa"
    }
  ]
}
```
### DELETE: DELETE STREAM
Deletes an existing stream.

URI: /stream/{streamId}

SAMPLE REQUEST
```
Accept: application/vnd.com.covisint.platform.stream.device.v1+json
X-Realm: IOT1
```
