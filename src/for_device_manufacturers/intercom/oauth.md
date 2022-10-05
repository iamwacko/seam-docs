# Creating OAuth Endpoints
This guide will help you implement the two endpoints required for OAuth 2.0 with the Authorization Code Flow, `/authorize` and `/oauth/token`. We'll also go over some OAuth concepts to make it as easy as possible.

## Terminology

- **Resource Owner (Intercom Owner):** The person, installer, company, or end-user who owns the intercoms or can grant access to a building. This person will sign in to your server.
- **Resource/Authorization Server (Your Server):** The sever granting access to the intercom, that's what we're creating here!
- **Client (Seam):** Application requesting access to the intercom on behalf of the Intercom Owner. This is Seam! We're a client requesting access on behalf of the intercom owner, so that the interco owner can get delivery services.

## Endpoints

#### Overview
- **/authorize** - This endpoint provides a web page for the Intercom Owner to sign into.
- **/oauth/token** - Client (Seam) calls this after the user signs in.

#### GET /authorize
This endpoint can return the HTML for a webpage for a user to sign into. You can use your own internal endpoints to validate the user, then, using your database, create an authorization code just that we'll use in a later step. The authorization code just represents that a user succesffully logged in. It can be a UUID or a random string. To avoid storing codes in your database, you may consider using a signed JWT for the authorization code.

It is very important that you validate that the `redirect_uri` goes to `*.integrations.getseam.com`, or a malicious actor could gain acces to your system by redirecting the Intercom Owner to their domain.

#### POST /oauth/token
Seam sends you an Authorization code it got from `/authorize`, as well as a Client ID of "seam" and Client Secret, which we will provide you. While testing your login flow, you can use "seamsecret" as your Client Secret.

You should return an Access Token, which can be a long random string, UUID, or signed JWT. You'll use this access token to allow seam to access Devices and Access Codes.

Seam will attach the access token in it's Authorization header like so: `Authorization: Bearer <access_token>`.

## Resources
- [Auth0 Authorization Code Flow documentation](https://auth0.com/docs/get-started/authentication-and-authorization-flow/authorization-code-flow)
