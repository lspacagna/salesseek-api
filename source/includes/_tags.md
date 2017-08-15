# Tags API

> An example response body for a tag would look like this:

```json
{
	"id": "6e9f2fa6-d376-4313-aaea-13dfde3856a4",
	"name": "Renewal",
    "creator_id": "8baadb17-d37e-47f7-b116-0f15c06f297e",
    "created": "2017-05-11T11:32:12.366298",
    "modified": "2017-05-11T11:32:12.366298",
    "last_modified_by_id": "8baadb17-d37e-47f7-b116-0f15c06f297e"
  }
```

## Tags Attributes

Parameter |  Description
--------- | ------- 
`id`      | The unique identifier for this tag **String**
`name` 	  | The name for this tag **String**
`creator_id` | The ID for the user that created the tag **String**
`created` | Tag creation timestamp **Timestamp (ISO 8601)**
`modified` | Tag last modified timestamp **Timestamp (ISO 8601)**
`last_modified_by_id` | The unique ID for the SalesSeek user that last modified this tag **String**






## Create Tag

> An example request body for creating a new tag would look like this:

```json
{
	"name": "Renewal"
}
```

Creates a new tag and then returns the newly created Tag ID.

### Request URL

`POST https://{CLIENT_ID}.salesseek.net/api/tags`






## Update Tag

Updates values of organization by `tag_id`. The resulting tag is returned. 

### Request URL

`PATCH https://{CLIENT_ID}.salesseek.net/api/tags/{tag_id}`

Parameter |  Description
--------- | ------- 
`id`      | The ID for the organization you'd like to update **String**

### Request Body

The only value that can be updated for tags via the API is the Tag `name`. Pass the updated name as a JSON object.






## Delete Organization

Deletes the tag matching the `tag_id`

### Request URL

`DELETE https://{CLIENT_ID}.salesseek.net/api/tags/{tag_id}`

### Request Query Parameters

Parameter |  Description
--------- | ------- 
`tag_id` | The ID for the tag to be deleted.





## List Organizations

> An example request to get all tags in your SalesSeek account (when ordered alphabetically by modified date) would be:

```http
https://example.salesseek.net/api/tags?start=0&rows=-1&order_by=modified%20desc
```

> The reponse header contains the following information:

```
Records-Rows: 50
Records-Start: 0
Records-Total: 2000
```

Returns a list of tags from your SalesSeek account.

### Request URL

`GET https://{CLIENT_ID}.salesseek.net/api/tags`

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
