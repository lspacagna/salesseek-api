# User API

## User Attributes

```json 
{
    "id": "40575ca1-381c-4542-a556-e3c2d81ef67e",
    "name": "Example User",
    "email_address": "example@salesseek.com",
    "is_admin": true,
    "email_signature": "",
    "ical_url": "/users/40575ca1-381c-4542-a556-e3c2d81ef67e/icalendar_feed?token=11753b32-c9c3-45f8-948a-e2682ae7c8db",
    "created": "2017-03-07T17:33:48.856990",
    "modified": "2017-08-23T12:40:39.122870",
    "password_reset_required": false,
    "notification_settings": {
      "instant_email_notifications": "False",
      "new_lead_email_notification": "False",
      "evening_email_notification": "False",
      "morning_email_notification": "False"
    },
    "preferences": {
      ...
    },
    "quota": [
      {
        "value": 1000,
        "bucket_id": "b42b5b3f-8ee4-43f5-8992-a6779beb78e0"
      },
      {
        "value": 0,
        "bucket_id": "4dfec57c-3525-49da-b7ef-a84523aeabef"
      },
      {
        "value": 0,
        "bucket_id": "16228274-85aa-459b-ad78-fa9ae69de302"
      }
    ]
}

```

Parameter |  Description
--------- | ------- 
`id`      | The unique identifier for this user **String**
`name` | The name given to this user **String**
`email_address` | Email address for this user, used to login to SalesSeek **String**
`is_admin` | Set to `true` if this user is an adminstrator **Boolean**
`email_signature` | This users email signature in HTML. Used in Direct Emails **String**
`ical_url` | URL for the user iCal connection **String (URL)**
`created` | User creation timestamp **Timestamp (ISO 8601)**
`modified`| User last modified timestamp **Timestamp (ISO 8601)**
`password_reset_required` | Set to `true` if this User will be required to reset their password when they next login **Boolean**
`notification_settings` | Object contianing users email notification settings **Object**
`notification_settings.instant_email_notifications` | Set to `'True'` if user has instant email notifications when a task has been assigned to them enabled **String**
`notification_settings.evening_email_notification` | Set to `'True'` if user has enabled a daily email of all completed tasks, and today's uncompleted tasks **String**
`notification_settings.morning_email_notification` | Set to `'True'` if user has enabled a daily email with tasks that need completing today **String**
`notification_settings.new_lead_email_notification` | Set to `'True'` if user has enabled a an email each time a new lead is assigned to them **String**
`preferences` | Object containing this users app preferences (not editable via the API) **Object**
`quota` | Object continaing targets for each revenue bucket for this user (used in Sales Manager Dashboard) **Array (Object)**
`quota[x].bucket_id` | The ID for the bucket this quota is related to **String**
`quota[x].value` | The target value for this bucket **Double**

## Get User

Returns the user matching the `user_id`

### Request URL

<span class='verb get'>GET</span> `https://{CLIENT_ID}.salesseek.net/api/users/{user_id}`

Parameter |  Description
--------- | ------- 
`user_id` | The ID for the user you'd like to retrieve



## Create User

> An example request body to create a user look like:

```json
{
	"email_address":"example@example.com",
	"name":"example"
}
```

Creates a new user and then returns the newly created user. 

### Request URL

<span class='verb post'>POST</span> `https://{CLIENT_ID}.salesseek.net/api/users/`


<div class="wrap">
  <p class="flash info">
   	When adding a new SalesSeek user, the user is emailed a temporary password. During first login the user will be able to set their own password.
  </p>
</div>



## Update User

> A sample request body to change the user email address

```json
{
	"email_address": "example@example.co.uk"
}
```

Updates values of the user by `user_id`. The resulting deal is returned. 

### Request URL

<span class='verb patch'>PATCH</span> `https://{CLIENT_ID}.salesseek.net/api/users/{user_id}`

Parameter |  Description
--------- | ------- 
`user_id`      | The ID for the deal you'd like to update

### Request Body

The only fields updated are the one passed on the request body JSON. You can pass [attributes](#deal-attributes) to update.



## Delete User

Deletes the user matching the `user_id`

### Request URL

<span class='verb delete'>DELETE</span> `https://{CLIENT_ID}.salesseek.net/api/users/{user_id}`

## Request Query Parameters

Parameter |  Description
--------- | ------- 
`user_id` | The unique ID for the user to be deleted.

<div class="wrap">
  <p class="flash info">
  	When deleting a user all records owned by this user will be reassigned to the user performing the deletion. Any activity records will remain associated with the deleted user.
  </p>
</div>