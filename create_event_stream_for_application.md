### Create Event Stream For Application
Create an event stream to connect an application. This event stream is a secure channel that allows the application to publish commands and subscribe to events. This service will require the applicationId in order to create an event stream.

#### POST: CREATE STREAM
Create an application stream using the applicationId and the security parameters.

SAMPLE REQUEST
```
{
    "creator": "solutionImpl",
    "creatorAppId": "solutionImplApp",
    "realm": "IOT4RENTALCO",
    "ownerId": "d6dc2178-f75b-4f7f-b314-22f3da2908d5",
    "name": [{
      "lang": "en_us", 
      "text": "Application Stream for Car Fault Monitor App"
    }],
    "streamType": "APPLICATION",
    "protocolType": "JMS",
    "protocolSecurityType": "BASIC",
    "ownerSecurityType": "BASIC",
    "payloadSecurityType": "ENCRYPTED",

    "streamConfiguration": {
       "pullingThreads": 5,
       "sleepTime": 60,
       "quota": 10
    }

}
```
SAMPLE RESPONSE
```
{
    "id": "c109ea32-9786-4f57-9668-12a4d96aa644",
    "version": "g2wAAAABaAJtAAAADCDMPMOaSy7tAAE5SGEBag==",
    "creator": "solutionImpl",
    "creatorAppId": "solutionImplApp",
    "creation": 1441799941388,
    "realm": "IOT4RENTALCO",
    "ownerId": "d6dc2178-f75b-4f7f-b314-22f3da2908d5",
    "name": [{
      "lang": "en_us", 
      "text": "Application Stream for Car Fault Monitor App"
    }],
    "streamType": "APPLICATION",
    "protocolType": "JMS",
    "protocolSecurityType": "BASIC",
    "ownerSecurityType": "BASIC",
    "payloadSecurityType": "ENCRYPTED",
  "consumerTopic": "jmscb82a5b7Q0a33Q43b8Qbfc2Q017a5e8c820f",
  "producerTopic": "jmsef7bdfc3Qf563Q44eeQ9e7fQd35e8efea80c",
  "alertConsumerTopic": "jms186d086dQ190aQ4b80Qaf73Q263ef77b4d90",
  "messageProcessorTopic": "c79c8402-fc3d-419e-bd77-ce1e4b5c2284",
  "streamConfiguration": {
    "logMode": "INFO",
    "pullingThreads": 5,
    "sleepTime": 60,
    "quota": 10
  },
  "protocolSecurityAttributes": [
    {
      "name": "accountId",
      "value": "a233b0a7-033e-49e6-a7a5-d49e748280f1"
    },
    {
      "name": "password",
      "value": "admin"
    },
    {
      "name": "jmsProvider",
      "value": "CovisintJMSProvider"
    },
    {
      "name": "port",
      "value": "6849"
    },
    {
      "name": "connectionFactory",
      "value": "CovisintQueueConnectionFactory"
    },
    {
      "name": "host",
      "value": "10.96.2.116"
    },
    {
      "name": "brokerName",
      "value": "Broker #1"
    },
    {
      "name": "providerURL",
      "value": "wmjmsnaming://Broker #1@10.96.2.116:6849/CovisintJMSProvider"
    },
    {
      "name": "initialContextFactory",
      "value": "com.webmethods.jms.naming.WmJmsNamingCtxFactory"
    },
    {
      "name": "username",
      "value": "admin"
    }
  ],
  "payloadSecurityAttributes": [
    {
      "name": "consumerPrivateKey",
      "value": "MIIBSwIBADCCASwGByqGSM44BAEwggEfAoGBAP1/U4EddRIpUt9KnC7s5Of2EbdSPO9EAMMeP4C2USZpRV1AIlH7WT2NWPq/xfW6MPbLm1Vs14E7gB00b/JmYLdrmVClpJ+f6AR7ECLCT7up1/63xhv4O1fnxqimFQ8E+4P208UewwI1VBNaFpEy9nXzrith1yrv8iIDGZ3RSAHHAhUAl2BQjxUjC8yykrmCouuEC/BYHPUCgYEA9+GghdabPd7LvKtcNrhXuXmUr7v6OuqC+VdMCz0HgmdRWVeOutRZT+ZxBxCBgLRJFnEj6EwoFhO3zwkyjMim4TwWeotUfI0o4KOuHiuzpnWRbqN/C/ohNWLx+2J6ASQ7zKTxvqhRkImog9/hWuWfBpKLZl6Ae1UlZAFMO/7PSSoEFgIULX67QTUsRDuQH3sIGDani7YiVvo="
    },
    {
      "name": "producerPublicKey",
      "value": "MIIBtzCCASwGByqGSM44BAEwggEfAoGBAP1/U4EddRIpUt9KnC7s5Of2EbdSPO9EAMMeP4C2USZpRV1AIlH7WT2NWPq/xfW6MPbLm1Vs14E7gB00b/JmYLdrmVClpJ+f6AR7ECLCT7up1/63xhv4O1fnxqimFQ8E+4P208UewwI1VBNaFpEy9nXzrith1yrv8iIDGZ3RSAHHAhUAl2BQjxUjC8yykrmCouuEC/BYHPUCgYEA9+GghdabPd7LvKtcNrhXuXmUr7v6OuqC+VdMCz0HgmdRWVeOutRZT+ZxBxCBgLRJFnEj6EwoFhO3zwkyjMim4TwWeotUfI0o4KOuHiuzpnWRbqN/C/ohNWLx+2J6ASQ7zKTxvqhRkImog9/hWuWfBpKLZl6Ae1UlZAFMO/7PSSoDgYQAAoGAXkkg/xc86SKNcEsfduvWFJhzQP/1VCjwLR3U0BSSR10SLodCsyHJtVtH8oqSIYm0n56NKs4aSXh7Lz7gWbBvTfQWXy3wi0bk1X4SmOf5ucFduvQyxp2gb8+UXFq68PblWJpzfUSTOXMmYUvHNb2krsh9GAz7A8X+SVnLMDNcdaE="
    },
    {
      "name": "producerPrivateKey",
      "value": "MIIBSwIBADCCASwGByqGSM44BAEwggEfAoGBAP1/U4EddRIpUt9KnC7s5Of2EbdSPO9EAMMeP4C2USZpRV1AIlH7WT2NWPq/xfW6MPbLm1Vs14E7gB00b/JmYLdrmVClpJ+f6AR7ECLCT7up1/63xhv4O1fnxqimFQ8E+4P208UewwI1VBNaFpEy9nXzrith1yrv8iIDGZ3RSAHHAhUAl2BQjxUjC8yykrmCouuEC/BYHPUCgYEA9+GghdabPd7LvKtcNrhXuXmUr7v6OuqC+VdMCz0HgmdRWVeOutRZT+ZxBxCBgLRJFnEj6EwoFhO3zwkyjMim4TwWeotUfI0o4KOuHiuzpnWRbqN/C/ohNWLx+2J6ASQ7zKTxvqhRkImog9/hWuWfBpKLZl6Ae1UlZAFMO/7PSSoEFgIUHZ8sk17MfIlrevtMyEVrN/qkbqk="
    },
    {
      "name": "consumerPublicKey",
      "value": "MIIBtzCCASwGByqGSM44BAEwggEfAoGBAP1/U4EddRIpUt9KnC7s5Of2EbdSPO9EAMMeP4C2USZpRV1AIlH7WT2NWPq/xfW6MPbLm1Vs14E7gB00b/JmYLdrmVClpJ+f6AR7ECLCT7up1/63xhv4O1fnxqimFQ8E+4P208UewwI1VBNaFpEy9nXzrith1yrv8iIDGZ3RSAHHAhUAl2BQjxUjC8yykrmCouuEC/BYHPUCgYEA9+GghdabPd7LvKtcNrhXuXmUr7v6OuqC+VdMCz0HgmdRWVeOutRZT+ZxBxCBgLRJFnEj6EwoFhO3zwkyjMim4TwWeotUfI0o4KOuHiuzpnWRbqN/C/ohNWLx+2J6ASQ7zKTxvqhRkImog9/hWuWfBpKLZl6Ae1UlZAFMO/7PSSoDgYQAAoGANQ/I9UyX0MZFAd7kYpLt2M1o864PD3qceWCvhka1a0iABgfIvp/420Xk4/CkfvjT7y8ChO+EUZjnAp8thrlkg8py/1wAdy5DID5dc9XerT/J6g1wrSd+4zBztm7gvEuj73UB9/0J71Ybxi2vXgBKyOYD6BH1erPLUswiQ0Big44="
    }
  ],
  "ownerSecurityAttributes": [
    {
      "name": "password",
      "value": "29360826-7a1f-48a9-9967-08feb161c456"
    },
    {
      "name": "salt",
      "value": "3da95573-b3e7-4cba-a18a-2cd6b9d91344"
    },
    {
      "name": "passwordHash",
      "value": "a154c8349ae2c6f66217b36ad685918d"
    }
  ]
}
```