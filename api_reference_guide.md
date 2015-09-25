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
