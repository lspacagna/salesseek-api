# Activity API

## Activity Attributes

> An example response body for an activity note would look like this:

```json
{
    "id": "ef59f293-9838-4043-b0f4-9b0a6f467d73",
    "activity_type": "note",
    "target_type": "individuals",
    "owner_id": "8da68e42-baef-42b2-9c72-4a00b5e20082",
    "owner": {
        ...
    },
    "creator_id": "8da68e42-baef-42b2-9c72-4a00b5e20082",
     "creator": {
       	...
    },
    "tags": [
    	...
    ],
    "created": "2017-08-03T10:42:41.843271",
    "modified": "2017-08-03T10:42:41.843271",
    "last_modified_by_id": "8da68e42-baef-42b2-9c72-4a00b5e20082",
    "individual_id": "079f2797-df8d-4141-b10b-7c26553132e9",
    "individual_name": "Chelsea Wallace",
	"opportunity_id": null,
	"opportunity_name": null,
    "organization_id": null,
    "organization_name": null,
    "note": "<p>Agreed payment plan</p>",
    "params": null,
    "target_date": null,
    "communication": null,
    "communication_id": null,
    "real_created": "2017-08-03T10:42:41.843271",
    "user_created": "2017-08-03T10:42:41.843271",
    "target_is_parent": true,   
}
```

> An example response body for a sent direct email campaign to an individual would look like:

```json
{
    "id": "a3365acc-831c-45ec-b83d-f5d2b31dbc24",
    "activity_type": "automation:archive:mailshot_sent",
    "target_type": "individuals",
    "owner_id": "69c5bc2a-c8e5-4d11-a102-6ec0fb410d1b",
    "owner": {
      ...
    },
    "creator_id": "69c5bc2a-c8e5-4d11-a102-6ec0fb410d1b",
    "creator": {
      ...
    },
    "tags": [
      ...
    ],
    "created": "2017-08-14T12:10:59.048847",
    "modified": "2017-08-14T12:10:59.048847",
    "last_modified_by_id": "69c5bc2a-c8e5-4d11-a102-6ec0fb410d1b",
    "individual_id": "285ae016-58d4-4dbc-bff3-339c2b4540ff",
    "individual_name": "Gregory John",
    "opportunity_id": null,
    "opportunity_name": null,
    "organization_id": null,
    "organization_name": null,
    "note": "SalesSeek sent Welcome Email to Gregory John",
    "params": {
        "mailshot_id": "91c2c7f6-71d2-4d57-909d-66bc6a978023",
        "campaign_id": "91c2c7f6-71d2-4d57-909d-66bc6a978023",
        "mailshot_name": "Welcome Email",
        "campaign_type": "direct",
        "campaign_name": "Welcome Email"
    },
    "target_date": null,
    "communication": null,
    "communication_id": null,
    "real_created": "2017-08-14T12:10:59.048847",
    "user_created": "2017-08-14T12:10:59.048847",
    "target_is_parent": true
}
  
```

> An example response body for a deal phase move would look like:

```json
{
    "id": "a300284d-b708-4d50-8d42-e2e8ab4cceeb",
    "activity_type": "auto:opportunity_movement",
    "target_type": "opportunities",
    "owner_id": "69c5bc2a-c8e5-4d11-a102-6ec0fb410d1b",
    "owner": {
      ...
    },
    "creator_id": "69c5bc2a-c8e5-4d11-a102-6ec0fb410d1b",
    "creator": {
      ...
    },
    "tags": [
      ...
    ],
    "created": "2017-08-14T13:27:23.254368",
    "modified": "2017-08-14T13:27:23.254368",
    "last_modified_by_id": "69c5bc2a-c8e5-4d11-a102-6ec0fb410d1b",
    "individual_id": null,
    "individual_name": null,
    "opportunity_id": "81e96bca-abdc-4753-8763-fc642afb3c99",
    "opportunity_name": "Aptui",
    "organization_id": null,
    "organization_name": null,
    "note": "SalesSeek moved Aptui from Engaged to Won",
    "params": {
        "from_funnel_id": "7d40c1e6-1e66-4dac-bd4b-0e29184c6dcd",
        "to_id": "c8a2a4c1-420b-4d7e-99d9-3f54eb503f2b",
        "to": "Lost",
        "from": "Engaged",
        "from_funnel": "Online",
        "who": "Dale Goulding",
        "from_id": "c4329a4a-44fe-4948-9c90-46a589266643"
    },
    "target_date": null,
    "communication": null,
    "communication_id": null,
    "real_created": "2017-08-14T13:27:23.254368",
    "user_created": "2017-08-14T13:27:23.254368",
    "target_is_parent": true,
}
```


Parameter |  Description
--------- | ------- 
`id`      | The unique identifier for this activity **String**
`activity_type` | The [type of activity](#activity-types)  **String**
`target_type` | The record type the activity relates to (`organization`, `opportunity`, `individual`) **Enum (string)**
`owner_id` | The ID for the SalesSeek [User](#user-api) that has ownership of this activity **String**
`owner` | Object containing detailed information about the [User](#user-api) that owns this activity **Object**
`creator_id` | The unique ID for the SalesSeek [User](#user-api) that created this activity **String**
`creator` | Object containing detailed information about the [User](#user-api) that created this activity **Object**
`tags` | Array of tags associated with this activity **Array**
`created` | Activity creation timestamp **Timestamp (ISO 8601)**
`modified`| Activity last modified timestamp **Timestamp (ISO 8601)**
`last_modified_by_id` | The unique ID for the SalesSeek [User](#user-api) that last modified this activity **String**
`individual_id` | The ID for the [individual](#individual-api) record this activity is associated to - `null` if not associated with an individual **String**
`individual_name` | The name of the [individual](#individual-api) record that this activity is associated to - `null` if not associated with an individual **String**
`opportunity_id` | The ID for the [deal](#deal-api) record this activity is associated to - `null` if not associated with a deal **String**
`opportunity_name` | The name of the [deal](#deal-api) record that this activity is associated to - `null` if not associated with a deal **String**
`organization_id` | The ID for the [organization](#organization-api) record this activity is associated to - `null` if not associated with an organization **String**
`organization_name` | The name of the [organization](#organization-api) record that this activity is associated to - `null` if not associated with an organization **String**
`note` | The activity note contents in HTML - `null` if activity not a note **String**
`params` | Object containing detailed informaiton about the activity - `null` if activity is not a phase move. **Object**
`params.to_id` | ID for the phase that the deal has been moved to (shown if activity was a phase move) **String**
`params.to` | Name for the phase that the deal has been moved to (shown if activity was a phase move) **String**
`params.from_id` | ID for the phase that the deal was moved from (shown if activity was a phase move) **String**
`params.from` | Name for the phase that the deal was moved from (shown if activity was a phase move) **String**
`params.to_funnel_id` | The ID for the funnel that the deal was moved to (shown if activity was a phase move) **String**
`params.to_funnel` | The name for the funnel that the deal was moved to (shown if activity was a phase move) **String**
`params.from_funnel_id` | The ID for the funnel that the deal was moved from (shown if activity was a phase move) **String**
`params.from_funnel` | The name for the funnel that the deal was moved from (shown if activity was a phase move) **String**
`params.who` | Name of the [User](#user-api) who performed the activity (shown if activity was a phase move) **String**
`params.campaign_id` | The ID for the campaign where the activity originates (shown if activity was related to a campaign) **String**
`params.campaign_name` | The name for the campaign where the activity originates (shown if activity was related to a campaign) **String**
`params.campaign_type` | The type of email campaign (direct, campaign) (shown if activity was related to a campaign) **String**
`params.url` | The URL that was clicked in the campaign email (shown if activity was related to a campaign link being clicked) **String**
`params.subject` | The email subject (shown if activity was an archived email) **String**
`params.completed_by` | The name of the [User](#user-api) that completed the task (shown if activity was a completed task) **String**
`params.description` | Descripion of completed tasks (shown if activity was a comlpleted task) **String**
`target_date` | Timestamp for the activity target date **Timestamp (ISO 8601)**
`communication` | TODO
`communication_id` | TODO
`real_created` | TODO
`user_created` | TODO
`target_is_parent` | TODO


## Activity Types

Types | Description
------| ------------- 
`auto:organization_import` | An [organization](#organization-api) was imported
`auto:individual_import` | An [individual](#individual-api) was imported 
`auto:opportunity_import` | A [deal](#deal-api) was imported 
`auto:organization_creation` | An [organization](#organization-api) was created
`auto:individual_creation` | An [individual](#individual-api) was created
`auto:opportunity_creation` | A [deal](#deal-api) was created
`archive:email` | An email was archived
`archive:mailshot_sent` | A [campaign](#campaign-api) was sent
`archive:mailshot_opened ` | A [campaign](#campaign-api) was opened
`automation:archive:mailshot_url_clicked` | A link in a [campaign](#campaign-api) was clicked
`automation:archive:mailshot_sent` | A [campaign](#campaign-api) was sent
`auto:call` | A call was logged
`task:completed` | A task was completed




## Get Activity

Returns the unique organization matching the `activity_id`

### Request URL

<span class='verb get'>GET</span> `https://{CLIENT_ID}.salesseek.net/api/activities/{activity_id}`

### Request Query Parameters

Parameter |  Description
--------- | ------- 
`activity_id`  | The ID for the activity you'd like to retrieve **String**






## Create Activity

> A sample request body to add an activity note would look like:

```json
{
  "note": "<p>Called today and agreed on deal terms.</p>",
  "created": null,
  "target_date": null,
  "activity_type": "note",
  "item_type": "opportunities",
  "item_id": "0d98b2fa-c4c8-4d56-9cda-17b62b198f4f",
  "tags": []
}
```

Creates a new activity record and then returns the newly created activity.

### Request URL

<span class='verb post'>POST</span> `https://{CLIENT_ID}.salesseek.net/api/activities`







## Update Activity

> A sample request body to change the activity note text would be:

```json
{
  "note": "<p>Called yesterday and agreed on deal terms.</p>",
}
```

Updates values of activity by `activity_id`. The resulting activity is returned. 

### Request URL

<span class='verb patch'>PATCH</span> `https://{CLIENT_ID}.salesseek.net/api/activities/{activity_id}`

Parameter |  Description
--------- | ------- 
`activity_id`      | The ID for the activity you'd like to update **String**

### Request Body

The only fields updated are the one passed on the request body JSON. You can pass any [attribute](#activity-attributes) to update. 






## Delete Activity

Deletes the activity matching the `activity_id`

### Request URL

<span class='verb delete'>DELETE</span> `https://{CLIENT_ID}.salesseek.net/api/activities/{activity_id}`

### Request Query Parameters

Parameter |  Description
--------- | ------- 
`activity_id` | The unique ID for the organization to be deleted.





## List Activities

> An example request to get the first 50 activites for a particular opportunity, ordered by creation date descending, with all activity types returned.

```http
GET https://example.salesseek.net/api/activities?start=0&rows=50&order_by=created%20desc&notes=true&communications=true&contact_updates=true&deals=true&campaign_emails=true&automation_emails=true&include_ind_related=true&include_org_related=true&include_deal_related=true&item_type=opportunities&item_id=0d98b2fa-c4c8-4d56-9cda-17b62b198f4f
```

> The reponse header contains the following information:

```
Records-Rows: 50
Records-Start: 0
Records-Total: 2000
```

Returns a list of activities.

### Request URL

<span class='verb get'>GET</span> `https://{CLIENT_ID}.salesseek.net/api/activities`

### Request Query Parameters

Parameter |  Description
--------- | ------- 
`rows` | The maximum number of organizations to be returned.
`start` | The row number to start to retrieve data. (0 for start)
`order_by` | Results are ordered by the provided field name followed by `&desc` or `&asc`
`notes` | Set to `true` to request activity notes (`true` or `false`)
`communications` | Set to `true` to request all communication activity (`true` or `false`)
`contact_updates` | Set to `true` to request all contact update activity (`true` or `false`)
`deals` | Set to `true` to request all deal activity (`true` or `false`)
`campaign_emails` | Set to `true` to request all campaign email activity (`true` or `false`)
`automation_emails` | Set to `true` to request all automation email activity (`true` or `false`)
`include_ind_related` | Set to `true` to request all activities from related individuals (`true` or `false`)
`include_org_related` | Set to `true` to request all activities from related organizations (`true` or `false`)
`include_deal_related` | Set to `true` to request all activities from related deals (`true` or `false`)
`item_type` | Set type of record activities to get related activities from (`opportunities`, `organizations`, `indviduals`)
`item_id` | ID for the recrod to get related activities from