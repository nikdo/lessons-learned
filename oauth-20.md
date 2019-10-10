# OAuth 2.0

## Stateful vs. stateless server

There are [two distinct characters of server](https://www.quora.com/What-is-the-difference-between-Stateful-and-Stateless-Server):

*Stateful* keeps session across requests, user agent has to keep session ID across requests. Server uses `Set-cookie` response header so that session ID is sent to the server alongside with further requests.

*Stateless* server does not maintain any information across requests. Exception can be the token to verify user. If server is stateless, client, DB or both has to be stateful:

```
Web Browser (has state) <-> Web Server (stateless) <-> Database (has state)
```

A good explanation [on StackExchange](https://softwareengineering.stackexchange.com/a/346869).

## OAuth flow in user-agent vs. backend

There is a scale of options who should perform which part of OAuth flow:

1. The whole authentication flow including login screen is server-side. Client app is served by server. Client calls server for log out. All authorisation data including token are kept server-side. User-agent keeps only session ID. Backend is stateful.
2. Login button is in client app, redirect URI is a server route. The rest of the flow is server-side, client is redirected after successful authorisation. All authorisation data including token are kept server-side. User-agent keeps only session ID. Backend is stateful.
3. The whole authentication flow is on client, only exchanging a code for token is on server. Token is kept client-side, client-secret server-side. Backend is stateless.

The exchange of the OAuth code for token is necessary to [avoid storing client secret on user-agent](https://www.quora.com/Why-does-OAuth-server-return-a-authorization-code-instead-of-access-token-in-the-first-step). Client secret should be available only on client server.

But for security reasons, if there is a backend, [OAuth flow is advised to happen on backend](https://auth0.com/docs/security/store-tokens#if-a-backend-is-present) so that user-agent has access to as little information as possible.

### Persisting OAuth token

In case of SPA, received OAuth token can be stored in memory or in a cookie or local storage for persistent login. Cookie is recommended because all JavaScript code on the page has access to the local storage making the token vulnerable to attack.

URL query parameters should not be used to exchange sensitive data.

## OAuth vs JWT

OAuth 2.0 defines a protocol, i.e. specifies how tokens are transferred, JWT defines a token format. ([source](https://stackoverflow.com/a/39911472/5763764))

## Facebook OAuth

For Facebook OAuth login, there is a most popular plugin `react-facebook-login` that should handle the whole flow.

Other resources:

- [Authentication in SPA the right way](https://jcbaey.com/authentication-in-spa-reactjs-and-vuejs-the-right-way?utm_source=medium&utm_campaign=spa-authentication)
- [OAuth 2 Simplified](https://aaronparecki.com/oauth-2-simplified/)
