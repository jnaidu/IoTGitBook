# OAuth 2.0 Authorization
Covisint uses the OAuth 2.0 for authentication and authorization of the Covisint APIs. OAuth 2.0 is a protocol designed to let third-party applications authenticate to perform actions as a user, without getting the user's password. For application-only authentication, Covisint’s implementation is based on the Client Credentials Grant flow of the OAuth 2 specification.

At a high-level, all applications go through the following basic steps to access a Covisint API using OAuth 2.0.

## 1. Obtain OAuth 2.0 Client Credentials
To begin the process, obtain OAuth 2.0 client credentials such as client ID and client secret from Developer Portal console.

## 2. Obtain an Access Token
Your client application must request an access token from the Covisint Authorization server. The parameters that need to be passed to obtain an access token are dictated by the grant type:
* *Authorization Code:* Get an OAuth 2.0 authorization. A successful call will result in a redirection to the authorization server in order to receive the resource owner's consent. The redirection will be to the login page or directly to the consent page (if the user is already authenticated and login is not forced). Once consent is granted then the authorization server will send the user agent to the redirect_uri with query parameters state, scope, and code. For the authorization code grant type the scope is dictated by the scope value in the /authorization call.
* *Password:* This is used in conjunction with the username (or user_id) parameter to validate the resource owner's credentials. Will be ignored for any other grant type.
* *Client Credentials:* Use Client ID and Client Secret in an HTTP authorization header - Base64 encoded.
* *Refresh Token:* The refresh token returned by a previous "Authorization Code", "client Credentials" or "Password" call. For refresh_token, the scope list must not include a scope not originally granted by the resource owner.

This token is then used to access the Covisint Platform API you want to access.

In application-only authentication flow, client application accesses resources on a server without user involvement. The third-party app simply presents its client ID and client secret in an encoded format, and if they are valid, Authorization server returns an access token (also called bearer tokens).

## 3. Use the Access Token to Access a Covisint API
Bearer token is passed in Authorization headers and acts as a pre-requisite to invoke any Covisint API.

In order to make authorized calls to Covisint APIs, the application must first obtain an OAuth2.0 bearer token.

**Sample Request:**
```
POST /oauth/v3/token HTTP/1.1
Host: api.us1.covisint.com
Authorization: Basic {authorization code}
Content-Type: application/x-www-form-urlencoded
grant_type= client_credentials&scope=all
```

**Sample Response:**
```
{
"access_token": "2|uxyoDbuisAehSKMhipjgdh56t2v",
"expires_in": "899",
"scope": "email",
"token_type": "BearerToken"
}
```

## 4. Refresh the Access Token
Access tokens have a limited lifetime. An application can obtain a refresh token if it needs access to a Covisint API beyond the lifetime of an access token.