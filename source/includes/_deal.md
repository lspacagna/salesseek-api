# Deal API

## Deal Attributes

> The JSON encoded response looks like this.

```json
{
  "id": "08956ba9-ed0c-4bdd-9b8f-29efeb1d254d",
  "name": "2015 Building Works",
  "abbreviation": "PWL",
  "organization_id": "db5b165f-24aa-4c49-bbb7-a19d87a6a901",
  "funnel_id": "6cfc3549-c674-4ba6-8f02-3043d0beb174",
  "phase_name": "Contacted",
  "phase_id": "bf2005c2-bcf0-4978-8c49-af8d41bdb225",
  "owner_id": "39ee847e-3391-4d34-9114-e26fc5bbe7d2"
  "weight": 0.1,
  "status": "none",
  "value": 2225,
  "weighted_value": 222.5,
  "currency": "GBP",
  "bubble_representation_value": 2225,
  "is_favorite": false,
  "phase_last_changed": "2017-07-04T10:36:27.503306",
  "expected_close_date": "2017-02-15T00:00:00",
  "creator_id": "247f5cd0-f6b7-42d3-8b01-47b1e1941fa9",
  "tags": [],
  "comments": "",
  "created": "2016-06-23T11:40:43.770201", 
  "modified": "2017-07-04T10:36:27.407967",
  "last_modified_by_id": "247f5cd0-f6b7-42d3-8b01-47b1e1941fa9",
  "last_viewed": "2017-07-31T09:53:21.713977",
  "latest_activity_in_days": 26,
  "related_file_ids": [],
  "generated_files": [],
  "funnel": {
    "id": "6cfc3549-c674-4ba6-8f02-3043d0beb174",
    "created": "2016-06-23T10:44:18.093750",
    "modified": "2017-07-29T14:38:47.784098",
    "last_modified_by_id": "247f5cd0-f6b7-42d3-8b01-47b1e1941fa9",
    "bubble_representation": "deal_value",
    "creator_id": "247f5cd0-f6b7-42d3-8b01-47b1e1941fa9",
    "name": "Product",
    "order": 0,
    "owner_id": "247f5cd0-f6b7-42d3-8b01-47b1e1941fa9"
  },
  "phase": {
    "id": "bf2005c2-bcf0-4978-8c49-af8d41bdb225",
    "created": "2016-06-23T10:44:18.099864",
    "modified": "2017-06-07T11:47:51.508875",
    "last_modified_by_id": "247f5cd0-f6b7-42d3-8b01-47b1e1941fa9",
    "creator_id": "247f5cd0-f6b7-42d3-8b01-47b1e1941fa9",
    "funnel_id": "6cfc3549-c674-4ba6-8f02-3043d0beb174",
    "name": "Contacted",
    "hint": "Someone who has shown some interest, e.g. registered on your website. Must have email and/or phone contact details.",
    "default_weight": 0.1,
    "order": 0,
  },
  "buckets": [
    {
      "value": 2050,
      "name": "Installation",
      "id": "bf96647a-d6d5-455e-83f2-9d09e7fde25c"
    },
    {
      "value": 0,
      "name": "Services",
      "id": "299a2ae6-4d52-4dfa-b7fe-fe7a3931bb65"
    }
  ],
  "custom_fields": {
    "1e681f65-59b0-4509-a7da-a0bf34d4b9e7": "09/22/2016"
  },
  "creator": {
    ...
  },
  "owner": {
    ...
  },
  "organization": {
   ...
  }
}
```


Parameter |  Description
--------- | ------- 
`id`      | The unique identifier for this deal **String**
`name`    | The user provided name for the deal **String**
`abbreviation` | 3 letter abbreviation derived from the deal name **String**
`organization_id` | ID for the assocciated organization **String**
`funnel_id` | ID for the funnel this deal is assigned to **String**
`phase_name` | Name for the phase this deal is assigned to **String**
`phase_id`  | ID for the phase this deal is assigned to **String**
`owner_id` | ID the the owner of this deal **String**
`weight` | Weight value for deal. Weights are assigned to phases in the funnel. Used for forecast calculations. **Double**
`status` | Deal forecast status. (None, None Upside, Committed Downside, Committed) **Enum (String)**
`value` | Deal monetary value. Sum of all deal bucket values. **Double**
`weighted_value` | `value` multiplied by `weight`. Used in forecasating. **Double**
`currency` | Abbreviation for the currency for all revenue buckets **Enum (String)**
`bubble_representation_value` | Value used to determine deal bubble size **Double**
`is_favorite` | Is this deal a favorite? **Boolean**
`phase_last_changed` | Timestamp of when the deal phase was last changed. Used for UI activity colouring **Timestamp (ISO 8601)**
`expected_close_date` | User provided expected close date **Timestamp (ISO 8601)**
`creator_id` | The ID for the user that created this deal **String**
`tags` | User provided tags associated with this deal **Array (Object)**
`comments` | User provided comments associated with this deal **String**
`created` | Deal creation timestamp **Timestamp (ISO 8601)**
`modified`| Deal last modified timestamp **Timestamp (ISO 8601)**
`last_modified_by_id` | ID of the user that last modifed this deal **String**
`last_viewed`| Timestamp of the last time this deal was viewed **Timestamp (ISO 8601)**
`latest_activity_in_days` | Number of days since the last activity on deal **Int**
`related_file_ids` | Array of related file IDs associated with this deal **Array (String)**
`generated_files` | Array of gelated file IDs associated with this deal **Array (String)**
`funnel` | Object containing detailed information about the funnel the deal is associated to **Object**
`funnel.id` | ID for the associated funnel
`funnel.created` | Funnel creation timestamp **Timestamp (ISO 8601)**
`funnel.modified`| Funnel last modified timestamp **Timestamp (ISO 8601)**
`funnel.last_modified_by_id` | ID of the user that last modifed this funnel **String**
`funnel.bubble_representation` | The value from deal used to generate bubble size **String**
`funnel.creator_id` | The ID for the user that created this deal **String**
`funnel.name`    | The user provided name for the funnel **String**
`funnel.order` | When using multi-funnel the position this funnel should be shown **Int**
`funnel.owner_id` | ID the the owner of this funnel **String**
`phase` | Object containing detailed information about the phase the deal is associated to **Object**
`phase.id` | ID for the associated funnel
`phase.created` | Phase creation timestamp **Timestamp (ISO 8601)**
`phase.modified`| Phase last modified timestamp **Timestamp (ISO 8601)**
`phase.last_modified_by_id` | ID of the user that last modifed this phase **String**
`phase.creator_id` | The ID for the user that created this phase **String**
`phase.funnel_id` | The ID for the funnel the phase is a member of **String**
`phase.name` | The user provided name for the phase **String**
`phase.hint` | User provided detail for the criteria for a deal to enter this phase **String** 
`default_weight` | The default weight provided to deals when entering this phase **Double**
`order` | The position this phase should be shown in the UI **Int**
`buckets` | Array of objects containg deal bucket values **Objects**
`buckets.value` | The value applied to this bucket **Double**
`buckets.name` | The user provided name for this bucket **String**
`buckets.id` | The unique identifier for this bucket **String**
`custom_fields` | Custom Fields and their values **Object**
`creator` | Object containing detailed information about the deal creator **Object**
`owner` | Object containing detailed information about the deal owner **Object**
`organization` | Object containing detailed information about the organization this deal is related to **Object**

## Get Deal

Returns the deal matching the `deal_id`

### Request URL

`GET https://{CLIENT_ID}.salesseek.net/api/opportunities/{deal_id}`

Parameter |  Description
--------- | ------- 
`id`      | The ID for the deal you'd like to retrieve


## Create Deal

Creates a new deal and then returns the newly created deal.

### Request URL

`POST https://{CLIENT_ID}.salesseek.net/api/opportunities/`


## Update Deal

> A sample request body to change the deal phase

```json
{
  "phase_id": "299a2ae6-4d52-4dfa-b7fe-fe7a3931bb65"
}
```

Updates values of deal by `deal_id`. The resulting deal is returned. 

### Request URL

`PATCH https://{CLIENT_ID}.salesseek.net/api/opportunities/{deal_id}`

Parameter |  Description
--------- | ------- 
`id`      | The ID for the deal you'd like to update

### Request Body

The only fields updated are the one passed on the request body JSON. You can pass any [attribute](#deal-attributes) to update. 



## Delete Deal

Deletes the deal matching the `deal_id`

### Request URL

`DELETE https://{CLIENT_ID}.salesseek.net/api/opportunities/{deal_id}`

### Request Query Parameters

Parameter |  Description
--------- | ------- 
`deal_id` | The unique ID for the deal to be deleted.


## List Deals

> An example request to get the first 50 deals in your SalesSeek (when ordered alphabetically by name) would be:

```http
GET https://example.salesseek.net/api/opportunities?rows=50&start=0&order_by="name asc"
```

> The reponse header contains the following information:

```
Records-Rows: 50
Records-Start: 0
Records-Total: 2000
```

Returns a list of deals from your SalesSeek account.

### Request URL

`GET https://{CLIENT_ID}.salesseek.net/api/opportunities`

### Request Query Parameters

Parameter |  Description
--------- | ------- 
`rows` | The maximum number of deals to be returned.
`start` | The row number to start to retrieve data. (0 for start)
`order_by` | Results are ordered by the provided field name followed by &desc or &asc

<div class="wrap">
  <p class="flash info">
    The response header contains the total number of records. 
  </p>
</div>

### Response Header Parameters

Parameter |  Description
--------- | ------- 
`Records-Rows` | The number of rows returned in this request
`Records-Start` | The start number of rows in this request (out of total)
`Records-Total` | The total number of rows available