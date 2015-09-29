## Routes
Routes connect source and destination topics.

### POST: CREATE ROUTE
Create a new route.

URI: /routes

SAMPLE REQUEST
```
Accept: application/vnd.com.covisint.platform.messaging.route.v1+json
Content-type: application/vnd.com.covisint.platform.messaging.route.v1+json
x-Realm: IOT1
{
	"creator": "SGORIAL2",
  	"creatorAppId": "postman",
  	"realm": "{{iotRealmHeader}}",
  	"routeType": "EVENT",
  	"streamId": "stream01",
  	"routeSourceId": "5acb7b8e017x",
  	"routingTopic": "RoutingTopic01",
  	"workflowId": "workflow_1",
  	"workflowTopic": "WorkflowTopic01",
  	"workflowTopology": "WorkflowTopology01"
}
```
SAMPLE RESPONSE
```
{
  "id": "bf069bb8-c4cf-418f-814f-216b4aac7ec2",
  "version": "g2wAAAABaAJtAAAADNYQX5stnA6MAAAEdGEBag==",
  "creator": "SGORIAL2",
  "creatorAppId": "postman",
  "creation": 1442389711913,
  "realm": "IOT1",
  "routeId": "bf069bb8-c4cf-418f-814f-216b4aac7ec2",
  "routeSourceId": "5acb7b8e017x",
  "routeType": "EVENT",
  "streamId": "stream01",
  "workflowId": "workflow_1",
  "workflowTopology": "WorkflowTopology01",
  "workflowTopic": "WorkflowTopic01",
  "routingTopic": "RoutingTopic01"
}
```

### GET: LIST ROUTE
List of available routes.

URI: /routes

SAMPLE REQUEST
```
Accept: application/vnd.com.covisint.platform.messaging.route.v1+json
x-Realm :IOT1
```
SAMPLE RESPONSE
```
[
  {
    "id": "bd8e0952-a7fa-4654-86b2-687e94a527e6",
    "version": "g2wAAAABaAJtAAAADCDMPMOaSzKTAAE5fWEBag==",
    "creator": "SGORIAL2",
    "creatorAppId": "postman",
    "creation": 1441795645043,
    "realm": "IOT1",
    "routeId": "bd8e0952-a7fa-4654-86b2-687e94a527e6",
    "routeSourceId": "5acb7b8e017x",
    "routeType": "EVENT",
    "streamId": "stream01",
    "workflowId": "workflow_1",
    "workflowTopology": "WorkflowTopology01",
    "workflowTopic": "WorkflowTopic01",
    "routingTopic": "RoutingTopic01"
  }
]
```
### GET: GET ROUTE
This method is used to retrieve the requested route.

URI: /routes/{routeId}

SAMPLE REQUEST
```
Accept: application/vnd.com.covisint.platform.messaging.route.v1+json
x-realm : IOT1
```
SAMPLE RESPONSE
```
{
  "id": "bd8e0952-a7fa-4654-86b2-687e94a527e6",
  "version": "g2wAAAABaAJtAAAADCDMPMOaSzKTAAE5fWEBag==",
  "creator": "SGORIAL2",
  "creatorAppId": "postman",
  "creation": 1441795645043,
  "realm": "IOT1",
  "routeId": "bd8e0952-a7fa-4654-86b2-687e94a527e6",
  "routeSourceId": "5acb7b8e017x",
  "routeType": "EVENT",
  "streamId": "stream01",
  "workflowId": "workflow_1",
  "workflowTopology": "WorkflowTopology01",
  "workflowTopic": "WorkflowTopic01",
  "routingTopic": "RoutingTopic01"
}
```
### PUT: UPDATE ROUTE
This method updates the route.

URI: /routes/{routeId}

SAMPLE REQUEST
```
Accept: application/vnd.com.covisint.platform.messaging.route.v1+json
x-realm : IOT1
{
  "id": "bf069bb8-c4cf-418f-814f-216b4aac7ec2",
  "version": "0",
  "creator": "SGORIAL2",
  "creatorAppId": "postman",
  "creation": 1442389711913,
  "realm": "IOT1",
  "routeId": "bf069bb8-c4cf-418f-814f-216b4aac7ec2",
  "routeSourceId": "5acb7b8e017x",
  "routeType": "EVENT",
  "streamId": "stream01",
  "workflowId": "workflow_1",
  "workflowTopology": "WorkflowTopology02",
  "workflowTopic": "WorkflowTopic02",
  "routingTopic": "RoutingTopic02"
}
```
SAMPLE RESPONSE
```
{
  "id": "bf069bb8-c4cf-418f-814f-216b4aac7ec2",
  "version": "g2wAAAACaAJtAAAADKEXbw0nF1JWAAAEfmEBaAJtAAAADNYQX5stnA6MAAAEdGEBag==",
  "creator": "SGORIAL2",
  "creatorAppId": "postman",
  "creation": 1442395373085,
  "realm": "IOT1",
  "routeId": "bf069bb8-c4cf-418f-814f-216b4aac7ec2",
  "routeSourceId": "5acb7b8e017x",
  "routeType": "EVENT",
  "streamId": "stream01",
  "workflowId": "workflow_1",
  "workflowTopology": "WorkflowTopology02",
  "workflowTopic": "WorkflowTopic02",
  "routingTopic": "RoutingTopic02"
}
```
### DELETE: DELETE ROUTE
Delete an existing route. Throws an error if {routeId} does not already exist.

URI: /routes/{routeId}

SAMPLE REQUEST
```
Accept: application/vnd.com.covisint.platform.messaging.route.v1+json
x-realm : IOT1
```