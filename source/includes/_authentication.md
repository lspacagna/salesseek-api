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
  "client": {
    "created": "2017-03-07T17:33:48.856990",
    "currencies": {
      "AED": "0.5"
    },
    "default_currency": "GBP",
    "email_sending_domains": [
      "example.com"
    ],
    "facebook_page_id": null,
    "feature_tier": null,
    "marketing_groups": null,
    "name": "Example",
    "selective_unsubscribing": false,
    "short_id": "example",
  },
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
`id`      | The unique identifier for the [User](#user-api) logging in **String**
`name`    | The name of the [User](#user-api) logging in **String**
`is_admin` | Set to `true` if this [User](#user-api) is an admin **Boolean**
`email_address` | The [User](#user-api) email address **String**
`client_id` | The unique identifier for the current SalesSeek account **String**
`client.created` | SalesSeek account creation timestamp **Timestamp (ISO 8601)**
`client.currencies` | The currencies and their conversions in this SalesSeek account **Object**
`client.default_currency` | The default currency for this account **String**
`client.email_sending_domains` | The domains that this SalesSeek account is authorized to send emails from (not user editable)**Array (String)**
`client.facebook_page_id` | The ID for the connected facebook page to this account **String**
`client.feature_tier` | The current tier that this SalesSeek account is registered to (`starting`, `growing`, `enterprise`)(not user editable) **Enum (String)**
`client.marketing_groups` | Array of IDs of the groups in this SalesSeek account which are mailing lists **Array (String)**
`client.name` | The name for this SalesSeek account **String**
`client.selective_unsubscribing` | Set to `true` if this account has selective unsubscribing enabled **Boolean**
`client.short_id` | The short ID for this SalesSeek account. Also used in the account subdomain **String**
`modified`| [User](#user-api) last modified timestamp **Timestamp (ISO 8601)**
`created` | [User](#user-api) creation timestamp **Timestamp (ISO 8601)**
`ical_url` | URL for the [User](#user-api) iCal connection **String (URL)**
`password_reset_required` | Set to `true` if this [User](#user-api) will be required to reset their password when loggin in **Boolean**
`notification_settings` | Object contianing users email notification settings **Object**
`notification_settings.instant_email_notifications` | Set to `'True'` if user has instant email notifications when a task has been assigned to them enabled **String**
`notification_settings.evening_email_notification` | Set to `'True'` if user has enabled a daily email of all completed tasks, and today's uncompleted tasks **String**
`notification_settings.morning_email_notification` | Set to `'True'` if user has enabled a daily email with tasks that need completing today **String**
`notification_settings.new_lead_email_notification` | Set to `'True'` if user has enabled a an email each time a new lead is assigned to them **String**



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


<span class='verb post'>POST</span> `https://{CLIENT_ID}.salesseek.net/api/login`


### Request Body Parameters

Parameter |  Description
--------- | ------- 
`email_address` | Your email address used to access your account. **String**
`password` | The password used to access your account. **String**

<div class="wrap">
  <p class="flash warn">
    You must set the following Content-Type in the request header: <br>
    <code>Content-Type: application/x-www-form-urlencoded</code>
  </p>
</div>


## Logout

Executes the logout process for the currently authenticated SalesSeek user

### Request URL

<span class='verb delete'>DELETE</span> `https://{CLIENT_ID}.salesseek.net/api/logout`

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

<span class='verb post'>POST</span> `https://{CLIENT_ID}.salesseek.net/api/forgotten`

### Request Body Parameters

Parameter |  Description
--------- | ------- 
`email_address` | Your email address for the user that would like to reset their password. **String**
`callback_url` | The next web page to open after reset **String**

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

<span class='verb post'>POST</span> `https://{CLIENT_ID}.salesseek.net/api/reset`

### Request Body Parameters

Parameter |  Description
--------- | ------- 
`user_id` | The ID for the user to have the password reset. **String**
`token` | Unique token provided in reset confirmation email **String**
`password` | New password to be assigned to account **String**

<div class="wrap">
  <p class="flash warn">
    The token in the request confirmation email must be used to reset the user password.
  </p>
</div>