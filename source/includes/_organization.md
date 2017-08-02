# Organization API

## Organization Attributes

> The JSON encoded response looks like this.

```json
{
  "id": "84087907-6bf4-437a-aa52-200eb40aa5d2",
  "name": "Chiswick Marketing",
  "abbreviation": "CHM",
  "created": "2017-03-28T08:53:04.914564",
  "modified": "2017-03-28T08:53:04.914564",
  "creator_id": "7a7cb0c5-6222-4c70-8327-217e49f39e1e",
  "last_modified_by_id": "7a7cb0c5-6222-4c70-8327-217e49f39e1e",
  "owner_id": "7a7cb0c5-6222-4c70-8327-217e49f39e1e",
  "last_viewed": "2017-07-28T13:34:53.010019",
  "communication": [
  ],
  "locations": [
  ],
  "creator": {
  },
  "owner": {
  },
  "comments": "This is a comment",
  "tags": [
  ],
  "related_file_ids": [
  ],
  "is_favorite": false,
  "custom_fields": {
    "06bda654-4ca9-4e74-b616-8d3bb53706f0": "63effe75-b52b-4c92-a523-713c2f0e8be9"
  },
}
```


Parameter |  Description
--------- | ------- 
`id`      | The unique identifier for this organization **String**
`name`    | The user provided name for the organization **String**
`abbreviation` | A system generated abbreviation, derived from the organization name **String**
`created` | Organization creation timestamp **Timestamp (ISO 8601)**
`modified`| Organization last modified timestamp **Timestamp (ISO 8601)**
`creator_id` | The unique ID for the SalesSeek user that created this organization **String**
`last_modified_by_id` | The unique ID for the SalesSeek user that last modified this organization **String**
`owner_id` | The unique ID for the SalesSeek user that has ownership of this organization **String**
`last_viewed` | Organization last viewed timestamp **Timestamp (ISO 8601)**
`communication` | An array containing the different communication methods associated with this organization **Array (Object)**
`locations` | An array containing the different locations associated with this organization **Array (Object)**
`creator` | Object containing detailed information about the organization creator **Object**
`owner` | Object containing detailed information about the organization owner **Object**
`comments` | User provided comments associated with this organization **String**
`tags` | User provided tags associated with this organization **Array (Object)**
`related_file_ids` | Array of Related File IDs associated with this organization **Array (String)**
`is_favorite` | Is this marked as a favorite? **Boolean**
`custom_fields` | Custom Fields and their values **Object**


## Get Organization

Returns the unique organization matching the `organization_id`

### Request URL

`GET https://{CLIENT_ID}.salesseek.net/api/organizations/{organization_id}`

### Request Query Parameters

Parameter |  Description
--------- | ------- 
`organization_id`      | The ID for the organization you'd like to retrieve **String**



## Create Organization


Creates a new organization and then returns the newly created organization.

### Request URL

`POST https://{CLIENT_ID}.salesseek.net/api/organizations`



## Update Organization

> A sample request body to change the organization name would be:

```json
{
  "name": "Chiswick Marketing Ltd."
}
```

Updates values of organization by `organization_id`. The resulting organization is returned. 

### Request URL

`PATCH https://{CLIENT_ID}.salesseek.net/api/organizations/{organization_id}`

Parameter |  Description
--------- | ------- 
`id`      | The ID for the organization you'd like to update **String**

### Request Body

The only fields updated are the one passed on the request body JSON. You can pass any [attribute](#organization-attributes) to update. 



## Delete Organization

Deletes the organization matching the `organization_id`

### Request URL

`DELETE https://{CLIENT_ID}.salesseek.net/api/organizations/{organization_id}`

### Request Query Parameters

Parameter |  Description
--------- | ------- 
`organization_id` | The unique ID for the organization to be deleted.



## List Organizations

> An example request to get the first 50 organizations in your SalesSeek (when ordered alphabetically by name) would be:

```http
GET https://example.salesseek.net/api/organizations?rows=50&start=0&order_by="name asc"
```

> The reponse header contains the following information:

```
Records-Rows: 50
Records-Start: 0
Records-Total: 2000
```

Returns a list of organizations from your SalesSeek account.

### Request URL

`GET https://{CLIENT_ID}.salesseek.net/api/organizations`

### Request Query Parameters

Parameter |  Description
--------- | ------- 
`rows` | The maximum number of organizations to be returned.
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


## Search Organizations

> An example request for organizations where the name contains 'example'

```
https://example.salesseek.net/api/organizations?search=example
```

Provides the the subset of organizations where the Organization name matches the `search_string`. 

### Request URL

`GET https://{CLIENT_ID}.salesseek.net/api/organizations?search={search_string}`

### Request Query Parameters

Parameter |  Description
--------- | ------- 
`search_string` | Searches for all Organizations containing this string.

<div class="wrap">
  <p class="flash info">
    The set of information returned is reduced to maintain search performance.
  </p>
</div>