# EventSource
Event source is a grouping of events by eventTemplateID and deviceID or eventTemplateID and deviceTemplateID.

## POST: CREATE EVENT SOURCE
Create a new eventsource.

SAMPLE REQUEST
```
Accept: application/vnd.com.covisint.platform.eventSource.v1+json
Content-type: application/vnd.com.covisint.platform.eventSource.v1+json
x-Realm: 
{
    "name": [ { "lang": "en", "value": "An event source." } ]
}
```
SAMPLE RESPONSE
```
{
  "id": "6ecf4721-1608-40f6-81a4-19ccdd335911",
  "version": "g2wAAAABaAJtAAAADNYQX5strNlqAAAzEGEBag==",
  "creation": 1442472840600,
  "name": [
    {
      "lang": "en",
      "value": "An event source."
    }
  ]
}
```
## GET: GET EVENT SOURCE
Retrieve the event source by its unique ID.

URI: /eventSources/{eventSourceId}

SAMPLE REQUEST
```
Accept: application/vnd.com.covisint.platform.eventSource.v1+json
Authorization	Bearer 34jhbf9uinvun98v098eijre
```
SAMPLE RESPONSE
```
{
  "id": "9568b779-b05f-4924-8147-50a30a4e08c7",
  "version": "g2wAAAABaAJtAAAADKEXbw0nFaz5AAACymEBag==",
  "creation": 1441971175074,
  "name": [
    {
      "lang": "en",
      "value": "{{eventSourceName}}"
    }
  ]
}
```
## GET: SEARCH EVENT SOURCE
Searches event sources based on the given query parameters.

URI: /eventSources

SAMPLE REQUEST
```
Accept: application/vnd.com.covisint.platform.eventSource.v1+json
Authorization	Bearer 34jhbf9uinvun98v098eijre
```
SAMPLE RESPONSE
```
[
  {
    "id": "9568b779-b05f-4924-8147-50a30a4e08c7",
    "version": "g2wAAAABaAJtAAAADKEXbw0nFaz5AAACymEBag==",
    "creation": 1441971175074,
    "name": [
      {
        "lang": "en",
        "value": "{{eventSourceName}}"
      }
    ]
  }
]
```
## PUT: UPDATE EVENT SOURCE
Updates an existing event source. Throws an error if {eventSourceId} does not already exist.

URI: /eventSources/{eventSourceId}

SAMPLE REQUEST
```
Accept: application/vnd.com.covisint.platform.eventSource.v1+json
Authorization	Bearer 34jhbf9uinvun98v098eijre
{
    "id": "9568b779-b05f-4924-8147-50a30a4e08c7",
    "version": "0",
    "creation": 1441971175074,
    "name": [
      {
        "lang": "en",
        "value": "{{eventSourceName}}"
      }
    ]
}
```
SAMPLE RESPONSE
```
{
  "id": "9568b779-b05f-4924-8147-50a30a4e08c7",
  "version": "g2wAAAABaAJtAAAADKEXbw0nFaz5AAACymECag==",
  "creation": 1442474369552,
  "name": [
    {
      "lang": "en",
      "value": "{{eventSourceName}}"
    }
  ]
}
```
## GET: DELETE EVENT SOURCE
Delete an existing event source. Throws an error if {eventSourceId} does not already exist.

URI: /eventSources/{eventSourceId}

SAMPLE REQUEST
```
Accept: application/vnd.com.covisint.platform.eventSource.v1+json
Authorization	Bearer 34jhbf9uinvun98v098eijre 
```