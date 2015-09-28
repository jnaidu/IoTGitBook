# Create Event Stream For Device
In order to connect a device, we need to create a event stream for it. This event stream is a secure channel that allows the device to publish events and subscribe to commands. You will need the deviceId in order to create an event stream.

## POST: CREATE STREAM
Create stream service will require information on the protocol used to connect to the device and all the security information.

SAMPLE REQUEST
```
{
    "creator": "solutionImpl",
    "creatorAppId": "solutionImplApp",
    "realm": "IOT4RENTALCO",
    "ownerId": "2bbb69c0-4551-4b91-b06b-c77a6865e44c",
    "name": [{
      "lang": "en_us", 
      "text": "Device Stream for Standard IoT Car – Instance 1"
    }],
    "streamType": "DEVICE",
    "protocolType": "MQTT",
    "protocolSecurityType": "BASIC",
    "ownerSecurityType": "BASIC",
    "payloadSecurityType": "ENCRYPTED",

    "streamConfiguration": {
       "pullingThreads": 1,
       "sleepTime": 10000,
       "quota": 1
    }

}
```
SAMPLE RESPONSE
```
{
    "id": "21a98b8e-745f-48ff-b4c5-fc2a2fa04149",
    "version": "g2wAAAABaAJtAAAADCDMPMOaSy7tAAE5SGEBag==",
    "creator": "solutionImpl",
    "creatorAppId": "solutionImplApp",
    "creation": 1441488610329,
    "realm": "IOT4RENTALCO",
    "ownerId": "2bbb69c0-4551-4b91-b06b-c77a6865e44c",
    "name": [{
      "lang": "en_us", 
      "text": "Standard IoT Car – Instance 1"
    }],
    "streamType": "DEVICE",
    "protocolType": "MQTT",
    "protocolSecurityType": "BASIC",
    "ownerSecurityType": "BASIC",
    "payloadSecurityType": "ENCRYPTED",
  "ownerId": "7d7289e5-a45b-42a1-a762-1a662756e715",
  "consumerTopic": "jms99b5cc42Q2179Q421cQb2faQ125810c7f8ee",
  "producerTopic": "jms97acaf26Q5976Q4b7cQ9a71Q1014232afd0a",
  "messageProcessorTopic": "9d7d813c-24c0-47ec-8534-d0fc1d028f2b",
  "streamConfiguration": {
    "logMode": "INFO",
    "pullingThreads": 5,
    "sleepTime": 60,
    "quota": 10
  },
  "protocolSecurityAttributes": [
    {
      "name": "clientId",
      "value": "7d02da38d2db4c93"
    },
    {
      "name": "password",
      "value": "in4k3lkmlk34"
    },
{
      "name": "port",
      "value": "6849"
    },
{
      "name": "host",
      "value": "10.96.2.116"
    },
{
      "name": "username",
      "value": "3kj4n4kj3n"
    }
  ],
  "payloadSecurityAttributes": [
    {
      "name": "consumerPrivateKey",
      "value": "MIIBTAIBADCCASwGByqGSM44BAEwggEfAoGBAP1/U4EddRIpUt9KnC7s5Of2EbdSPO9EAMMeP4C2USZpRV1AIlH7WT2NWPq/xfW6MPbLm1Vs14E7gB00b/JmYLdrmVClpJ+f6AR7ECLCT7up1/63xhv4O1fnxqimFQ8E+4P208UewwI1VBNaFpEy9nXzrith1yrv8iIDGZ3RSAHHAhUAl2BQjxUjC8yykrmCouuEC/BYHPUCgYEA9+GghdabPd7LvKtcNrhXuXmUr7v6OuqC+VdMCz0HgmdRWVeOutRZT+ZxBxCBgLRJFnEj6EwoFhO3zwkyjMim4TwWeotUfI0o4KOuHiuzpnWRbqN/C/ohNWLx+2J6ASQ7zKTxvqhRkImog9/hWuWfBpKLZl6Ae1UlZAFMO/7PSSoEFwIVAIjZ0t/tMemIc5sWThfv7AXzqXUV"
    },
    {
      "name": "producerPublicKey",
      "value": "MIIBtzCCASwGByqGSM44BAEwggEfAoGBAP1/U4EddRIpUt9KnC7s5Of2EbdSPO9EAMMeP4C2USZpRV1AIlH7WT2NWPq/xfW6MPbLm1Vs14E7gB00b/JmYLdrmVClpJ+f6AR7ECLCT7up1/63xhv4O1fnxqimFQ8E+4P208UewwI1VBNaFpEy9nXzrith1yrv8iIDGZ3RSAHHAhUAl2BQjxUjC8yykrmCouuEC/BYHPUCgYEA9+GghdabPd7LvKtcNrhXuXmUr7v6OuqC+VdMCz0HgmdRWVeOutRZT+ZxBxCBgLRJFnEj6EwoFhO3zwkyjMim4TwWeotUfI0o4KOuHiuzpnWRbqN/C/ohNWLx+2J6ASQ7zKTxvqhRkImog9/hWuWfBpKLZl6Ae1UlZAFMO/7PSSoDgYQAAoGADTl8YRZw6/79kehg6r6xZ/9yzqm05cAeIrh/VROlQc1U/5BCL3eglHjjArZ2hghje4WZ0QqprzJf/KlL3zHsEb+bmOf00gbIgsl0G+SXNiOcIFWVdYWPrU8XUCtu8EikdNDmDCjJhzU4+XZpxtkQtZJeQag+AlXefzBxCEkwufg="
    },
    {
      "name": "producerPrivateKey",
      "value": "MIIBSwIBADCCASwGByqGSM44BAEwggEfAoGBAP1/U4EddRIpUt9KnC7s5Of2EbdSPO9EAMMeP4C2USZpRV1AIlH7WT2NWPq/xfW6MPbLm1Vs14E7gB00b/JmYLdrmVClpJ+f6AR7ECLCT7up1/63xhv4O1fnxqimFQ8E+4P208UewwI1VBNaFpEy9nXzrith1yrv8iIDGZ3RSAHHAhUAl2BQjxUjC8yykrmCouuEC/BYHPUCgYEA9+GghdabPd7LvKtcNrhXuXmUr7v6OuqC+VdMCz0HgmdRWVeOutRZT+ZxBxCBgLRJFnEj6EwoFhO3zwkyjMim4TwWeotUfI0o4KOuHiuzpnWRbqN/C/ohNWLx+2J6ASQ7zKTxvqhRkImog9/hWuWfBpKLZl6Ae1UlZAFMO/7PSSoEFgIUWeAidocfQHqZ8Dvr7XUl8/ZpzHI="
    },
    {
      "name": "consumerPublicKey",
      "value": "MIIBuDCCASwGByqGSM44BAEwggEfAoGBAP1/U4EddRIpUt9KnC7s5Of2EbdSPO9EAMMeP4C2USZpRV1AIlH7WT2NWPq/xfW6MPbLm1Vs14E7gB00b/JmYLdrmVClpJ+f6AR7ECLCT7up1/63xhv4O1fnxqimFQ8E+4P208UewwI1VBNaFpEy9nXzrith1yrv8iIDGZ3RSAHHAhUAl2BQjxUjC8yykrmCouuEC/BYHPUCgYEA9+GghdabPd7LvKtcNrhXuXmUr7v6OuqC+VdMCz0HgmdRWVeOutRZT+ZxBxCBgLRJFnEj6EwoFhO3zwkyjMim4TwWeotUfI0o4KOuHiuzpnWRbqN/C/ohNWLx+2J6ASQ7zKTxvqhRkImog9/hWuWfBpKLZl6Ae1UlZAFMO/7PSSoDgYUAAoGBAKOrHnrPOMXe0Qz4F2DMcGELxaT+qgoVvdu+73alqg+vgX4IepFi8nKDroj+aqDtgSG+WhVMsvYleeoFZFCsVwD1gY5GSL8EyExdOAg0Nf/MTA8Dm8vdbK8UOVGN3o6dwvnRolsJ54MGT/93girk0mOwWWt3De9bDu+sE8tZRMcI"
    }
  ],
  "ownerSecurityAttributes": [
    {
      "name": "password",
      "value": "ea9fbdd3-b26f-4b2c-af60-f067d66e4bf2"
    },
    {
      "name": "salt",
      "value": "1f8401b2-36f1-455c-b531-2d099ab6fad4"
    },
    {
      "name": "passwordHash",
      "value": "d6fa153b9677008e3818f9f85e9f4c08"
    }
  ]
}
```