# Individual API

<div class="wrap">
  <p class="flash info">
    To add a 'lead' to SalesSeek you should add an Indvidual and set the <code>source</code> field to a valid value. You can read more about this in our <a href="http://support.salesseek.net/general/deals-organizations-and-individuals/what-are-individuals-and-what-are-leads">help centre article</a>
  </p>
</div>

## Individual Attributes

> The JSON encoded response looks like this.

```json
{
  "id": "e6b52466-69d8-41c5-b8c5-ab00de5865ac",
  "photo_url": "https://www.example.com/man.png",
  "first_name": "Aaron",
  "last_name": "Henlow",
  "full_name": "Aaron Henlow",
  "role": "Associate",
  "organization_name": "Riffroute",
  "organization_id": "3d4cd1a4-1a01-445c-84a7-b4d98643b4ce",
  "organization": {
    ...
  }
  "created": "2016-06-23T11:23:59.997891",
  "modified": "2017-01-23T14:16:04.309723",
  "creator_id": "247f5cd0-f6b7-42d3-8b01-47b1e1941fa9",
  "last_modified_by_id": "247f5cd0-f6b7-42d3-8b01-47b1e1941fa9",
  "owner_id": "247f5cd0-f6b7-42d3-8b01-47b1e1941fa9",
  "last_viewed": "2017-07-28T14:53:15.350053",
  "communication": [
    ...
  ],
  "locations": [
    ...
  ],
  "creator": {
    ...
  },
  "owner": {
    ...
  },
  "comments": "",
  "tags": [
  ],
  "related_file_ids": [
  ],
  "is_favorite": false,
  "custom_fields": {
    "a649e75e-cec4-49ad-bd75-0a249270065c": "35000",
    "aa00d7c8-3ab1-4315-929f-341d99e0f62d": "01/20/2017",
    "6163e374-97fa-4f81-b132-5f622ed24a1b": "true",
    "3c7db37f-66a0-4dfb-85cd-f51a5a9d509b": "4b0a7982-1471-499d-bbcb-6022dade415e"
  },
  "unsubscribed_all": false,
  "source_id": "500c679d-b859-4d51-8026-93ad946a5e45",
  "became_lead_date": "2016-06-23T11:24:00.043888",
  "source": {
    ...
  }, 
}
```

Parameter |  Description
--------- | ------- 
`id`      | The unique identifier for this individual **String**
`photo_url` | URL for the individual profile photo **URL**
`first_name` | Individual first name **String**
`last_name` | Individual last name **String**
`full_name` | Individual first name concatenated with last name **String**
`role` | Individual's Job Role **String**
`organization_name` | The name for the [Organization](#organization-api) this individual is linked to **String**
`organization_id` | The unique ID for the [Organization](#organization-api) this individual is linked to **String**
`organization` | Object containing detailed information about [Organization](#organization-api) this individual is linked to **Object**
`created` | Individual creation timestamp **Timestamp (ISO 8601)**
`modified`| Individual last modified timestamp **Timestamp (ISO 8601)**
`creator_id` | The unique ID for the SalesSeek [User](#user-api) that created this individual **String**
`last_modified_by_id` | The unique ID for the SalesSeek [User](#user-api) that last modified this individual **String**
`owner_id` | The unique ID for the SalesSeek [User](#user-api) that has ownership of this individual **String**
`last_viewed` | Individual last viewed timestamp **Timestamp (ISO 8601)**
`communication` | An array containing the different communication methods associated with this individual **Array (Object)**
`locations` | An array containing the different locations associated with this individual **Array (Object)**
`creator` | Object containing detailed information about the [User](#user-api) that created this individual **Object**
`owner` | Object containing detailed information about the [User](#user-api) the has ownership over this individual **Object**
`comments` | User provided comments associated with this individual **String**
`tags` | User provided tags associated with this organization **Array (Object)**
`related_file_ids` | Array of Related File IDs associated with this individual **Array (String)**
`is_favorite` | Is this marked as a favorite? **Boolean**
`custom_fields` | Custom Fields and their values **Object**
`unsubscribed_all` | Set to `true` if this individual has unsubscribed from all [Campaigns](#campaign-api) **Boolean**
`source_id` | The ID for the associated lead source **String**
`became_lead_date` | Timestamp of the individual becoming a lead **Timestamp (ISO 8601)**
`source` | Detailed information about the associated lead source **Object**

## Get Individual

Returns the individual matching the `individual_id`

### Request URL

<span class='verb get'>GET</span> `https://{CLIENT_ID}.salesseek.net/api/individuals/{individual_id}`

### Request Query Parameters

Parameter |  Description
--------- | ------- 
`individual_id` | The unique ID for the individual to be retrieved.


## Create Individual

Creates a new Individual and returns the resulting Individual.

### Request URL

<span class='verb post'>POST</span> `https://{CLIENT_ID}.salesseek.net/api/individuals/`



## Update Individual

> A sample request body to change the individual last name would be:

```json
{
  "last_name": "Seek"
}
```


Updates an Individual by `individual_id` and returns the resulting Individual. 

### Request URL

<span class='verb post'>POST</span> `https://{CLIENT_ID}.salesseek.net/api/individuals/{individual_id}`

### Request Query Parameters

Parameter |  Description
--------- | ------- 
`individual_id` | The unique ID for the individual to be updated.

### Request Body

The only fields updated are the one passed on the request body JSON. You can pass any [attribute](#individual-attributes) to update. 


## Delete Individual

Deletes the individual matching the `individual_id`

### Request URL

<span class='verb delete'>DELETE</span> `https://{CLIENT_ID}.salesseek.net/api/individuals/{individual_id}`

### Request Query Parameters

Parameter |  Description
--------- | ------- 
`individual_id` | The unique ID for the individual to be updated.


## List Individuals

> An example request to get the first 50 individuals in your SalesSeek (when ordered by last modified) would be:

```http
GET https://example.salesseek.net/api/individuals?rows=50&start=0&order_by=modified%20desc
```

> The reponse header contains the following information:

```
Records-Rows: 50
Records-Start: 0
Records-Total: 2000
```

Returns the entire list of individuals from your SalesSeek account. 

### Request URL

<span class='verb get'>GET</span> `https://{CLIENT_ID}.salesseek.net/api/individuals`

### Request Query Parameters

Parameter |  Description
--------- | ------- 
`rows` | The maximum number of organizations to be returned.
`start` | The row number to start to retrieve data. (0 for start)
`order_by` | Results are ordered by the provided field name followed by desc or asc

### Response Header Parameters

Parameter |  Description
--------- | ------- 
`Records-Rows` | The number of rows returned in this request
`Records-Start` | The start number of rows in this request (out of total)
`Records-Total` | The total number of rows available


## Search Individuals

> An example request for individuals where the name contains 'Seek'

```
https://example.salesseek.net/api/organizations?search=seek
```

Provides the the subset of indidivuals where the individual name matches the `search_string`. 

### Request URL

<span class='verb get'>GET</span> `https://{CLIENT_ID}.salesseek.net/api/individuals?search={search_string}`

### Request Query Parameters

Parameter |  Description
--------- | ------- 
`search_string` | Searches for all Organizations containing this string.

<div class="wrap">
  <p class="flash info">
    The set of information returned is reduced to maintain search performance.
  </p>
</div>