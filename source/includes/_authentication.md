# Authentication

SalesSeek uses cookies as the authentication method. Cookies are encrypted by the server in the HTTPS Response after login.

SalesSeek expects the cookie to be included in all API requests to the server after login. For this reason the first step should be Login and then any sequence of requests to the API can follow.

## Authentication Attributes

> The JSON encoded response looks like this.

```json
{
  "id": "a938196a-152d-40f3-ab3d-404385143a4b",
  "name": "Example Login",
  "is_admin": true,
  "email_address": "example@salesseek.co.uk",
  "client_id": "913fa210-edf2-49c3-86a2-ec8f063d92ea",
  "modified": "2017-04-27T15:57:34.916670",
  "created": "2017-03-13T10:41:37.403733",
  "ical_url": "/users/a938196a-152d-40f3-ab3d-404385143a4b/icalendar_feed?token=308e39c8-584f-402c-b5d2-4b9214be8424",
  "password_reset_required": false,
  "notification_settings": {
    "instant_email_notifications": "False",
    "evening_email_notification": "False",
    "morning_email_notification": "False",
    "new_lead_email_notification": "False"
  }
}
```


Parameter |  Description
--------- | ------- 
`id`      | The unique identifier for the user logging in **string**
`name`    | The name of the user logging in **string**
`is_admin` | Set to `true` if this user is an admin **boolean**
`email_address` | The user email address **string**
`email_address` | The user email address **string**
`client_id` | _TO DO_
`modified`| User last modified timestamp **Timestamp (ISO 8601)**
`created` | User creation timestamp **Timestamp (ISO 8601)**
`ical_url` | URL for the user iCal connection **string (URL)**
`password_reset_required` | Set to `true` if this user will be required to reset their password when loggin in. **boolean**
`notification_settings` | Object contianing users email notification settings **object**


## Login

> When logging in you must add the following to the reqest header:

```http
Content-Type: application/x-www-form-urlencoded
```

> A sample request body to login as example user would be:

```json
{
  "email": "example@salesseek.com",
  "password": "V84gFHyAckt%b@bNRy$fW"
}
```

> If login is successful, the following cookie will be present in the response header:

```http
Set-Cookie: salesseek=54fe7b67-a08a-4467-b95b-8689084b1f89; Path=/
```


To login, send your email address and password to the endpoint below. If login is successful a cookie will be returned in the response header. This cookie should be used in all future calls to the API. 

### Request URL

`POST https://{CLIENT_ID}.salesseek.net/api/login`

### Request Body Parameters

Parameter |  Description
--------- | ------- 
`email_address` | Your email address used to access your account. **string**
`password` | The password used to access your account. **string**

<div class="wrap">
  <p class="flash warn">
    You must set the following Content-Type in the request header: <br>
    <code>Content-Type: application/x-www-form-urlencoded</code>
  </p>
</div>


## Logout

Executes the logout process for the currently authenticated SalesSeek user

### Request URL

`DELETE https://{CLIENT_ID}.salesseek.net/api/logout`

## Request Password Reset

> A sample request body to request a user password reset would be:

```json
{
  "email_address": "example@salesseek.com",
  "callback_url": "https://example.salesseek.net/#reset"
}
```

If a user has forgoten their password for their SalesSeek account make a call to this API to reset their password. After providing their email address SalesSeek will send link via email to validate this person wanted to change their password. The token sent in this email is requried to reset a password.

### Request URL

`POST https://{CLIENT_ID}.salesseek.net/api/forgotten`

### Request Body Parameters

Parameter |  Description
--------- | ------- 
`email_address` | Your email address for the user that would like to reset their password. **string**
`callback_url` | The next web page to open after reset **string**

## Complete Password Reset

> A sample request body to complete the reset of a user password would be:

```json
{
    "user_id": "a938196a-152d-40f3-ab3d-404385143a4b",
    "token": "76ef98545e738a51",
    "password": "I_will_remember_this_new_password"
}
```

Once the password reset email has been received, the token in the email must be used to reset the user password.

### Request URL

`POST https://{CLIENT_ID}.salesseek.net/api/reset`

### Request Body Parameters

Parameter |  Description
--------- | ------- 
`user_id` | The ID for the user to have the password reset. **string**
`token` | Unique token provided in reset confirmation email **string**
`password` | New password to be assigned to account **string**

<div class="wrap">
  <p class="flash warn">
    The token in the request confirmation email must be used to reset the user password.
  </p>
</div>