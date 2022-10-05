# Connect Views

The first step to controlling a user's device is gettin g your application authorized against the device. To do so, Seam provides Connect Views, fully managed device authorization flows.

Here we describe what problems Connect Views solve for you, and how to use them.

## Authorizing Against Third-Party Devices is Hard
Most device manufactururers lack third-party auth strategies, such as OAuth.

Thus, to authorize their application, developers have to collect device credentials to create a session.

This is not ideal for a few resons.
1. First, selecting the brand adn collecting credentials requires building complex UX-flows. You have to manage mobile vs web, or 2-factor auth flows.
2. Second, collecting and storing device credentials is non-trivial. This increases the security and regulatory burden on developers.
3. Third, each device brand has different ways to handle authentication. This creates many edge cases and complexities.

## Connect Views
Our solution to these challanges is **Connect Views.**

Connect Views are fully implemented UI-flows. They guide your users through selecting their device brand. They securely collect their credentials. They handle 2FA. They showcase what device permissions are requested, when, and how. 

Most importantly, they handle all aspects of creating, refreshing, and deleting device authorizations.

### Creating a Connect View

When a user is ready to authorize your app against their device, create a new Connect View. Then redirect them to it.

A Connect View object has a unique URL, as well as a status indicating its completion state. 

```json
{
  "connect_webview_id": "14db0efd-50ae-45ef-9042-7f95c09082c2",
  "custom_redirect_url": null,
  "url": "https://connect.getseam.com/v1/connect_webviews/view?connect_webview_id=14db0efd-50ae-45ef-9042-7f95c09082c2&auth_token=N4ZJau88guo5adHyBAPLsYdiCdoQvxpDb",
  "workspace_id": "ab804f5a-7dd2-42c8-8d09-0beff4f795eb",
  "device_selection_mode": "none",
  "accepted_providers": [ "august", "yale", "schlage", "wyze", "nest", "kwikset" ],
  "accepted_devices": [],
  "any_provider_allowed": false,
  "any_device_allowed": null,
  "created_at": "2022-02-16T17":45":10.523Z",
  "login_successful": false,
  "status": "pending"
}
```

### Redirect & Authorize

When you redirect the user to the Connect Webview URL, they will be guided through the folowing steps:

- Select their device brand.
- Enter their credentials.
- Complete 2-factor authorization (if enabled).
- Review request device permissions by your app.

If they approve it, the Connect View's status will be updated to completed. Furthermore, their devices will be linked to your workspace

Note that if your user wishes to link devices from different brands, you will need to create a new Connect View for each brand. 
