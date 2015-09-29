OAuth2 is a protocol designed to let third-party applications authenticate to perform actions as a user, without getting the user's password. Covisint uses OAuth2 for authentication and authorization of the Covisint APIs. For application-only authentication, Covisint’s implementation is based on the Client Credentials Grant flow of the OAuth 2 specification.

In application-only authentication flow, client application accesses resources on a server without user involvement. The 3rd party app simply presents its client ID and client secret in an encoded format, and if they are valid, Authorization server returns an access token (also called bearer tokens). Bearer token is passed in Authorization headers and acts as a pre-requisite to invoke any micro-services API.

**Sample Request:**
```
POST /oauth/v2/token HTTP/1.1
Host: api.us1.covisint.com
Authorization: Basic {authorization code}
Content-Type: application/x-www-form-urlencoded
grant_type= client_credentials&scope=all
```

Sample Response:
{
"access_token": "2|uxyoDbuisAehSKMhipjGG13zwt2v",
"expires_in": "899",
"scope": "email",
"token_type": "BearerToken"
}