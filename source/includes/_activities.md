# Activities API

## Activities Attributes

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

Parameter |  Description
--------- | ------- 
`id`      | The unique identifier for this activity **String**
`activity_type` | The type of activity **String**
`target_type` | The record type the activity relates to (organization, opportunity, individual) **Enum (string)**
`owner_id` | The ID for the SalesSeek user that has ownership of this activity **String**
`owner` | Object containing detailed information about the activity owner **Object**
`creator_id` | The unique ID for the SalesSeek user that created this activity **String**
`creator` | Object containing detailed information about the activity creator **Object**
`tags` | Array of tags associated with this activity **Array**
`created` | Activity creation timestamp **Timestamp (ISO 8601)**
`modified`| Activity last modified timestamp **Timestamp (ISO 8601)**
`last_modified_by_id` | The unique ID for the SalesSeek user that last modified this activity **String**
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
`params.who` | Name of the user who performed the activity (shown if activity was a phase move) **String**
`params.campaign_id` | The ID for the campaign where the activity originates (shown if activity was related to a campaign) **String**
`params.campaign_name` | The name for the campaign where the activity originates (shown if activity was related to a campaign) **String**
`params.campaign_type` | The type of email campaign (direct, campaign) (shown if activity was related to a campaign) **String**
`params.url` | The URL that was clicked in the campaign email (shown if activity was related to a campaign link being clicked) **String**
`params.subject` | The email subject (shown if activity was an archived email) **String**
`params.completed_by` | The name of the user that completed the task (shown if activity was a completed task) **String**
`params.description` | Descripion of completed tasks (shown if activity was a comlpleted task) **String**
`"target_date` | Timestamp for the activity target date **Timestamp (ISO 8601)**
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
`auto:call` | A call was logged
`task:completed` | A task was complted