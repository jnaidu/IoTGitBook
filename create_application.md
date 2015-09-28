# Create Application
The rental car company’s application which will be monitoring the health of all the vehicles needs to be created in this IoT solution.

## POST: CREATE APPLICATION
Create an application inside IoT solution. A unique applicationId for the application is returned.

SAMPLE REQUEST
```
{
    "creator": "",
    "creatorAppId": "",
    "realm": "",
    "name": [{
      "lang": "en_us", 
      "text": "Car Health Monitor App"
    }],
    "description": [{ 
      "lang": "en_us", 
      "text": "An external partner application to monitor faults in car."
    }]
}
```
SAMPLE RESPONSE
```
{
    "id": "65eb9268-b0d1-4f75-a855-71eac716a351",
    "version": "0",
    "creator": "",
    "creatorAppId": "",
    "creation": 1441377362856,
    "realm": "",
    "name": [{
      "lang": "en_us", 
      "text": "Car Health Monitor App"
    }],
    "description": [{ 
      "lang": "en_us", 
      "text": "An external partner application to monitor faults in car."
    }]
}
```