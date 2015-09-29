# CommandTemplate
Command templates are created so that the response from devices can be captured in a standard form.

## POST: CREATE COMMAND TEMPLATE
Create a new command template.

URI: /commandTemplates

SAMPLE REQUEST
```
{   
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
  "creation": 1442223545432,
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
## GET: SEARCH COMMAND TEMPLATE
This method is used search event templates based on the given filter parameters.

URI: /commandTemplates

SAMPLE REQUEST
```
Accept: application/vnd.com.covisint.platform.commandTemplate.v1+json
Content-Type: application/vnd.com.covisint.platform.commandTemplate.v1+json
Authorization	Bearer 34jhbf9uinvun98v098eijre 
```
SAMPLE RESPONSE
```
[
  {
    "id": "bc02b60f-90f8-4eed-ad17-8d10f8b9bfa8",
    "version": "g2wAAAABaAJtAAAADNYQX5stIjkQAAABW2EBag==",
    "creator": "",
    "creatorAppId": "",
    "creation": 1441958618261,
    "realm": "",
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
    "realm": "",
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
    "creator": "",
    "creatorAppId": "",
    "creation": 1442223526270,
    "realm": "",
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
    "creator": "",
    "creatorAppId": "",
    "creation": 1442223545432,
    "realm": "",
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
## GET: GET COMMAND TEMPLATE
This method is used to retrieve the requested command template.

URI: /commandTemplates/ {commandTemplateId}

SAMPLE REQUEST
```
Accept: application/vnd.com.covisint.platform.commandTemplate.v1+json
Content-Type: application/vnd.com.covisint.platform.commandTemplate.v1+json
X-Realm: 
```
SAMPLE RESPONSE
```
{
  "id": "bc02b60f-90f8-4eed-ad17-8d10f8b9bfa8",
  "version": "g2wAAAABaAJtAAAADNYQX5stIjkQAAABW2EBag==",
  "creator": "",
  "creatorAppId": "",
  "creation": 1441958618261,
  "realm": "",
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
## PUT: TAG COMMAND TEMPLATE
This method tags the specified command template. 

URI: /commandTemplates/ {commandTemplateId}/tags/{tag}

## DELETE: UNTAG COMMAND TEMPLATE
Removes a tag from the event template.

URI: /commandTemplates/ {commandTemplateId}/tags/{tag}

## POST: ACTIVATE COMMAND TEMPLATE
Activates the command template.  Invoking this on an active command template has no effect.

URI: /commandTemplates/ {commandTemplateId}/tasks/activate

## POST: DEACTIVATE COMMAND TEMPLATE
Deactivates the command template.  Invoking this on an inactive command template has no effect.

URI: /eventTemplates/ {eventTemplateId}//tasks/deactivate