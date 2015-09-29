# Stream
Create a new stream.

## POST: CREATE STREAM
Create a new stream.

URI: /streams

SAMPLE REQUEST
```
{
  "creator": "",
   "creatorAppId": "",
  "realm": "",
  "ownerId": "Admin",
  "name": [
    {
      "lang": "zh",
      "text": "流"
    },
    {
      "lang": "en",
      "text": "Stream test"
    }
  ],
  "streamType": "DEVICE",
  "protocolType": "MQTT",
  "deviceSecurityType": "BASIC",
  "payloadSecurityType": "ENCRYPTED"
}
```
SAMPLE RESPONSE
```
{
  "id": "af57ec91-c123-4b98-96da-40a04b28e40b",
  "version": "g2wAAAABaAJtAAAADCDMPMOaSx/qAAE8V2EBag==",
  "creator": "",
  "creatorAppId": "",
  "creation": 1442303332104,
  "realm": "",
  "name": [
    {
      "lang": "en",
      "text": "Stream test"
    },
    {	
      "lang": "zh",
      "text": "流"
    }
  ],
  "streamType": "DEVICE",
  "protocolType": "MQTT",
  "payloadSecurityType": "ENCRYPTED",
  "ownerId": "Admin",
  "streamConfiguration": {
    "logMode": "INFO",
    "pullingThreads": 1,
    "sleepTime": 60,
    "quota": 10
  },
  "payloadSecurityAttributes": [
    {
      "name": "consumerPrivateKey",
      "value": "MIIBSwIBADCCASwGByqGSM44BAEwggEfAoGBAP1/U4EddRIpUt9KnC7s5Of2EbdSPO9EAMMeP4C2USZpRV1AIlH7WT2NWPq/xfW6MPbLm1Vs14E7gB00b/JmYLdrmVClpJ+f6AR7ECLCT7up1/63xhv4O1fnxqimFQ8E+4P208UewwI1VBNaFpEy9nXzrith1yrv8iIDGZ3RSAHHAhUAl2BQjxUjC8yykrmCouuEC/BYHPUCgYEA9+GghdabPd7LvKtcNrhXuXmUr7v6OuqC+VdMCz0HgmdRWVeOutRZT+ZxBxCBgLRJFnEj6EwoFhO3zwkyjMim4TwWeotUfI0o4KOuHiuzpnWRbqN/C/ohNWLx+2J6ASQ7zKTxvqhRkImog9/hWuWfBpKLZl6Ae1UlZAFMO/7PSSoEFgIUR/PBBma5H4RfGiXVh1cSGtXOrI0="
    },
    {
      "name": "producerPublicKey",
      "value": "MIIBtzCCASwGByqGSM44BAEwggEfAoGBAP1/U4EddRIpUt9KnC7s5Of2EbdSPO9EAMMeP4C2USZpRV1AIlH7WT2NWPq/xfW6MPbLm1Vs14E7gB00b/JmYLdrmVClpJ+f6AR7ECLCT7up1/63xhv4O1fnxqimFQ8E+4P208UewwI1VBNaFpEy9nXzrith1yrv8iIDGZ3RSAHHAhUAl2BQjxUjC8yykrmCouuEC/BYHPUCgYEA9+GghdabPd7LvKtcNrhXuXmUr7v6OuqC+VdMCz0HgmdRWVeOutRZT+ZxBxCBgLRJFnEj6EwoFhO3zwkyjMim4TwWeotUfI0o4KOuHiuzpnWRbqN/C/ohNWLx+2J6ASQ7zKTxvqhRkImog9/hWuWfBpKLZl6Ae1UlZAFMO/7PSSoDgYQAAoGAHogkEJzK8Q1/9qjL+EPdbGMaxACs8/0PQ8oNgZfCxkAF4jTJRtKK+6cerjf6N0kwe0bMKEhS1NnGRKM0AM3GW0/zx8EJkFdTtSBJPtsAeQNDeQHWmhYcq4YA2gXBP+n2F1NEVcgXFKROYy3zsTNsUG/xmVta15HeeG8FDnayY+Q="
    },
    {
      "name": "producerPrivateKey",
      "value": "MIIBSwIBADCCASwGByqGSM44BAEwggEfAoGBAP1/U4EddRIpUt9KnC7s5Of2EbdSPO9EAMMeP4C2USZpRV1AIlH7WT2NWPq/xfW6MPbLm1Vs14E7gB00b/JmYLdrmVClpJ+f6AR7ECLCT7up1/63xhv4O1fnxqimFQ8E+4P208UewwI1VBNaFpEy9nXzrith1yrv8iIDGZ3RSAHHAhUAl2BQjxUjC8yykrmCouuEC/BYHPUCgYEA9+GghdabPd7LvKtcNrhXuXmUr7v6OuqC+VdMCz0HgmdRWVeOutRZT+ZxBxCBgLRJFnEj6EwoFhO3zwkyjMim4TwWeotUfI0o4KOuHiuzpnWRbqN/C/ohNWLx+2J6ASQ7zKTxvqhRkImog9/hWuWfBpKLZl6Ae1UlZAFMO/7PSSoEFgIULku7TX6ezXhsWpg+xYaQZbtpJJc="
    },
    {
      "name": "consumerPublicKey",
      "value": "MIIBtzCCASwGByqGSM44BAEwggEfAoGBAP1/U4EddRIpUt9KnC7s5Of2EbdSPO9EAMMeP4C2USZpRV1AIlH7WT2NWPq/xfW6MPbLm1Vs14E7gB00b/JmYLdrmVClpJ+f6AR7ECLCT7up1/63xhv4O1fnxqimFQ8E+4P208UewwI1VBNaFpEy9nXzrith1yrv8iIDGZ3RSAHHAhUAl2BQjxUjC8yykrmCouuEC/BYHPUCgYEA9+GghdabPd7LvKtcNrhXuXmUr7v6OuqC+VdMCz0HgmdRWVeOutRZT+ZxBxCBgLRJFnEj6EwoFhO3zwkyjMim4TwWeotUfI0o4KOuHiuzpnWRbqN/C/ohNWLx+2J6ASQ7zKTxvqhRkImog9/hWuWfBpKLZl6Ae1UlZAFMO/7PSSoDgYQAAoGAKwzWUj8W72SPoPKBGHOzXJLYb2guqFQfWYgf2XeyFruGM39fTt2pesxHCp70kvNjPc8HYZMa9SfhsWHkL6gZfqaLLI3St7N7WdwCgipO1R+c55vBnaO2Ts+gF+80p9n/Y5Nay8PlvwMI5ZqpYEzth9NuETnh37uh/0prdIHag7g="
    }
  ]
}
```
## GET: SEARCH STREAM
This method is used to search stream based on the given filter parameters.

URI: /streams

SAMPLE REQUEST
```
Accept: application/vnd.com.covisint.platform.stream.v1+json 
X-Realm: 
```
SAMPLE RESPONSE
```
{
  "id": "af57ec91-c123-4b98-96da-40a04b28e40b",
  "version": "g2wAAAABaAJtAAAADCDMPMOaSx/qAAE8V2EBag==",
  "creator": "",
  "creatorAppId": "",
  "creation": 1442303332104,
  "realm": "",
  "name": [
    {
      "lang": "en",
      "text": "Stream test"
    },
    {
      "lang": "zh",
      "text": "流"
    }
  ],
  "streamType": "DEVICE",
  "protocolType": "MQTT",
  "payloadSecurityType": "ENCRYPTED",
  "ownerId": "Admin",
  "streamConfiguration": {
    "logMode": "INFO",
    "pullingThreads": 1,
    "sleepTime": 60,
    "quota": 10
  },
  "payloadSecurityAttributes": [
    {
      "name": "consumerPrivateKey",
      "value": "MIIBSwIBADCCASwGByqGSM44BAEwggEfAoGBAP1/U4EddRIpUt9KnC7s5Of2EbdSPO9EAMMeP4C2USZpRV1AIlH7WT2NWPq/xfW6MPbLm1Vs14E7gB00b/JmYLdrmVClpJ+f6AR7ECLCT7up1/63xhv4O1fnxqimFQ8E+4P208UewwI1VBNaFpEy9nXzrith1yrv8iIDGZ3RSAHHAhUAl2BQjxUjC8yykrmCouuEC/BYHPUCgYEA9+GghdabPd7LvKtcNrhXuXmUr7v6OuqC+VdMCz0HgmdRWVeOutRZT+ZxBxCBgLRJFnEj6EwoFhO3zwkyjMim4TwWeotUfI0o4KOuHiuzpnWRbqN/C/ohNWLx+2J6ASQ7zKTxvqhRkImog9/hWuWfBpKLZl6Ae1UlZAFMO/7PSSoEFgIUR/PBBma5H4RfGiXVh1cSGtXOrI0="
    },
    {
      "name": "producerPublicKey",
      "value": "MIIBtzCCASwGByqGSM44BAEwggEfAoGBAP1/U4EddRIpUt9KnC7s5Of2EbdSPO9EAMMeP4C2USZpRV1AIlH7WT2NWPq/xfW6MPbLm1Vs14E7gB00b/JmYLdrmVClpJ+f6AR7ECLCT7up1/63xhv4O1fnxqimFQ8E+4P208UewwI1VBNaFpEy9nXzrith1yrv8iIDGZ3RSAHHAhUAl2BQjxUjC8yykrmCouuEC/BYHPUCgYEA9+GghdabPd7LvKtcNrhXuXmUr7v6OuqC+VdMCz0HgmdRWVeOutRZT+ZxBxCBgLRJFnEj6EwoFhO3zwkyjMim4TwWeotUfI0o4KOuHiuzpnWRbqN/C/ohNWLx+2J6ASQ7zKTxvqhRkImog9/hWuWfBpKLZl6Ae1UlZAFMO/7PSSoDgYQAAoGAHogkEJzK8Q1/9qjL+EPdbGMaxACs8/0PQ8oNgZfCxkAF4jTJRtKK+6cerjf6N0kwe0bMKEhS1NnGRKM0AM3GW0/zx8EJkFdTtSBJPtsAeQNDeQHWmhYcq4YA2gXBP+n2F1NEVcgXFKROYy3zsTNsUG/xmVta15HeeG8FDnayY+Q="
    },
    {
      "name": "producerPrivateKey",
      "value": "MIIBSwIBADCCASwGByqGSM44BAEwggEfAoGBAP1/U4EddRIpUt9KnC7s5Of2EbdSPO9EAMMeP4C2USZpRV1AIlH7WT2NWPq/xfW6MPbLm1Vs14E7gB00b/JmYLdrmVClpJ+f6AR7ECLCT7up1/63xhv4O1fnxqimFQ8E+4P208UewwI1VBNaFpEy9nXzrith1yrv8iIDGZ3RSAHHAhUAl2BQjxUjC8yykrmCouuEC/BYHPUCgYEA9+GghdabPd7LvKtcNrhXuXmUr7v6OuqC+VdMCz0HgmdRWVeOutRZT+ZxBxCBgLRJFnEj6EwoFhO3zwkyjMim4TwWeotUfI0o4KOuHiuzpnWRbqN/C/ohNWLx+2J6ASQ7zKTxvqhRkImog9/hWuWfBpKLZl6Ae1UlZAFMO/7PSSoEFgIULku7TX6ezXhsWpg+xYaQZbtpJJc="
    },
    {
      "name": "consumerPublicKey",
      "value": "MIIBtzCCASwGByqGSM44BAEwggEfAoGBAP1/U4EddRIpUt9KnC7s5Of2EbdSPO9EAMMeP4C2USZpRV1AIlH7WT2NWPq/xfW6MPbLm1Vs14E7gB00b/JmYLdrmVClpJ+f6AR7ECLCT7up1/63xhv4O1fnxqimFQ8E+4P208UewwI1VBNaFpEy9nXzrith1yrv8iIDGZ3RSAHHAhUAl2BQjxUjC8yykrmCouuEC/BYHPUCgYEA9+GghdabPd7LvKtcNrhXuXmUr7v6OuqC+VdMCz0HgmdRWVeOutRZT+ZxBxCBgLRJFnEj6EwoFhO3zwkyjMim4TwWeotUfI0o4KOuHiuzpnWRbqN/C/ohNWLx+2J6ASQ7zKTxvqhRkImog9/hWuWfBpKLZl6Ae1UlZAFMO/7PSSoDgYQAAoGAKwzWUj8W72SPoPKBGHOzXJLYb2guqFQfWYgf2XeyFruGM39fTt2pesxHCp70kvNjPc8HYZMa9SfhsWHkL6gZfqaLLI3St7N7WdwCgipO1R+c55vBnaO2Ts+gF+80p9n/Y5Nay8PlvwMI5ZqpYEzth9NuETnh37uh/0prdIHag7g="
    }
  ]
}
```
## GET: GET STREAM
This method is used to retrieve stream by stream ID.

URI: /streams/{streamId}

SAMPLE REQUEST
```
Accept: application/vnd.com.covisint.platform.stream.v1+json
X-Realm: 
```
SAMPLE RESPONSE
```
[
  {
    "id": "af57ec91-c123-4b98-96da-40a04b28e40b",
    "version": "g2wAAAABaAJtAAAADCDMPMOaSx/qAAE8V2EBag==",
    "creator": "",
    "creatorAppId": "",
    "creation": 1442303332104,
    "realm": "",
    "name": [
      {
        "lang": "en",
        "text": "Stream test"
      },
      {
        "lang": "zh",
        "text": "流"
      }
    ],
    "streamType": "DEVICE",
    "protocolType": "MQTT",
    "payloadSecurityType": "ENCRYPTED",
    "ownerId": "Admin",
    "streamConfiguration": {
      "logMode": "INFO",
      "pullingThreads": 1,
      "sleepTime": 60,
      "quota": 10
    },
    "payloadSecurityAttributes": [
      {
        "name": "consumerPrivateKey",
        "value": "MIIBSwIBADCCASwGByqGSM44BAEwggEfAoGBAP1/U4EddRIpUt9KnC7s5Of2EbdSPO9EAMMeP4C2USZpRV1AIlH7WT2NWPq/xfW6MPbLm1Vs14E7gB00b/JmYLdrmVClpJ+f6AR7ECLCT7up1/63xhv4O1fnxqimFQ8E+4P208UewwI1VBNaFpEy9nXzrith1yrv8iIDGZ3RSAHHAhUAl2BQjxUjC8yykrmCouuEC/BYHPUCgYEA9+GghdabPd7LvKtcNrhXuXmUr7v6OuqC+VdMCz0HgmdRWVeOutRZT+ZxBxCBgLRJFnEj6EwoFhO3zwkyjMim4TwWeotUfI0o4KOuHiuzpnWRbqN/C/ohNWLx+2J6ASQ7zKTxvqhRkImog9/hWuWfBpKLZl6Ae1UlZAFMO/7PSSoEFgIUR/PBBma5H4RfGiXVh1cSGtXOrI0="
      },
      {
        "name": "producerPublicKey",
        "value": "MIIBtzCCASwGByqGSM44BAEwggEfAoGBAP1/U4EddRIpUt9KnC7s5Of2EbdSPO9EAMMeP4C2USZpRV1AIlH7WT2NWPq/xfW6MPbLm1Vs14E7gB00b/JmYLdrmVClpJ+f6AR7ECLCT7up1/63xhv4O1fnxqimFQ8E+4P208UewwI1VBNaFpEy9nXzrith1yrv8iIDGZ3RSAHHAhUAl2BQjxUjC8yykrmCouuEC/BYHPUCgYEA9+GghdabPd7LvKtcNrhXuXmUr7v6OuqC+VdMCz0HgmdRWVeOutRZT+ZxBxCBgLRJFnEj6EwoFhO3zwkyjMim4TwWeotUfI0o4KOuHiuzpnWRbqN/C/ohNWLx+2J6ASQ7zKTxvqhRkImog9/hWuWfBpKLZl6Ae1UlZAFMO/7PSSoDgYQAAoGAHogkEJzK8Q1/9qjL+EPdbGMaxACs8/0PQ8oNgZfCxkAF4jTJRtKK+6cerjf6N0kwe0bMKEhS1NnGRKM0AM3GW0/zx8EJkFdTtSBJPtsAeQNDeQHWmhYcq4YA2gXBP+n2F1NEVcgXFKROYy3zsTNsUG/xmVta15HeeG8FDnayY+Q="
      },
      {
        "name": "producerPrivateKey",
        "value": "MIIBSwIBADCCASwGByqGSM44BAEwggEfAoGBAP1/U4EddRIpUt9KnC7s5Of2EbdSPO9EAMMeP4C2USZpRV1AIlH7WT2NWPq/xfW6MPbLm1Vs14E7gB00b/JmYLdrmVClpJ+f6AR7ECLCT7up1/63xhv4O1fnxqimFQ8E+4P208UewwI1VBNaFpEy9nXzrith1yrv8iIDGZ3RSAHHAhUAl2BQjxUjC8yykrmCouuEC/BYHPUCgYEA9+GghdabPd7LvKtcNrhXuXmUr7v6OuqC+VdMCz0HgmdRWVeOutRZT+ZxBxCBgLRJFnEj6EwoFhO3zwkyjMim4TwWeotUfI0o4KOuHiuzpnWRbqN/C/ohNWLx+2J6ASQ7zKTxvqhRkImog9/hWuWfBpKLZl6Ae1UlZAFMO/7PSSoEFgIULku7TX6ezXhsWpg+xYaQZbtpJJc="
      },
      {
        "name": "consumerPublicKey",
        "value": "MIIBtzCCASwGByqGSM44BAEwggEfAoGBAP1/U4EddRIpUt9KnC7s5Of2EbdSPO9EAMMeP4C2USZpRV1AIlH7WT2NWPq/xfW6MPbLm1Vs14E7gB00b/JmYLdrmVClpJ+f6AR7ECLCT7up1/63xhv4O1fnxqimFQ8E+4P208UewwI1VBNaFpEy9nXzrith1yrv8iIDGZ3RSAHHAhUAl2BQjxUjC8yykrmCouuEC/BYHPUCgYEA9+GghdabPd7LvKtcNrhXuXmUr7v6OuqC+VdMCz0HgmdRWVeOutRZT+ZxBxCBgLRJFnEj6EwoFhO3zwkyjMim4TwWeotUfI0o4KOuHiuzpnWRbqN/C/ohNWLx+2J6ASQ7zKTxvqhRkImog9/hWuWfBpKLZl6Ae1UlZAFMO/7PSSoDgYQAAoGAKwzWUj8W72SPoPKBGHOzXJLYb2guqFQfWYgf2XeyFruGM39fTt2pesxHCp70kvNjPc8HYZMa9SfhsWHkL6gZfqaLLI3St7N7WdwCgipO1R+c55vBnaO2Ts+gF+80p9n/Y5Nay8PlvwMI5ZqpYEzth9NuETnh37uh/0prdIHag7g="
      }
    ]
  }
]
```
## PUT: UPDATE STREAM
Updates an existing stream.  Throws an error if {streamId} does not already exist.

URI: /streams/{streamId}

SAMPLE REQUEST
```
{
  "id": "877ac67d-5590-424a-b2f1-5ef129b714df",
  "version": "0",
  "creator": "",
  "creatorAppId": "",
  "creation": 1442401643958,
  "realm": "",
  "name": [
    {
      "lang": "en",
      "text": "Stream test"
    },
    {
      "lang": "zh",
      "text": "流"
    }
  ],
  "streamType": "DEVICE",
  "protocolType": "MQTT",
  "payloadSecurityType": "ENCRYPTED",
  "ownerId": "Admin",
  "streamConfiguration": {
    "logMode": "INFO",
    "pullingThreads": 1,
    "sleepTime": 80,
    "quota": 10
  },
  "payloadSecurityAttributes": [
    {
      "name": "consumerPrivateKey",
      "value": "MIIBSwIBADCCASwGByqGSM44BAEwggEfAoGBAP1/U4EddRIpUt9KnC7s5Of2EbdSPO9EAMMeP4C2USZpRV1AIlH7WT2NWPq/xfW6MPbLm1Vs14E7gB00b/JmYLdrmVClpJ+f6AR7ECLCT7up1/63xhv4O1fnxqimFQ8E+4P208UewwI1VBNaFpEy9nXzrith1yrv8iIDGZ3RSAHHAhUAl2BQjxUjC8yykrmCouuEC/BYHPUCgYEA9+GghdabPd7LvKtcNrhXuXmUr7v6OuqC+VdMCz0HgmdRWVeOutRZT+ZxBxCBgLRJFnEj6EwoFhO3zwkyjMim4TwWeotUfI0o4KOuHiuzpnWRbqN/C/ohNWLx+2J6ASQ7zKTxvqhRkImog9/hWuWfBpKLZl6Ae1UlZAFMO/7PSSoEFgIUJFdoEHuwc0dNwDqaDXwGhXZttYk="
    },
    {
      "name": "producerPublicKey",
      "value": "MIIBuDCCASwGByqGSM44BAEwggEfAoGBAP1/U4EddRIpUt9KnC7s5Of2EbdSPO9EAMMeP4C2USZpRV1AIlH7WT2NWPq/xfW6MPbLm1Vs14E7gB00b/JmYLdrmVClpJ+f6AR7ECLCT7up1/63xhv4O1fnxqimFQ8E+4P208UewwI1VBNaFpEy9nXzrith1yrv8iIDGZ3RSAHHAhUAl2BQjxUjC8yykrmCouuEC/BYHPUCgYEA9+GghdabPd7LvKtcNrhXuXmUr7v6OuqC+VdMCz0HgmdRWVeOutRZT+ZxBxCBgLRJFnEj6EwoFhO3zwkyjMim4TwWeotUfI0o4KOuHiuzpnWRbqN/C/ohNWLx+2J6ASQ7zKTxvqhRkImog9/hWuWfBpKLZl6Ae1UlZAFMO/7PSSoDgYUAAoGBANU35vjNf2TkQyhZODnGXnyX/hS8sOZC6Chms6F8BlHAW2BwC1BbxF2QCbM3vg+bzSqjcCd7n6i6pkLfsUb+r9mrVFPzgQpTeIyJtlmMt7OBS8fJEp3dyNmHixbYyrj9yG8XRhEz6UBjVLdk46/5wXZUopjyOO/uXZMOL6BkPfH8"
    },
    {
      "name": "producerPrivateKey",
      "value": "MIIBTAIBADCCASwGByqGSM44BAEwggEfAoGBAP1/U4EddRIpUt9KnC7s5Of2EbdSPO9EAMMeP4C2USZpRV1AIlH7WT2NWPq/xfW6MPbLm1Vs14E7gB00b/JmYLdrmVClpJ+f6AR7ECLCT7up1/63xhv4O1fnxqimFQ8E+4P208UewwI1VBNaFpEy9nXzrith1yrv8iIDGZ3RSAHHAhUAl2BQjxUjC8yykrmCouuEC/BYHPUCgYEA9+GghdabPd7LvKtcNrhXuXmUr7v6OuqC+VdMCz0HgmdRWVeOutRZT+ZxBxCBgLRJFnEj6EwoFhO3zwkyjMim4TwWeotUfI0o4KOuHiuzpnWRbqN/C/ohNWLx+2J6ASQ7zKTxvqhRkImog9/hWuWfBpKLZl6Ae1UlZAFMO/7PSSoEFwIVAIPsYTDQkGIElKEFqXxFrkewHGbL"
    },
    {
      "name": "consumerPublicKey",
      "value": "MIIBuDCCASwGByqGSM44BAEwggEfAoGBAP1/U4EddRIpUt9KnC7s5Of2EbdSPO9EAMMeP4C2USZpRV1AIlH7WT2NWPq/xfW6MPbLm1Vs14E7gB00b/JmYLdrmVClpJ+f6AR7ECLCT7up1/63xhv4O1fnxqimFQ8E+4P208UewwI1VBNaFpEy9nXzrith1yrv8iIDGZ3RSAHHAhUAl2BQjxUjC8yykrmCouuEC/BYHPUCgYEA9+GghdabPd7LvKtcNrhXuXmUr7v6OuqC+VdMCz0HgmdRWVeOutRZT+ZxBxCBgLRJFnEj6EwoFhO3zwkyjMim4TwWeotUfI0o4KOuHiuzpnWRbqN/C/ohNWLx+2J6ASQ7zKTxvqhRkImog9/hWuWfBpKLZl6Ae1UlZAFMO/7PSSoDgYUAAoGBAKWcP+9dHXtXz2gzXUz504J+rx00vEGVV5XTO55AALl9+hXRJP2jW8QZaOBQaE3kUNFvOamBaerpVLAyeAGk9Zw/tSmidlBKKhxB6Ye7EcIM12Rij599IUn8D7C/ol6a9vj9Lj/dRMoO4EaOD3Qrm5wvR1C70FZ+KSRgp6+YKAVa"
    }
  ]
}
```
SAMPLE RESPONSE
```
{
  "id": "877ac67d-5590-424a-b2f1-5ef129b714df",
  "version": "g2wAAAACaAJtAAAADKEXbw0sq0pXAAAEtmEBaAJtAAAADNYQX5ssZoElAAAErGEBag==",
  "creator": "",
  "creatorAppId": "",
  "creation": 1442401776937,
  "realm": "",
  "name": [
    {
      "lang": "en",
      "text": "Stream test"
    },
    {
      "lang": "zh",
      "text": "流"
    }
  ],
  "streamType": "DEVICE",
  "protocolType": "MQTT",
  "payloadSecurityType": "ENCRYPTED",
  "ownerId": "Admin",
  "streamConfiguration": {
    "logMode": "INFO",
    "pullingThreads": 1,
    "sleepTime": 80,
    "quota": 10
  },
  "payloadSecurityAttributes": [
    {
      "name": "consumerPrivateKey",
      "value": "MIIBSwIBADCCASwGByqGSM44BAEwggEfAoGBAP1/U4EddRIpUt9KnC7s5Of2EbdSPO9EAMMeP4C2USZpRV1AIlH7WT2NWPq/xfW6MPbLm1Vs14E7gB00b/JmYLdrmVClpJ+f6AR7ECLCT7up1/63xhv4O1fnxqimFQ8E+4P208UewwI1VBNaFpEy9nXzrith1yrv8iIDGZ3RSAHHAhUAl2BQjxUjC8yykrmCouuEC/BYHPUCgYEA9+GghdabPd7LvKtcNrhXuXmUr7v6OuqC+VdMCz0HgmdRWVeOutRZT+ZxBxCBgLRJFnEj6EwoFhO3zwkyjMim4TwWeotUfI0o4KOuHiuzpnWRbqN/C/ohNWLx+2J6ASQ7zKTxvqhRkImog9/hWuWfBpKLZl6Ae1UlZAFMO/7PSSoEFgIUJFdoEHuwc0dNwDqaDXwGhXZttYk="
    },
    {
      "name": "producerPublicKey",
      "value": "MIIBuDCCASwGByqGSM44BAEwggEfAoGBAP1/U4EddRIpUt9KnC7s5Of2EbdSPO9EAMMeP4C2USZpRV1AIlH7WT2NWPq/xfW6MPbLm1Vs14E7gB00b/JmYLdrmVClpJ+f6AR7ECLCT7up1/63xhv4O1fnxqimFQ8E+4P208UewwI1VBNaFpEy9nXzrith1yrv8iIDGZ3RSAHHAhUAl2BQjxUjC8yykrmCouuEC/BYHPUCgYEA9+GghdabPd7LvKtcNrhXuXmUr7v6OuqC+VdMCz0HgmdRWVeOutRZT+ZxBxCBgLRJFnEj6EwoFhO3zwkyjMim4TwWeotUfI0o4KOuHiuzpnWRbqN/C/ohNWLx+2J6ASQ7zKTxvqhRkImog9/hWuWfBpKLZl6Ae1UlZAFMO/7PSSoDgYUAAoGBANU35vjNf2TkQyhZODnGXnyX/hS8sOZC6Chms6F8BlHAW2BwC1BbxF2QCbM3vg+bzSqjcCd7n6i6pkLfsUb+r9mrVFPzgQpTeIyJtlmMt7OBS8fJEp3dyNmHixbYyrj9yG8XRhEz6UBjVLdk46/5wXZUopjyOO/uXZMOL6BkPfH8"
    },
    {
      "name": "producerPrivateKey",
      "value": "MIIBTAIBADCCASwGByqGSM44BAEwggEfAoGBAP1/U4EddRIpUt9KnC7s5Of2EbdSPO9EAMMeP4C2USZpRV1AIlH7WT2NWPq/xfW6MPbLm1Vs14E7gB00b/JmYLdrmVClpJ+f6AR7ECLCT7up1/63xhv4O1fnxqimFQ8E+4P208UewwI1VBNaFpEy9nXzrith1yrv8iIDGZ3RSAHHAhUAl2BQjxUjC8yykrmCouuEC/BYHPUCgYEA9+GghdabPd7LvKtcNrhXuXmUr7v6OuqC+VdMCz0HgmdRWVeOutRZT+ZxBxCBgLRJFnEj6EwoFhO3zwkyjMim4TwWeotUfI0o4KOuHiuzpnWRbqN/C/ohNWLx+2J6ASQ7zKTxvqhRkImog9/hWuWfBpKLZl6Ae1UlZAFMO/7PSSoEFwIVAIPsYTDQkGIElKEFqXxFrkewHGbL"
    },
    {
      "name": "consumerPublicKey",
      "value": "MIIBuDCCASwGByqGSM44BAEwggEfAoGBAP1/U4EddRIpUt9KnC7s5Of2EbdSPO9EAMMeP4C2USZpRV1AIlH7WT2NWPq/xfW6MPbLm1Vs14E7gB00b/JmYLdrmVClpJ+f6AR7ECLCT7up1/63xhv4O1fnxqimFQ8E+4P208UewwI1VBNaFpEy9nXzrith1yrv8iIDGZ3RSAHHAhUAl2BQjxUjC8yykrmCouuEC/BYHPUCgYEA9+GghdabPd7LvKtcNrhXuXmUr7v6OuqC+VdMCz0HgmdRWVeOutRZT+ZxBxCBgLRJFnEj6EwoFhO3zwkyjMim4TwWeotUfI0o4KOuHiuzpnWRbqN/C/ohNWLx+2J6ASQ7zKTxvqhRkImog9/hWuWfBpKLZl6Ae1UlZAFMO/7PSSoDgYUAAoGBAKWcP+9dHXtXz2gzXUz504J+rx00vEGVV5XTO55AALl9+hXRJP2jW8QZaOBQaE3kUNFvOamBaerpVLAyeAGk9Zw/tSmidlBKKhxB6Ye7EcIM12Rij599IUn8D7C/ol6a9vj9Lj/dRMoO4EaOD3Qrm5wvR1C70FZ+KSRgp6+YKAVa"
    }
  ]
}
```
## DELETE: DELETE STREAM
Deletes an existing stream.

URI: /stream/{streamId}

SAMPLE REQUEST
```
Accept: application/vnd.com.covisint.platform.stream.device.v1+json
X-Realm: 
```
## POST: REGISTER DEVICE WITH STREAM
Registers a device with a Connector Stream.

URI: /streams/{streamId}/devices

SAMPLE REQUEST
```
{
  "creator": "EADAMS",
  "creatorAppId": "postman",
  "realm": "{{iotRealmHeader}}",
  "deviceId": "{{$timestamp}}",
  "streamId": "6cc3260f-f5a2-4cfe-ab28-f5a0cba27785"
}
```
SAMPLE RESPONSE
```
{
  "id": "357b36af-208f-4549-b257-7e47d80cf684",
  "version": "g2wAAAABaAJtAAAADCDMPMOaSx/qAAE8c2EBag==",
  "creator": "EADAMS",
  "creatorAppId": "postman",
  "creation": 1442316982919,
  "realm": "",
  "deviceId": "1442316983",
  "streamId": "6cc3260f-f5a2-4cfe-ab28-f5a0cba27785"
}
```
## GET: GET ALL DEVICES WITH STREAM
List all devices attached to this stream.

URI: /streams/{streamId}/devices

SAMPLE REQUEST
```
Accept: application/vnd.com.covisint.platform.stream.device.v1+json
X-Realm: 
```
SAMPLE RESPONSE
```
[
  {
    "id": "357b36af-208f-4549-b257-7e47d80cf684",
    "version": "g2wAAAABaAJtAAAADCDMPMOaSx/qAAE8c2EBag==",
    "creator": "EADAMS",
    "creatorAppId": "postman",
    "creation": 1442316982919,
    "realm": "",
    "deviceId": "1442316983",
    "streamId": "6cc3260f-f5a2-4cfe-ab28-f5a0cba27785"
  },
  {
    "id": "3ec81cdb-fea9-4b3d-a768-49356711f13d",
    "version": "g2wAAAABaAJtAAAADCDMPMOaSy7tAAE8e2EBag==",
    "creator": "EADAMS",
    "creatorAppId": "postman",
    "creation": 1442316681139,
    "realm": "",
    "deviceId": "1442316680",
    "streamId": "6cc3260f-f5a2-4cfe-ab28-f5a0cba27785"
  }
]
```

## GET: GET DEVICE BY ID FROM STREAM
Retrieves the device associated with the stream by its unique id.

URI: /streams/{streamId}/{deviceId}

SAMPLE REQUEST
```
Accept: application/vnd.com.covisint.platform.stream.device.v1+json
X-Realm: 
```
SAMPLE RESPONSE
```
{
  "status": 404,
  "apiMessage": "A resource with the following ID was not found: 1442316983",
  "apiStatusCode": "framework:resource:missing"
} 
```
## PUT: UPDATE DEVICE WITH STREAM
PENDING

URI: /streams/{streamId}/{deviceId} 

## PUT: REMOVE DEVICE FROM STREAM
PENDING

URI: /streams/{streamId}/{deviceId}