# Campaign API

## Campaign Attributes

> The JSON encoded response looks like this.

```json
{
  "id": "0a6a5701-99c9-4a80-ad78-c5g05c9497bc",
  "name": "Free Webinar today at 3pm",
  "status": "draft",
  "subject": "Free Webinar today at 3pm",
  "campaign_type": "campaign",
  "to_group_id": "99c90-a6a5701-4a80-ad78-c5g05c9497bc",
  "to_group": null,
  "sent": null,
  "used_in_automations": false,
  "used_in_live_automations": null,
  "include_signature": true,
  "campaign_schedule_id": a1053ecf-ef72-4f5f-8b74-56ce1b7b401e,
  "campaign_schedule": {
    "id": "a1053ecf-ef72-4f5f-8b74-56ce1b7b401e",
    "timezone": "UTC",
    "utc_offset": "-60",
    "when": "2017-09-29T12:00:00",
    "when_utc": "2017-09-29T11:00:00"
  },
  "track": true,
  "owner_id": "1445cf43-06c5-4821-9e92-7b5810840a92",
  "creator_id": "a4c510ac-5f3b-4a2a-b3bd-ef0dc1ae1680"
  "last_modified_by_id": "a4c510ac-5f3b-4a2a-b3bd-ef0dc1ae1680",
  "created": "2017-05-23T08:56:14.036080",
  "modified": "2017-07-31T11:13:07.689772",
  "from_user_id": "a4c510ac-5f3b-4a2a-b3bd-ef0dc1ae1680",
  "from_user": {
    ...
  },
  "creator": {
    ...
  },
  "owner": {
    ...
  },
  "email_status_stats": {
    "sent": 0,
    "queued": 0,
    "in_progress": 0,
    "failed": 0,
    "cancelled": 0
  },
  "email_event_stats": {
    "undelivered_rate": 4,
    "unsubscribed_rate": 0,
    "click": 74,
    "queued": 0,
    "delivered": 15536,
    "soft_bounce": 460,
    "reject": 18,
    "soft_bounce_rate": 2,
    "spam": 627,
    "spam_rate": 3,
    "send": 16347,
    "unsubscribed_list": 0,
    "unsubscribed_all_rate": 0,
    "bounce_rate": 4,
    "click_rate": 0,
    "open_rate": 10,
    "hard_bounce": 333,
    "delivered_rate": 95,
    "send_rate": 0,
    "hard_bounce_rate": 2,
    "open": 1678,
    "undelivered": 811,
    "unsubscribed_list_rate": 0,
    "bounce": 793,
    "unsubscribed": 136,
    "reject_rate": 0,
    "unsubscribed_all": 136
  },
  "content": "<!DOCTYPE html><h1>Example HTML Email</h1></html>",
  
}

```




Parameter |  Description
--------- | ------- 
`id`      | The unique identifier for this campaign **String**
`name`    | The user provided title for the campaign **String**
`status`  | Current status of the campaign (`draft`, `ready`, `scheduled`, `sent`) **Enum (String)**
`subject` | The subject line for the campaign **String**
`campaign_type` | The type of the campaign (`direct`, `campaign`) **Enum (String)**
`to_group_id` | The ID for the group the campaign is to be sent to **String**
`to_group` | Object containing detailed information about the group associated with this campaign **Object**
`sent` | Timestamp for when the campaign was sent **Timestamp (ISO 8601)**
`used_in_automations` | Set to `true` if this campaign is currently accociated with an automation **Boolean**
`used_in_live_automations` | Set to `true` if this campaign is currently accociated with an automation which is currently set to live **Boolean**
`include_signature` | Set to `true` if the signature for the user this campaign will be sent from will be appended to the email (direct emails only) **Boolean**
`campaign_schedule_id` | Unique identifier for the campaign schedule **String**
`campaign_schedule` | Object containing detailed information about the schedule assigned to this campaign **Object**
`campaign_schedule.id` | Unique identifier for the campaign schedule **String**
`campaign_schedule.timezone` | Three character representation of the timezone for this schedule. **String**
`campaign_schedule.utc_offset` | The UTC offset from schedule in minutes **Integer**
`campaign_schedule.when` | Timestamp for when this campaign should be sent **Timestamp (ISO 8601)**
`campaign_schedule.when_utc` | Timestamp for when this campaign should be sent in UTC **Timestamp (ISO 8601)**
`track` | Set to `true` if SalesSeek should track statistics on this campaign **Boolean**
`owner_id` | The ID for the [User](#user-api) that has ownership over this campaign **String**
`creator_id` | The ID for the [User](#user-api) that created this campaign **String**
`last_modified_by_id` | The ID for the SalesSeek [User](#user-api) that last modified this campaign **String**
`created` | Campaign creation timestamp **Timestamp (ISO 8601)**
`modified`| Campaign last modified timestamp **Timestamp (ISO 8601)**
`from_user_id` | ID of the [User](#user-api) the campaign will be sent from **String**
`from_user`| Object containing detailed information about the [User](#user-api) the campaign will be sent from **Object**
`creator` | Object containing detailed information about the [User](#user-api) that created this campaign **Object**
`owner` | Object containing detailed information about the [User](#user-api) that owns this campaign **Object**
`email_status_stats` | Object containing email status statistics **Object**
`email_status_stats.sent` | Number of sent emails in campaign **Integer**
`email_status_stats.queued` | Number of emails queued in campaign **Integer**
`email_status_stats.in_progress` | Number of emails in progress in campaign **Integer**
`email_status_stats.failed` | Number of emails failed in campaign **Integer**
`email_status_stats.cancelled` | Number of emails queued in campaign **Integer**
`email_event_stats` | Object containing email event statistics **Object**
`email_event_stats.delivered` | Number of delivered emails in campaign **Integer**
`email_event_stats.open` | Number of delivered opened in campaign **Integer**
`email_event_stats.undelivered_rate` | Rate of un-delivered emails in campaign **Integer**
`email_event_stats.queued` | Number of emails queued in campaign **Integer**
`email_event_stats.click` | Number of clicked emails in campaign **Integer**
`email_event_stats.click_rate` | Rate of clicked emails in campaign **Integer**
`email_event_stats.hard_bounce_rate` | Rate of hard bounces in campaign **Integer**
`email_event_stats.delivered_rate` | Rate of delivered emails in campaign **Integer**
`email_event_stats.soft_bounce_rate` | Rate of soft bounces in campaign **Integer**
`email_event_stats.bounce_rate` | Rate of bounces in campaign **Integer**
`email_event_stats.hard_bounce` | Rate of hard bounces in campaign **Integer**
`email_event_stats.send` | Number of emails sent in campaign **Integer**
`email_event_stats.unsubscribed` | Number of unsubscribes from this campaign **Integer**
`email_event_stats.bounce` | Number of bounces in campaign **Integer**
`email_event_stats.spam` | Number of emails marked as spam in campaign **Integer**
`email_event_stats.open_rate` | Rate of emails opened in campaign **Integer**
`email_event_stats.unsubscribed_all_rate` | Rate of unsubscribes from all email campaigns **Integer**
`email_event_stats.spam` | Rate of emails marked as spam in this campaign **Integer**
`email_event_stats.reject` | Number of emails rejected in this campaign **Integer**
`email_event_stats.send_rate` | Rate of emails sent in this campaign **Integer**
`email_event_stats.undelivered` | Rate of emails not delivered in this campaign **Integer**
`email_event_stats.soft_bounce` | Number of soft bounces in this campaign **Integer**
`email_event_stats.unsubscribed_rate` | Rate of unsubscribes in this campaign **Integer**
`email_event_stats.reject_rate` | Rate of rejections in this campaign **Integer**
`email_event_stats.unsubscribed_all` | Number of individuals who have unsubscibed from all email campaigns **Int**
`content` | HTML content for this email **String**


## Get Campaign

Returns the unique organization matching the `campaign_id`

### Request URL

<span class='verb get'>GET</span> `https://{CLIENT_ID}.salesseek.net/api/campaigns/{campaign_id}`

Parameter |  Description
--------- | ------- 
`campaign_id`      | The ID for the campaign you'd like to retrieve **String**


## Create Campaign

Creates a new campaign and then returns the newly created campaign.

### Request URL

<span class='verb post'>POST</span> `https://{CLIENT_ID}.salesseek.net/api/campaigns`

## Update Campaign

> A sample request body to update the campaign subject.

```json
{
  "subject": "Free Webinar @5pm"
}
```

Updates values of a campaign by `campaign_id`. The resulting campaign is returned.

### Request URL

<span class='verb patch'>PATCH</span> `https://{CLIENT_ID}.salesseek.net/api/campaigns/{campaign_id}`

Parameter |  Description
--------- | ------- 
`campaign_id`      | The ID for the campaign you'd like to update **String**

### Request Body

The only fields updated are the one passed on the request body JSON. You can pass any [attribute](#campaign-attributes) to update. 


## Delete Campaign

Deletes the campaign matching the `campaign_id`

### Request URL

<span class='verb delete'>DELETE</span> `https://{CLIENT_ID}.salesseek.net/api/campaigns/{campaign_id}`

### Request Query Parameters

Parameter |  Description
--------- | ------- 
`campaign_id` | The unique ID for the campaign to be deleted.


## List Campaigns

> An example request to get the first 50 *unsent* campaigns in your SalesSeek account (when ordered by modfied date) would be:

```http
GET https://example.salesseek.net/api/campaigns?rows=50&start=0&order_by=modified%20desc&status=ready,draft
```

> The reponse header contains the following information:

```
Records-Rows: 50
Records-Start: 0
Records-Total: 2000
```

Returns a list of campaigns from your SalesSeek account.


### Request URL

<span class='verb get'>GET</span> `https://{CLIENT_ID}.salesseek.net/api/campaigns`

### Request Query Parameters

Parameter |  Description
--------- | ------- 
`rows` | The maximum number of organizations to be returned.
`start` | The row number to start to retrieve data. (0 for start)
`order_by` | Results are ordered by the provided field name followed by &desc or &asc

<div class="wrap">
  <p class="flash info">
    The response header contain the total number of records.
  </p>
</div>

### Response Header Parameters

Parameter |  Description
--------- | ------- 
`Records-Rows` | The number of rows returned in this request
`Records-Start` | The start number of rows in this request (out of total)
`Records-Total` | The total number of rows available


## Send Campaign Test

> An example request to send a test of a campaign to *example@salesseek.com* would be made to:

```http
POST https://{CLIENT_ID}.salesseek.net/api/campaigns?test=example@salesseek.com
```

> An example request body would be:

```json
{
  "campaign_type": "direct",
  "content": "<!DOCTYPE html>\n<html>\n<head>\n</head>\n<body>\n<p>Example Email</p>\n</body>\n</html>",
  "status": "draft",
  "from_user": {
    "id": "a938196a-1d2d-40f3-ab3d-804985143a4b",
    "name": "SalesSeek Example",
    "email_address": "example@salesseek.com",
    "email_signature": "<h2>Email Signature</h2>"
  },
  "include_signature": true,
  "track": true,
  "name": "Example Email",
  "subject": "Example Email",
  "to_group": {
    "id": "68b2647d-bf9d-4f6f-9cbc-0d1f21687ae0",
    "name": "Email Group"
  }
}
```

> This enpoint will respond with `null`.

Sends a test email of the campaign content to chosen SalesSeek users. 

### Request URL

<span class='verb post'>POST</span> `https://{CLIENT_ID}.salesseek.net/api/campaigns?test={user_email}`

### Request Query Parameters

Parameter |  Description
--------- | ------- 
`user_email` | The maximum number of organizations to be returned.

### Request Body Parameters

Parameter |  Description
--------- | ------- 
`campaign_type` | The type of the campaign (`direct`, `campaign`) **Enum (String)**
`content` | HTML content for this email **String**
`status`  | Current status of the campaign (`draft`, `ready`, `scheduled`, `sent`) **Enum (String)**
`from_user`| Object containing detailed information about the [User](#user-api) the campaign will be sent from **Object**
`from_user.id` | ID of the SalesSeek [User](#user-api) the email will be sent from **String**
`from_user.name` | Name of the SalesSeek [User](#user-api) the email will be sent from **String**
`from_user.email_address` | Email address of the SalesSeek [User](#user-api) the email will be sent from **String**
`from_user.email_signature` | Signature for the SalesSeek [User](#user-api) the email will be sent from **String**
`include_signature` | Set to `true` if the signature for the [User](#user-api) this campaign will be sent from will be appended to the email (direct emails only) **Boolean**
`track` | Set to `true` if SalesSeek should track statistics on this campaign **Boolean**
`name`    | The user provided title for the campaign **String**
`subject` | The subject line for the campaign **String**
`to_group` | Object containing detailed information about the group associated with this campaign **Object**
`to_group.id` | ID for the group the campaign will be sent to **String**
`to_group.name` | Name for the group the campaign will be sent to **String**

<div class="wrap">
  <p class="flash info">
    Values for the request body can be obtained by performing a <a href='#get-campaign'> GET Request </a> on the campaign ID 
  </p>
</div>

## Set Campaign Live

Sets a campaign to live and ready for sending.

<span class='verb post'>POST</span> `https://salesseek.salesseek.net/api/campaigns?send`

### Request Query Parameters

(none)

### Request Body Parameters

Parameter |  Description
--------- | ------- 
`campaign_type` | The type of the campaign (`direct`, `campaign`) **Enum (String)**
`content` | HTML content for this email **String**
`status`  | Current status of the campaign (`draft`, `ready`, `scheduled`, `sent`) **Enum (String)**
`from_user`| Object containing detailed information about the [User](#user-api) the campaign will be sent from **Object**
`from_user.id` | ID of the SalesSeek [User](#user-api) the email will be sent from **String**
`from_user.name` | Name of the SalesSeek [User](#user-api) the email will be sent from **String**
`from_user.email_address` | Email address of the SalesSeek [User](#user-api) the email will be sent from **String**
`from_user.email_signature` | Signature for the SalesSeek [User](#user-api) the email will be sent from **String**
`include_signature` | Set to `true` if the signature for the [User](#user-api) this campaign will be sent from will be appended to the email (direct emails only) **Boolean**
`track` | Set to `true` if SalesSeek should track statistics on this campaign **Boolean**
`name`    | The user provided title for the campaign **String**
`subject` | The subject line for the campaign **String**
`to_group` | Object containing detailed information about the group associated with this campaign **Object**
`to_group.id` | ID for the group the campaign will be sent to **String**
`to_group.name` | Name for the group the campaign will be sent to **String**

<div class="wrap">
  <p class="flash info">
    Values for the request body can be obtained by performing a <a href='#get-campaign'> GET Request </a> on the campaign ID 
  </p>
</div>