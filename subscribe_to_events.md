# Subscribe To Events
After creating event streams for the device and the application, we need to specify how to route events. This is done by subscribing to appropriate stream and routing topic.

## POST: CREATE ROUTE
This service is used to create a route between source and destination topics. With this message, any event sent by the device should be received by the application.

SAMPLE REQUEST
```
{
    "creator": "solutionImpl",
    "creatorAppId": "solutionImplApp",
    "realm": "IOT4RENTALCO",
    "routeType": "EVENT",
    "streamId": "a724dfc1-38a5-45c7-b609-8eefb66f65c8",
    "routeSourceId": "3fb1ad85-edc3-4586-8fc0-c564328e6a45",
    "routingTopic": "90f71720-519b-4b36-b7ae-6c38eb956c7d"
}
```
SAMPLE RESPONSE
```
  {
    "id": "1766682f-3d7c-47a7-8f9f-468bef155b4d",
    "version": "g2wAAAABaAJtAAAADCDMPMOaTGC2AAE5jWEBag==",
    "creator": "solutionImpl",
    "creatorAppId": "solutionImplApp",
    "realm": "IOT4RENTALCO",
    "creation": 1441819423946,
    "routeSourceId": "5acb7b8e017x",
    "routeType": "EVENT",
    "streamId": "stream01",
    "routingTopic": "RoutingTopic01"
  }
```