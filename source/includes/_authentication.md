# Authentication

SalesSeek uses cookies as the authentication method. Cookies are encrypted by the server in the HTTPS Response after login.

SalesSeek expects the cookie to be included in all API requests to the server after login. For this reason the first step should be Login and then any sequence of requests to the API can follow.

## Login

<blockquote class="highlight tab-request">
  <h3>Request Header</h3>
</blockquote>

<pre class="highlight json-doc tab-request"><code>Content-Type: application/x-www-form-urlencoded</code></pre> 


<blockquote class="highlight tab-request">
  <h3>Request Body</h3>
</blockquote>

<pre class="highlight json tab-request"><code>{
  "email_address" : "example@salesseek.net"
  "password":"BrfqxWrZFegnVuE382GbWQyM)n"
}</code></pre> 

<blockquote class="highlight tab-response">
  <h3>Response Header</h3>
</blockquote>

<pre class="highlight json tab-response"><code>Set-Cookie: salesseek=54fe7b67-a08a-4467-b95b-8689084b1f89; Path=/</code></pre> 

<blockquote class="highlight tab-response">
  <h3>Response Body</h3>
</blockquote>

<pre class="highlight json tab-response"><code>{
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
}</code></pre> 
 

To login, send your email address and password to the endpoint below. If login is successful a cookie will be returned in the response header. This cookie should be used in all future calls to the API. 


### Request URL

`POST https://{CLIENT_ID}.salesseek.net/api/login`

### Request Body Parameters

Parameter |  Description
--------- | ------- 
`email_address` | Your email address used to access your account.
`password` | The password used to access your account.

<aside class="notice">
You must set the following Content-Type in the request header: <br>
<code>Content-Type: application/x-www-form-urlencoded</code>

</aside>


## Logout

Executes the logout process for the currently authenticated SalesSeek user

### Request URL

`DELETE https://{CLIENT_ID}.salesseek.net/api/logout`

## Request Password Reset

<blockquote class="highlight tab-request">
  <h3>Request Body</h3>
</blockquote>

<pre class="highlight json tab-request"><code>{
    email_address: "example@salesseek.net"
    callback_url: "https://example.salesseek.net/#reset"
}</code></pre> 

<blockquote class="highlight tab-response">
  <h3>Response Body</h3>
</blockquote>

<pre class="highlight json tab-response"><code>null</code></pre> 


If a user has forgoten their password for their SalesSeek account make a call to this API to reset their password. After providing his email address SalesSeek will send link via to validate this person wanted to change manually their password.

### Request URL

`DELETE https://{CLIENT_ID}.salesseek.net/api/logout`

## Reset Password

<blockquote class="highlight tab-request">
  <h3>Request Body</h3>
</blockquote>

<pre class="highlight json tab-request"><code>{
    user_id:"b8146356634",
    token:"76ef98545e738a51",
    password:"I_will_remember_this_new_password"
}</code></pre> 

<blockquote class="highlight tab-response">
  <h3>Response Body</h3>
</blockquote>

<pre class="highlight json tab-response"><code>{
    user_id:"b8146356634",
    token:"76ef98545e738a51",
    password:"I_will_remember_this_new_password"
}</code></pre> 

Once the password reset email has been received, use the information to reset the user password

### Request URL

`DELETE https://{CLIENT_ID}.salesseek.net/api/reset`

