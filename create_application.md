# Create Application
In this IoT solution, create the rental car company’s application that will monitor vehicle health.

## POST: CREATE APPLICATION
Create an application inside IoT solution. A unique applicationId for the application is returned.

SAMPLE REQUEST
```
{
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
    "creation": 1441377362856,
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