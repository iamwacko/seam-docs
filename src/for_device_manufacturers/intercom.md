# Creating a Seam-Compatible Intercom API
Seam integrates with Intercom systems to enable them to receive deliveries from major delivery providers. After making your intercom API seam-compatible, you don’t need to do any additional effort to be compatible with major US delivery providers, a major selling point for US intercom systems.

To make your system compatible, you should create a HTTP REST API with OAuth for authentication and CRUD-style endpoints for listing intercoms, unlocking doors, and managing access codes. This guide will walk you through creating that API, and have examples for requests/responses. If you need any support, contact `integrations@getseam.com`.

## Get Started
There are several links below, each link will walk you through the endpoints you'll need to create for Seam to interact with your system.

You'll need to host these endpoints on a publicly accessible server. We recommend something like `devicecloud.companyname.com`. If you already have a server and a domain, you can use a base path on your existing server, e.g. `companyname.com/somebasepath/...`. Seam will prepend the base path to all of our requests.

1. [Creating OAuth Endpoints](intercom/oauth.md)
2. [Creating Intercom Endpoints](intercom/crud.md)
3. []()
4. []()
5. Example Project in Python (coming soon)
