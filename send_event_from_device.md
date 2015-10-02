# Send Event from Device
To send an event from the car, the gateway on the car must perform the following steps:
1. Read engine fault code: The gateway will read the engine fault code every minute.
2. Construct message: The gateway will construct JSON string for the event. -
For example:
```
{ “engine_fault_code”: 10200 }
```
3. Encrypt message: The JSON event string must be encrypted using the producerPublicKey and encode the message in Base64 format.  
For example:
```
”ew0KInRlbXAiOiAyNS4zLA0KImh1bWlkaXR5Iiw1NC44DQp9”
```
4. Generate a messageID: A unique messageID is generated to identify the message.        
For Example:
```
“65eb9268-b0d1-4f75-a855-71eac716a351”
```
5. Construct event message: Construct a JSON message including messageID, deviceID, eventTemplateID and the encoded message.          
For Example:
```
{
    “messageID”: “65eb9268-b0d1-4f75-a855-71eac716a351”,
    “deviceID”: “7d7289e5-a45b-42a1-a762-1a662756e715”,
    “eventTemplateID”: “48c713f8-5b69-49f0-afb1-e5618ac9bae9”,
    “message”: “ew0KInRlbXAiOiAyNS4zLA0KImh1bWlkaXR5Iiw1NC44DQp9”
}
```
6. Send event: Send the event to IoT platform.