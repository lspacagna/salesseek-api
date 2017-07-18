---
title: SalesSeek API

language_tabs: # must be one of https://git.io/vQNgJ
  - json-doc: Request
  - json: Response

includes:
  - organization

search: true
---

# Introduction

Welcome to the SalesSeek API! You can use our API to access all our API endpoints, such as the [Deal API](https://github.com/tripit/slate) to look up deal values, or the [Individual API](https://github.com/tripit/slate) to look up email addresses. 

The API is organized around [REST](http://en.wikipedia.org/wiki/Representational_State_Transfer). All requests should be made over SSL. All request and response bodies, including errors, are encoded in JSON.

URIs for SalesSeek's REST API resource have the following structure:

`https://{CLIENT_ID}.salesseek.net/api/{RESOURCE}?{KEY1}={VALUE1}&{KEY2}={VALUE2}`

Variable |  Description
--------- | ------- 
CLIENT_ID | The unique ID for your SalesSeek account. You can find this as the sub-domain when accessing your account. 
RESOURCE | Specific [resource]() type  to be requested.
KEYx | Parameter identifier matching one resource's parameter (optional)
VALUEx | Value asociated to KEYx


# Authentication

SalesSeek uses cookies as the authentication method. Cookies are encrypted by the server in the HTTPS Response after login.

SalesSeek expects the cookie to be included in all API requests to the server after login. For this reason the first step should be Login and then any sequence of requests to the API can follow.

## Login

<blockquote class="highlight json-doc tab-json-doc">
  <h3>Request Header</h3>
</blockquote>

```json-doc
  Content-Type: application/x-www-form-urlencoded
```

<blockquote class="highlight json-doc tab-json-doc">
  <h3>Request Body</h3>
</blockquote>

```json-doc
{
  "email_address" : "example@salesseek.net"
  "password":"BrfqxWrZFegnVuE382GbWQyM)n"
}
```

<blockquote class="highlight json tab-json">
  <h3>Response Header</h3>
</blockquote>

```json
Set-Cookie: salesseek=54fe7b67-a08a-4467-b95b-8689084b1f89; Path=/
```

<blockquote class="highlight json tab-json">
  <h3>Response Body</h3>
</blockquote>

```json
{
  "id": "a938196a-152d-40f3-ab3d-404385143a4b",
  "name": "Example Login",
  "is_admin": true,
  "uri": "users/a938196a-152d-40f3-ab3d-804985143a4b",
  "short_id": "a938196a-152d-40f3-ab3d-804985143a4b",
  "email_address": "example@salesseek.co.uk",
  "latest": true,
  "client_id": "913fa210-edf2-49c3-86a2-ec8f063d92ea",
  "deleted": false,
  "modified": "2017-04-27T15:57:34.916670",
  "created": "2017-03-13T10:41:37.403733",
  "type": "users",
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

> 

To login, send your email address and password to the endpoint below. If login is successful a cookie will be returned in the response header. This cookie should be used in all future calls to the API. 

### Request URL

`POST https://{CLIENT_ID}.salesseek.net/api/login`

### Request Body Parameters

Parameter |  Description
--------- | ------- 
email_address | Your email address used to access your account.
password | The password used to access your account.

<aside class="notice">
You must set the following Content-Type in the request header: <br>
<code>Content-Type: application/x-www-form-urlencoded`</code>

</aside>

## Logout

Executes the logout process for the currently authenticated SalesSeek user

### Request URL

`DELETE https://{CLIENT_ID}.salesseek.net/api/logout`




## Request Password Reset

<blockquote class="highlight json-doc tab-json-doc">
  <h3>Request Body</h3>
</blockquote>

```json-doc
{
    email_address: "example@salesseek.net"
    callback_url: "https://example.salesseek.net/#reset"
}
```

<blockquote class="highlight json tab-json">
  <h3>Response Body</h3>
</blockquote>

```json
null
```

If a user has forgoten their password for their SalesSeek account make a call to this API to reset their password. After providing his email address SalesSeek will send link via to validate this person wanted to change manually their password.

### Request URL

`DELETE https://{CLIENT_ID}.salesseek.net/api/logout`




## Reset Password

<blockquote class="highlight json-doc tab-json-doc">
  <h3>Request Body</h3>
</blockquote>

```json-doc
{
    user_id:"b8146356634",
    token:"76ef98545e738a51",
    password:"I_will_remember_this_new_password"
}
```

<blockquote class="highlight json tab-json">
  <h3>Response Body</h3>
</blockquote>

```json
null
```

Once the password reset email has been received, use the information to reset the user password

### Request URL

`DELETE https://{CLIENT_ID}.salesseek.net/api/reset`
