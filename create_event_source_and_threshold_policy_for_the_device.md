# Create Event Source And Threshold Policy For The Device
In order to receive an event from the device, we will have to create an event source with the deviceId and the eventTemplateId.

## POST: CREATE EVENT SOURCE
Create event source service will create an event source on IoT platform. Event source is a group of events. Events can be grouped based on all the devices that have the particular event or specific devices that have the particular event. In the following example, we will create an engine fault event source for the specific device which we created.

SAMPLE REQUEST
```
{
   "name": [{ 
      "lang": "en_US", 
      "text": "Engine fault event source"
    }],
   "description": [{ 
      "lang": "en_US", 
      "text": "A standard engine fault event source."
   }],
  "sourceDevices": [{
     "deviceId": [ "23f6db35-3416-4058-97a7-2e50e8b152e2" ],
     "eventTemplateId": [ "48c713f8-5b69-49f0-afb1-e5618ac9bae9" ]
   }]
}
```
SAMPLE RESPONSE
```
{
  "id": "231034ca-96ee-48bc-9937-aa964d8c9813",
  "version": "g2wAAAABaAJtAAAADCDMPMOaTHL2AAIpj2EBag==",
  "creation": 1442863150834,
   "realm": "",
   "name": [{ 
      "lang": "en_US", 
      "text": "Engine fault event source"
    }],
   "description": [{ 
      "lang": "en_US", 
      "text": "A standard engine fault event source."
   }],
  "sourceDevices": [{
     "deviceId": [ "23f6db35-3416-4058-97a7-2e50e8b152e2" ],
     "eventTemplateId": [ "48c713f8-5b69-49f0-afb1-e5618ac9bae9" ]
   }]
}
```
## POST: CREATE EVENT THRESHOLD POLICY
On the incoming events from the device, we can attach policies to detect if a certain condition has met. In the rental car usecase, we would like to detect if the engine fault code is greater than default value 10000.

SAMPLE REQUEST
```
{
   "name”: “Engine fault detection policy”,
   "description": [{ 
      "lang": "en_US", 
      "text": "This policy detects engine fault greater than 10000"
   }],
  "condition": {
     "all": [ { “expr”: "greaterThan(f:engine_fault_code, v:decimal(10000))”
     }]
  }
}
```
SAMPLE RESPONSE
```
{
  "id": "da920956-c33c-4ef6-bb4e-6e106be6eb09",
  "version": "g2wAAAABaAJtAAAADCDMPMOaTHL2AAIpj2EBag==",
  "creation": 1444763256834,
   "name”: “Engine fault detection policy”,
   "description": [{ 
      "lang": "en_US", 
      "text": "This policy detects engine fault greater than 10000"
   }],
  "condition": {
     "all": [ { “expr”: "greaterThan(f:engine_fault_code, v:decimal(10000))”
     }]
  }
}
```
## POST: VALIDATE EVENT THRESHOLD POLICY
Event threshold policy can be validated by some sample values. The web service will return true if the value satisfied the policy or else false.

SAMPLE REQUEST
```
{
  “engine_fault_code”: 10200
}
```
SAMPLE RESPONSE
```
{
  “result”: true
}
```